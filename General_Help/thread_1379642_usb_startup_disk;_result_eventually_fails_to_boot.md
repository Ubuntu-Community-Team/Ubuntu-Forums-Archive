---
title: "usb startup disk; result eventually fails to boot"
date: 2010-01-12
forum: General Help
---

### Post by maestrobwh1 on 2010-01-12
This is "solved" eventually on page 2 of this thread.  It is actually more or less a workaround.  Issue in a nutshell:

The *Ubuntu usb start up disk creator* requires fat-32 to create a disk, but when the SD card was later mounted in windows, the unetbootin menu could no longer find the boot kernel for Ubuntu.  Fat-32 is crap.  I have seen posts were it is mentioned that fat-16 does not caue this issue (but you are limited to a 2 GB partition - not really helpful). If you have this issue:

1)make an ext2 or ext3 partition of ~1GB, I labeled it "ubuntu"
2)make an ext2 or ext3 partition of how much space you want for home and other files (installing apps sucks up space really fast), be sure to give it the label of casper-rw.  I used gparted.
3)use unetbootin to install the iso
on the first partition
4)edit the resulting syslinux.cfg and make the first entry look like this
```

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash **persistent** -- 
```
--> this did not work for me; I had a second file on that partition "extlinux.conf" and I did more or less the same thing to that file.  I actually copied the lines and made the first entry persistent, but left the original entry as my second so that I could boot without persistence if need be.

*There are other "tunings" that are on the second page here that, if you used ext3, speed up the disk access to your casper-rw partition.  
I also had to, to make firefox usable (and this only seems to be an issue with ext3 on slow media), at least the version with jaunty, I disabled the first three tick boxes in >edit>preferences>security.  I also set my cache limit to 0.  DO NOT set the cache directory to /tmp.  This works well for a regular install with plenty of ram, but it will suck up your memory running ubuntu this way (live).  Since Ubuntu runs more or less out of ramdisk with this kind of setup, there seems to be little space in /tmp for a firefox cache.  I tried it, and my system kept locking up and eventually figured out it was this modification.

Original Post:

I ran into this problem on two very different devices (one 8 GB A-Data SD and a 4 gb Sandisk micro).  If I write to the disk (other than to the persistent casper-rw file) The disk will often boot into the kernel (usplash comes up) but dies to a blank screen.  The same SD card had grub on it and I never had problems with this.  Unetbootin/USB creator use LILO, correct?  If I copy my casper-rw to another disk and then reinitialize the disk (using the Ubuntu usb startup creator, Unetbootin, or the win XP lili program) then copy my casper-rw back to the drive, I am good to go until I decide to write other data to the disk (i.e. in XP)

I hate fat formatted disks.  I find it to be so unreliable.  I am thinking I am getting data corruption somewhere but fsck doesn't seem to pick it up.

**Anyone have any ideas to prevent the issue, other than not to write to the disk (it is an 8 GB sd card).**

---

### Post by C.S.Cameron on 2010-01-12
Instead of using the unreliable FAT32 casper-rw file consider making two partitions in EXT3 (or EXT4). and naming one casper-rw and the other home-rw and leave about a gig for your usb-creator or unibootin install.
You can then screw up your install as much as you want and not loose any data

---

### Post by garvinrick4 on 2010-01-12
Are you going to use this on different machines than the one you produce it on?
They are 2 different animals. Using ext3 or 4 and installing off a Live CD just like a
Hard drive install will work but the grub will look for HD mbr on update-grub. Will freak
the owner of machine out and give him a grub2 and chainload his Windows.
With Fat32 can get persistence up to 4 gig but can use on any machine without updating
grub2.
 Some USB flash drives just do not work. If you have the kernel installed in grub that is going to be on USB install seems to work everytime for partitioning and using ext3 or 4
something like 500 meg /boot and 14 gig / with remainder swap. And in advanced in about page 8 or so of gparted mirror the boot. Like sba1 in this install. Change b to what ever your device is. This using 16 gig. 

Remember it seems 3/4 of these work and if it can find the kernel already in grub works everytime. That is what I have found.

Centos brand sure seems to work nice, have no idea why.

---

### Post by maestrobwh1 on 2010-01-13
Ok, so here is what I am thinking: 

Is Ext2 more reliable than FAT 32?  I think I know the answer.

The reason I ask is that if I make the first partition ext3 for the base file system, I can make the second partition into Ext2 so I can use the Ext2-IFS driver to read it in Windows (it says it can read Ext3 but I never have luck with that).  I could then share my home files with both OS's

Unfortunately, I guess an NTFS casper-rw won't get read by the bootloader (LILO?) used by either unetbootin or the Ubuntu startup disk creator.  I assume NTFS is ignored by all but grub2.

---

