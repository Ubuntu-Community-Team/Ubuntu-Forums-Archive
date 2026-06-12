---
title: "Need Help removing Ubuntu and resizing partition"
date: 2009-10-16
forum: General Help
---

### Post by rdsizzle on 2009-10-16
Hello,

I recently had a friend of mine shrink my windows vista partition inorder to install Ubuntu OS.  Anyways long story short I want to remove Ubuntu Resize the partition to the original size and then do a system restore. I do not want to reinstall Ubuntu. So I am hoping for some guidance. I'm not sure if this is the correct forum to post in but I figured it wouldnt hurt to ask.

Thanks

---

### Post by Bucky Ball on 2009-10-16
Boot from the Live CD, 'Try Ubuntu without changing your system', once at the desktop go to System->Administration->Partition Editor, remove the partitions. You MUST defrag the Windows partition before resizing. Hope that helps.

Just one question: What don't you like about it? You can always ask questions and no question is too dumb in the 'Absolute Beginners' forum ... ;-)

ps: if you don't have a Ubuntu install cd, you can download a bootable Gparted LIVE CD which just has the Partition Editor. Download the ISO from here and burn the disk image to disk:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Windows will not recognise the Ubuntu partitions  (EXT3) so forget that avenue for removal (you may have discovered this already).

---

### Post by razorboy5 on 2009-10-16
u can re partition using gparted on the live CD

