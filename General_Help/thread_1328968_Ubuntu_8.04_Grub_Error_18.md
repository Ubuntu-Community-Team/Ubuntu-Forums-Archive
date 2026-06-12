---
title: "Ubuntu 8.04 Grub Error 18"
date: 2009-11-16
forum: General Help
---

### Post by DrewJ21 on 2009-11-16
So I have tried searching the forums for help on this problem but none seem to fix my computer.

I have a Spartan D47V notebook with a Pentium 4 and 30gb hard drive.
Ubuntu has worked just fine for the last 2-3 months and all of a sudden yesterday I was using Firefox and it kept locking up so I restarted only to get the Grub error 18 message.

I'm fairly new to Ubuntu so if anyone can help it would be greatly appreciated.

---

### Post by coldReactive on 2009-11-17
This might help:

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

### Post by DrewJ21 on 2009-11-17
Thanks for the link coldReactive, but I'm looking for something to guide me through whatever I need to do to get my computer running again.

Do you have any other ideas?

---

### Post by DrewJ21 on 2009-11-17
bump

---

### Post by louieb on 2009-11-17
Its really weird to get GRUB error 18 any more. Mostly happens on computers built before 2000, or newer computers that have been upgraded with a large hard drive.  And since you have a small 30GB hdd, you should not have ever gotten that error. Maybe an indication of a problem somewhere else either hardware or the file-system

1st thing I would try is boot to an older kernel. Just to see if it will boot ok.

2nd thing I would do is use a live CD with Gparted on it. Start Gparted, right click on the the partition and select **check**. Then select apply. This will check the file-system for errors, fixing them if it can.

BTW  **coldReactive's **link does have the only works every time solution for a true GRUB error 18.

> This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

---

### Post by DrewJ21 on 2009-11-17
Thanks, like I said I have no idea what I am doing would you mind guiding me through it?

---

### Post by louieb on 2009-11-17
Do you get the GRUB menu when you boot to the hard drive?
Do you have a live CD - will the computer boot to it?

---

### Post by DrewJ21 on 2009-11-17
I don't get a menu for Grub, and I have a 8.04 live disk which I can boot to.
I have tried running the command:
sudo umount /dev/sda5 and get the output:
umount: /dev/sda5

I tried this after reading another thread, but I can't get any farther than that

---

### Post by DrewJ21 on 2009-11-17
I don't get a menu for Grub, and I have a 8.04 live disk which I can boot to.
I have tried running the command:
sudo umount /dev/sda5 and get the output:
umount: /dev/sda5: not mounted

I tried this after reading another thread, but I can't get any farther than that

---

### Post by louieb on 2009-11-17
press <esc> when booting see if that get you the grub menu.

boot to the 8.04 CD  open the places menu - removible media - see if you can browse the files on your hard drive.

---

### Post by DrewJ21 on 2009-11-17
I've tried to hit esc and I still get nothing.

---

### Post by louieb on 2009-11-18
Use your live CD.


[LIST]
[*]Go to System>Administration>Partition Editor.and run the check like I asked earlier? What were the results?
[*]Try browsing the hdd with the live CD. Do you your files and folder?
[*]Please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  and put the results.txt file in your next post.
[/LIST]

---

### Post by DrewJ21 on 2009-11-18
I am running GParted right now, but here is my RESULTS.txt:

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c1d6c1d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    56,098,979    56,098,917  83 Linux
/dev/sda2    *     56,098,980    58,605,119     2,506,140   5 Extended
/dev/sda5          56,099,043    58,605,119     2,506,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="f40b4150-e29e-4818-8524-2ef5d628c88e" TYPE="ext3" 
/dev/sda5: UUID="cc8e9e11-cc24-4ada-9ad3-2e7d918bad3f" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

---

### Post by DrewJ21 on 2009-11-18
contd:

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

---

### Post by DrewJ21 on 2009-11-18
SUCCESS!!!

After running GParted I restarted the computer and it booted up.

Thank you very much for all your help louieb!

---

### Post by louieb on 2009-11-19
Nice its working again. Thanks for letting us know. 
Please click on thread tool and mark as solved. It might help someone in a similar situation.

---

### Post by pewterbot9 on 2009-11-19
> **louieb said:**
> It might help someone in a similar situation.

??!!!?!?? But he didn't *do* anything except run partition editor, and take a look-see. Not even a check...at least, he didn't say he did. So he rebooted and everything was copasetic once more. That can happen, but nothing's been learned, and I don't see how this is going to be of any help.

---

### Post by louieb on 2009-11-20
>  But he didn't *do* anything 
Checking an ext3 partition w/Gparted runs:
```
e2fsck -f -y -v /dev/sda#
```

 e2fsck - check a Linux ext2/ext3 file system

-f force 
-y answer yes 
-v verbose

---

### Post by DrewJ21 on 2009-11-20
> **pewterbot9 said:**
> ??!!!?!?? But he didn't *do* anything except run partition editor, and take a look-see. Not even a check...at least, he didn't say he did. So he rebooted and everything was copasetic once more. That can happen, but nothing's been learned, and I don't see how this is going to be of any help.

Actually yes I did run a check, after running it I was able to boot up again.

---

