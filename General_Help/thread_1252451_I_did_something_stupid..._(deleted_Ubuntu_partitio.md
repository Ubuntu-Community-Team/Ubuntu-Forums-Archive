---
title: "I did something stupid... (deleted Ubuntu partition)"
date: 2009-08-28
forum: General Help
---

### Post by pFREDq on 2009-08-28
Just for fun, the other day I decided to try my hand at dual booting Windows Vista and Ubuntu 9.04, because I heard it was pretty cool. So, I went into Vista's disk manager and created a 10GB partition that I would later install Ubuntu onto. I then proceeded to burn a CD and installed Ubuntu and everything worked perfect.
 That is, until I decided I wasn't too fond of Linux, so I decided I'd get rid of it and free up some disk space. I (incorrectly) assumed that if I deleted the Ubuntu partition, GRUB would be deleted as well. *sigh* I guess that's what happens when you assume...
 So when I later turned on my laptop, an error message appeared. "Error 22" and it froze. So, after getting a little spastic, I calmed down a little and decided to pop in the Ubuntu disc and boot from it. I chose the "Try Ubuntu without any change to your system" (if I were to install it, it would delete Vista!) and researched the error.
 It appears it can be resolved by booting your Vista disc and going into some recovery thing and typing "fixmbr". Haha, funny story about that Vista disc. I have a Compaq laptop, and apparently Compaq is too cheap to give us discs, so they instead have a program installed that you can burn to a disc and it will restore it to factory default settings, completely getting rid of all my personal data, which I intend to keep.
 So I tried to find out if there was a way to uninstall GRUB through Ubuntu and all I could find was typing "dd if=/dev/null of=/dev/hda bs=446 count=1" in the Terminal, but that would wipe the MBR, including Vista's original bootup scripts, right?
 So is there a way to safely uninstall GRUB through Ubuntu 9.04 using the "Try without changes to your system" option and then be able to boot Vista normally?

Any help would be greatly appreciated!

---

### Post by jpeddicord on 2009-08-28
As far as I know (and someone else feel free to correct me) you may be stuck without that installation disk. You can't just remove grub from the MBR, then you will be left without a bootloader at all. You need Vista to re-install its own loader. I recommend calling Compaq and explaining your situation. They'll likely send out an install disk; after all you did pay for the OS.

Another somewhat hacky option would be to re-install Ubuntu into that partition again and use it to boot Vista. Perhaps you may be able to re-set Vista as the bootloader while Vista is loaded using bootrec.exe /fixmbr.

---

### Post by pFREDq on 2009-08-28
Ah, I forgot to mention that after I deleted the partition I used Vista's disk manager to extend the C drive back to it's full capacity, so the partition is no longer there. If there's a way to shrink the drive and make a partition with Ubuntu, and I'm sure there is (I'm looking it up now), I'll give it a try.

And if that doesn't work, it looks like I'd have to have that installation disc.

---

### Post by bchurchill on 2009-08-28
One thing you could do is keep grub around to do the booting.  You can setup grub so that it doesn't even show up, it just loads windows automatically.

If you choose this option, you would need to create a small partition formatted as EXT3.  It could be 20MB for example.  In reality it could probably be even smaller.  I don't think my GRUB files take more than a megabyte, but I'd go for more to be safe.  (And if you return to linux, you *might* put kernels there later).  Then you'll install GRUB to that tiny partition, and then setup GRUB to boot windows automatically.

To do this you'll use the Ubuntu live CD to create a partition (don't install the O/S though).  One way is from a terminal issuing the command

sudo apt-get install gparted

and then running Applications->System Tools->Gnome Partition Editor.  Make note of the device name /dev/... of the partition you create.

Then follow the instructions at [https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

to install GRUB to this partition.

After that you can optionally configure GRUB to make sure it's right and choose options.  You'll mount the tiny partition you just created.  From a command line:

sudo mkdir /newboot
sudo mount /dev/... /newboot

(where /dev/... is the device file name from above)

then do the following:

sudo cd /newboot/grub
sudo gedit menu.lst

The menu.lst contains information to configure GRUB.  There should be a Windows entry in there.  The file is probably alright as it is, however you can:

- Make windows boot automatically.  To do this make sure there are no extra boot entries that shouldn't be there (such as anything for Ubuntu).  This shouldn't be necessary if Ubuntu is already gone.  Any lines preceded by # can be ignored.
- Hide the GRUB screen
     change the line that says "# hiddenmenu" to "hiddenmenu"
- Alternatively you can change the timeout before Windows is booted
     change the line "timeout ..." to "timeout <newvaluehere>"

Hopefully this'll work out for you until you can fix your MBR with a Windows CD.  Let me know if you run into problems.

---

### Post by pFREDq on 2009-08-28
After typing that first part into Terminal, it said the latest version was already installed. The only partitioning tool on here is called "GParted", which was under "System>Administration"
According to that program, there is already 1.34 MB of unallocated space. When I try to use that to create a new partition, it says "A partition cannot have a length of 0 sectors". It won't allow me to make a new partition with the HDD, and from what I recall from using the tool in Vista, you first have to shrink the volume to create more unallocated space, and there doesn't seem to be an option to do so through GParted.

Sorry if I'm coming off as an idiot here, I'm new to the whole disk partitioning and Linux thing.

---

### Post by michy99 on 2009-08-28
You can restore the Windows MBR with the Ubuntu disk! 

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by pFREDq on 2009-08-28
Thanks, but unfortunately I've run into problems with that as well, michy99. When trying to install "ms-sys" I get a "Couldn't find package" error.

---

### Post by bchurchill on 2009-08-28
> **pFREDq said:**
> Thanks, but unfortunately I've run into problems with that as well, michy99. When trying to install "ms-sys" I get a "Couldn't find package" error.

It would be more work but you should be able to install ms-sys from source here: [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

It was once a package for dapper, but doesn't show up in current packages.  You could try downloading the dapper .deb package from: 

[http://packages.ubuntu.com/dapper/amd64/ms-sys/download](http://packages.ubuntu.com/dapper/amd64/ms-sys/download)

and then use:

dpkg -i --force-all <name-of-downloaded-package>

I'm not sure that you should use --force-all, you might not need it and should try ommitting it first.  If it complains you're using the wrong operating system, you can use --force-all, or find another --force option to use (I can't get to the man at the moment... so I can't be sure)

---

### Post by pFREDq on 2009-08-28
After messing around with that (turns out I had to add "sudo" before "dpkg..." to get it to work), I continued with the tutorial michy99 posted and upon entering "sudo ms-sys -m /dev/sda" I get this:

 *garbled text*LF*garbled text* not found
Syntax error: "(" unexpected

I'm beginning to think Ubuntu doesn't like me.

---

### Post by bchurchill on 2009-08-28
> **pFREDq said:**
> After messing around with that (turns out I had to add "sudo" before "dpkg..." to get it to work), I continued with the tutorial michy99 posted and upon entering "sudo ms-sys -m /dev/sda" I get this:

 *garbled text*LF*garbled text* not found
Syntax error: "(" unexpected

I'm beginning to think Ubuntu doesn't like me.

I'm not sure I can help with this... it seems like it might be a bug.  But post the output of

sudo fdisk -l

so we can see what your partitions are.  Also how garbled is that text from the failed step?  Post it for us... maybe it mentions a dependency that wasn't installed for some reason.

P.S.  Ubuntu loves you.

---

### Post by pFREDq on 2009-08-28
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8d64c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18238   146492384    7  HPFS/NTFS
/dev/sda2           18238       19457     9794560    7  HPFS/NTFS
I tried using both "/dev/sda" and "/dev/sda1" for that last command, both of which produced an error code.

The first part of the error with garbled text was "ELF: not found"

---

### Post by bchurchill on 2009-08-29
mmm Ok.  So it looks like that utility doesn't work, but from your output it looks like we've got a work around.

You didn't actually expand your Windows partition (or it doesn't look like it rather).  Rather, you have a lage partition (/dev/sda1) and a smaller one, about 1/15 the size (/dev/sda2).  If you only are using one of these, then my guess is that the second one is empty, and is the reformatted Ubuntu partition.  **Double check to make sure this is the case.**  If indeed the second one isn't being used, you can reformat your hard drive to include a small boot partition (as described earlier) and a slightly smaller NTFS partition.  As your previous error indicated, you do need at least one HD sector free possibly more.

So I would (if the second partition is empty):
1. Delete it.
2. Create boot partition of size 10-20 MB or so (more or less, depending on what the partitioner allows)
3. Recreate your other partition to take up the rest of your drive.

Then install GRUB using the instructions above to the boot partition and configure it, as above.
[B]
EDIT: To be on your safe side, backup your whole hard drive first, as always before reformatting/partitioning.

[/B]Edit #2:  Although the old .deb package didn't work, the newest version of ms-sys from source might work too, so if you don't want GRUB you can try that as well.

---

### Post by oldfred on 2009-08-29
One more choice to try - super grub disk. Supposedly repairs windows
[http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)

---

### Post by pFREDq on 2009-08-29
Actually, I think that second 9-10GB partition is a recovery program that can be used to restore every thing to the factory default settings, like the disc they use as their substitute for a Vista disc. :/
Even though I have the disc(s) I'd rather not get rid of that, just in case.

EDIT: I tried out SGD just now and it doesn't seem to want to cooperate. There are several options to use. My laptop doesn't have a floppy disc drive, so that's out. Whenever I try to open the disc tray to put in a CD-R, I get an error message, because Ubuntu is being read from the disc, so it needs to be in all the time. And for some reason, no clue why, my laptop refuses to load from USB. I changed the BIOS settings so that it loads USB first no matter what, but it still tries to load from the HDD instead! Maybe I just messed up somewhere, I'm pretty tired right now so that's a possibility...

---

### Post by pFREDq on 2009-08-29
I tried downloading the newest version of ms-sys, which was a .tgz file, my worst enemy. Many error messages ensued.

Just out of curiosity, since apparently all I should have to do to fix the MBR is run a Vista installation disc and run a simple DOS prompt, wouldn't I just be able to access that from a XP install disc? Would that just uninstall GRUB or would that install XP's bootup?



EDIT: Okay, since absolutely nothing seems to be working for me, I've decided to just upload all my crap to MegaUpload (since I can't burn discs using the live cd) and use the recovery discs to return everything to the factory default settings, then re-download everything. It'll take a while to upload and download 15-20 GB of stuff, but it seems to be my best option at the moment.

Thanks for your help, guys! I really appreciate it. :)

I'll post back later if it works.

---

### Post by bchurchill on 2009-08-29
> **pFREDq said:**
> I tried downloading the newest version of ms-sys, which was a .tgz file, my worst enemy. Many error messages ensued.

Just out of curiosity, since apparently all I should have to do to fix the MBR is run a Vista installation disc and run a simple DOS prompt, wouldn't I just be able to access that from a XP install disc? Would that just uninstall GRUB or would that install XP's bootup?
  :)


Yeah, compiling things from source can sometimes be a pain.  There are usually dependencies.  It's worth trying though.

My understanding is that the Windows disks only fix the MBR, which is the first 512 bytes on your hard drive.  This removes the instructions to start GRUB, and in your case it would remove its last traces.  However, in general, it doesn't delete GRUB's files... but you already dd that when you deleted your Ubuntu partition!

Good luck on the backup/restore.

---

### Post by pFREDq on 2009-08-30
MegaUpload and other similar sites wouldn't load right for some reason, but a friend let me use his laptop to burn my files to DVDs. And now everything is nearly back to normal, I just have to redownload all my programs.

Thanks again for all your help guys. :)

---

### Post by str8outtacpt on 2009-08-30
i think i may have done something stupid myself. I ran ubuntu from the live cd and it worked fine then i decided to install it. then it had a choice b/w running windows xp and ubuntu 8.10 and i chose ubuntu then i opened partition to partition my sd card for my android phone so i could run apps to sd and i think i clicked create a partition table on accident but i had to leave so i leave to go for an emergency so i left the window open and when i came back the screen was at the login screen so i assume i had a power glitch when i was gone so now i cant even find windows xp. any sugguestions?

---

