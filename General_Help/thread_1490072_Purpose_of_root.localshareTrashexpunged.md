---
title: "Purpose of /root/.local/share/Trash/expunged ?"
date: 2010-05-21
forum: General Help
---

### Post by mbrigdan on 2010-05-21
In the interest of making an excessively long story (mostly about huge amounts of disk space going into thin air) short, here's what happened:

I discovered the directory: /root/.local/share/Trash/expunged
and found that it contained near 2 million files (nearly 400GB!), that I had previously deleted (from the trash, after saying yes to "delete permanently?"). My question is, what is the purpose of this directory, and how can I stop it from doing this again? (It estimates 16 hours to remove all the files.)

---

### Post by somethingkindawierd on 2010-08-12
I second this question. I was trying to find the source of Ubuntu crying for more hard drive space -- it gave the warning message it was running out. I found that ~/.local/share/trash had gobs of data in it that I had placed in the trash and emptied. 

Why?

---

### Post by smausert on 2010-08-14
I have the same problem with 32G I deleted now showing up in a backup!  Anybody going to answer?

---

### Post by AlphaLexman on 2010-08-14
This is the 'Trash' directory for the 'root' user, are you deleting files as 'root'? Because my /root/.local/share/Trash/ has two dirs: files & info. They were both empty.

It can be dangerous to your system to delete **anything** as root.

---

### Post by WorMzy on 2010-08-14
Why have you been using root's account to delete files in the first place? o.O

Sounds to me like you're all abusers of "gksu nautilus", you should really try to kick that habit.

Just remove the contents of that directory (and the other root trash directories) with

```
sudo -i
```
followed by
```
rm -rf /root/.local/share/Trash/expunged/* /root/.local/share/Trash/files/* /root/.local/share/Trash/info/*
```

Oh, and to get out of sudo -i mode, just type
```
exit
```

---

### Post by somethingkindawierd on 2010-08-14
In my case it's not the trash for root, it's my ~/.local/share/trash directory, which is in my user folder. The root trash folder never gets garbage in it, only my user trash dir.

And no, I don't use root to delete, nor do I use gksu Nautilus.

---

### Post by somethingkindawierd on 2010-08-17
Does this have to do with restarting? Is the share/Trash cleaned (or supposed to be cleaned) on restart?

I ask because I don't have this problem on my laptop, which I restart often. But my desktop, on for weeks at a time between restarts, has this problem often.

---

### Post by smausert on 2010-08-25
I believe you are probably correct.  As near as I can tell the expunged directory will be clear after a restart or two.....  Anyway, mine is now clear.  Without direct action on it by me.  And no, I don't go running around as root user.

---

### Post by ubuntu27 on 2010-10-30
Please visit, comment, and add yourself among affected people on [Bug #422012]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/422012")

---

### Post by lucacerone on 2011-06-20
Hi guys,
I actually have no trouble with the trash folder,
but I'd like to know why it is organized with the expunged,
files and info subfolders.

Reason I'm asking is that I'd like that objects deleted in matlab gui
would go to the trash rather than be deleted permanently (and I guessed
if I move the deleted files in the trash I'd have gained this,
but this hierachy of directory makes me think it might not be a good idea).

Cheers, -Luca

---

### Post by JanC on 2012-09-25
> **lucacerone said:**
> (...) but I'd like to know why it is organized with the expunged,
files and info subfolders.

Reason I'm asking is that I'd like that objects deleted in matlab gui
would go to the trash rather than be deleted permanently (and I guessed
if I move the deleted files in the trash I'd have gained this,
but this hierachy of directory makes me think it might not be a good idea).

I'm not sure where the "expunged" directory is documented, but the "files" & "info" structure is documented in the [FreeDesktop.org Trash specification]("http://standards.freedesktop.org/trash-spec/trashspec-latest.html").

---

