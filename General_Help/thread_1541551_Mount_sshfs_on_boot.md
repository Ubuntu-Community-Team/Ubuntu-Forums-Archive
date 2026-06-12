---
title: "Mount sshfs on boot?"
date: 2010-07-29
forum: General Help
---

### Post by hirolau on 2010-07-29
Hi. I have some documents located at a server.

Currently, to be able to access them i need to mount a it using sshfs.

sshfs [email]user@server.com[/email]:/home/at/server /home/mount

Then it askes me for a password, everything is fine.

Now, is there anyway to make it mount this at boot? And also make it reed the password form a file so i do not have to type it every time?

Thx

---

### Post by prodigy_ on 2010-07-29
You need to use key-based authentication to be able to mount sshfs at boot time, I believe. Read [this HOWTO](http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/). Also read [this HOWTO](https://help.ubuntu.com/community/SSHFS) about how to edit your /etc/fstab.

---

### Post by hirolau on 2010-07-29
Thank you. I do howerer dont have the rights to change settings on the server.

Anyone know if this can be done using something called pam_mount? 
sshfs says it can take password from stdin if i use pam_mount.

Anyone know what it means?

---