oh uninstalling Ubuntu i did a quick google and [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

### Post by mocoloco on 2009-10-16
Sorry to see you go :(.  After you resize the partition you'll also want to have the windows boot loader installed to your MBR (master boot record).  The method depends on your version. For XP I believe you boot from an XP CD and choose the recovery console, then in the console type "fixboot c:".

---

### Post by Bucky Ball on 2009-10-16
Repair from Windows install disk.

```
chkdisk
fixboot
fixmbr
```

---

### Post by rdsizzle on 2009-10-16
I don't need to boot from a CD it was installed in a partition created by shrinking my vista partition by 10GB so I am not sure what you mean by that.

Basically I did a system restore on my computer without using the recovery disks and it fixed a problem where windows would sometimes fail to start but now it is slower then it was before. Unfortunately, I had Ubuntu installed after I did the restore but before I fully realized how much slower my computer was with or without Ubuntu. I also don't really have any use for Ubuntu at this time and am much more comfortable with windows. I only installed it to do basic c++ programming which I later realized was totally unnecessary because there are free c++ compilers available online for vista. Plus I like to game which is how I realized how slow my computer was when I tried to play one of my fav games after taking time off gaming at the beginning of school. I just dont want it right now and can reinstall it later if I change my mind

---

### Post by rdsizzle on 2009-10-16
> **Bucky Ball said:**
> Repair from Windows install disk.

```
chkdisk
fixboot
fixmbr
```


so when I put in the recovery disks will these be options? keep in mind I am not that skilled with this kind of stuff

---

### Post by Bucky Ball on 2009-10-16
> **rdsizzle said:**
> I don't need to boot from a CD it was installed in a partition created by shrinking my vista partition by 10GB so I am not sure what you mean by that.



Well how do you suggest removing the EXT3 partitions when you don't have any software that recognises them?? That's what I am talking about if you are addressing my last post. :-k

---

### Post by rdsizzle on 2009-10-16
Ok so I use the bootable Gparted live cd. so I Boot from this cd and remove the Ubuntu partition thereby deleting everything that was within it?

---

### Post by Mr. Picklesworth on 2009-10-16
> **rdsizzle said:**
> I don't need to boot from a CD it was installed in a partition created by shrinking my vista partition by 10GB so I am not sure what you mean by that.

Basically I did a system restore on my computer without using the recovery disks and it fixed a problem where windows would sometimes fail to start but now it is slower then it was before. Unfortunately, I had Ubuntu installed after I did the restore but before I fully realized how much slower my computer was with or without Ubuntu. I also don't really have any use for Ubuntu at this time and am much more comfortable with windows. I only installed it to do basic c++ programming which I later realized was totally unnecessary because there are free c++ compilers available online for vista. Plus I like to game which is how I realized how slow my computer was when I tried to play one of my fav games after taking time off gaming at the beginning of school. I just dont want it right now and can reinstall it later if I change my mind

The reason it is suggested to boot from a live cd is because a running operating system can not resize or reformat the same partition it is stored on because all file access on that partition must cease (and it must be unmounted), which is, naturally, quite impossible if the software to do that stuff is on that drive. Granted, Windows Vista, as I understand it, has a few neat tricks to work around that sort of thing at least for resizing its partition, but it's still a real puzzle and kind of a hair-raiser.

Therefore, the best route for playing with partitions is to boot from a CD (or a USB flash drive), because that way no files need to be accessed from your hard drive.

So, yes, boot the live cd, delete the partitions Ubuntu is installed on (probably listed as an ext3 and a "linux-swap" partition) and then resize the ntfs one to fill all the available space. You need to do this step, as it doesn't happen automatically. (If you forget, there is also Disk Utility in Windows, somewhere under "Computer Management", wherever that is).

As for the slowing down issue, I should make it clear that Ubuntu *is not* directly causing this. It doesn't mount your Windows partition by default, which means that the files on that disk can not be touched. Unless you explicitly tell it to start reading from the disk, the only thing the software can see is an incomprehensible glob of data.

I think the most likely explanation is that resizing the Windows partition was a shakey process, in which case you will want to run defrag and chkdisk from Windows once the dust is settled.

If you are still looking for an IDE that fits you, I understand Code::blocks is quite good. (Although I don't do C++, so haven't really used it).

---

### Post by PrePenguin on 2009-10-16
If you do not want to save any files just put in the windows CD and re-install using all your HD space if not if your using Vista just download EasyBCD and fix your MBR with it and delete your ubuntu partition in the control panel under Administrative tools then Computer management then disk management in that order. Look at your partitions then right click on the ubuntu partition and just delete then right afterwords right click again and recover it in the menu of the right click. Remember use EasyBCD to fix your MBR(master boot record) First. Good Luck!

---

### Post by Jive Turkey on 2009-10-16
If you haven't started on this yet, good.  These steps should help make this as painless as possible.

[LIST=1]
[*]Boot into windows and back up everything you can't replace to either a CD/DVD, thumb drive, or network share.  There are two types of computer users, those who have never hosed a file system, and those who do backups, resizing your partition can fail resulting in the total loss of the data on you hard disk.
[*]Put in your windows installation disk and reboot your computer.  You may have to temporarily change the bios setting to boot from cd instead of the hard drive.  Later you can change it back.  select the repair from the console option after the windows CD boots.  If your Vista has become slow it is not because you have ubuntu installed on another partition.  The easy answer is (maybe not the best) to reinstall windows completely, deleting all partitions and making one new big one.  Anyway, at the repair console type "fixmbr" then exit and reboot, (taking out the CD).  Now defragment the hard drive.
[*]The next day, when your defragmentation has completed, put in either of the live CDs mentioned above, boot into the live CD environment and in the case of the ubuntu CD open the partition editor program.  Find your hard drive, which will probably look like either "/hda" or "/sda" and look at the different partitions, your windows partition is formatted as ntfs most likely, delete all of the other partitions, resize the ntfs partition to use the entire disk, and hit "apply."  If you're on a laptop, make sure it is plugged in as this may take a while and if your battery dies during this process you will likely lose everything on the partition being resized.
[*]When the resizing operation has finished, reboot, take out the CD when prompted, go back to your bios and set the first boot device to your HDD (optional), then you should load into Vista.  Dont panic if Vista shows a blue screen with text output of the checkdisk operation, this is normal when you have traumatized windows this way.  If the operation failed, you can thank me for telling you to make backups first and reinstall Vista using the entire disk.  I seriously doubt that ubuntu is slowing down your Vista so maybe consider the reinstall option as it will give you a clean slate.  You might also consider instead of using the whole disk for vista, making a backup partition to re image vista onto after the fresh install, It can take hours to days to reinstall windows, but it only takes about 20min to an hour to re-image a windows partition.  
[/LIST]
Good luck and happy gaming.

---

### Post by Bucky Ball on 2009-10-16
> **rdsizzle said:**
> Ok so I use the bootable Gparted live cd. so I Boot from this cd and remove the Ubuntu partition thereby deleting everything that was within it?

Yep. Unless you can find another software app that can read EXT3 partitions.

---

### Post by PrePenguin on 2009-10-16
Dont know why everyone telling ya to use the Live CD if you are done with ubuntu throw the damn CD to the side and do as I said above. I have recovered many systems doing just as I stated above.. People sometimes make things more difficulty then they are and you can do all this inside of Vista running ..

---

### Post by mocoloco on 2009-10-16
PrePenguin, it's because rdsizzle wants to keep what's on the drive, not format it all and re-install.  A windows disc won't allow you to just change partitions unless you're actually doing a install.  Booting from a liveCD and using gparted is the easiest way to handle it, without having to burn anything new or reformat and reinstall.

---

### Post by PrePenguin on 2009-10-16
> **mocoloco said:**
> PrePenguin, it's because rdsizzle wants to keep what's on the drive, not format it all and re-install. A windows disc won't allow you to just change partitions unless you're actually doing a install. Booting from a liveCD and using gparted is the easiest way to handle it, without having to burn anything new or reformat and reinstall.
 
 
Alright well i guess i got confused I thought he just wanted to recover the ubuntu partition disk space and not save any of the ubuntu files.. If this is the case he can do exactly as i stated above if the otherway around i guess he can move the files manually then do as i stated it keeps you from doing a reformat and reinstall of windows and recovers the MBR and the disk space used by ubuntu.. So if i misunderstood I appologise.

---

### Post by Bucky Ball on 2009-10-16
Anybody out there? A Windows install WILL NOT recognise the EXT3 partitions, let alone delete them, so PrePenguin, that is why we are suggesting the LIVE CD. :)

---

### Post by PrePenguin on 2009-10-16
> **Bucky Ball said:**
> Anybody out there? A Windows install WILL NOT recognise the EXT3 partitions, let alone delete them, so PrePenguin, that is why we are suggesting the LIVE CD. :)
 
 
You can delete these partitions inside of vista trust me I am sitting here looking at it as i type in my control panel and have done it a 100 times however saving files off its another story.  The install may not however i was trying to get him back to just vista and he could save himself a reformat and a reinstall of windows, but i wasnt realizing he was wanting to save files off that ubuntu partition and for that sorry for any confusion.

