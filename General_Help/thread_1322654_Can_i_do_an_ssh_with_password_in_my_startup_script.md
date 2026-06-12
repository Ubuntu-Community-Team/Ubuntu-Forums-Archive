---
title: "Can i do an ssh with password in my startup script?"
date: 2009-11-11
forum: General Help
---

### Post by Max Williams on 2009-11-11
I have an ssh call, which requires a password, which i have to do whenever i start up.  Is it possible to put this in /etc/rc.local in such a way that it will send the password through and make the connection without me having to do anything?    Can i do it by setting up the password to be sent through automatically from somewhere else?  (i can't remember how to do this)
 
grateful for any advice
max

---

### Post by tuwe on 2009-11-11
No, but you could use public key authentication. The basic idea is that you generate a key/lock pair, place the lock on the computer you want to ssh to, and keep the key in a safe place and use this to log in instead of a password.

```
ssh-keygen -t dsa
```
Accept all defaults and press enter when asked for a password. Now you have to files: ~/.ssh/id_dsa and ~/.ssh/id_dsa.pub which are key and lock, respectively.
To use it the way you plan to, place the id_dsa file into /root/.ssh/ ```
sudo cp ~/.ssh/id_dsa /root/.ssh/id_dsa
``` and make sure the permissions are set correctly ```
sudo chmod 600 /root/.ssh/id_dsa
```
Then place the lock on the remote computer ```
ssh-copy-id -i ~/.ssh/id_dsa.pub user@remote-system
```

Finally, place your ssh call into /etc/rc.local.
If you want to mount a remote filesystem via sshfs, it might be a better idea to put it into /etc/fstab though.

---

### Post by Max Williams on 2009-11-11
Thanks tuwe - when you say 'lock' you mean the public key and 'key' being the private key, right?

I'll speak to my colleague who 'owns' the server and see if he'll let me do this :)  

thanks!
max

---

### Post by tuwe on 2009-11-11
> **Max Williams said:**
> Thanks tuwe - when you say 'lock' you mean the public key and 'key' being the private key, right?

I'll speak to my colleague who 'owns' the server and see if he'll let me do this :)  

thanks!
max

Exactly, public and private key. I just couldn't remember :)

---

### Post by Bruce H on 2009-11-11
If you can log in, you can put your public key in your remote home folder's .ssh/authorized_keys file. You wouldn't need an administrator to do this. You may wish to consult your colleague anyway, but you do have the power to do it without him or her.

---

