---
title: "Meerkat/XP Dual Boot - Ubuntu to Primary or Logical Partition..."
date: 2011-01-11
forum: General Help
---

### Post by casparov on 2011-01-11
Hi, Everyone... 

I just assembled a low-to-mid-level PC w/ a terabyte drive, divided into ntfs(primary)/swap/ext4(primary).  WXP installed w/o a problem into the first primary, but the Meerkat installation, while proceeding nominally, did not reveal a GRUB menu from which to select Ubuntu upon reboot.

I partitioned and formatted the drive through Gparted.  Should the ext4 partition have been set to logical for the Ubuntu install?  The way things are now the PC slips right into XP w/ no competing boot option or GRUB menu.  

Many thanks for any insights into this problem.


Regards,  Casp

---

### Post by Bucky Ball on 2011-01-11
It really doesn't matter. You should have just left free space. Ubuntu is going to reformat and repartition it during install anyway. Ubuntu will exist quite happily within an extended partition on a logical drive.

In this situation: Install Windows to a partition big enough. Leave the rest free space. Install Ubuntu. Simple. I would use 10.04 LTS as 10.10 has some major and minor issues at the moment. Problems with side-by-side install is one of them and you are taking a risk attempting this with 10.10!!! 10.04 is stable.

Also, better to manual partition and have:

/ = OS, 20Gb heaps;
/home = your settings and personal data;
/swap = 2Gb or 4Gb for hibernate.

Make 'em EXT4 ('cept /swap which looks after itself). Those partition names are defaults in the partitioner.

You'll clearly see your Windows partition there: NTFS. Just don't touch it. ;)

ps: always backup your valuable data before installing any OS. (but I'm sure you've done that ...)

---

### Post by casparov on 2011-01-11
Bucky... 

(How can you possibly reply that fast w/ that much information?  Thank-you...)

Well, I tried twice and both times GRUB was not available.  First, Windows was installed to a (roughly) 500GB partition formatted NTFS prior to the installation.  Next, Ubuntu installed into the free space by my checking the "manual" option (as opposed to the Ubuntu radio button calling for "side by side" (or something like that) installation (whatever that means).  As I say, I elected to choose a primary partition installation from the drop-down list through the Meerkat options.  (I also indicated "/" as a mount point in the appropriate menu.)  

The second installation I did provide an ext4 partition, and a 2GB swap, but I also directed that the partition be formatted so Meerkat did that first.  But both times the installation was to a primary partition.  The upshot is that, right now, I have a nicely installed XP ntfs parition--about 500GB--and a Meerkat installation, which I cannot boot.  

If you had this layout what would you do next?  (I believe that you already stated what you would do, but I had some difficulty following that because you are ahead of me.)

Thanks so much for any help,   C.

---

### Post by Bucky Ball on 2011-01-11
When you switch on, do you get to a boot menu where you can choose kernels with Windows at the bottom?

If so, choose the second on the list, the one that ends with 'Recovery'. When you get to the options, try 'failsafe x'. Does that get you in with low resolution?

When you say grub not available do you mean this list of choices at boot?

---

### Post by casparov on 2011-01-11
Bucky...

Thanks so much, again...

No, it slides right into XP w/o so much as a second's hesitation or glimpse of a GRUB.

You know, I did perform the install w/o being connected to the Net (in the basement).  Would this have some kind of bearing on the problem?

I was thinking that, perhaps, I should redo things and just select "logical" for the partition type.  

So, that is where things are...  

C.

---

### Post by Bucky Ball on 2011-01-11
Being offline shouldn't have made a lot of difference although I always install while online with a cable. 

Yea, not sure what went on there. Maybe run Ubuntu from the install disk, go to Gparted (System >Admin >Gparted), and have a look in there at what you have on the disk you installed to. Let us know.

---

### Post by casparov on 2011-01-11
I will try to reinstall within a logical partition--I will post the results.

All Regards,  C.

---

### Post by casparov on 2011-01-11
Hi, again...

I tried reinstalling Meerkat into both logical and primary partitions and it did no good.  Grub never appears on restart; all I get is an XP boot.

I did encounter, at every attempt before the Ubuntu install reboots, a screen w/ I/O errors to disk sectors, several dozen, I would guess.  In other words, when Ubuntu states that it will restart to complete the install operation, things go to a black screen w/ several lines of fine text I/O errors, which sits there.  I hit enter and the restart initiates.

I don't know how to run a utility on this.  Windows will not see the unallocated space, and I can't get a Linux boot to run a disk check.

One other thing...   I do have an IDE disk w/ a few partitions on it.  That disk is denominated sda within Gparted (though it is not SATA).  Gparted indicates that my SATA disk is denominated sdb, and the Ubuntu target partition is sdb5.

So, that's where things are--don't have any idea now what to do, except that I will run and fsck command and try to see if it performs some kind of error check on the Ubuntu target partition from within the Live CD.

All Regards,   C.

---

### Post by Bucky Ball on 2011-01-11
You are trying this with 10.04 LTS?

---

### Post by Quackers on 2011-01-11
It may be that grub is not installing to the right place, for some reason.
This often happens when a usb flash drive is used for installation, as it can become the first drive on the system.

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by casparov on 2011-01-11
Bucky, Quackers (btw, love the monikers) and All Whom Read...

First, I apologize for being out of touch for the last day...

Secondly, I fear that I have let many astray, as it occurred to me that the other disk/partitions on the system (an IDE disk, 320GB) is undoubtedly where the GRUB is residing.  I arrived at this while walking the dog--Taiga (white German shepherd and yellow lab) could see this when I couldn't.  It didn't occur to me earlier because the system is set to boot from the new 1TB drive; of course, the install wouldn't comprehend this, at all.

Anyway, I am reinstalling yet again and guess what...?  There it was, right in front of my face, an option for a location where GRUB will reside, AND I MISSED IT COMPLETELY EVERY TIME!!!!! :confused: 

So, I will let this install go and report the results.

Now I'm almost wishing that it won't work.  

Many, many thanks...     C.

---

### Post by casparov on 2011-01-11
Yes, that was it--everything works.  :P

Thanks, again...      C.

---

### Post by Quackers on 2011-01-11
Lol, glad you got things working anyway :-)

---

### Post by Bucky Ball on 2011-01-11
heh, heh; nice work. Yea, I come up with stuff while walking the dog, too!

Our pleasure and enjoy. ;)

---

