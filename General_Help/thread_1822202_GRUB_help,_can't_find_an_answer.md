---
title: "GRUB help, can't find an answer"
date: 2011-08-10
forum: General Help
---

### Post by match417 on 2011-08-10
I've been googling for hours, now it's past midnight and I want to solve this, but I want to sleep..agh dilemmas. So I'm putting my mind at ease by posting a simple question that I'm sure I'll get an answer to by the morning...that way I can at least get my mind off of this...

I have been running Ubuntu 11.04, and I decided to install OpenSUSE 11.3. After the install process, grub only showed OpenSUSE. Now I'm trying to add my kernel and nothing is working. Chainloader didn't work and I'm stuck. I've looked at a lot of grub files online and I can't mimic one so that I can boot into 11.04 again. Currently it looks like this...the main thing I don't understand is the root=/dev/disk/blah.blah.blah.number.number.number, when I add in the "root=/dev/disk/stuff" do I copy everything from that section of one of the other options? I would appreciate it if someone can tell me what the "root=/dev/disk/stuff" is about instead of telling me what I should add in to the grub file...good night all! Here is menu.lst

```

###Don't change this comment - YaST2 identifier: Original name: linux###
title Desktop -- openSUSE 11.3 - 2.6.34-12
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part3 resume=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part5 splash=silent quiet showopts vga=0x317
    initrd /boot/initrd-2.6.34-12-desktop

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3 - 2.6.34-12
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.34-12-desktop root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x317
    initrd /boot/initrd-2.6.34-12-desktop

title Ubuntu 11.04, Natty Narwhal, 2.6.38-10
    root (hd0,1)
    kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part3
    initrd /boot/initrd.img-2.6.38-10-generic
```

---

### Post by mikewhatever on 2011-08-10
Those are just partitions' identifiers, or, in other words, ways to refer to partitions. A more human readable way would be /dev/sda1, but that may change it you repartition. In Suse, run **ls /dev/disk/by-id/** to see all available choices. Obviously, the entry for Ubuntu can't be the same as for Suse, because they are on separate partitions.

---

### Post by YesWeCan on 2011-08-10
There are a number of different ways to specify a disk partition.
You can see them if you go to /dev/disk and you will see directories for each:
```
$ ls /dev/disk
by-id  by-label  by-path  by-uuid
```
OpenSUSE is using the "by-id" specifier which is very robust because it includes a unique disk serial number. Ubuntu now normally uses the "by-uuid" specifier which is fine unless you clone a partition and don't change its uuid. Sometimes Ubuntu uses a device path like /dev/sda5.

You possibly need this for your Ubuntu entry: root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part[COLOR="Red"]2[/COLOR]

OpenSUSE uses legacy Grub. You need to find a legacy Grub guide to explain how to add your Ubuntu to menu.lst.

---

### Post by raja.genupula on 2011-08-10
> **YesWeCan said:**
> There are a number of different ways to specify a disk partition.
You can see them if you go to /dev/disk and you will see directories for each:
```
$ ls /dev/disk
by-id  by-label  by-path  by-uuid
```OpenSUSE is using the "by-id" specifier which is very robust because it includes a unique disk serial number. Ubuntu now normally uses the "by-uuid" specifier which is fine unless you clone a partition and don't change its uuid. Sometimes Ubuntu uses a device path like /dev/sda5.

You possibly need this for your Ubuntu entry: root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part[COLOR=Red]2[/COLOR]

OpenSUSE uses legacy Grub. You need to find a legacy Grub guide to explain how to add your Ubuntu to menu.lst.
i gad tried this on my terminal but i get as same what i have given , no other things as you said 

linux@genupulas:~$ ls /dev/sda1
/dev/sda1
**this is what i got after typing that no terms like label path uuid **

---

### Post by mikewhatever on 2011-08-10
Who told you to use ls? Try **sudo tune2fs -l /dev/sda1** instead.

---

### Post by haresear on 2011-08-10
> **raja.genupula said:**
> i gad tried this on my terminal but i get as same what i have given , no other things as you said 

linux@genupulas:~$ ls /dev/sda1
/dev/sda1
**this is what i got after typing that no terms like label path uuid **

I think you misunderstood the command. /dev/disk is a directory with the four subdirectories:
by-id  by-label  by-path  by-uuid

Inside each of these subdirectories are the corresponding names of all your partitions (actually named links to all your partitions) by the method indicated in the subdirectory name.

For example "ls /dev/disk/by-id" will list the id names of all your partitions. "ll /dev/disk/by-id" will show you the device path linked to each name.

---

### Post by match417 on 2011-08-10
So since my bootloader is in SUSE, and since SUSE uses the dev/disk/by-id identifier and ubuntu uses the dev/disk/by-uuid identifier should I use by-uuid since I'm running ubuntu or by-id since the bootloader is in SUSE.

Also, My partitions are setup like this
dev/sda1 Ubuntu
dev/sda3 SUSE /
dev/sda4 SUSE /Home

---

### Post by match417 on 2011-08-10
I just tried inserting the uuid of sda1 where I have Ubuntu loaded, but it's not booting still.

The weird thing is that I changed the by-id to a uuid and when I rebooted, tried to open ubuntu, didn't work, then turned back on SUSE, my uuid was after the by-id. I tried running just a uuid instead of by-id and this is what happened. Now ubuntu (or suse) added resume uuid to show after the by-id

