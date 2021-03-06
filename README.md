# libSSH-Authentication-Bypass
Spawn to shell without any credentials by using CVE-2018-10933

Information about CVE-2018-10933 by libSSH : https://www.libssh.org/security/advisories/CVE-2018-10933.txt

Bugfix Release by libSSH : https://www.libssh.org/2018/10/16/libssh-0-8-4-and-0-7-6-security-and-bugfix-release/

## Find the right server with these fingerprints:
https://gist.github.com/0x4D31/35ddb0322530414bbb4c3288292749cc

## Check the version of server that you trying to bypass with testversionofserver.py
If output is 0.7.5, 0.6.*, or lowest then the server is vulnerable.

If isn't then it's probably patched, truncated or not using libSSH.

## Generate Fake SSH Key for bypasswithfakekey.py:
https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

## Create a ssh server that vulnerable to channels OR directly use tool to bypass remote server:

**Important** : "People trying to reproduce libssh bug: the sample code (samplesshd-cb) is not vuln because it has explicit auth handlers. You can open a channel but nothing will happen."

As we can see this section is just for opening channel. You can't spawn to a shell in server that ran by "samplesshd-cb"

**It's just for opening channel. PoCs that i wrote is just for remote hosts.**

Download, uncompress and build the vulnerable libSSH Version : https://www.libssh.org/files/0.7/libssh-0.7.4.tar.xz

And then compile and run libSSH on your own server with ssh.

```
PWD: /libssh-0.7.4/build/examples/samplesshd-cb
./samplesshd-cb --dsakey==yourdsakey 127.0.0.1 --port=2222
```

## libSSH Authentication Bypass with two different tools
**If you have got any fake ssh keys use the second bypasswithfakekey.py**
```
pip install -r requirements.txt
If paramiko==2.0.8 doesn't works try : pip install paramiko==2.4.2

python libsshauthbypass.py --help
python bypasswithfakekey.py --help
```

## Shodan.io libSSH

![](https://i.imgur.com/SWEfcGR.png)
