---
title: "Constant Drive Access + Low Disk Space"
date: 2009-11-20
forum: General Help
---

### Post by ArgentStar on 2009-11-20
I tagged a post on to the end of another thread earlier, but things have got more complicated now.  First, the original post:
> **ArgentStar said:**
> I had this same problem.  Two log files in /var/log were ~18GB each.  Every time I open the log file viewer it crashed - unsurprisingly.  So I deleted them, emptied the wastebasket and rebooted.

Now I get the same message [about Low Disk Space], except those files don't exist.  Every time I reboot/log-in I'm told I've only 950MB space left.  But when I click Examine and see where the files are I get something very odd.  At the top it tells me my total space on the partition is ~50GB, my used space it ~47GB and my free-space ~3GB.  However,in the break down of file distribution below, the files only total ~9.5GB.  

I've searched through the whole file system, nothing is taking up that extra ~40GB, yet I'm getting the Low Disk Space error message and the Disk Utility program tells me 98% of the partition is full.

I have a horrible feeling I'm missing something blindingly obvious, but I'll be damned if I can... err... see it.  Look like the two mega log files have been deleted by this isn't being registered properly for some reason.  I've run fsck at boot and had no luck.

Ubuntu 9.10
Kernel Linux 2.6.31-14-generic
Gnome 2.28.1

Hugely appreciative of any help or advice anyone could offer, please. :)

Now there is constant disk accessing, which is making everything involving disk access sluggish.  There are no processes in the System Monitor eating up CPU, though.  As far as I can tell, it's just disk accessing.

I've done full virus scans with clam, which revealed five virus items, all of which I removed.  Haven't found anything since, but the problem hasn't gone away.  So either there's some other virus I've missed, or those weren't the problem in the first place.  

I'm completely stumped and I'd be eternally grateful for any assistance people may offer. :)

---

### Post by ArgentStar on 2009-11-20
Ah, OK.  The second part of the problem has been fixed.  I remounted a partition that for some reason had failed to mount properly. Now the disk accessing is back to normal, but I'm still stuck with the phantom files.

---

### Post by ArgentStar on 2009-11-20
Oh you have to be kidding me!

Apologies, people.  I am officially retarded.  The two deleted files were in the '/root' trash bin and could only be removed using the command line.  I'm still baffled as to how two 20GB log files managed to spawn, but other than that everything else has been solved.  Typical, I spend hours stressing over the problem alone, and as soon as I ask for help I fix it myself.  Apologies.  

Mods/Admin, feel free to delete.  The only bit that might be useful is reminding people to check the root trash.

---

### Post by dcstar on 2009-11-20
> **ArgentStar said:**
> Oh you have to be kidding me!

Apologies, people.  I am officially retarded.  The two deleted files were in the '/root' trash bin and could only be removed using the command line.  I'm still baffled as to how two 20GB log files managed to spawn, but other than that everything else has been solved.  Typical, I spend hours stressing over the problem alone, and as soon as I ask for help I fix it myself.  Apologies.  

Mods/Admin, feel free to delete.  The only bit that might be useful is reminding people to check the root trash.

You could actually **look** at the log files to see what the messages are.

---

### Post by w1ll1am on 2009-11-20
help me i can not figure out how to make a new thread sorry for posting here but i need help

---

### Post by ArgentStar on 2009-11-21
> **dcstar said:**
> You could actually **look** at the log files to see what the messages are.

That was the first thing I did. :) I did mention that every time I tried to view them the system crashed.  Twice with the Log File Viewer and once with gedit.  After that I couldn't think of another way to view them.  Could've tried nano, I guess.  Is there a text editor that only loads small segments of a file into memory at a time?  That's what I'd need.

---

### Post by ArgentStar on 2009-11-21
> **w1ll1am said:**
> help me i can not figure out how to make a new thread sorry for posting here but i need help

Go to the section in which you wish to create a thread, then click "New thread" button on the left of the page, below the description of the forum section.  For example, in this General Help section it's between:

> **General Help**
All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.

[New thread]

[SIZE="5"][COLOR="Red"]Threads in Forum : General Help[/COLOR][/SIZE]

---

### Post by DeMus on 2009-11-21
> **w1ll1am said:**
> help me i can not figure out how to make a new thread sorry for posting here but i need help

In the attached picture of the forum site you see a button called New thread. Click it, fill in the subject of your thread, choose the OS you are having the problem with and start typing. It's that easy.

---

