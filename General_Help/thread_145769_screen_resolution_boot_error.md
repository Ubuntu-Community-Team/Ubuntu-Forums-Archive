---
title: "screen resolution boot error"
date: 2006-03-16
forum: General Help
---

### Post by brentlidstone on 2006-03-16
i just got ubuntu and never used it before today but am an experienced computer techie... after spending about an hour familiarizing myself with the OS using the live CD I installed on the third partition of my hard drive to be able to dual-boot windows xp or ubuntu. The problem is that i set the OS to use a screen resolution that actually does not work. I know this because i tried changing the same settings on the live CD and got the same error. Every time I try to boot ubuntu my monitor gives a "framerate out of sync" error. Is there a way to change my screen resolution settings without reinstalling ubuntu?

---

### Post by bluevoodoo1 on 2006-03-16
Try using (from the command line)...

```
sudo dpkg-reconfigure xserver-xorg
```


EDIT: I misread what you wrote, *if* you can actually get to a command line... try that...

---

### Post by brentlidstone on 2006-03-17
thanks, that worked, but i ran into another problem... i got to the login screen then entered root and the password and it says the administrator cannot login from this screen... but i never set up any user accounts, having planned to login as administrator. Where can i set them up?

---

### Post by bluevoodoo1 on 2006-03-17
[https://wiki.ubuntu.com/AddUsersHowto](https://wiki.ubuntu.com/AddUsersHowto)
I haven't had to add a user, but this seems like it'll work. You'll have to do it from the command line... 

Might also want to read this too... 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

(It is safer to use "sudo <command>" [then, enter your user password] rather than logging in as root. The root account is disabled by default. Later, you might have to add your user to the list of sudoers, which is easy to do. Many people around here strongly disapprove of logging in as root, including myself, using 'sudo' is the way to go.)

---

