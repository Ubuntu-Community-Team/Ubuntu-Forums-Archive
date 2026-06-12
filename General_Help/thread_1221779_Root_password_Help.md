---
title: "Root password Help"
date: 2009-07-24
forum: General Help
---

### Post by Psycho.mario on 2009-07-24
Hi, i wrote a script that changes my password on each boot. This works perfectly, however, it also changes the sudo password. Is there any way i can change my password but not change the root password?

Thanks

---

### Post by t0p on 2009-07-24
I don't think you can change which password sudo will ask for.  It will be your user password.

You could edit the sudo configuration file /etc/sudoers so you can use sudo without needing to supply a password.   Check the **visudo** man page for info on how to edit /etc/sudoers.  And make sure to backup the file first!

If you decide to edit /etc/sudoers, it could be a good idea to enable the root password first.  So if you screw up the file, you can log in as root and replace the messed-up file with the backed-up original.  Use google to see how to set the root password in Ubuntu.  I'd tell you how, but the mods here wouldn't like it.

**Mods**: I know the policy this site has about enabling root login.  But in my opinion, this is a situation which benefit from being able to login as root.

---

### Post by 505 on 2009-07-24
Your password and sudo password are the same. If you prefix a command with sudo you must type your password, not the root password. By default, the root login is disabled, and has no password. You can however set a password for root. However, using sudo from your account, will still need your password.

---

### Post by Psycho.mario on 2009-07-24
Does sudoers also work for gksudo (e.g when starting synaptics)

---

### Post by wojox on 2009-07-24
+1 your sudo password is your user password and not the root password.

---

### Post by kdetech on 2009-07-24
Gksu uses sudo as backend so changes done to sudo cause changes to gksu and kdesu as well

---

### Post by faizan_comsian on 2009-07-24
yah its posible
go to system->administration->user and group
select your account and change it by properties

---

### Post by Psycho.mario on 2009-07-24
I added myself to /etc/sudoers. This works for sudo ing from the command line, however, how can i get it to work for gksudo and gksu? Like when you start synaptics, it asks you for the password. Can i stop it asking me from the sudoers file?
Thanks

---

### Post by Psycho.mario on 2009-07-24
Got it sorted. Thanks for all the help.

---

