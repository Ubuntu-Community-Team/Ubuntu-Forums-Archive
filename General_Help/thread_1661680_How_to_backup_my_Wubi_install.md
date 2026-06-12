---
title: "How to backup my Wubi install?"
date: 2011-01-07
forum: General Help
---

### Post by sandy13an on 2011-01-07
I've used wubi to install ubuntu and dual booting with Windows 7 32-bit..
My Windows 7 is on C Drive and ubuntu is on Drive D(25GB)..

I'm planning to install a fresh Windows 7 64-bit on my C Drive.. How do I backup my ubuntu install.I need to make sure all my Ubuntu data(updates and packages) are still there and my MBR/Bootloader works just like it does now..

I need to backup my Wubi.. Help..!!

---

### Post by dandnsmith on 2011-01-07
That's a really interesting problem - after all, you've installed in a way which thoroughly entangles the 2, and I don't suppose for a minute that the embedded ubuntu filesystem is in a separate partition (else why would you go for wubi).

Best I can think of is copy the complete filesystem content for ubuntu onto a usb external device.
Re-install Windows
Re-install the wubi
Overwrite the ubuntu content with that saved.

That may look comprehensive, but contains pitfalls (to do with the copy process) which I haven't yet thought about (but know about, from past endeavours).

---

### Post by sandy13an on 2011-01-07
Thanx for the reply..!!
Btw Windows7 and Ubuntu are on seperate partitions..

---

### Post by wilee-nilee on 2011-01-07
> **sandy13an said:**
> Thanx for the reply..!!
Btw Windows7 and Ubuntu are on separate partitions..

Not a ideal set up I think your going to have problems. Wubi is not designed to be backed up and reinstalled.

Wubi has some problems already, and was designed as a try out method for actual dual booting into a partition built for a Linux setup.

Yes it is in D which is a different partition then C but it is just a file in Windows.

You might take a look at this thread for reference.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by dandnsmith on 2011-01-07
The different partitions (I must have been effectively asleep to miss that), make it slightly easier.

The obvious next step is to read the thread wilee-nilee points to, and also post the results of running the bootscript (referred to in both places).

---

### Post by Rubi1200 on 2011-01-07
Thank you wilee-nilee for pointing sandy13an in the right direction.

Our forum friend drs305 posted about an article which gives instructions on how to backup a Wubi install:
[http://ubuntuforums.org/showpost.php?p=10304745&postcount=49](http://ubuntuforums.org/showpost.php?p=10304745&postcount=49)

I do not know how well tested this is, but makes for interesting reading.

From the same thread, there is also a tutorial at the end of the first post by bcbc on migrating a Wubi install to a partition on the drive.

---

### Post by dandnsmith on 2011-01-08
> **Rubi1200 said:**
> 
From the same thread, there is also a tutorial at the end of the first post by bcbc on migrating a Wubi install to a partition on the drive.

Thanks for pointing out the FullCircle article (pp10-12).
That procedure sounds like one which has been debugged, even if it doesn't work in all circs.

The tutorial on migration to full partition is [here](http://ubuntuforums.org/showthread.php?t=1519354), incase anyone else looks in vain at the first bcbc post in the megathread on wubi.

HTH

---

### Post by adeee on 2011-01-15
same problem here. i read every post.
 i know wubi is not design for backup. but can i back up my software packages?

becoz now am installing ubuntu sepratly with windows,,.

means window is separate and ubuntu is separate.
so can i backup my software packages? like gparted, kpatiense game, vlc, opera, etc..
 so that i can back my software in first condition.

---

### Post by Rubi1200 on 2011-01-15
If you are planning on separate partitions for Windows and Ubuntu that is a great idea.

I have not tested this method, but it might be what you are looking for:
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

I assume you will need to backup this up to an external media like a USB stick and then place it back on Ubuntu once you set things up.

---

### Post by erelsgl on 2011-02-07
What do you think about the following algorithm:
* boot Windows 
* copy the entire c:\ubuntu folder to an external drive
* format, install Windows
* install wubi
* copy the entire c:\ubuntu folder from the external drive
* boot Ubuntu
?

---

### Post by Rubi1200 on 2011-02-07
> **erelsgl said:**
> What do you think about the following algorithm:
* boot Windows 
* copy the entire c:\ubuntu folder to an external drive
* format, install Windows
* install wubi
* copy the entire c:\ubuntu folder from the external drive
* boot Ubuntu
?

There is actually no need to copy the entire folder. A quick and dirty method would be to just copy the root.disk to a safe location. Then, if something goes wrong, simply copy it back over.

For a separate Windows and Ubuntu install, migrate to a dedicated partition. That way, all the files and settings are saved.

Alternatively, if you just want to save the programs installed, use the fakeroot method:
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

Another method:
[http://ubuntuforums.org/showpost.php?p=9500907&postcount=6](http://ubuntuforums.org/showpost.php?p=9500907&postcount=6)

---

