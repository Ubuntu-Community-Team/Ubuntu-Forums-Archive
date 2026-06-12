---
title: "Can not gain root access"
date: 2010-08-29
forum: General Help
---

### Post by s1mp13m4n on 2010-08-29
Hello everyone.  I recently installed Ubuntu 10.04 32bit on my laptop.  I am trying to learn the command line and also install software via the command line.  I type in su and hit enter it asks me for my password and I type that in.  The password fails, why is this?  I am the one who set this up and installed the OS.  Now I am logged in using my normal user account when doing this from the GUI.  What is going on?

---

### Post by Naitsirhc Hsem on 2010-08-29
su logs you in as root for that terminal, it needs the root password.

sudo allows you to run a single command as root using your password, eg: sudo gedit /etc/hostname.

if you want to become root in the terminal for more that 1 command at a time, use su. to change the root password to use su, ```
sudo passwd root
```.  it will ask you for your password and then to type the new root password.

---

### Post by QLee on 2010-08-29
> **s1mp13m4n said:**
> ...
 What is going on?

Indeed, what is going on? I see you joined the forum in 2007 and so I am surprised by your question. The super user doesn't have a password on Ubuntu, admin tasks are done with sudo. Could you really have been using Ubuntu this long and never found this out?

Have a look at this page:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by conradin on 2010-08-29
login as root by typing sudo -i
then the password.

---

### Post by s1mp13m4n on 2010-08-29
I joined the forum back then, but I have been on and off with Linux in general as I find it frustrating.  For example you can not "really" game with it and from the little that I know I can not find Linux eqivilents to software such as AnyDVD, Imgburn, etc I like Linux I really do but it can be a pain to use at times.  You are right, I should know more but somehow I do not.  I even took a Linux class in college but it was little help in the real world.

---

### Post by Smart Viking on 2010-08-29
> **s1mp13m4n said:**
> Linux eqivilents to software such as AnyDVD, Imgburn, etc

Brasero and k3b are two really good image burning programs. :)

---

### Post by s1mp13m4n on 2010-08-29
Yes they are and they work well, but what about a program such as DVDShrink?  :)  Thanks for all this help.  Sometimes i wish Linux while being safe could be easier to use.  For example Tor on Windows is much easier to setup, all point and click, no CLI to deal with and nothing to compile, etc.  That is what I mean by Linux being frustrating.  :)

---

### Post by Naitsirhc Hsem on 2010-08-31
thoggen dvd ripper, best out of all windows and linux programs I have tried

---

### Post by andrewthomas on 2010-08-31
> **s1mp13m4n said:**
>  but what about a program such as DVDShrink?  
K9 Copy

---

