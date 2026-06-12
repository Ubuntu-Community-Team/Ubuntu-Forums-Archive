---
title: "Countless Problems. Please help!"
date: 2010-02-16
forum: General Help
---

### Post by Ignado on 2010-02-16
So my problems all started today when i was downloading videos on Transmission the bit torrent client. My computer suddenly hung up and i was forced to restart the computer manually since the computer was not responding at all. Once restarted my computer would hang up as soon as i started using anything that involved the Internet and no amount of restarts did anything. 

First thing I did was load my ubuntu disk in and start a live session. While in the live session i ran a fsck on my / and my /home partitions. The /home partition had some errors which were then fixed. I then logged back into ubuntu normally and still had the same problems whenever i did anything with the internet. 

Next thing i know a bad sector error popped up for my hard drive with the / and /home partitions, the same error i had on the hard drive i just replaced with this hard drive. I then logged into windows and ran windows disk checker and Western Digitals disk checker and neither of them reported any problems on either this hard drive or the other one that i just replaced. 

So i decided to call the bad sector error off as a false positive. I then came across an article about disabling IPV6. So i followed the steps and restarted and now using the Internet doesn't hang my computer up anymore. But this was not the end of my problems.

As i was copying a file from my windows 7 mounted hard drive over to netbeans in ubuntu my computer suddenly hung and then endless error messages popped up. So i had to manually turn my computer off and when i turned it back on my filesystem was no longer mounted. I then booted back into the live cd and ran fsck again. This time it found problems on my / partiton. There where a couple of orphaned inodes and thats it i think. 

For the past hour i have been logged in and it has not crashed yet but whenever i mount my one hard drive ( and it happens with just one ) my desktop disappears and the folder for the harddrive auto closes and any other file folders i have opened. I have 5 harddrives other then my ubuntu hard drive and only one of my random storage drives has this problem.

Also, and i dont know if its related, but my modem keeps losing signal and every time my computer hung up the internet would go out of my laptop.

I am running Ubuntu 9.1 and dual booting Windows 7. I have 6 separate hard drives and on one harddrive three separate partitions for the swap, /, and /home.

I think i have been as through as i possibly can i hope someone can help. thanks!

---

### Post by Richard1979 on 2010-02-16
Are you mounting more than one disk as /home?

---

### Post by Ignado on 2010-02-16
No just one. The other harddrives are formated to fat32 for storage and one as ntfs for windows. 

Update: While creating this post Firefox hung up for about a minute and my processor usage shot up to about 90%. Nothing else but Firefox is even opened.

---

### Post by pbpersson on 2010-02-16
> **Ignado said:**
> 

Next thing i know a bad sector error popped up for my hard drive with the / and /home partitions, the same error i had on the hard drive i just replaced with this hard drive. I then logged into windows and ran windows disk checker and Western Digitals disk checker and neither of them reported any problems on either this hard drive or the other one that i just replaced. 

Typically in Linux the file system for / and /home would be ext3 or ext4 and yet you said you ran a disk check in Windows for these partitions.  Windows does not recognize ext anything.

What file system are you using for / and /home?

---

### Post by Ignado on 2010-02-16
> **pbpersson said:**
> Typically in Linux the file system for / and /home would be ext3 or ext4 and yet you said you ran a disk check in Windows for these partitions.  Windows does not recognize ext anything.

What file system are you using for / and /home?

Yeah sorry i meant i used the windows disk checker on my other disk that used to be my /home till it had bad sector errors and ran Western Digital check on my / and /home harddrive which is formated to ext2 as far as i know. I just tried opening up  gparted to check but i got this error " Failed to execute child process "gksu" (Input/output error) ".

---

### Post by Ignado on 2010-02-16
Another update:

After the error trying to get into gparted i tried opening up one of my folders but nothing would open and restart wouldnt even work. So i manually restarted my computer and grub bootloader is not working now so i booted back into a live cd.

---

### Post by pbpersson on 2010-02-16
This hard drive that is giving you all the problems which is a new hard drive you just installed because the old hard drive was giving you problems......what kind is it and how is it interfaced with the motherboard?  Is this a SATA drive?  UltraIDE?  Is it connected directly to the motherboard or does it go through a controller that was later added to the computer?

Have you added any new hardware recently?

Is the motherboard BIOS up to date?

---

### Post by Richard1979 on 2010-02-16
>  Failed to execute child process "gksu" (Input/output error) "

"gksu" is a command used to execute a Gnome window as root (also known as "gksudo").
Were you running this under root?
You can run a pure root Terminal by typing "sudo su".

---

### Post by Ignado on 2010-02-16
> **pbpersson said:**
> This hard drive that is giving you all the problems which is a new hard drive you just installed because the old hard drive was giving you problems......what kind is it and how is it interfaced with the motherboard?  Is this a SATA drive?  UltraIDE?  Is it connected directly to the motherboard or does it go through a controller that was later added to the computer?

Have you added any new hardware recently?

Is the motherboard BIOS up to date?

