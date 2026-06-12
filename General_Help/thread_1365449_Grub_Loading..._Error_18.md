---
title: "Grub Loading... Error 18"
date: 2009-12-27
forum: General Help
---

### Post by kirano on 2009-12-27
Hi there,
 
This will be a lengthy intro to the problem, but I figure the more detail the better.
 
So, I started on my main computer with a 1Tb hard drive, with Windows XP installed. I created a new partition on it (creating about a 50:50 split) and installed the Windows 7 RC on the new paritition.
 
Now, I've been using Ubuntu (release 8.12 i think) on my Laptop for about a year now to do some computer programming; mainly C, though that's branched into C++. My final year project at uni revolves around a lot of computer programming and running some quite intensive simulations, which my laptop would probably die trying to run. So I decided that I'd try and install ubuntu on my main computer.
 
I concluded that the easiest way to do this would be to get a second hard drive (512gb) and install ubuntu on that. After some initial troubles ( i vaguely remember having to set up things like the swap partition on the 2nd hard drive manually, and i know i had some problems finding the right drivers for things like my graphics card, but it was back in June 2009 that i did this so my memory is a little fuzzy.)
 
Basically, i did get everything up and running (installed version 9.04). At boot, all i had to do was press F12 (which for my mobo access the boot menu) and then select the hard drive i wished to boot from (either the 512gb or the 1Tb one) and the computer would load up either Ubuntu of one of the Windows OS respectively. I had no problems running this at all.
 
A week ago, I decided to install the retail version I had of Windows 7 (as the Release Candidate would start shutting down my computer in March, demanding me to install a proper version)
 
The Windows 7 installation crashed out, saying that it couldn't find a proper system partition. After poking around online, i concluded the problem was the Ubuntu hard drive; the installation was detecting the Windows XP partition and the now empty partition where the Win7 RC had been but was also detecting the Ubuntu hard drive and partitions. So, I disconnected the Ubuntu hard drive and restarted the installation. It then went through without a hitch.
 
So, after restoring all the data i needed to the new Windows 7 installation, I decided to start being productive with my holiday and do some project work. I reconnected the Ubuntu Hard drive and then started up the computer and accessed the boot menu. This is where the problems started.
 
Normally, when i access the hard disk boot menu it lists three things
CH1: (the name of the Ubuntu hard drive, HD502IJ i think, which is the model no. of the hard drive.)
CH2: (HD103UJ, model no. for Windows hard drive)
Add-In bootable media cards.
 
It still listed CH1, CH2, but gave no name for CH1; the space after CH1 was just blank.
 
I selected it anyway and it began to load grub. And then the title of this post came up!
 
Grub loading...
Error 18
 
I never encountered this before the reinstall of Windows 7; I know that Windows 7 does strange things to boot manager and i can only assume that is the cause of the problem here. I've disconnected the Windows 7 hard drive and tried to boot only from the Ubuntu one: Error 18. I explored some similar posts and can confirm the following...
 
The whole of the 512gb hard disk was used for the Ubuntu installation. The partitions on it are as follows (according to Disk Management while in win7)
454.64GB (active, primary partition), 11.12GB (primary parition)
The latter is my swap partition.
 
I've tried changing the hard disk mode from auto to the three different modes available, none have made a difference.
 
Note that it does, intermittendly, display the model no. of the hard drive after CH1 in the boot menu.
 
Thinking about it more and more, I'm guessing the problem must be to do with the MBR and something Win7 has messed up.
 
Is there anyway i can fix this without having to reinstall Ubuntu?
 
Let me know what additional information you need and i'll provide it as quick as i can.
 
Many thanks,
 
Kirano

---

### Post by TetonsGulf on 2009-12-27
Google is our friend:

Error 18
Error 18: Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

Error 18 on Dual Boot Systems Using a Single Hard Drive
This error often occurs when creating a dual boot system (with Windows) on a single hard disk drive, as in a notebook PC, because the Linux partitions end up being beyond the LBA range. On a large notebook drive you may need to re-install Windows into a smaller primary partition (or resize the partition), then create an extended partition in the unallocated space and create partitions for Linux Root, Linux Swap, and Linux Home, then in the remaining unallocated space create another NTFS partition for Windows. In other words, the Linux partitions must be immediately after the Primary Windows partition so they are still within the LBA range, then you can place additional NTFS or FAT32 partitions after the Linux partitions.

On a 160GB notebook drive, the following gave Error 18:

Primary: 80GB Windows NTFS

Extended: 4GB (FAT32), 50GB (NTFS), 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3).


