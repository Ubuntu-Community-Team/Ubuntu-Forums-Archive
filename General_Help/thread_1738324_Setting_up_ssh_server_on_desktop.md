---
title: "Setting up ssh server on desktop"
date: 2011-04-24
forum: General Help
---

### Post by winchendonsprings on 2011-04-24
I'm setting up a ssh server on 10.10(soon to be 11.04) desktop. I have a few questions - 
```
ssh-keygen -t dsa
```  will create a key. 

I then simply attach(cat) that key to the end of the authorized_keys2 file on the remote computer?
That is secure? 
What is the difference between the public and private key?

How do I get the sshd daemon to start at startup? I'd like to run this headless without X starting.


references -
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
and
[https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH](https://help.ubuntu.com/community/SSH/OpenSSH/Advanced?action=show&redirect=AdvancedOpenSSH)

---

### Post by earthpigg on 2011-04-24
hi,

according to [this]("https://wiki.archlinux.org/index.php/Using_SSH_Keys#Copying_the_keys_to_the_remote_server"), the easiest way is to -

```
ssh-copy-id your-login@your-server.org
```

ssh-copy-id also has a man page explaining what, exactly, it automates. ssh is pretty secure by default and, based on this being the default tool to do this, i'd assume it was secure.

> How do I get the sshd daemon to start at startup? I'd like to run this headless without X starting.

are you sure it isn't, already?

```
[chris: ~]$ sudo service ssh start
[sudo] password for chris: 
start: Job is **already running: ssh**
[chris: ~]$ 
```

---

### Post by lithopsian on 2011-04-24
By default the ssh daemon will be started when your machine boots.   If not, you can reinstall the package or manually change your sshd.conf to start on runlevel S.

keygen creates a public/private key pair.  The private key can be used to "sign" any message and the public key can be used to check that the signature is valid.  The public key in this case has no other purpose.  So you keep the private key and you send the public key to anyone who might need to check that you are authentic.

---

### Post by winchendonsprings on 2011-04-24
I am going to have to look into this (ssh-copy-id) because I don't know what to do after running it.

I asked >                               How do I get the sshd daemon to start at startup? I'd like to run this headless without X starting.                       because I really need this to be failsafe. If it starts at boot time, awesome. 

>  keygen creates a public/private key pair.  The private key can be used  to "sign" any message and the public key can be used to check that the  signature is valid.  The public key in this case has no other purpose.   So you keep the private key and you send the public key to anyone who  might need to check that you are authentic.     I get it. 

Side note - I know this doesn't just apply to what we're talking about, but other things as well, But a  key contains other info regarding the interaction along with the really long password. Is there some meta data attached that isn't just in the actual characters? Know what I mean?

---

### Post by winchendonsprings on 2011-04-24
By the way, I posted this question on superuser.com. Check it out for a good breakdown. 

[http://superuser.com/questions/274934/setting-up-ssh-server-on-ubuntu-dektop](http://superuser.com/questions/274934/setting-up-ssh-server-on-ubuntu-dektop)

---

