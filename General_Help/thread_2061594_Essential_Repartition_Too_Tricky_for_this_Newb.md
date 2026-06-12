---
title: "Essential Repartition Too Tricky for this Newb"
date: 2012-09-22
forum: General Help
---

### Post by dialectical1 on 2012-09-22
Hello! For a good while, I've been stuck using a very outdated, unsupported version of ubuntu (9.10) due too-small linux partition. Last time I checked, the only volume I use only takes a small % of my whole system, but GParted won't let me resize my partitions. 

The option to resize is greyed out of the right-click menu.

(One partitions (ntsf) has a warning; but I have no idea why Gparted wouldn't be able to read its contents.)

I've never repartitioned, and am a total noob when it comes to even  basic-seeming things, so I would deeply appreciate some help with the  actual partitioning, as well.

Here's the *sudo fdisk -l* readout:

>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13843   109655142    7  HPFS/NTFS
/dev/sda3           13844       14594     6026424    5  Extended
/dev/sda5           14555       14594      313344   82  Linux swap / Solaris
/dev/sda6           13844       14554     5711076   83  LinuxAnd the *df -h* readout:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             5.4G  4.5G  610M  89% /
udev                  497M  252K  497M   1% /dev
none                  497M  332K  497M   1% /dev/shm
none                  497M  212K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda2             105G   34G   71G  33% /media/SQ004286V02
If there's any more info anyone needs, please feel more than welcome to ask! Thanks muchly ^_^

---

### Post by Bucky Ball on 2012-09-22
Boot from the LiveCD and when you're at the desktop, launch Gparted. Right click and *unmount partitions you want to delete. *Essential. You can right click and unmount from Gparted running regular hard drive install also, except for partition Ubuntu is running on, of course. ;)

Are you unmounting the partitions you want to delete first?

---

### Post by dialectical1 on 2012-09-22
Ah, sorry, forgot to mention - my CD drive has been out of commission for years :-/.

There's a bit of a chance a buddy has some extra space on his external drive ... what would be the procedure if he lets me use it?

I don't plan on deleting any partitions, just to resize the huge one - less than half of it is full with years worth of personal files - and then make this one much larger.

---

### Post by Bucky Ball on 2012-09-22
Burn the ISO to a USB dongle if you have one and boot from that.

You can launch Gparted in the hard drive install of Ubuntu, right click, unmount and shrink/expand any of the partitions, except the one you're running Ubuntu from (/).

The other option is to upgrade to 10.04 LTS through update manager. That is supported until April next year and gives is a one click option to upgrade to 12.04 LTS which is supported until 2017.

---

### Post by dialectical1 on 2012-09-23
When I unmount the large partition, it puts that caution symbol next to the device's name. 

Any I don't know what I'm doing - and I don't want to lose all my data just fooling around .... when I try to do the partition table, it says if I proceed, it will wipe out the disk.

---

### Post by Bucky Ball on 2012-09-23
As I said, if you are trying to resize a partition with any Win post-XP, don't. Use the Windows software to do it. A regular NTFS partition fine (and FAT).

You should ***ALWAYS*** do a backup of anything you don't want to lose before doing anything like this. What could possibly go wrong, right?

As for Ubuntu partitions, unmount and go right ahead. The exclaimation mark just means it's unmounted. To reassure yourself, right click and mount just to demonstrate you can.

Good luck with it ... I'd advise to research and read up a bit more about this so you do know what you're doing and feel more confident as you have the information about how to resize you originally requested. ;)

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8ABjV5Q8loA.gUK5gt.?p=resize%20partition%20ubuntu&fr=altavista&fr2=sfp](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8ABjV5Q8loA.gUK5gt.?p=resize%20partition%20ubuntu&fr=altavista&fr2=sfp)

---

### Post by dialectical1 on 2012-09-23
**The option to resize is greyed out on the right-click menu**. (This is why I haven't repartitioned - something's not working properly.)

---

### Post by dialectical1 on 2012-09-23
How do I move the .tgz/.tar.bz2 backup file onto an external drive? (As per [this tutorial]("http://ubuntuforums.org/showthread.php?t=35087")) I can't open the folder my most recent backup is in (root), and the tutorial doesn't explain how to change where the backup file will end up.

I have the GParted live USB mounted, but don't know how to run it.

---

