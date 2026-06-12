---
title: "Making my original partition bigger"
date: 2010-05-21
forum: General Help
---

### Post by alxpenguin on 2010-05-21
Hi! So I installed Jaunty Jackallope and Im really liking it. The thing is when I installed I just let the system do the dual boot partition and I think it assigned Ubuntu a very small amount of hard drive space. Now I want to download some updates and it says it doesnt have enough free space (it only needs like 500 megs so I must have a real small partition). Is there anyway to fix this or do I have to reinstall?? If so, how do I uninstall and do it right?

---

### Post by -humanaut- on 2010-05-21
You can use Gparted to shrink the NTFS partition and grow the Ext4 partition.

---

### Post by alxpenguin on 2010-05-21
Could you guide me through it?

---

### Post by alxpenguin on 2010-05-21
Help plz

---

### Post by alxpenguin on 2010-05-21
I installed gparted but I cant seem to resize the biggest partition or any other one for that matter. I have 97 gig HD and Im not sure I want to only use ubuntu just yet. I was thinking of reinstalling and do something like 60/30. Can i just pop the cd and reinstall??

---

### Post by john newbuntu on 2010-05-21
You need to first understand what OS or data lies in every partition.  A command such as this run on a terminal will help you:
sudo fdisk -l

Also, do not use gparted on mounted partitions.  Run it after booting from a liveCD instead.  Here are some screenshots/examples from gparted documentation.  Please go through these and understand it fully before you delve into moving partitions.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://gparted.sourceforge.net/larry/tips/gfs.htm](http://gparted.sourceforge.net/larry/tips/gfs.htm)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

Before you do any activities that involve shrinking/growing partitions, please backup all your data.  Not trying to scare you here.  But I have seen people who have had problems with disk/power failure etc midway through the process and have lost data as a result.

---

### Post by alxpenguin on 2010-05-21
Ok seems like Im in over my head here lol. What about just reinstalling? can i pop the cd and redo the install and ask it to make a bigger partition?

---

### Post by john newbuntu on 2010-05-21
At this point, I do not know what partition you are shrinking in order to create space.  But if it is windows OS (esp vista or 7), try to shrink it from within windows or at least defragment it.

Edit: At the time of re-install, you need to point it to a partition that is big enough to hold your data, for which you need enough space.  Otherwise you will end up in the same boat.  Could you also please post the output of "sudo fdisk -l" to help us understand the filesystem space allocations?

---

### Post by wilee-nilee on 2010-05-21
> **john newbuntu said:**
> At this point, I do not know what partition you are shrinking in order to create space.  But if it is windows OS (esp vista or 7), try to shrink it from within windows or at least defragment it.

Edit: At the time of re-install, you need to point it to a partition that is big enough to hold your data, for which you need enough space.  Otherwise you will end up in the same boat.  Could you also please post the output of "sudo fdisk -l" to help us understand the filesystem space allocations?
 
+1 do not resize the W7 partition if thats what you have with anything other then the virtual disk manager in W7, Vista I have no idea.

---

### Post by -kg- on 2010-05-21
> **alxpenguin said:**
> Ok seems like Im in over my head here lol. What about just reinstalling? can i pop the cd and redo the install and ask it to make a bigger partition?

Absolutely not!  Glad you asked before starting! :)  I've seen many jump headlong into it and get themselves into more trouble than they're already in! :P

First, you'll need to determine (if you haven't already) how much space the installation was given to work with.  There are two ways to do this.  One would be to open a terminal (Applications/Accessories/Terminal) and issue the command:

```
sudo fdisk -l
```

