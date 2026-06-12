---
title: "Freezes during program installations"
date: 2009-11-30
forum: General Help
---

### Post by Xog on 2009-11-30
Whenever I try to install any type of software in ubuntu, the system locks up and all the windows turn grey, then after a few minutes they come back to normal, then repeats. A few moments ago I was changing up my video drivers to see if it solved one of my video problems, and it took over an hour to install! Other than this, the computer runs smoothly, but I'm always getting these errors when scanning for viruses (this was done as a control test), downloading or installing something:

[http://img39.imageshack.us/img39/1645/screenshot1th.png](http://img39.imageshack.us/img39/1645/screenshot1th.png)

Please help me find the cause of these errors and how to stop all this message spam?

My HD has 50+GB of free space and 120GB total.
1.8Ghz dual core pentium with 1GB RAM.

---

### Post by hwttdz on 2009-11-30
It's likely your hard disk is nearing end of life, but it's also possible that you just have a few bad sectors.  It seems that forcing fsck while the drive isn't mounted is the way to proceed.  To do this you need to boot from a live cd and run fsck from that, see reference here

[http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)

good luck.  Also, I'd suggest looking into SMART hard disk health monitoring to see how your hard disk is managing.

---

### Post by john newbuntu on 2009-11-30
Just to reiterate, system->administration->disk utility.  Then click on "more information" on the right panel.  Choose run self test and check results.

---

### Post by hwttdz on 2009-11-30
Unfortunately there are parts of your disk that cannot be checked while the drive is mounted, so this needs to be done while the drive is not mounted.  But in order to run the test you need an operating system, and the easiest one to come by is that from a live cd.

---

### Post by Xog on 2009-11-30
thanks, i'll check it out

---

### Post by Xog on 2009-11-30
How many bad sectors is a "few"? Also, in the terminal, it's not going above 8.50% but the time still increases. I think I'll leave this on overnight, but please feel free to share your input on the situation.

[IMG]http://img130.imageshack.us/img130/3622/screenshotqt.png[/IMG]

---

### Post by hwttdz on 2009-11-30
Unfortunately that's not a few bad sectors, that qualifies as a failing drive.  Back up your data immediately, and start looking for a new hard disk/machine.  Sorry, wish there was better news to give.

Also, what's the name of that graphical front end to the SMART system?  Looks pretty.

---

### Post by Xog on 2009-11-30
> **hwttdz said:**
> Unfortunately that's not a few bad sectors, that qualifies as a failing drive.  Back up your data immediately, and start looking for a new hard disk/machine.  Sorry, wish there was better news to give.

Also, what's the name of that graphical front end to the SMART system?  Looks pretty.

It came up as soon as I logged in to the LiveCD, it's like when an antivirus program finds a virus, you're notified.

Is it possible to get a hard drive for a laptop? Anything I need to specify when I'm looking for one?

edit: nvm
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4434267&CatId=1277](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4434267&CatId=1277)

Good?

---

### Post by Agent ME on 2009-11-30
The drive really just needs to fit in the laptop (laptop-sized, think that would be 2.5") and have the right type of plug (probably something like SATA) as far as I know.

---