### Post by Bucky Ball on 2012-09-23
Boot from the Ubuntu LiveCD. Get to the desktop. Open a file manager. Move it ...

---

### Post by dialectical1 on 2012-09-23
I don't have a functioning CD drive. That's why I put the GParted iso on a usb. 

Should download another copy of *Ubuntu* onto an external drive?

---

### Post by Bucky Ball on 2012-09-23
> **dialectical1 said:**
> I don't have a functioning CD drive. That's why I put the GParted iso on a usb. 

Should download another copy of *Ubuntu* onto an external drive?

No. Scrap Gparted on the USB, download the Ubuntu ISO and put that on instead. Boot from that and get to the desktop ...

---

### Post by dialectical1 on 2012-09-23
Ok, I finally have the Ubuntu ISO mounted, but not a clue how to boot it.

I have very very limited space on my system, so if I were to (re?)install from the iso (as per [this]("http://www.ubuntu.com/download/help/install-ubuntu-desktop")), it may be very risky. Also, I likely don't have enough space on my drive to install startup disk creator, if[ this ]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")is the general procedure you want me to follow.

Currently, I have 578 MB free, subject to go to nil if firefox acts up. (If my system freezes with no space, I can't even log onto my desktop.)

---

### Post by Bucky Ball on 2012-09-23
Boot the machine and hit whatever key takes you to the BIOS. Make sure you are booting from the device with Ubuntu on (CD/USB). 

That should get you to a desktop. Launch gparted.

If you do reinstall, click 'Something Else' when you get to the partitioning stage and do it manually. You will see the already existing partitions quite clearly. Just don't touch 'em. Make an extended partition in the free space then put Ubuntu on logical partitions inside that:

/ = root partition; 15Gb fine;
/swap = swap; 2Gb fine.

Easy. If you want to reassure yourself, check that the existing partitions are set to 'Do Not Use' and they are not ticked to format. 

You should always backup data you don't want to lose in case things go pear-shaped.

---

### Post by dialectical1 on 2012-09-25
I keep fiddling, yet the new option is not showing up in the BIOS menu.

Also, how do I save the backup to the external drive rather than somewhere in root?

---

### Post by HiImTye on 2012-09-25
remember to swapoff before you start making changes to any hard drive with a swap partition.

---

### Post by Bucky Ball on 2012-09-26
> **dialectical1 said:**
> I keep fiddling, yet the new option is not showing up in the BIOS menu.



Use arrows to get to the Boot tab in BIOS. Where this is can vary depending on BIOS, but you need to set the CD/Optical drive as your first boot device and restart. If there is a CD in it that should boot before the hard drive. There will be no indication of what's in the device. BIOS sees it as just an optical boot device.

> **dialectical1 said:**
> 

Also, how do I save the backup to the external drive rather than somewhere in root?

Boot from a livecd and get to the desktop. Plug in the external drive. Backup the files.

---

### Post by dialectical1 on 2012-09-26
There's a number of even older versions of my ancient kernel, restore mode, as well as Windows (which actually wouldn't work, as I gutted its system files). I don't see any new options ... is it ok if it's in a subfolder of the external drive, or should it be in the main folder?

> Boot from a livecd and get to the desktop. Plug in the external drive. Backup the files. 	

Following[ this tutorial]("http://ubuntuforums.org/showthread.php?t=35087")? Or some other process?

---

### Post by dialectical1 on 2012-09-29
Okay, apparently I needed to enter the boot device selection menu (or something like that), but it's still not working. The external drive has only been used with a unpartitioned Windows machine (and mine), yet it fails to boot the Ubuntu .iso due to a "invalid partition table". No clue where/why it's getting that. Any ideas?

---

### Post by Bucky Ball on 2012-10-01
You're trying to install the ISO from a hard drive? Never heard of that but may be possible.

Why are you not installing from a USB or disk?

---

### Post by dialectical1 on 2012-10-02
An external storage device, rather. There's not enough space on the thumb drive to store the iso. And again, my cd drive doesn't work.

---

### Post by Bucky Ball on 2012-10-02
Could you post a link to the instructions you're using to do this? Sorry if you have already ...

---

