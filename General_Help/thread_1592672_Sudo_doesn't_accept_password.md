---
title: "Sudo doesn't accept password"
date: 2010-10-10
forum: General Help
---

### Post by xxjazzy on 2010-10-10
Hello everyone, I'm a complete ubuntu nub, and I'm having problems with the terminal

I've read through some threads here but the problem I'm having doesn't seem to be the problem others are having.

I just reinstalled 10.04 today after my last installation messed up after a month.

early when I first installed the terminal and sudo were working perfect but now, this is what I'm getting:

[sudo] password for dimebag: 
<password>
Sorry, try again.
[sudo] password for dimebag: 
<password>Sorry, try again.
[sudo] password for dimebag: 
<password>Sorry, try again.
sudo: 3 incorrect password attempts
dimebag@dimebaggery:~$ sudo cat /etc/sudoers
[sudo] password for dimebag: 
<password>
Sorry, try again.
[sudo] password for dimebag: 
<password>
Sorry, try again.
[sudo] password for dimebag: 
metal1234Sorry, try again.
sudo: 3 incorrect password attempts

I tried every solution I saw and nothing works. I've been having a heck of a time trying to install things. But anything you guys suggest will be used and hopefully works.
thanks!

---

### Post by andrewthomas on 2010-10-10
caps lock?
 
num lock?

---

### Post by WorMzy on 2010-10-10
Your sudo password is the same as the one you use to log in. Are you using that?

If you are, then have you messed around with /etc/sudoers recently, or removed yourself from the "admin" group?

You can fix sudoers by following these instructions: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by xxjazzy on 2010-10-10
> **WorMzy said:**
> Your sudo password is the same as the one you use to log in. Are you using that?

If you are, then have you messed around with /etc/sudoers recently, or removed yourself from the "admin" group?

You can fix sudoers by following these instructions: [http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

yes I'm using my same password, and I've viewed that page and I did all of the options and it still won't work. I'm still an admin and I haven't messed with any groups

---

