---
title: "Having trouble adding a skin to aMSN"
date: 2009-07-19
forum: General Help
---

### Post by Anonymous Rain on 2009-07-19
Ok ubuntu people, I am starting to rage. On Windows Vista I could do everything I wanted as Admin, on Ubuntu I can't even add a skin for aMSN without this message coming up. LInk is related.

[IMG]http://i32.tinypic.com/5lnr6q.png[/IMG]
Can anyone help me? I am going insane here.:confused:

---

### Post by Whiffle on 2009-07-19
Oh yes, welcome to the joys of Linux permissions.  They suck at first, but once you understand them, they aren't much of an issue.  


Anyway, you need put your new skins in /home/<yourname>/.amsn/skins, not the the skins folder under /usr/share.

---

### Post by Redundant Username on 2009-07-19
Try running Natilus (file browser with root privileges?)
Try this in the terminal:
```
gksudo natilus
```

---

### Post by themusicalduck on 2009-07-19
Doing anything that is not within your own Home directory (or other paritions/drives) needs root access.

You could either copy the file over to your desktop, extract it there and copy it using the sudo cp command (like "sudo cp ~/Desktop/filename /usr/share/amsn/skins" in a terminal without quotes), or just run the file browser under root by pressing alt+F2 and running gksudo nautilus

---

### Post by Anonymous Rain on 2009-07-19
> **Whiffle said:**
> Oh yes, welcome to the joys of Linux permissions.  They suck at first, but once you understand them, they aren't much of an issue.  


Anyway, you need put your new skins in /home/<yourname>/.amsn/skins, not the the skins folder under /usr/share.

I read that somewhere before, but here's the problem...
[IMG]http://i32.tinypic.com/o19ur.png[/IMG]

---

### Post by Whiffle on 2009-07-19
Yep.  Putting a "." as the first character of a filename or folder name makes it hidden.  If the .amsn folder isn't there, make it.  If you've run amsn though at least once, I'm sure its there.

EDIT: I also highly advice against putting it in /usr/share/  The reason being that if you upgrade something, and that folder gets changed/rewritten/deleted, you'll lose your skins.  They're nice and safe in your home directory.

---

### Post by Anonymous Rain on 2009-07-19
> **Whiffle said:**
> Yep.  Putting a "." as the first character of a filename or folder name makes it hidden.  If the .amsn folder isn't there, make it.  If you've run amsn though at least once, I'm sure its there.

EDIT: I also highly advice against putting it in /usr/share/  The reason being that if you upgrade something, and that folder gets changed/rewritten/deleted, you'll lose your skins.  They're nice and safe in your home directory.

Well how do I display hidden folders or files? I'm a complete newcomer to Ubuntu. I installed it yesterday.

---

### Post by Whiffle on 2009-07-19
> **Anonymous Rain said:**
> Well how do I display hidden folders or files? I'm a complete newcomer to Ubuntu. I installed it yesterday.

Not a problem :) 

View > Show Hidden Files.

---

### Post by Anonymous Rain on 2009-07-19
> **Whiffle said:**
> Not a problem :) 

View > Show Hidden Files.

:oops: Thanks lol. All sorted. Thanks for the help man you have reduced my stress levels by 60% lol.

---

### Post by Arup on 2009-07-19
For hidden files you can follow the advice above or do a quicker ctrl+H, to make it easy for you to copy paste files install nautilus-gksu from the repos, it will give you Widnows explorer like powers, however be aware, you goof up, you hose the system.

---

### Post by Whiffle on 2009-07-19
> **Anonymous Rain said:**
> :oops: Thanks lol. All sorted. Thanks for the help man you have reduced my stress levels by 60% lol.

More than happy to help.  Don't worry, Linux is definitely not windows and it takes some getting used to in order to be comfortable with it.  Ask all the questions you like, that is what this forum is for (but, don't forget about the search function) :)

---

### Post by Anonymous Rain on 2009-07-20
> **Whiffle said:**
> More than happy to help.  Don't worry, Linux is definitely not windows and it takes some getting used to in order to be comfortable with it.  Ask all the questions you like, that is what this forum is for (but, don't forget about the search function) :)

Will do, posted in a fit of rage XD I'll get used to it soon.

---