---

### Post by rdsizzle on 2009-10-17
So Prepenguin you are saying that my recovery disks will delete both partitions(everything) and then reinstall windows? I was told by a friend my recovery Disks may or may not be able to do this are you certain it will work?

 All the files on my computer I care about are either already on an independent hard drive or will be.

---

### Post by PrePenguin on 2009-10-17
> **rdsizzle said:**
> So Prepenguin you are saying that my recovery disks will delete both partitions(everything) and then reinstall windows? I was told by a friend my recovery Disks may or may not be able to do this are you certain it will work? All the files on my computer I care about are either already on an independent hard drive or can be easily put on it.
 
 
 
rdsizzle the installation disk should give you the option to format that whole drive when its setting up to install Vista yes. However if your files are safe doing what i posted above if Vista is not a mess can save you from having to do a fresh install . I am not sure of the state of your Vista but if its not corrupted or anything this could save you the hassle of reinstalling and updating everything and starting all over.

---

### Post by rdsizzle on 2009-10-17
Arent you originally just saying that I could run the recovery disks and reinstall windows and delete everything that is currently in existence on my hard drive? All I want to do is completely reformat and delete everything and then reinstall using the original disks to original, "factory" condition.
I dont care if I have to update I already did a restore less then a month ago so I may as well do another.

---

### Post by PrePenguin on 2009-10-17
> **rdsizzle said:**
> Arent you originally just saying that I could run the recovery disks and reinstall windows and delete everything that is currently in existence on my hard drive? All I want to do is completely reformat and delete everything and then reinstall using the original disks to original, "factory" condition.
I dont care if I have to update I already did a restore less then a month ago so I may as well do another.
 
 
Yes that is what I am saying when asked do a new install, not a repair of Vista when asked.

---

### Post by rdsizzle on 2009-10-17
[

---

### Post by rdsizzle on 2009-10-17
I should have been more clear from the beginning my intention all along was to do a complete reformatting of the hardrive not just a restore. And I was under the impression I would have to remove Ubuntu before I could do this. My friend said that the recovery disks in laymens terms(all I know) might not work because vista is partitioned. Which is why I was initially asking how to first remove Ubuntu.

---

### Post by Mr. Picklesworth on 2009-10-17
> **rdsizzle said:**
> I should have been more clear from the beginning my intention all along was to do a complete reformatting of the hardrive not just a restore. And I was under the impression I would have to remove Ubuntu before I could do this. My friend said that the recovery disks in laymens terms(all I know) might not work because vista is partitioned. Which is why I was initially asking how to first remove Ubuntu.

Just run the Windows installer, tell it to fill the whole hard drive and Ubuntu will be replaced.

---

