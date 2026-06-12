---
title: "Help locked out"
date: 2009-11-17
forum: General Help
---

### Post by stonebergftw on 2009-11-17
So everything was fine on my system, then I rebooted.

Now I can't access any settings at all.  Any time I have to click any of the lock icons to make any changes, I get an authentication failure.  I can't install software, I can't do anything.  Has anyone ever seen this?  Help!

[[IMG]http://img264.imageshack.us/img264/2130/screenshotwc.th.png[/IMG]](http://img264.imageshack.us/i/screenshotwc.png/)

---

### Post by hal8000 on 2009-11-17
From your terminal, you have enabled the root user and set a root password.
Make sure that when you are asked for the password you are typing the password of normal user "tim" not the root password.

If you need to type many commands as root
sudo su

(and regular user password) will allow you to do this.

---

### Post by stonebergftw on 2009-11-17
Ugh.

Well, I did a google search and it looks like I mistakenly activated the root account, instead of using sudo.

While logged in as root, I did something, and now I can't use sudo, and I can't log into root anymore (not to mention that I still can't change any of my settings).

Any help is much appreciated. :(

---

