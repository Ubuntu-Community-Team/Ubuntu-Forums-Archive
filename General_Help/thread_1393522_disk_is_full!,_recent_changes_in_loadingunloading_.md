---
title: "disk is full???!, recent changes in loading/unloading GUI"
date: 2010-01-29
forum: General Help
---

### Post by w0296094 on 2010-01-29
Have a kubuntu 8.10 installation, with a previous size of 50 GB free space(total size 80 GB).
Installed compiz -fusion, but then unisntalled it because my resolution was to low. After uninstalling compiz, pixels still remained low(sscreen looked big). So I decided to use the following address directions to improve mypixel size:

[http://www.linuxquestions.org/questions/linux-distributions-5/cant-change-resolution-kubuntukde-535107/](http://www.linuxquestions.org/questions/linux-distributions-5/cant-change-resolution-kubuntukde-535107/)

These are instructions to reset the desktop envronment. I did so. When I restarted my computer, I noticed that it asked me to boot from 5 different partitions(I just have one partition though, but it is pointing me to choose from the 5), and I chose the first partition. 
After loading to kubuntu 8.10 and loging in, every time I try to save a file(or download a plugin), my disk looks full. I point to storage media and my disk remains at 100% of its capacity(in other words, full). how do i revert these changes?

---

### Post by oldfred on 2010-01-29
this script will list your system so we all can see what is going on.

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by w0296094 on 2010-02-01
sorry it seems as if i cannot login to the computer(though i the administrator), any suggestions? In other words, i type my username, password, hit enter or click to login in, screen turns on and off, login screen appears again, but i cant seem to log in.

---

### Post by oldfred on 2010-02-01
Use a liveCD and from that you can download the boot_info_script. You may want to copy any important data from your install using the liveCD also if you do not have a recent backup.

---

### Post by w0296094 on 2010-02-02
i guessing I would put a command on the konsole, can i use just any kubuntu CD(should I use the one that I used for installing). 
Does the boot info script download automatically? thanks so far for the feedback.

---

### Post by audiomick on 2010-02-02
Any *buntu CD should do it. The only thing to bear in mind is that 9.10 downloads things to /home/user/downloads, and earlier versions downloaded to the desktop.

I will have a look at oldfred's link. There are a number of links to the boot info script; I don't know which one he linked to.

Edit: Ok, I have looked at Fred's link. The link to download the link there leads to the sourceforge paged where meiefra made the script available. The link at sourceforge will start the download.
I usually link to this
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
for that script. There is a bit more explanation there.

---

### Post by SuperSonic4 on 2010-02-02
> **w0296094 said:**
> i guessing I would put a command on the konsole, can i use just any kubuntu CD(should I use the one that I used for installing). 
Does the boot info script download automatically? thanks so far for the feedback.

Any cd will do.

Also if you can log in using a tty (ctrl+alt+f2 then log in) can youpost the output of ```
df -h
```

---

### Post by w0296094 on 2010-02-02
sorry guys, i had to format my disk due to time issues. thanks for everyone&#347; help though. 
For future reference, this even occured after installing all the updates for kubuntu(meaning my disk got full). Following that, I had played with compiz-fusion to install the cube, later I unistalled it because my graphics were too magnified(desktop looked too big). Following those two events I restarted my computer, and every time i tried to log in(and i could not log in, but not because of the password), it would appear as if I pressed crtl+alt+bacspce (restart xserver)

---