### Post by C.S.Cameron on 2010-01-13
Sounds like your ext2 idea should work for the home-rw partition, I have used reiserfs to format the home-rw partition and it worked OK.

---

### Post by WarrenKarl on 2010-01-13
I am a relatively unsophisticated users.  I have to work at home
and in the office on a number of computers and thought that
a usb startup disk would be great.  I am running 9.10.  I
bought a Kingston 16gb stick and spent four days trying everything
possible.  The Ubuntu usb startup disk creator fails consistently.

I follow the directions on Ubuntu, but then the computer won't
boot on a second computer.  I get a screen that asks me for
my preferred language.  I answer.  Then I choose to run ubuntu
without changing my computer.  It goes into the Ubuntu symbol
screen and then gives me a long list of errors.

I have tried all sorts of formatting.  I have even tried using
the dd command.  I have tried installing directly to the usb stick
as if it were my only hard drive.  I removed my hard drive for this exercise.  After much frustration, I am on the verge of giving up.  

If someone has successfully set up a usb startup disk, please
tell me the steps that you used.

Thanks.

---

### Post by C.S.Cameron on 2010-01-14
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

Unetbootin seems more reliable than usb-creator on large flash drives to me.
However if you use it to make a persistent the line to be modified is in syslinux/text.cfg

You might also try disabling your hard drive and try a full install using the Install Ubuntu option on the Live CD.

---

### Post by WarrenKarl on 2010-01-14
Thank you C.S.  I will try it over the weekend and let you know
what happened.

---

### Post by maestrobwh1 on 2010-01-14
I guess I was a bit obtuse.  If I wanted to do this, I need 3 partitions?  One for the extracted iso, one for home-rw and one for casper-rw?

I was assuming one partition was needed for the extracted iso and one was needed for the persistence.

I did try making one partition for the install, one ext2 called casper-rw for the persistence and added persistent to the end of the syslinux.cfg but when it booted, it dod not show the casper-rw space.

Is the casper-rw for all directories except /home? and the home-rw for /home/ubuntu?

---

### Post by C.S.Cameron on 2010-01-15
I think you can get by with just the casper-rw partition.
I Like adding the home-rw partition to keep things seperate.
Both of these partitions are invisible when booted from the thumbdrive.
You should find that your thumbdrive is persistent.
Yes home-rw is for the home folder only and casper-rw saves all the other stuff.

---

### Post by maestrobwh1 on 2010-01-15
Since I already had significant modifications, I figured I would try a few hybrid things.  I first tried just to make an ext2 partition and then copy my 2.8 GB casper-rw image to that partition and added -- **persistent** to the approgroate lines in syslinux.cfg.  Booted fine but no persistence.  I then removed the casper-rw, shrank the partition and added a new ext2 partition called casper-rw and then mounted the original casper-rw image (loop) and used the dump command from the mounted directory to the casper-rw partition.  Directory structure looked identical when I was done, no errors.  Booted the result.  Booted fine with but no persistence.  I double checked the spelling of persistent and its location in the boot line and it seemed fine.

I reformatted card, fat 32 (yuck) and just made it big enough to hold the boot files and my casper-rw then used the Ubuntu tool for making a boot disk and I was back in business. 

I will just make sure I don't write to the fat OS partition in other situations.  I used the hitachi driver for my sd card reader in windows so it will see multiple partitions so this works.

Not sure why the other methods would not see the casper-rw.  I never lose data except from fat.  Imagine that.  That filesystem stinks.

---

### Post by C.S.Cameron on 2010-01-15
sounds like it should have worked. Note that there should be a space between -- and persistent.

I know ext3 works for home-rw but I have never checked if it works for casper-rw.

I did notice while watching usb-creator work that the casper-rw file usb-creator makes has a ext2 file system inside of it.

---

### Post by maestrobwh1 on 2010-01-16
I figured it out: if the system unetbootin partition is ext2/3, it creates another file called extlinux.conf.  This is the one that I needed to append "persistent" to the append line.

---

### Post by C.S.Cameron on 2010-01-16
Yea, I gave it a try with just a casper-rw partition formatted ext2.
This seemed to work ok, the home folder ended up there instead of in home-rw.
I could not find extlinux.conf so I am still adding persistent to (cdrom)/syslinux.conf

Formatting in ext2 may be a good idea for pendrives as it is not a journaling file system like ext3, ext4 or reiserfs, and shoulld not cause as much wear on the flash drive.(or so I understand).

---

### Post by maestrobwh1 on 2010-01-16
How odd.  I wonder why I have a second config file?  No matter, it still works.  My /cdrom is mounted ro and I can't write there even as root.  I suppose I could issue a remount command but I made the system partition with only 50 MB extra anyway.

```
 sudo mount -n -o remount,rw /cdrom 
```

I notice firefox is clunky again.  For some reason when it writes from an image file on fat32, it is faster.  I disabled some stuff in firefox an it is usable.

