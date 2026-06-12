---
title: "Entire hard drive corrupted"
date: 2012-05-12
forum: General Help
---

### Post by Randymanme on 2012-05-12
I can recall now (earlier today I'd forgotten) when Mint 12 first came  out a couple of times when the OS lost Gparted in the middle of an  operation.  I'd have Gparted doing something that, "depending on . . .  this might take a long time.'  And so I'd find something else to do.   Later when I went to see if Gparted was finished, I wouldn't be able to  find it.  The only thing I could assume was that the operation was  finished and Gparted had closed on it's own, or that it had crashed.    But when restarted or shutdown, I'd briefly see the missing Gparted on  the screen (but too late to cancel the reboot or shut down).

Well  over the months since then I made it a point not to use Gparted on  Mint.  But today I'd forgotten why and used Mint 12 to resize my Ubuntu  home partition.  After a long time (say 45 minutes or so) I went to  check on Gparted and I couldn't find it.  When I restarted my computer, I  briefly saw the missing Gparted flash on the screen just before the OS  went off.

After rebooting, Lisa's Gparted showed, the Ubuntu home  partition (299 Gbs) as "unallocated."  So I installed Testdisk,  unearthed Ubuntu's home partition and selected "write."   Testdisk said  I'd have to reboot for the changes to take place.  But after I rebooted,  the grub error message popped up on a  black screen.  After booting a  live cd and invoking Gparted, it showed the entire hard drive as a  dismal gray and marked "unallocated."

I'm presently using a Natty  live cd. Natty's disk utility shows all the former partitions as  intact and when I select "Check Filesystem: check and repair the  filesystem"  they're all "Clean," but Gparted still shows the hard drive  as unallocated.  

Here's a screenshot of the disk utility gui.

And here's another screenshot of a Testdisk window.  It shows all my former partitions just the way I'll like to have them restored.  What do I do now?  How can I get Testdisk to write this to disk?

As always, any and all help would be very much appreciated.  Thanks.

---

### Post by Randymanme on 2012-05-12
Here's the second screenshot:

---

### Post by Randymanme on 2012-05-12
Hey, check out this next screenshot; it's of Ubuntu's home partition as seen under live home on this Natty live dvd!.  I'm feeling rather encouraged right now.  All the OSes and files show up here.  All doesn't seem to be lost.

Now how do I get  all these to uncorrupted??  Any help sure would  be appreciated.  Thank you.
!

---

### Post by carl4926 on 2012-05-12
Have you actually tried copying the data to a backup device?

---

### Post by prshah on 2012-05-12
> **Randymanme said:**
> But after I rebooted,  the grub error message popped up on a  black screen.  After booting a  live cd and invoking Gparted, it showed the entire hard drive as a  dismal gray and marked "unallocated."

From your subsequent posts, it looks like the partition structure has been restored correctly by testdisk, and, indeed the fact that you are able to load your former partitions seems that very little damage is done, if any.

GParted will show a full "unallocated" if it finds any inconsistencies in the partition structre. GRUB may refuse to boot either because the UUID of the boot partition is changed, or GRUB MBR is damaged, or boot partition is not set as active.

You can check these from the live CD. Boot off the live CD, open the terminal, and give the command ```
gksudo gparted
``` Ignore the gparted window that opens up (or close it after it opens). Please post back any error messages that may be present in the terminal.

Next, run the command ```
sudo fdisk -l
``` This will list your partition structure, and errors if any.

Please post back outputs for futher debugging.

I do not think you have lost any data; I believe all you will have to do is re-install grub, but I'd rather you don't try that now, until the above output is analysed.

---

### Post by Randymanme on 2012-05-12
Thank you very much for your willingness to help me.  Here's the output you requested.  Thank you very much.


	  ubuntu@ubuntu:~$ gksudo gparted 
 ====================== 
 libparted : 2.3 
 ====================== 
 Can't have a partition outside the disk! 
 ubuntu@ubuntu:~$ gksudo gparted 
  
 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe90be90b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2294    18426516+   7  HPFS/NTFS
/dev/sda2            2295        2307      104416+   7  HPFS/NTFS
/dev/sda3            2308       19904   141340664+   7  HPFS/NTFS
/dev/sda4           19905      121602   816889185    f  W95 Ext'd (LBA)
/dev/sda5           20687       32147    92055552   83  Linux
/dev/sda6           32148       32898     6024184   82  Linux swap / Solaris
/dev/sda7           32898       71962   313786368   83  Linux
/dev/sda8           71963       75287    26702848   83  Linux
/dev/sda9           75287       76071     6291448   82  Linux swap / Solaris
/dev/sda10          76071       94188   145530876   83  Linux
/dev/sda11          94189       97040    22906880   83  Linux
/dev/sda12          97041      100957    31457280   83  Linux
/dev/sda13         100957      121600   165819392   83  Linux
ubuntu@ubuntu:~$

---

### Post by prshah on 2012-05-12
> **Randymanme said:**
> 
	  ubuntu@ubuntu:~$ gksudo gparted 
 ====================== 
 libparted : 2.3 
 ====================== 
[color=red] Can't have a partition outside the disk! [/color]


There's your error. Somehow, the partition structure is not OK, probably misaligned.

Here's a explanation and small guide to fix the problem: [http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/)

I have run into this error before, however, fixing the problem is not an easy thing; are you sure your partition structure as shown in fdisk -l is correct?

If you are, the the problem is PROBABLY that "/dev/sda6" and "/dev/sda7" are sharing a common cluster ( 32898 ), as are /dev/sda8,9 and 12 (75287, 76071, 100957). However, I am not sure if they are MEANT to share a cluster, but I think not.

In any case, BEFORE you attempt to "fix" this, please take a backup of important files.

I had "fixed" the error, but it was a lot more convoluted than as shown in the link (manually used fdisk in expert mode). Please post back if you want more clarifications.

---

### Post by Randymanme on 2012-05-12
> **prshah said:**
> are you sure your partition structure as shown in fdisk -l is correct?

If you are, the the problem is PROBABLY that "/dev/sda6" and "/dev/sda7" are sharing a common cluster ( 32898 ), as are /dev/sda8,9 and 12 (75287, 76071, 100957). However, I am not sure if they are MEANT to share a cluster, but I think not.


                                   [SIZE=2]Thank you very much for your timely response and suggested link.  I often appreciate it when folks give me a response that contains information from other sources and/or incidental information too.  I much appreciate it.  Thanks.[/SIZE]
  [SIZE=2]
Now that I more carefully scrutinize the partition structure, I'm not so sure.  In fact, no, I don't think that my partition structure as shown in fdisk -l is correct.

I now have a much better appreciation for why Gparted often puts at least a one Mb gap between partitions.  [I'd been trying to get it to not do that only because the Gparted gui doesn't (to me) look as neat with the gaps.]

It seems more likely, now, that when I inadvertently interrupted Gparted's resizing operation, that that wrecked havoc on  my partition structure.  Or maybe I did that myself by placing partitions flush against one another.[/SIZE]
 

 [SIZE=2]I didn't know I could make partitions share a common cluster (are there any situations where I would intentionally want to do that?)[/SIZE]
 

 [SIZE=2]It's my custom to post problems or other requests for advice on more than one forum.  It's also my custom to post the solutions to my threads (verbatim, if I can).[/SIZE]
 

  **[SIZE=2][HughT]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=68644") [/SIZE]**[SIZE=2]on Linux Mint Forums ([http://forums.linuxmint.com/viewtopic.php?f=47&t=101934](http://forums.linuxmint.com/viewtopic.php?f=47&t=101934)) offered this suggestion:[/SIZE]
 

  [[SIZE=2]Re: Entire hard drive corrupted[/SIZE]]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101934#p578678")
  [[COLOR=#000080][IMG]http://forums.linuxmint.com/styles/linux-mint/imageset/icon_post_target.gif[/IMG][/COLOR]]("http://forums.linuxmint.com/viewtopic.php?p=578678#p578678")[SIZE=2]by [/SIZE]**[[SIZE=2]HughT[/SIZE]]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=68644")**[SIZE=2] on Sat May 12, 2012 7:41 am [/SIZE] 
 [SIZE=2]Hi, Pythzor,
I can't explain what has happened to Gparted, but Testdisk is showing all your files, so let's assume they're all okay. If you got a grub error message, then I'm guessing that the Testdisk 'write' operation has somehow corrupted Ubuntu's boot or grub files. You were using Ubuntu's grub? You could try re-installing and repairing either Ubuntu's or Mint's grub as follows:
from a live CD[/SIZE]
 [SIZE=2]Code: [Select     all]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101934#")[/SIZE]     [SIZE=2]sudo     mount /dev/sdXY /mnt[/SIZE]  [SIZE=2]
replace X and Y with the appropriate drive and partition for Ubuntu or Mint boot, depending on your preference.[/SIZE]
 [SIZE=2]Code: [Select     all]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101934#")[/SIZE]     [SIZE=2]sudo     grub-install --root-directory=/mnt /dev/sdX[/SIZE]  [SIZE=2]note - there's a gap between =/mnt and /dev, and no partition number after sdX.
re-boot into Ubuntu or Mint then[/SIZE]
 [SIZE=2]Code: [Select     all]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101934#")[/SIZE]     [SIZE=2]sudo     update-grub[/SIZE]  [SIZE=2]
hope this helps, regards[/SIZE]
 

 [SIZE=2]The partition structure shown on my screenshot of the disk utility isn't quite correct with the free space at the end of the disk – that wasn't there following the interrupted Gparted resizing.[/SIZE]
 

 [SIZE=2]After following HughT's solution,  what I end up with is a grub menu that shows all my previous Oses except Oz Unity 2 Onyx 64.  Disk Utility shows a reording of the partition numbering, some of the partitions are different sizes than before (before what, I'm not sure – I don't recall any changes in any partition sizes before my first Testdisk rewrite attempt).  [/SIZE] 
 

 [SIZE=2]For example, the Gparted resizing operation (and I acknowledge that the error wasn't Gparted's, it was Linux Mint 12's) that precipitated this (for me) crisis  was to increase Ubuntu /home from 244 Gb to 299 Gb; now it's 320 Gb.  Gparted still shows the hard drive as "unallocated," but trust me, I can live with that.  Mint 12 is ostensibly damaged although it still boots.
[/SIZE]
 

 [SIZE=2]But overall, I'm just tickled to death – extraordinarily grateful.[/SIZE]

---

