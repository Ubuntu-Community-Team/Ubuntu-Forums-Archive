---
title: "ex-windows user having problems with permissions"
date: 2010-02-03
forum: General Help
---

### Post by silver_Lantern on 2010-02-03
hey everyone,

i'm a 3rd year college student studying software engineering. i recently got my first IT job, and all the workstations have Ubuntu installed. I'm coming from Windows, so i have a lot to learn. Anyways, here's my problem:

I'm trying to set up some basic websites on an Apache 2 server running on my Linux box. At the moment, I have some really basic html files that I want to load into the /var/www directory. However, for whatever reason, I cannot save my html files. First, I thought it was because I didn't have permission on my account, so I switched to localadmin (i don't know if all Linux distros come with a localadmin account, but i know localadmin has "higher" permissions than, but less that root, of course). Even as localadmin, I could not save my html files!! WTF?! 

does anyone have any suggestions?  CL-based solutions are especially welcome because i'm starting to convert from using only GUIs to mostly CL XD

--Jonathan

---

### Post by audiomick on 2010-02-03
hi.
/var belongs to root, that means you need root privileges to write stuff there.

Logged on as a normal user, if you are using a terminal command to copy / move the stuff, put "sudo" in front of it. You will be asked for the user password, which you wont see when you type it in.

If you are wanting to use the file manager nautilus, start it with
```
gksu nautilus
```
which will start an instance of the file manager with root privileges.

---

### Post by Iowan on 2010-02-03
Some options:
**sudo** the files in with **cp** (copy) or **mv** (move)
Change permissions on the **/var/www ** (not advised)
Add yourself to the **root** group (also probably unwise).
Change the DocumentRoot to point elsewhere. (from [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page)

---

