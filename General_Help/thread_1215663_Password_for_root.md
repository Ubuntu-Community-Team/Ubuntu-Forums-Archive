---
title: "Password for root"
date: 2009-07-17
forum: General Help
---

### Post by oldtraveler on 2009-07-17
I have re-installed Ubuntu 9.04 three times, but I can't get an installation that will allow me to get to the root desktop. During the installation I was asked only once for a password.  I use this password to log in as my user name, but whenever I try to log in as root and use the same password I am told that the password is incorrect.  I have even tried to log in as root with no password.  Still no go.

---

### Post by oldos2er on 2009-07-17
Ubuntu disables the root account by default. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cityscape on 2009-07-17
I also need the root password. Any help?

---

### Post by AoSteve on 2009-07-17
This is a safety feature of Ubuntu.   Accessing the root account can be "Dangerous" as you have complete manipulation over everything.   It's possible to do, but unwise if you're not absolutely capable of managing the system.   You could end up roasting some beans that aren't supposed to be roasted leaving you with a bad operating system. 

I'd suggest using gksudo or sudo for applications that you need to run as root.  :)

---

### Post by baseface on 2009-07-17
```
sudo passwd root
```
 
dont run X as root.

---

### Post by jerome1232 on 2009-07-17
Root is locked by default, demonstrating how to unlock it is not allowed on this forum, basically if you have to ask and you can't google the answer to this one, you don't need it.

Here's some information about how to gain root privileges in Ubuntu.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TeoBigusGeekus on 2009-07-17
> **jerome1232 said:**
> demonstrating how to unlock it is not allowed on this forum
I didn't know that - was about ready to post the way.

---

