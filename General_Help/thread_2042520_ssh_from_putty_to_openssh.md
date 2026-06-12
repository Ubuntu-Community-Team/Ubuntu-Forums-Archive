---
title: "ssh from putty to openssh"
date: 2012-08-14
forum: General Help
---

### Post by ArtificialRed on 2012-08-14
This is truly driving me nuts guys, I've been at this practically all evening trying to get this work. I'm new with linux, I've read one tutorial after another and just can't get ssh working.

two computers, one with windows 7 and my linux box with xubuntu. At first I was trying to freenx into the thing but now I'd be happy with ssh. I got as far as the "server refused our key". Apparently an issue with some people was that the home directory is encrypted and you have to move the authorized_keys file outside the home folder, which I did. 

Right now when I try and ssh hostname -p port it comes up with  Permission denied (publickey). I've created the keys on puttygen, edited the authorized_keys file with the new key. I would really like to just start all over with everything but I wouldn't have the slightest clue where to start with that so I'm here hoping someone will know whats going on!

```
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.111 [192.168.1.111] port 8888.
debug1: Connection established.
debug1: identity file /home/dozo/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/dozo/.ssh/id_rsa-cert type -1
debug1: identity file /home/dozo/.ssh/id_dsa type -1
debug1: identity file /home/dozo/.ssh/id_dsa-cert type -1
debug1: identity file /home/dozo/.ssh/id_ecdsa type -1
debug1: identity file /home/dozo/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 0b:9e:84:a9:68:2e:4b:53:ab:49:bb:86:5a:88:82:ca
debug1: Host '[192.168.1.111]:8888' is known and matches the ECDSA host key.
debug1: Found key in /home/dozo/.ssh/known_hosts:3
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/dozo/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/dozo/.ssh/id_dsa
debug1: Trying private key: /home/dozo/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by steeldriver on 2012-08-14
how did you copy the public key from puttygen to the remote host's ~/.ssh/authorized_keys file? 

iirc you need to copy the plain pubkey from the box at the top of the puttygen window (where it says 'Public key for pasting into an OpenSSH authorized_keys file:') - if you use the 'Save public key' button then it saves it in a format that's incompatible with OpenSSH - you can't copy that file to OpenSSH

I presume you've verified it all works with password authentication?

---

### Post by ratcheer on 2012-08-14
Yes, I agree it is a real pain sharing ssh keys between Windows and Linux. I had to do it a few months ago. I'll see if I can find my notes and anything that might help you.

Tim

---

### Post by ArtificialRed on 2012-08-14
> **steeldriver said:**
> how did you copy the public key from puttygen to the remote host's ~/.ssh/authorized_keys file? 

iirc you need to copy the plain pubkey from the box at the top of the puttygen window (where it says 'Public key for pasting into an OpenSSH authorized_keys file:') - if you use the 'Save public key' button then it saves it in a format that's incompatible with OpenSSH - you can't copy that file to OpenSSH

to do this I just copied it from the dialogue box into a google drive file and then pasted it that way.

> 
I presume you've verified it all works with password authentication?Yep, turning off pubkeyauth and passwordauth on lets me log into ssh just fine on the linux box. When I go to the pc and try through putty, It will accept my login but wont accept the password. So even without the public key the windows machine still isn't able to ssh. I can telnet the ip and port and see it running though..

---

### Post by steeldriver on 2012-08-14
so you CANNOT connect from Win7/putty to the OpenSSH/Ubuntu box even using password auth? am I reading that right?

have you tried the verbose option from putty to see why the connection is failing? I just tried it and it looks like -v doesn't do anything in putty.exe but if you have the full Windows installation including plink then open a cmd window and try something like

```
"C:\Program Files (x86)\PuTTY\plink.exe" -v -l *user *-P *port server*
```(obviously adjust for your exe path etc.) - it should give a detailed connection report like
```

