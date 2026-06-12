---
title: "Terminal Command For Creating A Launcher"
date: 2009-08-29
forum: General Help
---

### Post by miike24 on 2009-08-29
Hi. I'm creating a small python installation script that will copy files from a "source" directory to, say, the user's desktop (so the end-user can easily run the application/game installed). I'm working on making it create a launcher on the user's desktop. I would use the os.system() command to create the launcher. This is so I can dynamically create it and include the installation directory without the user having to manually edit the launcher and change the directory. How could I go about doing this?
I've tried *ln -s /link/*, but that is for shortcuts. How could I create an actual application launcher, such as the one created when you right click your desktop, and select 'Create Launcher'?

Thanks for any help,
-Mike

---

### Post by DaithiF on 2009-08-29
Hi,
how about you create a launcher on your desktop, then take a look at the file created in a text editor  The file will be <somename>.desktop, and you will see that the structure is quite straightforward ... the most important part is the Exec=xxxx line which is the command to run when the launcher is launched.
So creating a launcher is just a case of creating a file which follows that structure.  No need for os.system, just write out a file with the appropriate contents.

good luck
d

---

### Post by miike24 on 2009-08-29
> **DaithiF said:**
> Hi,
how about you create a launcher on your desktop, then take a look at the file created in a text editor.
d

Why thank you kind sir!

Works like a charm ;)

---

