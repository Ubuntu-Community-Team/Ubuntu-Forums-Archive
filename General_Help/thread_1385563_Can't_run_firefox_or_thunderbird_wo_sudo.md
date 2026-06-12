---
title: "Can't run firefox or thunderbird w/o sudo"
date: 2010-01-19
forum: General Help
---

### Post by starsprout on 2010-01-19
Hi-

I just migrated into Ubuntu 9.10 from Windows and moved my mail profiles and also my bookmarks to Thunderbird and Firefox.

I can't see the Mail profiles and messages unless I run "sudo thunderbird" and I can't save or edit bookmarks in Firefox unless I run "sudo firefox".

Probably it's best if I don't run Firefox or Thunderbird as root, eh?

I've tried changing the file permissions for bookmarks.html, but no luck. And haven't even tried to tackle the Thunderbird issue yet.

Any suggestions? Are there other chmod targets I need to adjust?

Thanks!

---

### Post by oldfred on 2010-01-19
These are my default firefox permissions:
fred@fred-laptop:~$ cd .mozilla
[email]fred@fred-laptop:~/.mozill[/email]a$ ls -l
total 12
-rw-r--r-- 1 fred fred  335 2010-01-04 16:00 appreg
drwx------ 3 fred fred 4096 2009-12-21 23:44 extensions
drwxr-xr-x 3 fred fred 4096 2009-12-28 14:40 firefox
[email]fred@fred-laptop:~/.mozill[/email]a$ cd firefox
[email]fred@fred-laptop:~/.mozill[/email]a/firefox$ ls -l
total 16
-rwxr-xr-x 1 fred fred  137 2009-11-20 23:14 profiles.ini
drwxr-xr-x 5 fred fred 4096 2009-12-28 14:07 vkuuxfit.default
[email]fred@fred-laptop:~/.mozill[/email]a/firefox$

---

### Post by starsprout on 2010-01-19
chown'd the files and directories to those same settings, but I'm still unable to save bookmarks when I run firefox unless I'm sudo firefox

What could this be?

[email]shaimin@TZOTZIL:~/.mozill[/email]a$ ls -l
total 12
-rw-r--r-- 1 shaimin shaimin  335 2010-01-18 23:22 appreg
drwx------ 3 shaimin shaimin 4096 2010-01-18 23:04 extensions
drwxr-xr-x 3 shaimin shaimin 4096 2010-01-18 23:04 firefox
[email]shaimin@TZOTZIL:~/.mozill[/email]a$ 

[email]shaimin@TZOTZIL:~/.mozill[/email]a/firefox$ ls -l
total 8
-rwxr-xr-x 1 shaimin shaimin   94 2010-01-18 23:04 profiles.ini
drwxr-xr-x 9 shaimin shaimin 4096 2010-01-19 17:51 s2nir9az.default
[email]shaimin@TZOTZIL:~/.mozill[/email]a/firefox$

---

### Post by L a r r y on 2010-01-19
> **starsprout said:**
> Hi-


I can't see the Mail profiles and messages unless I run "sudo thunderbird" and I can't save or edit bookmarks in Firefox unless I run "sudo firefox".


Thanks!
I wonder if you show hidden files on the View menu and display your homer folder, and check to see who owns the .mozilla-thunderbird and .mozilla hidden folders?

Look at their properties under permissions.  The owner should be your user name - your name, and the group should be your user name.  Owner should have read-write-execute and group and others have none, according to what I see in my 9.04, looking at .nozilla-thunderbird.

I had an issue when I installed the 9.10 where I could not copy in my profiles for the mail, firefox and gftp as well.  So I reinstalled 9.04.  My profiles were from an 8.04 install on a now-dead computer.

If your home directory or the .mozilla* folders have the wrong owner, maybe you will have to sudo chown them to set ownership rights.

When I was experiencing my issue I never thought to try sudo firefox.

By the way, bookmarks.html is no longer used in firefox 3.x to store your bookmarks.  I believe the file is bookmarks.json, but I can't seem to do a find -r for a recursive search to verify my words.

---

### Post by aysiu on 2010-01-19
This should fix it:

**Step 1**
Close Firefox and Thunderbird completely.

**Step 2**
Paste these three commands into the terminal: ```
sudo chown -R fred:fred /home/fred/.mozilla
sudo chown -R fred:fred /home/fred/.mozilla-thunderbird
sudo chown -R fred:fred /home/fred/.thunderbird
```

**Step 3**
_Never_ launch Firefox or Thunderbird with *sudo*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by starsprout on 2010-01-19
> **L a r r y said:**
> I wonder if you show hidden files on the View menu and display your homer folder, and check to see who owns the .mozilla-thunderbird and .mozilla hidden folders?

Look at their properties under permissions.  The owner should be your user name - your name, and the group should be your user name.  Owner should have read-write-execute and group and others have none, according to what I see in my 9.04, looking at .nozilla-thunderbird.

I had an issue when I installed the 9.10 where I could not copy in my profiles for the mail, firefox and gftp as well.  So I reinstalled 9.04.  My profiles were from an 8.04 install on a now-dead computer.

If your home directory or the .mozilla* folders have the wrong owner, maybe you will have to sudo chown them to set ownership rights.

When I was experiencing my issue I never thought to try sudo firefox.

By the way, bookmarks.html is no longer used in firefox 3.x to store your bookmarks.  I believe the file is bookmarks.json, but I can't seem to do a find -r for a recursive search to verify my words.


I'm pretty sure the BASH ls -l results I posted above show the owner and group are "shaimin" and I'm logged in as shaimin so I should be able to run firefox and thunderbird without using sudo

---

### Post by aysiu on 2010-01-19
> **starsprout said:**
> I'm pretty sure the BASH ls -l results I posted above show the owner and group are "shaimin" and I'm logged in as shaimin so I should be able to run firefox and thunderbird without using sudo
That's not enough. You have to have recursive ownership of the folder, not just the top level.

---

### Post by starsprout on 2010-01-19
Ok this fixed it:

sudo chown -R fred:fred /home/fred/.mozilla
sudo chown -R fred:fred /home/fred/.mozilla-thunderbird
sudo chown -R fred:fred /home/fred/.thunderbird
Except it didn't find /home/shaimin/.thunderbird but I see all the problems I just posted about are resolved!

Thanks! Great stuff!!!

---

### Post by aysiu on 2010-01-19
I threw in that last command to be safe. Depending on what build of Thunderbird you have installed, the settings folder could live in .mozilla-thunderbird or .thunderbird.

---

