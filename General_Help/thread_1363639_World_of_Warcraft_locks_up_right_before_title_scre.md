---
title: "World of Warcraft locks up right before title screen"
date: 2009-12-24
forum: General Help
---

### Post by Saronn on 2009-12-24
So, me and my brother want WoW on our Ubuntu computers. My install went fine, nothing bad happened, I'm using 9.04. My brother's using 9.10, and he had the whole "permission denied" problem. We thought that it locking up before the title screen had something to do with that, so we launched WoW using Wow.exe. It still locked up. What's wrong with it? When we launch WoW, the whole intro video shows. After we either press escape to skip it, or we just wait, it still messes up. What's causing the lockups?

---

### Post by Vaphell on 2009-12-24
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-wow-permission-denied.-768225/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-wow-permission-denied.-768225/)

check if permissions are not messed up

---

### Post by Saronn on 2009-12-24
They aren't. I thought I said that :v

---

### Post by Saronn on 2009-12-24
bump

---

### Post by Saronn on 2009-12-25
Another bump... anyone?

---

### Post by Vaphell on 2009-12-25
you haven't said anything about permissions. I am talking about WoW files/directories, maybe some are flagged as readonly and the game can't write to some file and crashes?

```
cd ~/.wine/drive_c/path/to/wow
ls -l
wine WoW.exe

```

what it does:
1) goes to the wow dir (enter proper path)
2) lists all stuff, look for owner (should be set to accname not root) and rwxrwxrwx parts, 1st three define read/write/execute permissions of the user (next group and all) all items should have at least rw enabled
3) launches WoW from command line, you'll see a lot of internal stuff of wine spewed out and there can be some useful info at the moment of crash.

---

### Post by Saronn on 2009-12-27
Everything said the account name. 

This is the terminal output / WowError submission.

[http://pastebin.ca/1728905](http://pastebin.ca/1728905)

For some extremely stupid reason, I can't post here with size tags because it says I have 11 images, but I dunot see any.

Wot dos it meen :v

---

### Post by Vaphell on 2009-12-27
[http://ubuntuforums.org/showthread.php?t=391028](http://ubuntuforums.org/showthread.php?t=391028)
[http://ubuntuforums.org/showthread.php?t=374435](http://ubuntuforums.org/showthread.php?t=374435)

i found these (and few more) by googling 'wow wine error 132'
maybe one of the advices will work.

---

### Post by Saronn on 2009-12-27
I got it, after the last thirty minutes I figured it out.

Thankye! :3

---