Looking up host "xxx.xxx.xxx.xxx"
Connecting to xxx.xxx.xxx.xxx port YYYYY
Server version: SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
Using SSH protocol version 2
We claim version: SSH-2.0-PuTTY_Release_0.62
Doing Diffie-Hellman group exchange
Doing Diffie-Hellman key exchange with hash SHA-256
Host key fingerprint is:
ssh-rsa 2048 XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX
Initialised AES-256 SDCTR client->server encryption
Initialised HMAC-SHA1 client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised HMAC-SHA1 server->client MAC algorithm
Using username "user".
user@xxx.xxx.xxx.xxx's password:
Sent password
Access granted
Opened channel for session
Allocated pty (ospeed 38400bps, ispeed 38400bps)
Started a shell/command
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-22-generic i686)
```

---

### Post by ArtificialRed on 2012-08-14
> **steeldriver said:**
> so you CANNOT connect from Win7/putty to the OpenSSH/Ubuntu box even using password auth? am I reading that right?
Yep your reading it right. Little update, I now can log into ssh from the linux box with the public key. When I ssh ip port it now asks me for the passphrase and then I'm in. 
> 
have you tried the verbose option from putty to see why the connection is failing? 

```
C:\Users\Xxxx\Desktop>plink.exe -v xxx.xxx.xxx.xxx -P 8888
Looking up host "xxx.xxx.xxx.xxx"
Connecting to xxx.xxx.xxx.xxx port 8888
Server version: SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
Using SSH protocol version 2
We claim version: SSH-2.0-PuTTY_Release_0.62
Doing Diffie-Hellman group exchange
Doing Diffie-Hellman key exchange with hash SHA-256
Host key fingerprint is:
ssh-rsa 2048 xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx
Initialised AES-256 SDCTR client->server encryption
Initialised HMAC-SHA1 client->server MAC algorithm
Initialised AES-256 SDCTR server->client encryption
Initialised HMAC-SHA1 server->client MAC algorithm
login as: User@xxx.xxx.xxx.xxx
User@xxx.xxx.xxx.xxx's password:
Sent password
Password authentication failed
Access denied
User@xxx.xxx.xxx.xxx's password:
```

---

### Post by efflandt on 2012-08-15
It may be easier to configure PuTTY to use an openssh key than to plug a PuTTY key into ssh, because potential issues plugging a PuTTY key into .ssh/authorized_keys2 might be if the key wordwraps, and/or has DOS/Win line endings (carriage return, linefeed) instead of Unix line endings (linefeed).

Also ~/.ssh should typically have 700 permission and files in it should have 600 permission for you.  But that may not be an issue here if ssh from Linux works.

---

### Post by steeldriver on 2012-08-15
actually I intended you to enable password auth before trying the plink -v

if you want to jump straight to pubkey auth you will need to give the private key file on the plink command line as well:

```
C:\Users\steeldriver>"C:\Program Files (x86)\PuTTY\plink.exe" -v -l steeldriver -P 22 -i
 "My Documents\lan.ppk" xxx.xxx.xxx.xxx
```I just tried it to a 11.10 box on my LAN and was able to connect successfully. FYI I copied the puttygen public key to the remote host as follows:

- select all
- copy
- paste into notepad++ and save locally on the Windows box e.g. as pubkey_new
- use winSCP to copy pubkey_new to the Ubuntu box
- log into the Ubuntu box using password auth and cat pubkey_new >> ~/.ssh/authorized_keys

Hope this helps

---

### Post by ArtificialRed on 2012-08-15
> **steeldriver said:**
> actually I intended you to enable password auth before trying the plink -v

if you want to jump straight to pubkey auth you will need to give the private key file on the plink command line as well:

```
C:\Users\steeldriver>"C:\Program Files (x86)\PuTTY\plink.exe" -v -l steeldriver -P 22 -i
 "My Documents\lan.ppk" xxx.xxx.xxx.xxx
```I just tried it to a 11.10 box on my LAN and was able to connect successfully. FYI I copied the puttygen public key to the remote host as follows:

- select all
- copy
- paste into notepad++ and save locally on the Windows box e.g. as pubkey_new
- use winSCP to copy pubkey_new to the Ubuntu box
- log into the Ubuntu box using password auth and cat pubkey_new >> ~/.ssh/authorized_keys

Hope this helps

Hey Steeldriver, Looks like I was sort of confused about your last post, I ended up editing my last post with the passwordauth on. I really appreciate the help, I really don't want to give up on this till I find out whats wrong and get it working. 

So your saying it will work ok to put the authorized_keys file in the ~/.ssh/ folder? It doesn't have to be outside the home directory? And also from my post you'll see its saying access denied from the windows machine. I really don't think the public key will be a problem once I can connect with password authentication.. I don't have to forward any ports on my router do I?

---

### Post by steeldriver on 2012-08-15
sorry - my bad, I don't have an encrypted home - I have no idea how you handle that

the 'Access denied' message may be spurious I think, it is *probably* because putty by default attempts GSSAPI auth before anything else - you can turn that off (putty -> connection -> ssh -> auth -> GSSAPI and uncheck the box) but it doesn't actually prevent connection in my experience - it should still allow you to drop to password auth (or pubkey - once you figure it out) and login

the real question at this point is why you get 'Password authentication failed'

---

### Post by ArtificialRed on 2012-08-15
OK I've gotten a little further now, finally I am now able to ssh from windows to the linux box. Here's the catch, I can only ssh into one of the user accounts on the box. for some reason I cant ssh into my normal account or even root with permitrootlogin yes, its giving me access denied. If I add allowusers myusername, I'm right back to not being able to login even from the linux computer. But I just randomly typed the other user name on the box and sure enough I was in.

So whats different between these accounts? Is there some permission I need to set for my main account? What about root? Out of all the accounts I should be able to root in?

---

### Post by steeldriver on 2012-08-15
Above my paygrade I'm afraid - afaik my sshd_config is absolutely standard - whatever comes with openssh-server 1:5.8p1-7ubuntu1

There have been several threads recently about 'strange' ssh problems - someone mentioned possible issues with /etc/shadow?

One thing I did notice while playing around with this is that pubkey auth seems to fail if you don't have appropriate permissions on ~/.ssh (mode 700 seems to keep it happy - not sure what the official value is) - I made my authorized_keys file mode 600 for good measure. This shouldn't affect your password auth though.

---