The following worked:

Primary: 80GB Windows NTFS

Extended: 4GB Linux Root (ext3), 2GB Linux Swap, 20GB Linux home (ext3), 4GB (FAT32), 50GB (NTFS).

It can be somewhat of an annoyance to have the NTFS file system split into two partitions, but it's a workaround.


[Note: the reason for the 4GB FAT 32 partition is that it makes it possible for both Windows and Linux to access that partition, which can be useful when transferring files between the two operating systems.]

Removing GRUB After Error 18 on a Dual Boot System (Windows/Linux) Using a Single Hard Drive
If you install GRUB on a dual boot system with a single hard drive, and get Error 18, you will not be able to boot Windows. To fix this, you need to boot the system from a Windows Recovery CD, select "R" for Repair, and then run "fixmbr" (fix master boot record) at the DOS prompt in C:\windows. This will remove GRUB. If you don't have a recovery CD, you can download floppies from Microsoft for XP, see "http://support.microsoft.com/kb/310994".



Read more: [http://wiki.linuxquestions.org/wiki/GRUB#Removing_GRUB_After_Error_18_on_a_Dual_Boot_System_.28Windows.2FLinux.29_Using_a_Single_Hard_Drive#ixzz0atsJ61O2](http://wiki.linuxquestions.org/wiki/GRUB#Removing_GRUB_After_Error_18_on_a_Dual_Boot_System_.28Windows.2FLinux.29_Using_a_Single_Hard_Drive#ixzz0atsJ61O2)

---

### Post by kirano on 2009-12-27
You're right google is our friend; what you've posted is actually one of the first things i came across while investigating this problem. :D  Believe me when i say that i don't mean to sound ungrateful; i do appreciate you taking the time to post, but what you've posted doesn't really help me...
 
1) I have a 1Tb hard drive which the bios has no trouble booting AT ALL.  Thus it cannot be an issue of the bios being to old to handle a large hard disk.
 
2)I never had this problem BEFORE the reinstall of windows 7 and yet, as far as i'm aware, nothing has changed on the Ubuntu hard drive i.e. there was never a boot partition at the beginning of the disk before (which is how your post suggests i fix the problem) and yet it booted fine up until the win7 reinstall
 
3) I've dealing with dual boots (tri boots to be pedantic) across TWO hard drives, not a single one, which is the other part of your post.
 
Maybe I've missed the point of that help article you copied below, though I have read through it a few times.  I don't really see how i could implement it without a reinstall?  Even if i did create this smaller partition at the beginning of the 2nd hard drive for the kernel to go into, i'd surely have to reinstall Ubuntu to get the kernel INTO that partition?  I'd really rather not do a reinstall if at all possible....

---

### Post by TetonsGulf on 2009-12-27
No problem, my feelings aren't hurt. It's just a natural response anymore to check for a Google listing.

Let's see what we can do...

Are you able to boot the Ubuntu drive if the W7 is not connected?
You ARE still able to boot the W7 drive if Ubuntu is not connected, yes? If the answer to those questions are yes, then I don't think there is a MAJOR issue.

I believe you could get into XP or W7 and do the fixmbr mentioned above and/or maybe a reinstall of GRUB to fix your problems, but you may have to finagle with it to access the drives properly.