### Post by dialectical1 on 2012-10-03
The only one I'm trying to follow is [this for backing up]("http://ubuntuforums.org/showthread.php?t=35087") my files; however, until I find a way to control where it saves the backup file, it's kinda useless (for a little bit more info, see [this post]("http://ubuntuforums.org/showthread.php?p=12255385#post12255385")).

---

### Post by dialectical1 on 2012-10-06
Btw, I'm fine with following any method of backing up my files anyone might suggest, so long as it 

[LIST]
[*]can save files from multiple partitions
[*]doesn't involve installing any programs (not enough disk space)
[*]allows the backup file to be saved on an external storage device.
[/LIST]

---

### Post by Bucky Ball on 2012-10-07
Why don't you boot from a LiveCD and drag and drop the files to the external drive? Then you won't need to install software ...

---

### Post by dialectical1 on 2012-10-07
I suppose I can try that. Not sure there'll be enough room on the drive without some sorta compression ...

---

### Post by Bucky Ball on 2012-10-07
If you right click a folder you should get the option to 'Compress'.

---

### Post by critin on 2012-10-07
> **dialectical1 said:**
> I suppose I can try that. Not sure there'll be enough room on the drive without some sorta compression ...

Do you know how to boot from the usb?  Is there a boot key ID that flashes by when bio opens?  It could be f2, f12, esc, del, almost anything.  You need to press that key as soon as it shows on the BIO screen so it will go to a screen that lets you choose USB.    Or if there's no boot key, hit the setup key and place boot flash, usb or whatever that disc is called in your system.  Have it moved to the first boot.

When it boots, and asks if you want to install or TRY, choose TRY.  You will not be installing it.

When you get to the desktop you can find your files and drag them to the storage disc.  Of course the storage must be already plugged in to show.  Drag and drop everything.

When you get all off, you can continue on with what you need to do.  You can use  gparted from the USB and do what you needed with the hdd.

Don't install anything.

---

### Post by Bucky Ball on 2012-10-08
> **critin said:**
> 

When you get to the desktop you can find your files and drag them to the storage disc.  Of course the storage must be already plugged in to show.  Drag and drop everything

OP has a lot of stuff so wanting to compress, thus, as mentioned, perhaps put into a backup folder then right-click>Compress. ;)

---

### Post by critin on 2012-10-09
> **Bucky Ball said:**
> OP has a lot of stuff so wanting to compress, thus, as mentioned, perhaps put into a backup folder then right-click>Compress. ;)

Thank you.  I'm afraid I misunderstood and thought he still meant *the current drive *was too full to 'install' anything else in order to compress when he answered with:  

> I suppose I can try that. Not sure there'll be enough room on the drive without some sorta compression ...I see now that he meant the external drive lacked space, though he didn't specify that.     I meant he didn't have to install anything on the current drive to be able to compress his folders.  He could compress and move.   I was agreeing with your posts about using live cd & compressing though I left the word 'compress' out.  I guess I assumed he would understand that since your posts were first.    *Shouldn't ever assume. *

Moving single folders into *a separate folder* to compress, as you suggest here now, makes sense.  I'm not sure how large a compressed folder can be in order to move easily.  I wouldn't want many gib in one folder myself.   But I'm all about keeping it 'easy' to move **& **restore, and sometimes that's just not possible.

I didn't mean to confuse the issue.  Point taken, thanks.

---

### Post by dialectical1 on 2012-10-14
> **critin said:**
> Do you know how to boot from the usb?  Is there a boot key ID that flashes by when bio opens?  It could be f2, f12, esc, del, almost anything.  You need to press that key as soon as it shows on the BIO screen so it will go to a screen that lets you choose USB.    Or if there's no boot key, hit the setup key and place boot flash, usb or whatever that disc is called in your system.  Have it moved to the first boot.

When it boots, and asks if you want to install or TRY, choose TRY.  You will not be installing it.

When you get to the desktop you can find your files and drag them to the storage disc.  Of course the storage must be already plugged in to show.  Drag and drop everything.

When you get all off, you can continue on with what you need to do.  You can use  gparted from the USB and do what you needed with the hdd.

Don't install anything.

When I go to that screen, it doesn't seem to make any difference whether or not the external drive or a usb (both with the iso) are plugged in. 

As for the backup: The drive didn't seem to want to let me compress the files into one file, but thankfully they seem to fit on it anyhow. (But these are just personal files; not sure if it's worth also trying to save a copy of my system.)

---

