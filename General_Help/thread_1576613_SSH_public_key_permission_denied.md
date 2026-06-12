---
title: "SSH public key permission denied"
date: 2010-09-17
forum: General Help
---

### Post by rgiles43 on 2010-09-17
Hello Everyone, 

Currently I am having troubles getting my ssh key to work correctly. I have had a desktop crash which has been reformatted to use ubuntu. The key residing in id_rsa.pub has been copied over to the ssh server into the authorized keys of the given user. however When we try to login we get a "permission denied (public key, keyboard-interactive)" error.  below is the debug option:

[EMAIL="jv@ops-desktop:%7E/.ssh"]jv@ops-desktop:~/.ssh[/EMAIL]$ ssh -v jv@x.x.x.x
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to x.x.x.x [x.x.x.x] port 22.
debug1: Connection established.
debug1: identity file /home/jv/.ssh/identity type -1
debug1: identity file /home/jv/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/jv/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'x.x.x.x' is known and matches the RSA host key.
debug1: Found key in /home/jv/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /home/jv/.ssh/id_rsa
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Trying private key: /home/jv/.ssh/identity
debug1: Trying private key: /home/jv/.ssh/id_dsa
debug1: Next authentication method: keyboard-interactive
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: No more authentication methods to try.
Permission denied (publickey,keyboard-interactive).
[EMAIL="jv@ops-desktop:%7E/.ssh"]jv@ops-desktop:~/.ssh[/EMAIL]$ 

Any help for this would be greatly appreciated.

Thanks,

---

### Post by screaminfakah on 2010-09-17
[http://www.google.com/#sclient=psy&hl=en&q=permission+denied+publickey+keyboard-interactive&aq=f&aqi=g1g-m2g-o1&aql=&oq=&gs_rfai=&pbx=1&fp=6c33e009fc0ac8f5](http://www.google.com/#sclient=psy&hl=en&q=permission+denied+publickey+keyboard-interactive&aq=f&aqi=g1g-m2g-o1&aql=&oq=&gs_rfai=&pbx=1&fp=6c33e009fc0ac8f5)

---

### Post by Rocket2DMn on 2010-09-17
Do you still have your original private key on the client? If not, your public key on the server will not match. In this case you should generate a new key pair.

For some help documentation, have a look at these:
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
especially: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by rgiles43 on 2010-09-17
Hello,

I do not have the original private key on the clients desktop. I have generated a new key and have copied over the id_rsa.pub file over to the ssh server inside of the authorized_keys file for the correct user. However still getting a public key permission denied when trying to login. 

The following have been done on the server side also:
=======================================================================================
On the remote computer, ensure that the /etc/ssh/sshd_config contains the following lines, and that they are *uncommented*; 

PubkeyAuthentication yes RSAAuthentication yes[FONT=Verdana]
========================================================================================
Also:
========================================================================================[/FONT]
**Permission denied (publickey)**

 If you're sure you've correctly configured sshd_config, copied your ID, and have your private key in the .ssh directory, and still getting this error: 
  Permission denied (publickey).
  
Chances are, your /home/<user> or ~/.ssh/authorized_keys permissions are too open by OpenSSH standards. You can get rid of this problem by issuing the following commands: 

chmod go-w
 ~/ chmod 700 ~/.ssh
 chmod 600 ~/.ssh/authorized_keys
======================================================================================

however I am unsure about :
To solve, create a folder outside your home. For  example, /etc/<username> and move the authorized_keys file to it.  Then change the line in your /etc/ssh/sshd_config to: 
[FONT=monospace]
[/FONT]
[FONT=monospace][/FONT]AuthorizedKeysFile      /etc/<username>/authorized_keys
Then  
sudo /etc/init.d/ssh restart


Reference:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Help is appreciated

Thanks,

---

### Post by Rocket2DMn on 2010-09-17
First, try restarting ssh on the server.

Also, ensure that the ~/.ssh folder and its files are owned by jv:jv.  Unfortunately I can't find the server that I previously tested key authentication with.  I'll keep looking.

Finally, you may need to disable password authentication on the server as well.  Your ssh client may not be prompting you for the password, but the server may be expecting one.

---

### Post by rgiles43 on 2010-09-21
Hello,

I wanted to Thank everyone for their input on this issue that I was having. I have finally got the keys to work correctly the way that I want.

For me the biggest part was understanding the whole concept. After I read a good article I was able to setup the keys. The important steps I took is making sure that all the permissions are set correctly as the article says and to also make sure that all the files underneath .ssh are owned by the specific user. for example jv:jv. 

drwx------  2 giles3 giles3 4096 2010-09-21 14:25 .ssh


-rw-------  1 giles3 giles3  400 2010-09-21 14:25 authorized_keys
-rw-------  1 giles3 giles3 1743 2010-09-21 14:07 id_rsa
-rw-------  1 giles3 giles3  405 2010-09-21 14:07 id_rsa.pub

Reference article thanks to Rocket2DMn:  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

If you have any questions please let me know as I may be able to help out.

Thanks again,

---

