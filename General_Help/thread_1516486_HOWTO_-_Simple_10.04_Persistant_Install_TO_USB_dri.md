---
title: "HOWTO - Simple 10.04 Persistant Install TO USB drive."
date: 2010-06-23
forum: General Help
---

### Post by umv on 2010-06-23
Okay, I'm doing this from memory, so hopefully I won't forget any steps.

I used the 10.04 "alternative" ISO. I'm assuming you will start in Windows. I used a 16g USB for the persistent install.
 
1. Download the ISO.

2. Use "unetbootin" to make USB 1 (I used a 4g) into an installer drive. (You could make a boot CD instead if you wanted. My netbook doesn't have a CD so I did it this way.)

3. Boot from USB 1 (or the CD).

4. After the install has started, insert USB 2 into another slot.

Now the tricky part...

5. When you get to the part about partitioning, choose "Manual". You should see two drives (if not, then go back, to the previous screen and remove/re-insert USB 2 and try again. If you still can't see it, then stop here - you fail).

First in the list will be the computer's hard drive. DO NOT MAKE ANY CHANGES TO THE HARD DRIVE! If you do by mistake, then DON"T SAVE. Just go back and come at it again.

You should also see the USB 2 drive as /dev/sdb or /dev/sdc (usually...YMMV).

6. Remove any partitions on the USB 2 drive.

7. Decide what size your partitions will be. Make a new PRIMARY partition for Windows use (IF you want a partition that Windows can see.) Choose filesystem FAT32 and mount point as /windows. (I made this partition 10g.) This partition should be NOT BOOTABLE.

IMPORTANT:
MAKE THE WINDOWS ACCESSIBLE PARTITION THE *FIRST* PARTITION ON THE USB DRIVE! I have Win7 - it would NOT read that partition unless it was the first partition. It wanted to format it. When I tried that, it formatted the FIRST partition (which was my Ubuntu ext4 partition - bye bye Ubuntu install). If you make the fat32 partition the first partition then Win7 won't have a problem with it.

8. Make a PRIMARY partition for Ubuntu to be installed to. I made it 4g size. Choose filesystem EXT4 and mount as "/". Make this partition BOOTABLE.

9. Make a partition for swap. I used 2g (the remaining space). Choose logical (extended? can't remember) but NOT PRIMARY. Choose filesystem SWAP.

10. Save all that and proceed and it will inform you that it will format this as fat32 and that as ext4 and the other thing as swap. MAKE SURE that only partitions on the USB will be formatted. (I.e., don't format your Windows drive by mistake.) 

(If you have a dual-boot system like me, then at this point, it will also tell you that it is going to format the swap partition on your hard drive - that won't hurt anything so long as that is the ONLY thing on the hard drive that gets formatted.)

11. Proceed with the install. It will eventually ask if you want to install grub - say YES. It will install grub to the USB 2 drive. It will find your Windows install (and your Lunix if you have dual-boot like me) and will add them to the grub menu on the USB drive - you can remove those manually later if you want.

12. Finish install and reboot. Remove USB 1 and boot from USB 2. Should give you the new grub menu. Boot into Ubuntu and TADA! It's persistent!

You now have about 2g free on the Ubuntu ext4 partition, and whatever size you chose on the Windows partition. You might want to do this to make a shortcut on the Desktop to the /windows directory:

cd /home/<your user name>/Desktop
ln -s /windows Windows_Files


If this helps anybody, then you owe me a beer.

---

### Post by C.S.Cameron on 2010-06-23
Very important, at the end of partitioning you must select the Advanced tab and then tell it to install grub at the root of the USB flash disk, (ie sdb and not sdb1).
If you do not do this you will overwrite the MBR of the internal HDD and you will require the USB drive plugged in to boot it.
This can become an annoyance if it contains Windows boot loader.
I usually check the format box on the ext partitions but not the FAT32 one.
There is not an option to format the swap space.

It might not hurt to add an option for adding a separate ext2 "/home" partition also.
You can use primary for the swap partition but Logical is ok.

---

### Post by dcstar on 2010-06-24
> **umv said:**
> 
.........
12. Finish install and reboot. Remove USB 1 and boot from USB 2. Should give you the new grub menu. Boot into Ubuntu and TADA! It's persistent!
.........

You do understand that basically doing a standard install of Ubuntu onto a USB drive bypasses all the deliberate features that the proper "USB Startup Disk" has to minimise writes onto the device (and therefore extending its life), don't you?

---

### Post by C.S.Cameron on 2010-06-24
> You do understand that basically doing a standard install of Ubuntu onto a USB drive bypasses all the deliberate features that the proper "USB Startup Disk" has to minimise writes onto the device (and therefore extending its life), don't you? 

A flash drive is good for 10000 writes, a 16GB flash drive should be good for (16GB/(1GB/5min)) x 10000 = 800000 minutes = 13333 hours = 333 work weeks.

I'm not sure I have ever had a mechanical hard drive last over 5 years. 
In 5 years you will probably be able to replace a 16gb flash drive for under 5 bucks.

---

### Post by umv on 2010-06-24
> **C.S.Cameron said:**
> Very important, at the end of partitioning you must select the Advanced tab and then tell it to install grub at the root of the USB flash disk, (ie sdb and not sdb1).
If you do not do this you will overwrite the MBR of the internal HDD and you will require the USB drive plugged in to boot it.
This can become an annoyance if it contains Windows boot loader.
I usually check the format box on the ext partitions but not the FAT32 one.
There is not an option to format the swap space.

If you say so.

I don't remember having to diddle with Advanced or having to choose where grub was installed. I do remember being a bit nervous about where it would install, and being relieved when it installed to the proper place. (Not very nervous though...I've been using Linux since Slackware 1.0 came out in '93 so I figured I could fix my MBR if it got hosed. But it didn't.)

Perhaps because I used the alternative iso? Dunno. I personally don't use Ubuntu so I'm not that familiar with all the quirks. I did it as a favor for a guy in a wheelchair at the local library whose netbook hard drive failed and he couldn't afford a replacement. So he asked me to take his 16g thumbdrive and whip him up a persistent Ubuntu.

Since I couldn't find any nice and easy HOWTOs I figured I might as well write up how I did it.


> It might not hurt to add an option for adding a separate ext2 "/home" partition also. You can use primary for the swap partition but Logical is ok.That adds complexity. I wanted to try to keep it as simple as I possibly could.

It's a HOWTO. Aren't all HOWTOs automatically public domain? If they aren't they should be. Feel free to mod it and add any complexity that floats your boat. Use it as the basis for the Big Mother of all Ubuntu USB HOWTOs if you want.

I wouldn't though...it's pretty much a little wanker of a HOWTO and you could probably do better starting over from scratch. :D

---

### Post by umv on 2010-06-24
> **C.S.Cameron said:**
> A flash drive is good for 10000 writes, a 16GB flash drive should be good for (16GB/(1GB/5min)) x 10000 = 800000 minutes = 13333 hours = 333 work weeks.

I'm not sure I have ever had a mechanical hard drive last over 5 years. 
In 5 years you will probably be able to replace a 16gb flash drive for under 5 bucks.

Yea. What he said.

I couldn't care less about wearing out some goofy little USB stick. I've got old 1g and 2g sticks that I haven't used in years - they aren't anywhere near being worn out, I just don't use them anymore. Got another little pile of older SD cards. Same deal there.

Besides, the one I used belonged to the wheelchair guy and I told him it would wear out in a couple of years. He didn't give a hoot either.

---

