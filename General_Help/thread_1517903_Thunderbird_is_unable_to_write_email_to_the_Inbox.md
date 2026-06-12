---
title: "Thunderbird is unable to write email to the Inbox"
date: 2010-06-25
forum: General Help
---

### Post by rewyllys on 2010-06-25
I've managed to get Thunderbird 3.0.4 into an odd state, and I need advice.  I'm running GNOME under Lucid on a 64-bit machine.

Here's the background:  

Yesterday, I tried to delete a subfolder of my Local Folders directory.  Right-clicking on the subfolder offered the usual menu of options including "Delete", but selecting "Delete" left the folder in place.  In floundering around trying things to solve the problem, I tried opening Thunderbird from the command line, using "sudo thunderbird", following which I succeeded in deleting the recalcitrant subfolder.

Here's the first stage in the problem:

But when I next opened Thunderbird in ordinary mode (i.e., as "ron" not as "superuser"), I discovered that the Inbox was no longer accessible.  Clicking on "Get Mail" yielded only a small wheel-icon that spins, presumably showing activity in progress, without actually finishing by getting mail.  The other various folders seemed to operate normally, in that they showed their contents when clicked on.

I suspected a permissions problem.

What I tried:

I searched the Ubuntu Forums on terms "thunderbird, inbox, inaccessible" and looked at the single thread that resulted, "[Solved] Thunderbird doesn't have permissions to access mail folder?", whose URL is:

[http://ubuntuforums.org/search.php?searchid=74145998](http://ubuntuforums.org/search.php?searchid=74145998)

I applied both of the suggestions in that thread: viz.,

(from ricardo.gloe)
------------------------------------------
Re: Thunderbird doesn't have permissions to access mail folder?
If you have to access the folder and thunderbird through root, then the files/folder are most likely set to root ownership.

If you change the folder/files to your user, they should work.

If I'm not mistaken

Code:

sudo chown -R yourusername:username /folder

"R" option changes all files within the folder

the username repeat separated by ":" changes the user and group
-------------------------------------------------

(from cariboo907)
-------------------------------------------------    
Re: Thunderbird doesn't have permissions to access mail folder?
My ~/.mozilla-thunderbird directory has permissions of 755. I would suggest you open a terminal and type:

Code:

chmod -R 755 ~/.mozilla-thunderbird

to set the proper permissions.
-------------------------------------------

Here's the second stage of the problem:

I followed the advice of both ricardo.gloe and cariboo907.  Now, when I open Thunderbird as "ron", the Inbox is accessible (at least partly), in that I can see the messages in it.  However, clicking on "Get Mail" results in the following error message appearing in a popup:

"Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox."

Before floundering further, and possibly making matters worse, I decided to ask for suggestions.  Has anyone encountered a similar problem of being unable to write to the Inbox?  

Any and all suggestions and comments will be much appreciated.

---

### Post by andrewc6l on 2010-06-25
It really sounds as if your ~/.mozilla-thunderbird directory and probably its contents are still owned by root. What do you see if you do:

```

ls -al ~/.mozilla-thunderbird/*

```

You might also try:
```

ls -alR ~/.mozilla-thunderbird/*

```
but I'm not sure how much that will spew.

At any rate, if you see folders owned by root in there, that's the problem. You will need to chown -R youruser.youruser .mozilla-thunderbird if so.

Also, depending on the version of Thunderbird, you might need to look in ~/.thunderbird as well.

---

### Post by rewyllys on 2010-06-25
> **andrewc6l said:**
> It really sounds as if your ~/.mozilla-thunderbird directory and probably its contents are still owned by root. What do you see if you do:

```

ls -al ~/.mozilla-thunderbird/*

```You might also try:
```

ls -alR ~/.mozilla-thunderbird/*

```but I'm not sure how much that will spew.

At any rate, if you see folders owned by root in there, that's the problem. You will need to chown -R youruser.youruser .mozilla-thunderbird if so.

Also, depending on the version of Thunderbird, you might need to look in ~/.thunderbird as well.

Many thanks.  I had to change ownership of certain files to "ron" in both ~/.mozilla-thunderbird and ~/.thunderbird

In any case, the problem appears now to be solved.:popcorn:

---

### Post by Star88 on 2010-09-07
I can't reply, or write new emails in any form???

I do not understand why the below thread is locked?  Could this be the problem, if so how do I fix it. If not -any advice??
Thanks,


lrwxrwxrwx 1 dad dad      15 2010-09-07 12:25 lock -> 127.0.1.1:+2317

dad@dadstoy:~$ ls -al ~/.mozilla-thunderbird/*
-rw-r--r-- 1 dad dad  335 2010-09-02 20:38 /home/dad/.mozilla-thunderbird/appreg
-rw-r--r-- 1 dad dad   94 2010-09-02 20:38 /home/dad/.mozilla-thunderbird/profiles.ini

/home/dad/.mozilla-thunderbird/0cktobao.default:
total 7251

drwx------ 5 dad dad    1136 2010-09-07 12:27 .
drwx------ 3 dad dad     136 2010-09-02 20:38 ..
-rw-r--r-- 1 dad dad    1373 2010-09-03 15:15 abook.mab
drwxr-xr-x 2 dad dad     368 2010-09-07 12:12 Cache
-rw------- 1 dad dad   65536 2010-09-07 12:25 cert8.db
-rw------- 1 dad dad     170 2010-09-02 20:38 compatibility.ini
-rw-r--r-- 1 dad dad  173607 2010-09-02 20:38 compreg.dat
-rw-r--r-- 1 dad dad    2048 2010-09-07 12:12 cookies.sqlite
-rw-r--r-- 1 dad dad     512 2010-09-07 12:25 cookies.sqlite-journal
-rw-r--r-- 1 dad dad    4096 2010-09-04 23:18 downloads.sqlite
drwxr-xr-x 2 dad dad      48 2010-09-02 20:38 extensions
-rw-r--r-- 1 dad dad     106 2010-09-02 20:38 extensions.cache
-rw-r--r-- 1 dad dad     119 2010-09-02 20:38 extensions.ini
-rw-r--r-- 1 dad dad    1197 2010-09-02 20:38 extensions.rdf
-rw-r--r-- 1 dad dad     117 2010-09-07 12:25 folderTree.json
-rw-r--r-- 1 dad dad 1471488 2010-09-07 12:25 global-messages-db.sqlite
-rw-r--r-- 1 dad dad    1918 2010-09-03 18:02 history.mab
-rw------- 1 dad dad  114541 2010-09-05 16:11 impab.mab
-rw------- 1 dad dad   16384 2010-09-07 12:25 key3.db
-rw-r--r-- 1 dad dad    7247 2010-09-07 12:27 localstore.rdf
lrwxrwxrwx 1 dad dad      15 2010-09-07 12:25 lock -> 127.0.1.1:+2317
drwx------ 5 dad dad     144 2010-09-02 20:47 Mail
-rw-r--r-- 1 dad dad     482 2010-09-02 20:38 mailViews.dat
-rw-r--r-- 1 dad dad    1159 2010-09-07 10:43 mimeTypes.rdf
-rw-r--r-- 1 dad dad    5440 2010-09-07 12:25 panacea.dat
-rw-r--r-- 1 dad dad       0 2010-09-07 12:25 .parentlock
-rw-r--r-- 1 dad dad    2048 2010-09-02 20:38 permissions.sqlite
-rw------- 1 dad dad    2969 2010-09-03 15:37 pluginreg.dat
-rw-r--r-- 1 dad dad   10375 2010-09-07 12:25 prefs.js
-rw------- 1 dad dad   16384 2010-09-07 12:25 secmod.db
-rw-r--r-- 1 dad dad   11264 2010-09-03 15:24 signons.sqlite
-rw-r--r-- 1 dad dad   32768 2010-09-03 15:37 urlclassifier3.sqlite
-rw-r--r-- 1 dad dad     182 2010-09-07 12:25 virtualFolders.dat
-rw-r--r-- 1 dad dad 2278744 2010-09-02 21:20 XPC.mfasl
-rw-r--r-- 1 dad dad  126315 2010-09-02 20:38 xpti.dat
-rw-r--r-- 1 dad dad 3009110 2010-09-07 10:41 XUL.mfasl

---

### Post by amoun on 2011-01-27
Ok an update on this issue from another user.

Well all the files were read and write and the user was ok, but I couldn't delete the .msf files even via the terminal using user or root.

I had to copy the mail folder and delete them on the desktop - redirected thunderbird to that mail folder

Then all i got was an empty inbox with the whizzing circle

once the circle stopped still nothing - I though it was just making the msf files.

Once closed and restarted thunderbird all was ok, so I deleted the original mailbox and replaced it with the ammended.

maybe the problem was that once thunderbird was started it locked the original mailbox.

So only by relieving thunderbird of its link to the mailbox was I able to delete the whole thing.

Ok that's roughly it

taken me hours :(

---

