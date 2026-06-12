---
title: "Environment variables"
date: 2006-03-26
forum: General Help
---

### Post by kpgalligan on 2006-03-26
I'm having a really hard time figuring out where to set environment variables for my machine(s).  In various places I've seen:

.bashrc
.bash_profile
.gnomerc
/etc/profile
/etc/bash.bashrc

I've also seen a number of different suggestions in  different places.  It also seems that different places are ok depending on if you're in a graphical environment, logged in as root, etc.  What I CAN'T find is a clear explanation of where to set variables depending on what you're trying to do that applies to debian/ubuntu/gnome, etc.

In windows it was System > Advanced > Environment Variables.  Then it was either system or user.  That's pretty much it.

I really need some help because I can't seem to sort this out.  Various situations:

1) Running an application from a menu or desktop icon
2) Starting the gnome-terminal and running a program from there
3) Non-graphical (terminal) login
4) Server install

Thanks in advance.  I know this must seem like a question easily googled, but I've spent more time than I would've believed on it.

For example, I have a book that says I should add variables to .bash_profile.  I've been trying that, but even after logging out and back in, they aren't being picked up.  I also had them in /etc/profile, and that didn't work.  Then I read that /etc/profile was only for non-graphical logins.  I'm lost.

---

### Post by arnieboy on 2006-03-26
The **/etc/environment** file. Other profile files require that you use export to set the variables; the environment file doesn't.

---

### Post by Barrakketh on 2006-03-26
Use ~/.bashrc

Put whatever you need at the bottom of the file (just so it's easy to find).

---