Check this out: [http://paranoid-engineering.blogspot.com/2008/12/how-to-restore-grub-after-windows.html](http://paranoid-engineering.blogspot.com/2008/12/how-to-restore-grub-after-windows.html)

Anyone else want to chime in with any alternatives?

---

### Post by oldfred on 2009-12-27
I always look at Herman's page for grub errors
[http://members.iinet.net.au/~herman546/p15.html#18](http://members.iinet.net.au/~herman546/p15.html#18)

He has basically the same info but also mentions a couple of other things:
" I had the same problem. Error 18 and After GRUB. The solution is in the bios.
                                             Put the hard disk detection on auto and not on user. It did the trick for me."                                                                                                                                                                                                            

 * Make sure LBA is enabled in your BIOS.

---

### Post by kirano on 2009-12-28
oldfred - Thanks for you're link.  As far as i'm aware hard drive detection is already on auto; i've actually tried it on all the available settings and none make a difference :(  I'll have to check on the making sure LBA is enabled in my bios though....
 
TetonsGulf - to answer your questions.  No, i can't boot the Ubuntu hard drive at all, whether the windows one is connected to the mobo or not *cries*
Yes, i can boot the windows hard drive, whether the Ubuntu one is connected to the mobo or not.
So that's a No and a Yes; only one yes.  That means it's not a major issue right? :p
By the 'fixmbr mentioned above' you mean the contents of your orginal post?
As for the link you provided on reinstalling grub, i suspect that that is the answer here.  I'll give both that and the contents of your orginal post a run through as soon as i can.  Thankfully, my laptop still works, so if i do end up turning my computer into a large, expensive paper weight, i'll still be able to get in touch!
 
Thanks for everything so far folks!
 
A quick query; would reinstalling Ubuntu fix the problem i.e. set up the partitions and grub correctly?  If I run the risk of messing something up by fixing it manually then i'll just man up and do a reinstall.

---

### Post by TetonsGulf on 2009-12-28
I'm surprised you can't boot the Ubuntu drive at all. If the Ubuntu drive was not connected when you upgraded W7, there should be no changes to it. Weird. If you could get into the Ub drive we could check some other stuff out, but with it not booting at all it makes it harder.

To answer your question, yes, I would try the steps in the first response to fixmbr, but I'd leave both drives connected, What should happen is that GRUB would be removed and would then have to be reinstalled. If it still gives you problems you can always reinstall Ubuntu. Reinstalling Ubuntu will fix the problem, but it's a drastic step to take first!

If you have a lot of data on the Ubuntu drive you want to save you should still be able to get it if you pop in a Live CD and browse the hard drive. Make sure you follow one of the guides online so you are able to boot to all three OS you are using.

Also, if you are intending to install 9.10 Karmic, instead of reinstalling 9.04 Jaunty, some users have experienced problems with dual/tri boots. I had no troubles going 9.10/Vista/XP, but you want to be aware of them.

---

### Post by kirano on 2009-12-28
Well, i'm rather bemused to announce that I am talking to you from my Ubuntu hard drive?!?!

I was about to start what you (TetonsGulf) had suggested when I suddenly decided to fiddle around with my SATA cables.  Don't ask me why, i just had the urge to poke about.  So, I disconnected the Ubuntu cable and plugged it into a different SATA slot.  That didn't work; it still failed to boot, raising an Error 18.  I did notice though that, in the boot menu, it said that the windows 7 hard drive was ch2 M (for Master i'm guessing) and the ubuntu hard drive was ch2 S (for Slave).  I thought this was a bit strange but i did remember noticing when i was fiddling about in the bios yesterday that the ubuntu hard drive was ch1 M (before i moved it) and my cd/dvd drive (which also connected via sata) was set as ch1 Slave.

So i realised that, rather than my six SATA slots being independent, they must be coupled; split into three pairs Ch1, Ch2 and Ch3, with one of the pair being the master (the left most one on the board) and the other being the slave.  I moved the cables about until the two hard drives and the cd drive only occupied Master slots.  Went to boot up and here you have it, Ubuntu works!

Now, this, to me, makes utterly no sense.  The cables have been where they were before for months.  Why would reinstalling Windows 7 suddenly cause the previous configuration of SATA cables to cause a problem?  Why should moving them fix the problem?

This could of course be a fluke.  Whatever is causing the Error 18 could be an intermitent fault; whether that helps with a diagnosis or just makes this that much more bizarre i'm not sure.

At some point i'll pluck up the courage to reboot (as much as i want to, i can't keep my computer on 24/7 for the next 4 months :p ) and i'll find out then whether this was a fluke or whether i have actually fixed it!

---

### Post by kirano on 2009-12-28
Well, having, rebooted a few times, booted into windows and then booted into Ubuntu, it seems the problem is fixed.
Quite how moving SATA cables about fixed the problem, i do not know.  I've looked at the configuration again and, compared to how it was before, when i was having the problem, the only thing that's moved is the Cd/dvd drive cable.  It's now in a slot which i think puts it on its own master boot channel thing, rather than it being the Ch1 Slave, where the Ubuntu hard drive was (and is still) the Ch1 Master.  Reinstalling windows 7 obviously did something, but i really don't know what.
I'll leave it a few days before marking this as solved, just in case there's a relapse back to error 18.
If anyone has an explanation as to how the above might have fixed the problem, i'd be fascinated to hear it.  I could just label it as 'one of those bizarre things' but it would be nice to know what was really going on....

---

### Post by TetonsGulf on 2009-12-28
Glad to see it worked after a couple reboots. 

The only thing that makes immediate sense is that the drives were not attached to the same cables when you did the install as when you tried to boot, but that seems unlikely since you've done this before. 

Hope everything works out and welcome to the Forums!

---