[edit] 
There were issues with ownership of my home directory after using the dump command so I mounted my casper-rw directory and just removed /ubuntu from /home and after it reinitialized, I just had to reconfigure my desktop. I should have worked around this by allowing root login while running the casper-rw image file on the FAT-32 install so that I could have chown'ed the home directory back the the ubuntu user (dump is SUPPOSED to maintain ownerships but did not).

Also, after doing a blkid to make sure what my casper-rw was mounting as, I did a 
```
 sudo tune2fs -o journal_data_writeback /dev/sdb2 
``` 

I then added this command to /etc/rc.local

Then I edited mtab, because I did a "dump" of my original filesystem that was a casper-rw image on fat-32, the mtab entry was still there listing the system (boot)/dev/sdb1 as vfat, so I changed that to ext3 and options to defaults,relatime,ro (I don't want to write to it, and can just use remount it rw if I need to).

**Question @ C.S.Cameron: **Does the journal_data_writeback relieve some of the hammering that would normally occur to flash media?  If not, I can just revert it back to ext2 using a post I found.

---

### Post by WarrenKarl on 2010-01-17
Hi,

I seem to be having some problems with writing this, so I hope that I do not wind up with 5 replies.  If so, please excuse me.

I tried CS's strategy and it failed.  I formatted by 16gb Kingston stick
as suggested, but Unetbootin did not create a workable stick.  It booted
but quickly wound up giving me a bunch of errors.  It didn't matter if
I made 2 or 3 partitions.  One FAT32 and the other 2 (or 1) ext2.

I tried again taking out the hard drive and installing directly to the stick.  This also failed.  The Ubuntu startup stick command also failed.

I have now been at this for 5 days.  Without any other thoughts, I think I will give up.

Thanks for the help.

---

### Post by maestrobwh1 on 2010-01-18
This sounds like maybe you have a flash memory device that is incompatible or has some other issue.  **Can you experiment with another stick you have around?**  You can use as small as a 1 GB stick just to see if the method works for you.

It just seems like you tried a lot of things and NONE of it worked.  I have a guess that although the boot sector was written properly, the other files might be written to bad blocks or the disk gemoetry is just unusual (can't imagine that from kingston though).   Try the install on another device, like a cheap pen drive.

If your device is behaving this way, keep in mind **THERE IS A SMALL PERCENTAGE OF A CHANCE THAT YOU CAN KILL YOUR FLASH DEVICE** by doing some of the following.  These methods are NOT considered unsafe but sometimes in rare cases flash media just "dies" prematurely.   I had an ADATA 8GB sd card fail after a month but that company gives a limited lifetime warranty and replaced the card.  I was having an issue similar to yours.

If that works, and I am not sure what your kingston stick is (usb pen or SD) but if another drive works using these methods, you can try this on your kingston stick:

Mount the drive in XP and do a FULL format in NTFS.  Why?  It seems to wipe out all bits of data and seems to force bad blocks to be mapped out.  Ii did this before and it worked.  Then you can reformat it to ext3/2.  I have read that syslinux still has issues reading fat32, and my experience suggest that might be true.  If you don't have access to XP, I think you can use parted from the command line and do a full format to some filesystem.  You could also try formatting it to ext3 using gparted (front end for parted), then use this command from the terminal:

sudo fsck -f -c /dev/sdaX 

where x is your device.  This checks for bad blocks and writes them out.  Keep in mind that this seems to take a very long time on flash media.  Let it run over night.  You could also try the badblocks command
[http://linux.about.com/library/cmd/blcmdl8_badblocks.htm](http://linux.about.com/library/cmd/blcmdl8_badblocks.htm)

If you want to use the Ubuntu tool, format a 1GB partition to fat16 using gparted.  Choose persistence but keep it at 128.  See if that boots, make a ffew changes (like change your desktop background) and reboot and see if that is persisting.  If so, then this part is working.  

I am not sure if this part works, but you need to create a casper-rw partition in ext2 (2GB limit) or ext3 (no limit in size), and rename the casper-rw file on the fat16 boot partition (so that it is ignored), and do like above to see if your changes are taking effect.  If not, but your stick is now working, use my unetbootin instructions in my previous post.

---

### Post by C.S.Cameron on 2010-01-18
I have had problems with making Kingston Traveler sticks persistent.
More trouble with usb-creator than unetbootin and more trouble with 8.10 and 9.10 than 9.04.
After several attempts it always seems to work for me though.

With a 16GB stick I would try a full install. These are almost always successful.

---

### Post by maestrobwh1 on 2010-02-20
Yes, I found this to work well.  On another device, the fat32 setup seems to work just fine. The issue was on an older SD card so maybe it is wearing out and/or it just needs a low-level wipe kind of format.

---

