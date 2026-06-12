---
title: "Using Gparted to increase Ubuntus partition"
date: 2010-05-26
forum: General Help
---

### Post by alxpenguin on 2010-05-26
Can I use Gparted to downsize my windows xp partition (which has 80 free gigs) and increase my Ubuntu partition to give it more diskspace? I defragged windows xp and all the files are at the beggining of the disk.

I cant take a print screen cuz of space but heres what gparted shows:

                                                                                                                      total              used             Free       options

/dev/sda1                                         ntsf                                      90bg                  10                    10             boot
/dev/sda2 (keychain)   extended                            2.5gb
    /dev/sda5(keychain)                ext3                                      2.33gb    2.29gb           35mb         
    /dev/sda6(keychain) linux swap                   174mb

It lets me resize the first one but not the other ones as of right now. Will that change if I resize the windows partition??

---

### Post by drs305 on 2010-05-26
Yes you can. It's probably safer to shrink the Windows partition with Windows software. The rest you can do with Gparted from the LiveCD. 

One thing you are going to have to do after shrinking Windows is expand the extended partition (which holds all your Linux logical partitions) before trying to enlarge your Linux partition.

I wrote a guide about expanding the Linux / partition. Start about half way down the first post, as the first section deals with a bug that prompted the post in the first place.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by alxpenguin on 2010-05-26
Is there anyway to boot the LiveCd from Linux? Windows is being terrible and when I reboot it wont start up. even with the assisted boot it wont work. Anmy tips??

---

### Post by Miljet on 2010-05-27
You don't boot the Live CD from Linux or from Windows. You boot the Live CD from the Live CD itself. Just insert the CD and reboot from whatever operating system you are currently using.

---

### Post by alxpenguin on 2010-05-27
Thats the deal it wont go to the livecd when I reboot from windows, even when using the assisted reboot

---

### Post by Elfy on 2010-05-27
I assume that you have used the livecd previously - you need to set up whatever you are booting so that it boots from cd first - possibly you have a boot option/menu if not you'll need to set BIOS to do so.

If you've not booted with the livecd previosuly - did you burn it as an iso or image - not as data

---

### Post by Elfy on 2010-05-27
This is completely tied up with your other thread - please do not open duplicates. 

Closing this one - dupe here [http://ubuntuforums.org/showthread.php?t=1489310](http://ubuntuforums.org/showthread.php?t=1489310)

---