```
title Ubuntu 11.04, Natty Narwhal, 2.6.38-10
    root (hd0,1)
    kernel /boot/vmlinuz-2.6.38-10-generic root=/dev/disk/by-id/ata-ST95005620AS_5YX0XWGZ-part2 resume=/dev/disk/by-uuid/45f7af51-628b-4487-9fc2-975c39d7c25f
    initrd /boot/initrd.img-2.6.38-10-generic
```here is what I get when I sudo tune2fs -l /dev/sda1 (partition with ubuntu)
```
Filesystem volume name:   <none>
Last mounted on:          /media/disk
Filesystem UUID:          45f7af51-628b-4487-9fc2-975c39d7c25f
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              6111232
Block count:              24413696
Reserved block count:     1220684
Free blocks:              19974468
Free inodes:              5886849
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1018
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Aug  4 06:01:05 2011
Last mount time:          Wed Aug 10 07:27:15 2011
Last write time:          Wed Aug 10 16:11:50 2011
Mount count:              19
Maximum mount count:      29
Last checked:             Thu Aug  4 06:01:05 2011
Check interval:           15552000 (6 months)
Next check after:         Tue Jan 31 05:01:05 2012
Lifetime writes:          28 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      34b4cc29-96d2-45a3-8e82-c168fe04b524
Journal backup:           inode blocks
```

---

### Post by match417 on 2011-08-10
whenever I reboot it and I try to choose ubuntu, it says

filesystem type unknown 0x5
kernel..blah blah blah root..blah blah blah resume..blah blah blah
error code 17, cannot mount filesystem

I know suse can read my ext4 filesystem because my data partition is in ext4 just like my ubuntu load and I can navigate through the ubuntu filesystem via suse root fine. So why is it that I can't boot to ubuntu? This is getting irritating..

Can I just do away with the bootloader on the SUSE partition and put it on the Ubuntu part? I like the way the suse grub looks..but I don't care anymore, I want it to boot.

---

### Post by oldfred on 2011-08-10
With grub legacy you  have to use hd0,0 but on the kernel line it still is sda1.

Examples that should work:

title    Most Current Ubuntu on sda1
root    (hd0,0)
linux   /vmlinuz root=/dev/sda1 ro quiet splash
initrd  /initrd.img

Grub to grub2:
title    Ubuntu on sda1
root (hd0,0)
kernel /boot/grub/core.img
boot

---

### Post by oldfred on 2011-08-10
To reinstall grub2 for Ubuntu:

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

run this and it should find Suse or else we have to add a custom entry to 40_custom to boot it.

sudo update-grub

---

### Post by mikewhatever on 2011-08-10
Well, how about ata-ST95005620AS_5YX0XWGZ-part1? Alternatively, why not try the by-uuid option? At least it's clear which partition is which.

Here is a good example of dual booting Ubuntu and Suse with the latter in charge of the MBR.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)

...here is the entry used for Karmic
```

title Ubuntu 9.10 Karmic Koala
root (hd0,5)
chainloader (hd0,5)+1 
```

...that would translate to something like this for you
```

title Ubuntu 11.04 Natty
root (hd0,0)
chainloader (hd0,0)+1 
```

---

### Post by match417 on 2011-08-10
> **oldfred said:**
> With grub legacy you  have to use hd0,0 but on the kernel line it still is sda1.

Examples that should work:

title    Most Current Ubuntu on sda1
root    (hd0,0)
linux   /vmlinuz root=/dev/sda1 ro quiet splash
initrd  /initrd.img

Grub to grub2:
title    Ubuntu on sda1
root (hd0,0)
kernel /boot/grub/core.img
boot

awesome, thanks oldfred, it works great. Both distros work perfectly. I only used the first section you suggested, the second part I didn't use.

Just to satisfy my curiosity, what is "ro quiet splash"?

---

### Post by match417 on 2011-08-10
> **mikewhatever said:**
> Well, how about ata-ST95005620AS_5YX0XWGZ-part1? Alternatively, why not try the by-uuid option? At least it's clear which partition is which.

Here is a good example of dual booting Ubuntu and Suse with the latter in charge of the MBR.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)

...here is the entry used for Karmic
```

title Ubuntu 9.10 Karmic Koala
root (hd0,5)
chainloader (hd0,5)+1 
```...that would translate to something like this for you
```

title Ubuntu 11.04 Natty
root (hd0,0)
chainloader (hd0,0)+1 
```

I did, I replaced by-id with the uuid and when I rebooted it ended up adding the uuid after the by-id line, so I had both instead of one, and it still didn't work. oldfred chimed in and it works now, I think because it's suse's grub legacy it's a little different than the regular ubuntu grub. Thanks for all the help though, I haven't worked with grub this extensively before, it's been a learning experience.

I was two minutes away from putting my ubuntu DVD in and running it off of the DVD to go into ubuntu and delete SUSE so I would have my ubuntu load back.

Thanks guys!

---

### Post by oldfred on 2011-08-10
ro is read only on kernel boot, quiet is not to show all the boot lines and splash is to show something/Ubuntu logo.

Kernel parameters:
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

---

### Post by match417 on 2011-08-10
oh, that makes more sense, I thought quiet splash was all one, and it didn't make sense why the logo would come up if it said quiet splash. That makes more sense.

---

