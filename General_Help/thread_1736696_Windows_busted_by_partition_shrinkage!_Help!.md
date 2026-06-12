---
title: "Windows busted by partition shrinkage! Help!"
date: 2011-04-22
forum: General Help
---

### Post by natehall on 2011-04-22
I finally got around to doing a fresh install of Ubuntu. I have (had?) a dual boot computer with Windows and I took a chance and shrunk the Windows 7 partition from the HUGE 120 Gig space it was hogging before. Well sure enough the hog did not like his playpen reduced and the Windows repair disk did not repair it. 

   If I were to wipe the drive clean and run that Windows repair disk would it work or not? (I figured I'd load Ubuntu again after Windows since Windows is touchy about such things ). I paid my Windows tax and I'd like to keep it around for the rare times I need it.

---

### Post by coffeecat on 2011-04-22
A Windows 7 repair disk can only repair an installed system so if you were to wipe your drive, there would be no system to repair. Or am I misunderstanding you?

Did you shrink the Windows partition with Gparted? The repair disc *should* be able to fix Windows. In case you missed a step, have a look at this link:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

It refers to Vista, but Win7 is much of a muchness in this situation. The first part  is about using Gparted but scroll down a bit to get the Windows error and fix.

---

### Post by natehall on 2011-04-22
I tried G-Parted to increase the Windows partition but the program would not do so. A Windows install disk did not come with the computer so I made a Windows repair disk while I had the chance. The repair disk came back with an error that said the partition was too small. I suspect you are right about the repair disk not working on a clean drive but I was hoping somebody who has tried this already could confirm what happens.

---

### Post by Quackers on 2011-04-22
How did you make the repair disc? It sounds like it may be a recovery disc. Is it a dvd? What system is this on?

---

### Post by coffeecat on 2011-04-22
Good point from Quackers. Is that a repair disc or recovery disc? Very different animals.

Also - do you have a recovery partition on that machine? What make/model is it?

---

### Post by natehall on 2011-04-22
It was a Windows repair disk. The kind you make yourself from Windows. The computer is a Dell Inspiron 1545.

---

### Post by natehall on 2011-04-22
If there was a Windows recovery Partition it's gone now. I had two Ubuntu recovery partitions on the Hard drive I did not want anymore so I zeroed them out.

---

### Post by Quackers on 2011-04-22
When you run the repair disc what are you seeing? Are you getting options to restore the C: drive or one to restore the whole computer?
I have no idea what you mean about an Ubuntu recovery partition, unless you mean you had two entries in the grub menu for Ubuntu recovery (one for each installed kernel) perhaps?

---

### Post by natehall on 2011-04-22
From what I can recall it the disk was running fine, Windows splash and all then after awhile an error occurred and it stopped. If there was some way to increase the Windows partition into empty disk space that might work but G-parted is not giving me that option. I'll have to get back to you on what happen exactly as I don't have the disk right now.

---

### Post by coffeecat on 2011-04-22
I'm surprised that Gparted will not allow you to increase the size of the Windows partition. When you next boot into the live CD take a screenshot of the Gparted window and post it. That might give us a clue as to why not.

---

### Post by natehall on 2011-04-23
It is a Windows 7 repair Disk. It's a DVD but it is showing that it holds only 181 Megabytes. I don't think a full Windows will fit into such a small space! The G-parted image will have to wait until Monday when I have Internet access again.

---

### Post by Mark Phelps on 2011-04-25
Sorry I didn't see this sooner ...

But a Repair disk is just that -- it allows you to repair an EXISTING installation, not to install/reinstall Windows.

It's so small because it only contains the SW needed to repair/recreate the boot load files and a few utilities.  It does NOT contain any installation images.

So, unless you have an intact Recovery partition on your drive, Win7 is permanently gone.

---

### Post by natehall on 2011-04-25
Just as well. I hardly ever used it. I shall wait for the latest version of Ubuntu and use the whole drive this time. If it is as buggy and slow as 10.10 I'll go to pure Debian.

---

### Post by Dutch70 on 2011-04-25
Sorry I'm just dropping in here at the end, but if you're going to wait on 11.04. Why not go ahead and install it? I really don't think it's going to change that much over the next 3 days. If you want something more stable though...go with 10.04.2 LTS.

---

### Post by Dutch70 on 2011-04-25
Better yet, if you're having trouble resizing a partition, you may want to open Disk Utility from the live cd/usb and check the SMART data on your disk.

---

### Post by ManyBeers on 2011-04-25
> **natehall said:**
> I finally got around to doing a fresh install of Ubuntu. I have (had?) a dual boot computer with Windows and I took a chance and shrunk the Windows 7 partition from the HUGE 120 Gig space it was hogging before. Well sure enough the hog did not like his playpen reduced and the Windows repair disk did not repair it. 

   If I were to wipe the drive clean and run that Windows repair disk would it work or not? (I figured I'd load Ubuntu again after Windows since Windows is touchy about such things ). I paid my Windows tax and I'd like to keep it around for the rare times I need it.

You should shrink the partitions from within Windows. I did it on my Win7 desktop and I just did it yesterday on my Vista Home Premium netbook to make room for 10.04. It works. On my netbook with a fresh bare install of Vista with pagefile,hibernation, and system restore enabled disc usage was 22gb(on a 250gb drive) roughly. However when I proceeded to shrink the volume I was only
able to shrink it to 120gb. That's because some data was stored way out there. So I downloaded [Perfect Disk]("http://www.raxco.com/products/home-perfectdisk11-home-premium/learn-more") free trial which will get the job done. It has a graphical interface which shows all used blocks on the drive.
Also you need to turn off pagefile,hibernation, and system restore before you consolidate the drive, reboot and then proceed. My Windows partition is now 60gb. Don't blame Windows. [GParted link]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

---

### Post by jagwinn on 2011-04-25
Hello,
I am running WinXP and Ubuntu 10, side-by-side.
When I reduced the size of the Win partition (after Ubuntu installed itself) Win would not start.
I just let the recovery go forward, and the Win was recovered to the new size partition and Ubuntu was not disturbed.

So I did it again, just to get familiar with the process and it behaved just as it did the first time.

I have a restore disk that I bought from RestoreDisk.com for the WinXP and when Win says it is in trouble, I insert it and let it run the restore. Again, it does nothing at all to Ubuntu.

So, don't give up too soon! Try restore.

---

### Post by Dutch70 on 2011-04-25
> **ManyBeers said:**
> 
Also you need to turn off pagefile,hibernation, and system restore before you consolidate the drive, reboot and then proceed. My Windows partition is now 60gb. Don't blame Windows.

Yes, don't blame windows for scattering stuff all over the disk...just spend more money on it and be happy. :wink:

---

### Post by ManyBeers on 2011-04-25
> **Dutch70 said:**
> Yes, don't blame windows for scattering stuff all over the disk...just spend more money on it and be happy. :wink:

He blamed Windows for his own shortcomings. Unfair.

---