Its a Western Digital 750 GB caviar black. Sata drive which is connected directly to the computer. No new hardware for atleast a couple months and my BIOS is up to date as far as i know. It is a EVGA 680i. 

I opened up gparted in the live cd and my harddrive with / and /home mounted is not even listed, all the other ones are though. Im gonna pull open my computer and make sure these cables are all snug.

---

### Post by Ignado on 2010-02-16
> **Richard1979 said:**
> "gksu" is a command used to execute a Gnome window as root (also known as "gksudo").
Were you running this under root?
You can run a pure root Terminal by typing "sudo su".

Terminal would not even open for me. Nor would anything else.

---

### Post by pbpersson on 2010-02-16
I recently had a problem with a SATA 2 hard drive because I was using it with an older SATA 1 motherboard.  I had to install a jumper on the hard drive to drop the data transfer speed down to 1.5 Gbps so the motherboard could handle it.

I don't know if that helps.  I am quickly running out of ideas here.

---

### Post by Ignado on 2010-02-16
I unplugged my sata cable and r plugged it in and my computer read my harddrive again. But now onto more problems. This is what i got when i tried logging back into ubuntu....

[]("http://img638.imageshack.us/i/018v.jpg/")[[IMG]http://img69.imageshack.us/img69/6214/018nm.jpg[/IMG]]("http://img69.imageshack.us/i/018nm.jpg/")

---

### Post by pbpersson on 2010-02-16
That tells us that your SDA hard drive is toast.  We knew that, the question is why?

---

### Post by pbpersson on 2010-02-16
If you can boot into the live CD and can get to a terminal prompt, post the output of:

fdisk -l

that is a lower case "L" and not the number one.

I am assuming that if you are on the live CD you do not need a "sudo" in front of that.

Then you can explain to us exactly which partitions on which drives are giving you which problems because with 6 hard drives this could get confusing

---

### Post by Ignado on 2010-02-16
Unplugged two of the harddrives since they were not being used and getting in my way when unplugging and replugging in my / and /home drive which we can now refer to as sda. But here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006ba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648       91201   703277505    5  Extended
/dev/sda5           89986       91201     9767520   82  Linux swap / Solaris
/dev/sda6            3648       89984   693501889+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa1aba1ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18242   146521088    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e089d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    b  W95 FAT32

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82f182f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    b  W95 FAT32

```

sdd was the one i was refering to before that would make all the file windows close. sda is obviously my / and /home harddrive and the other two havent really had an effect on anything in any way from what i can tell.

---

### Post by pbpersson on 2010-02-16
Can you also post the output of your /etc/fstab file?

---

### Post by pbpersson on 2010-02-16
It seems as though your connection between the motherboard and the sda drive is intermittent.  Bad cable?  Problem with the motherboard connector?  

There are a number of things that could cause this.....

---

### Post by Ignado on 2010-02-16
> **pbpersson said:**
> Can you also post the output of your /etc/fstab file?

```

ryan@ryan-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=99515298-dbb9-494e-b9f0-fab756710b89 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=8b67d68e-b554-40d6-bef2-bb4d4ce4f60c /home           ext3    relatime        0       2
# /dev/sdc5
UUID=3bc2aeba-dd38-4336-943a-7c7240618160 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Ignado on 2010-02-16
> **pbpersson said:**
> It seems as though your connection between the motherboard and the sda drive is intermittent.  Bad cable?  Problem with the motherboard connector?  

There are a number of things that could cause this.....

Did you come to this conclusion from my fdisk info? And if so what in the fdisk info told you this. . . just would like to know for my own personal knowledge. 

But this analysis seems quite right just from what i have seen switching my sata cables around.

---

### Post by pbpersson on 2010-02-16
> **Ignado said:**
> Did you come to this conclusion from my fdisk info? And if so what in the fdisk info told you this. . . just would like to know for my own personal knowledge. 

But this analysis seems quite right just from what i have seen switching my sata cables around.

Your fdisk and fstab info was requested so some expert could review and comment on them.  I don't see anything wrong off the top of my head, although I wonder where sda3 and sda4 are in the midst of this but I cannot think of this now, I need to get myself into work.

Ah....OK, I just looked at my fdisk and it is the same.

Yes, your setup looks fine - I am still suspecting hardware based on the experiences I have had with my computers here.


Phil

---

### Post by linuxguy2009 on 2010-02-16
My best advice is to wipe out your hard drive in question and install ANY other distro other than Ubuntu. Chances of 2 hard drives dying back to back is slim to none. I would say 99% of your problem is most likely the rush for release of 9.10 and the sheer number of problems that it comes with. Try out some distro thats not based on packages in Debian that are clearly labeled as 'UNSTABLE". Let us know how it goes then.

---

### Post by Ignado on 2010-02-17
After a lot of testing i came to the conclusion that my brand new hard drive was failing. I sent it back to newegg for a new one and now have ubuntu running as smooth as ever on one of my other hard drives. Thanks for the help!

---