(That's a lowercase "L") and post it here.  The other method would be to run GPartEd (System/Administration/GPartEd, if you have it already installed, or you could use the [GPartEd Live CD]("http://gparted.sourceforge.net/livecd.php")), and post the snapshot of the partition setup.

If at that point it is obvious that you need to increase the size of your Ubuntu partition (and if your Ubuntu installation is relatively new and you don't have much data to save), then you will likely want to reinstall.  In order to do this, you will need to delete the partitions that your original installation is in.  But you will need to further decrease the size of your Windows partition in order to free up space first.  ***Please*** read at the "How To Partition" pages linked to in my signature block before doing these operations!  It might save you significant grief.

If you need to do so, then it is best that you shrink the size of your Windows partition from Windows itself ***_before_*** trying to reinstall.  As a couple of posters said, boot into Windows (especially if it's Vista or 7), go into "Partition Manager", and shrink your Windows partition as much as you can or to whatever size you want to (8 GB is relative minimum - I would suggest 10, or 20 if possible).

Once this is done, you need to boot either to the Ubuntu Live CD or the GPartEd Live CD and delete the partitions that were created for your current installation. ***_Be sure_*** that you don't delete the Windows partition...just the Ubuntu partitions.  If an Extended partition was created, you will need to delete that, too (again, re: the link in my signature block).

After you have deleted these partitions, then use the Live CD to reinstall Ubuntu.  When you get to the partitioning section of the installer, select "Install to the largest contiguous area" and it will create all the requisite partitions for your installation in the free space that you've created and install Ubuntu into them.

If you have any further questions, post here. :-D

---

### Post by alxpenguin on 2010-05-21
> **-kg- said:**
> Absolutely not!  Glad you asked before starting! :)  I've seen many jump headlong into it and get themselves into more trouble than they're already in! :P

First, you'll need to determine (if you haven't already) how much space the installation was given to work with.  There are two ways to do this.  One would be to open a terminal (Applications/Accessories/Terminal) and issue the command:

```
sudo fdisk -l
```(That's a lowercase "L") and post it here.  The other method would be to run GPartEd (System/Administration/GPartEd, if you have it already installed, or you could use the [GPartEd Live CD]("http://gparted.sourceforge.net/livecd.php")), and post the snapshot of the partition setup.

If at that point it is obvious that you need to increase the size of your Ubuntu partition (and if your Ubuntu installation is relatively new and you don't have much data to save), then you will likely want to reinstall.  In order to do this, you will need to delete the partitions that your original installation is in.  But you will need to further decrease the size of your Windows partition in order to free up space first.  ***Please*** read at the "How To Partition" pages linked to in my signature block before doing these operations!  It might save you significant grief.

If you need to do so, then it is best that you shrink the size of your Windows partition from Windows itself ***_before_*** trying to reinstall.  As a couple of posters said, boot into Windows (especially if it's Vista or 7), go into "Partition Manager", and shrink your Windows partition as much as you can or to whatever size you want to (8 GB is relative minimum - I would suggest 10, or 20 if possible).

Once this is done, you need to boot either to the Ubuntu Live CD or the GPartEd Live CD and delete the partitions that were created for your current installation. ***_Be sure_*** that you don't delete the Windows partition...just the Ubuntu partitions.  If an Extended partition was created, you will need to delete that, too (again, re: the link in my signature block).

After you have deleted these partitions, then use the Live CD to reinstall Ubuntu.  When you get to the partitioning section of the installer, select "Install to the largest contiguous area" and it will create all the requisite partitions for your installation in the free space that you've created and install Ubuntu into them.

If you have any further questions, post here. :-D

Wow I need to do all of this just to reinstall?? This laptop has windows xp, is the partition process the same? Once I delete the partition ubuntu is in, does that uninstall the program? I understand I can do this from the livecd right?

---

### Post by wilee-nilee on 2010-05-21
If you remove the Ubuntu OS You wont be able to boot XP without reloading its bootloader. So you want to defrag XP with a optimizer like auslogics. This particular defragger will go very fast and move everything that can to the beginning of the disc, look in the preferences/programs for the optimizing setting, don,t just click on optimize.
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

Now you want to leave the XP partition large enough so that it is not filled up, and wont be, and isn't damaged by making it smaller. You can use gparted on the live cd to shrink XP but before you reinstall Ubuntu or do anything with it you want to reboot XP and make sure it is working, chances are it will do a chkdsk when you restart it.

If XP is resized and everything is working then you can reinstall Ubuntu in the empty space you will make by deleting it. 

When you originally installed you used the side by side but this time use the install in the largest free space.

The problem you had originally with the side by side is that there is a slider at the bottom of that gui that controls the size of each side, and actually lucky for you, you missed it as resizing a MS partition is always a bit of a risk and has to be done with care and then checked to make sure it is working afterward. 

Also the link in the previous post to dual booting is good to have at your disposal. In all we just want your operating systems to work and be the same as you started with only setup the way you need.

---

### Post by -kg- on 2010-05-22
> **alxpenguin said:**
> Wow I need to do all of this just to reinstall?? This laptop has windows xp, is the partition process the same? Once I delete the partition ubuntu is in, does that uninstall the program? I understand I can do this from the livecd right?

(An additional quote from elsewhere):

> As i stand, the original partition assigned 2 gigs for ubuntu. Do I really need to manage the windows xp partition? Doenst the install do it by itself when I move the bar to assign partition size? will I have a prompt to delete partition?

OK, let's go through this point by point:

> First, you'll need to determine (if you haven't already) how much space the installation was given to work with. 

From the second quote, you have.  I'm assuming that the 2 GB partition you're referencing is your root partition and that there is an additional swap partition of some size.  2 GB is certainly too little for a good installation, and it leads to other questions:

First is, how did you handle partitioning operations in the original installation?  Did you choose to "Install Side By Side?" "Install in Largest Contiguous Free Space" (in which you created the free space by shrinking the Windows partition)? Manual partitioning?  If manual partitioning, did you create a separate "/home" partition?

Secondly, if you used "Install Side By Side," how much unused space did (do) you have in the Windows partition?  Did you defrag that partition *(WELL!)* before installation?  The reason I ask you this is, if there wasn't much room in the XP partition to begin with, the partitioner wouldn't be able to give much room for the Ubuntu installation because it wouldn't be able to shrink it enough.

The best way to get this information (and to enable *us* to see all that information) is to run the command, "sudo fdisk -l" (referenced above) and copy and paste the results here in the thread.  That way, we can see the information we need to see and don't have to ask you point by point.

> In order to do this, you will need to delete the partitions that your original installation is in.

It is necessary to do this, also.  You can do this with an external Partitioning tool (like GPartEd or Ubuntu Live CD) or from the installer (but only if you elect the "Manual Partitioning" selection).  If you elect to install "Side by Side," the partitioner will not automatically erase the old partitions, nor will it reinstall into those old partitions.  It will merely shrink what it can and install, giving you even more of the same problems that you already have.  Those partitions will have to be deleted in any circumstance.

> Once I delete the partition ubuntu is in, does that uninstall the program?

Ubuntu isn't a "program" to be uninstalled (unlike a WUBI installation).  When you delete the partitions the old Ubuntu will be gone.  The portion of GRUB in the MBR will still be there, but since the partition is gone (and along with it, the other portions of GRUB that portion needs that were in that partition), it will not work for anything...even to boot Windows.

> I understand I can do this from the livecd right?

Yes, you can.  The Live CD has GPartEd on it (System/Administration/GPartEd).

> will I have a prompt to delete partition?

You certainly will.  Read the link in my signature block and it will show you how, where, and why, with illustrations.

> ...you will need to further decrease the size of your Windows partition in order to free up space...

This is also necessary, for obvious reasons.  You already don't have enough room for your installation, and in order to free up sufficient space, you must first shrink one or more of your existing partitions.  Since you're going to delete the existing Ubuntu partitions, that leaves the Windows partition (as far as I know at this point...I really need that "fdisk -l" information).

> If an Extended partition was created, you will need to delete that, too

Not *necessarily,* but you *_are_* going to have to deal with it, if it exists.  You are either going to have to delete it, or expand it to encompass the entire available free space (after shrinking the Windows partition).  The installer can install Ubuntu in an Logical partition (which is what a partition created within an Extended partition is), and Ubuntu will run totally from it.

On retrospect, my suggestion would be to expand the Extended partition to encompass the entire free space (again, after further shrinking the Windows partition), and if an Extended partition doesn't exist, I would create one.  This way you'll never run into the 4 Primary partition limit.

> ...boot into Windows (especially if it's Vista or 7), go into "Partition Manager", and shrink your Windows partition as much as you can or to whatever size you want to...

Since you're running XP, using the Windows partition manager is not *absolutely* necessary (with Vista or 7, I would say it is), but it never hurts to use it.  The Windows partition manager is set up to deal specifically with its own partitions.  For XP, though, you can use GPartEd with relatively little danger, as long as there's sufficient room in the partition and you have fairly well defragged it first.

I say, "defrag the partition first" because if not defragged, there is the possibility of files spread all over the hard drive, including the end of it (the "right side" in the partitioner display, which is the end you want to shrink from).  If there are files there, it will take more time to shrink the partition and increase the possibility of data loss.

> After you have deleted these partitions, then use the Live CD to reinstall Ubuntu. When you get to the partitioning section of the installer, select "Install to the largest contiguous area" and it will create all the requisite partitions for your installation in the free space [COLOR="Red"](inside the Extended partition that I mentioned above)[/COLOR] that you've created and install Ubuntu into them.

The above assumes that you just want to install Ubuntu and be done with it.  It will create a root and swap partition, and your /home directory will be included on the root partition as a directory.

Of course, if you want to do this yourself and learn, or if you want to create a separate "/home" and/or other partitions, you can do the installation using the "Manual Partitioning" selection.  I won't go into that here; there are many excellent tutorials on the subject and it is beyond the scope of this thread.

<edit> Darn!  I thought I had posted this earlier, but found I was just previewing it and hadn't posted it yet.  Sorry!

---

### Post by alxpenguin on 2010-05-24
Ok heres what shows up with the command 


Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
       fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
       fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
       fdisk -v                     Obtiene versión de fdisk
El valor de DISCO tiene el formato /dev/hdb o /dev/sda
y el valor de PARTICIÓN tiene el formato /dev/hda7
-u: Obtener Principio y Final en sectores (en lugar de cilindros)
-b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes

Sorry that its in spanish hope you can still get what you need from that

---

### Post by alxpenguin on 2010-05-24
Oh and I installed side by side but i didnt slide the bar to give it more space

---

### Post by -kg- on 2010-05-24
> **alxpenguin said:**
> Ok heres what shows up with the command 


Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
       fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
       fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
       fdisk -v                     Obtiene versión de fdisk
El valor de DISCO tiene el formato /dev/hdb o /dev/sda
y el valor de PARTICIÓN tiene el formato /dev/hda7
-u: Obtener Principio y Final en sectores (en lugar de cilindros)
-b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes

Sorry that its in spanish hope you can still get what you need from that

I'm not too good with Spanish, but what that looks like is the help file or man page for the command.  Did you enter:

```
sudo fdisk -l
```

(The second command listed in the above list) and then enter your password at the prompt?

The easiest way to do that is to copy the above and paste it into the terminal window.  That way there's no typos or wrong letters.  What I (we) need is the "Lista tabla(s) de particiones", which I translate (loosely) as the list of partition tables.  The "-l" in the command is the small letter "L", not the number "1" and there is a space between "fdisk" and "-l".

The results you get should look something like this:

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        9409    74033152    7  HPFS/NTFS
/dev/sda3            9409       10531     9020081+   7  HPFS/NTFS
/dev/sda4           10532       12161    13092975    5  Extended
/dev/sda5   *       10532       12161    13092864   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    f  W95 Ext'd (LBA)
/dev/sdb5               1        2439    19585012    7  HPFS/NTFS
/dev/sdb6            2440        5652    25808391    7  HPFS/NTFS
/dev/sdb7           14193       14593     3221001   82  Linux swap / Solaris
/dev/sdb8            5653        6868     9767488+  83  Linux
/dev/sdb9            6869        8692    14651248+  83  Linux
/dev/sdb10           8693        8719      216846   83  Linux
/dev/sdb11           8721       11343    21069216   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2      121601   976752000    f  W95 Ext'd (LBA)
/dev/sdc5               2       60801   488375968+   b  W95 FAT32
/dev/sdc6          101173      121569   163838871   83  Linux
/dev/sdc7           60802       67341    52532518+   7  HPFS/NTFS

Partition table entries are not in disk order

(except in Spanish, of course)

That is the results of "fdisk -l" on my laptop (sdc being my external TB Drive).

<edit> having re-read a few things, it would ***really*** be helpful if you could run GPartEd from the Live CD and post an image of your hard drive.  What I didn't realize is that "fdisk -l" doesn't tell you the disk-usage statistics (i.e., "Used Space" and "Free Space") of the partitions. Notice in the example below that below the graphics there are columns for "Partition", "Filesystem", "Size", "Used", and "Unused".  The "Used" and "Unused" are the information that's not listed with "fdisk -l" and would be quite useful.

---

### Post by alxpenguin on 2010-05-25
Im having a heck of a time uploading the pic to a website so I can link it here...is there an easier way?? Your patience with me must be wearing thin lol

---

### Post by alxpenguin on 2010-05-25
BTW I already did the defrag on the disk and moved the files to the beginning of the disk. Playing with the XP partition is a pain in the butt. If I delete the ubuntu partition and the just slide the bar to make the new partition bigger that should take care of it right?

---

### Post by alxpenguin on 2010-05-25
Ok I was being ignorant here you go

---

### Post by -kg- on 2010-05-27
Frankly, I can't figure out what's going on.

I always manually handle my partitioning (I'm fairly experienced with it), so I've never tried the "Side by Side" option when installing, but it's my understanding that when you choose that, the installer shrinks the Windows partition and creates the ext3/4 partitions _automatically_.  If it does, there should be no "slider" as you describe.  Perhaps I'm wrong...all I know is, 2.33 GB is *_definitely_* too small for an effective installation.  I'm surprised it installed at all!

Since you have defragged the XP partition, what I would do is boot to your Live CD to the desktop, launch GPartEd, and, after deleting the ext3 and Linux Swap partitions, manually decrease the size of the XP partition from the right side.  This page from my How To: [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition") will take you step by step through it.

You need to shrink that partition so that you end up with around 10 GB of free space at the end of the drive (more, if you can and want to).  That will give you sufficient space to make an Ubuntu installation with sufficient room.

BTW, don't panic...this operation is likely to take a lot of time...several hours.  If you have problems with power in your area, it would behoove you to have your computer on a UPS (Uninterruptable Power Supply) so the operations will not be interrupted.  If they are, data loss is very possible.  Let the operation complete totally.

I personally like to have around 20-25 GB for my installation, but I do a lot of stuff and store certain files.  10 GB is only sufficient...if you can (and want to) do more, it certainly would give you more room to breathe.  Just a suggestion, though.

Once you have decreased the size of the XP partition, then you will want to do the same operation and expand the size of the Extended partition to take up the entire amount of free space.  If you deleted it along with the ext3 and swap, it's no problem...just recreate it and make it the size of the free space.

After this, close GPartEd and click on the "Install" Icon.  When you get to the "Partitioning" step, select "Install to Largest Contiguous Free Space" (whatever that is in Spanish).  This selection will automatically select the space you freed (inside the Extended partition) and automatically create the partitions you need for the installation.

And that ***_should_*** be a wrap.  You should have a dual-boot system between XP and Ubuntu, selectable from GRUB in the MBR, with sufficient room in the ext4 partition (Lucid defaults to an ext4 format) to update and expand for some time in the future.

<edit> BTW: I'm going to be out of town (and mostly away from any Internet connection) for the weekend.  I'll be back next Tuesday or Wednesday.  Hopefully you'll have no problems.

---

### Post by alxpenguin on 2010-05-27
Thanks man youve been a heck of alot of help. Unfortunately now Im having trouble with XP and the darn thing wont boot the livecd......I feel like shooting the laptop. When I try to run the livecd like when I did the first install...and that means I cant delete the partitions beacuse they are locked......Anyway to boot the livecd from ubuntu??

---

### Post by alxpenguin on 2010-05-27
I finally got it to work!! I will let you know if this does  the trick thanks!!!

---

