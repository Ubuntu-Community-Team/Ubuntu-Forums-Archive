---
title: "Duel boot ubuntu problem"
date: 2010-01-03
forum: General Help
---

### Post by andy1983 on 2010-01-03
Hi,

I had win7 on my laptop. Before sometime I install Ubuntu 9.10 and it worked fine. Bur later that I resize the partition using third party software. Now when I restart the system it is giving me an error 
[B]
GRUB Loading
error: unknown filesystem
grub rescue>[/B]

I am not able to access the harddrive. I am very new to ubuntu. I read the other article but I did not understand. Pls help:(

---

### Post by lindsay7 on 2010-01-03
Try this first. Type in the terminal

"sudo update-grub" without the quotation marks

---

### Post by andy1983 on 2010-01-03
do you want to say terminal mean the terminal window in ubuntu?

I typed the sudo update-grub at the start screen but it is giving error
**Unknown command 'sudo'**:confused:

---

### Post by lindsay7 on 2010-01-03
Can you boot to the recovery setup or the command line from any options that you get.

Try booting from the live Ubuntu cd and type this in the terminal and post the results.

Sudo fdisk -l

That is a small letter L.  This will tell us what is on your partitions.

---

### Post by andy1983 on 2010-01-03
I really dont know how to do that but there is a option when laptop starts System recovery.

I tried that also but gives the same error. Pls tell me how to do it.

---

### Post by lindsay7 on 2010-01-03
Ok, Do Not Mess with the System Recovery that you see. It is probably the Widows recovery option.

You need to have a Unbuntu install cd. and start you computer with it.  Do no do an installation. Just use it to start Ubuntu. find the terminal under Applications/accessories and type in sudo fdisk -l and post the results. This will show what in on your computer and you can get help from there.  I have to go off line now but will check tomorrow. Most likely someone else can help you tonight. You may just need to reset the grub menu and that first command I gave you may do that. or your repartition may have gone bad and your installation is messed up. The fdisk -l command will help show that. You may in the mean time want to download the Ubuntu alternet installation cd. It has a recovery option and you can use it to reinstall the grub menu if needed.

---

### Post by andy1983 on 2010-01-03
Thanks for the reply tha there is a hope:)
 but there is a problem. I don't have ubuntu CD but do have bootable pendrive. Will it work?

---

### Post by andy1983 on 2010-01-03
Thanks for the reply that there is a hope:)
 
I insert ubuntu 8.10 CD and then use first option Try ubuntu without installation and after that I use sudo fdisk-l command in terminal. Below is the result I got

[B]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/tracks, 19457 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31a431a3


    Device    Boot    Start      End              blocks        ID    System
/dev /sda1    *           1      3917        31463271        7     HPFS/NTFS
/dev /sda2           3918    19456    124817017+        f     W95 Ext'd (LBA)
/dev /sda5           3918      7282        27029331        7     HPFS/NTFS
/dev /sda6           8772    10368       12827871       83     Linux
/dev /sda7         10369    10444         610438+       82     Linux swap / Solaris
/dev /sda8         10445    15666       41945683+       7     HPFS/NTFS
/dev /sda9         15667    19456       30443143+       7     HPFS/NTFS
/dev /sda10         7283      8702     11406118+       83     Linux
/dev /sda11         8703      8771           554211       82     Linux swap / Solaris

[/B]I have attached the notepad also[B].
[/B]

---

### Post by Leppie on 2010-01-03
please [download meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") to the desktop and run it:
```
$sudo bash ~/Desktop/boot_info_script*.sh
```
and post the generated RESULTS.txt

---

### Post by andy1983 on 2010-01-03
Here is the result

---

### Post by Leppie on 2010-01-03
could you mount your ext4 partitions as ext3 and run the script again?
ext4 should be backwards compatible with ext3 and even ext2.

---

### Post by andy1983 on 2010-01-03
pls tell me how to do it!!!!

---

### Post by hatewindows7 on 2010-01-03
hey I got the same problem.....it is becuase grub is not reconizing the linux booting system....I fixed it using windows 7 installtion cd and fixing boot record 

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

follow this steps let me know if you need any help

---

### Post by Leppie on 2010-01-03
> **andy1983 said:**
> pls tell me how to do it!!!!
to mount it:
```
$sudo mkdir /mnt/sda1
$sudo mount -t ext3 /dev/sda1 /mnt/sda1
```

---

### Post by andy1983 on 2010-01-03
> **hatewindows7 said:**
> hey I got the same problem.....it is becuase grub is not reconizing the linux booting system....I fixed it using windows 7 installtion cd and fixing boot record 

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

follow this steps let me know if you need any help


It gives me a blue screen error:confused::confused:

---

### Post by andy1983 on 2010-01-03
> **Leppie said:**
> to mount it:
```
$sudo mkdir /mnt/sda1
$sudo mount -t ext3 /dev/sda1 /mnt/sda1
```

It gives me the following error 

[B]ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]:(

---

### Post by Leppie on 2010-01-03
> **andy1983 said:**
> It gives me the following error 

[B]ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]:(

i'm sorry, my fault. it should've been sda6 and sda10, sda1 is a windows partition.
so:
```
$sudo mkdir /mnt/sda6
$sudo mount -t ext3 /dev/sda6 /mnt/sda6
```

---

### Post by andy1983 on 2010-01-04
> **Leppie said:**
> i'm sorry, my fault. it should've been sda6 and sda10, sda1 is a windows partition.
so:
```
$sudo mkdir /mnt/sda6
$sudo mount -t ext3 /dev/sda6 /mnt/sda6
```

It is giving me the following error

[B]ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda6 /mnt/sda6
mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/B]

---

### Post by Leppie on 2010-01-04
could you then post the output of that suggested command:
```
dmesg | tail
```

---

### Post by andy1983 on 2010-01-04
> **Leppie said:**
> could you then post the output of that suggested command:
```
dmesg | tail
```

Here is the out put

[B]ubuntu@ubuntu:~$ dmesg | tail
[  184.147203] [drm] TV-14: set mode NTSC 480i 0
[ 1498.353289] eth0: link down
[ 1534.131211] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1642.030931] wlan0: authenticate with AP 00:1b:da:29:16:51
[ 1642.032581] wlan0: authenticated
[ 1642.032585] wlan0: associate with AP 00:1b:da:29:16:51
[ 1642.035125] wlan0: RX AssocResp from 00:1b:da:29:16:51 (capab=0x411 status=0 aid=1)
[ 1642.035131] wlan0: associated
[ 1642.036076] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1652.640204] wlan0: no IPv6 routers present[/B]

And also want to let you know that now I do have both CDs those are Ubuntu 9.10 Desktop and Ubuntu 9.10 Alternate Installation which has Rescue mode. I downloaded it as per previous reply from [lindsay7]("http://ubuntuforums.org/member.php?u=762393"). Will it help me?

---

### Post by Leppie on 2010-01-04
yes, try booting with one of those.

---

### Post by andy1983 on 2010-01-04
ok but how to reinstall that grub? How to use rescue mode? I tried it but I did not know what would help me?:(

---

### Post by darkod on 2010-01-04
First of all, you seem to have two linux systems, one on /dev/sda6 and one on /dev/sda10. Do you have two linuxes installed?
Second, if you were resizing the root partition with third party software as you said, try running the filesystem check command, fsck.
Boot with ubuntu 9.10 cd, Try Ubuntu option, and in terminal execute:
sudo fsck /dev/sda6

Do the same for /dev/sda10 if necessary. See if that helps. This doesn't seem like grub error if it happened after resizing the partition so there is no need to reinstall grub at the moment.

---

### Post by Leppie on 2010-01-04
> **andy1983 said:**
> ok but how to reinstall that grub? How to use rescue mode? I tried it but I did not know what would help me?:(

did this livecd mount your linux partitions without problems?

---

### Post by andy1983 on 2010-01-04
> **darkod said:**
> First of all, you seem to have two linux systems, one on /dev/sda6 and one on /dev/sda10. Do you have two linuxes installed?
Second, if you were resizing the root partition with third party software as you said, try running the filesystem check command, fsck.
Boot with ubuntu 9.10 cd, Try Ubuntu option, and in terminal execute:
sudo fsck /dev/sda6

Do the same for /dev/sda10 if necessary. See if that helps. This doesn't seem like grub error if it happened after resizing the partition so there is no need to reinstall grub at the moment.

  First of thank a lot for so quick reply.:)
Yes I tried to install ubuntu 2 times that's why there might be two linux partitions.
 I tried the fsck command for both sda6 and sda10
below is the result

[B]ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda6: clean, 127793/802816 files, 591316/3206967 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sda10
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda10: clean, 127745/713856 files, 565932/2851529 blocks[/B]

---

### Post by andy1983 on 2010-01-04
> **Leppie said:**
> did this livecd mount your linux partitions without problems?


I dont understand what exactly you want say but I run the live cd with first option that is try Ubuntu without installation in you system.

---

### Post by Leppie on 2010-01-04
yes, but it should still be able to mount your ubuntu partitions.

---

### Post by andy1983 on 2010-01-04
> **Leppie said:**
> yes, but it should still be able to mount your ubuntu partitions.

I can browse my all drives in my hard drive but not able to boot from it. I mean to say I can not run ubuntu or win7 installed on my laptop.

---

### Post by Leppie on 2010-01-04
could you download and run the script from post #9 and post the results again?

---

### Post by andy1983 on 2010-01-04
I ran that script.

and here is the result

---

### Post by Leppie on 2010-01-04
issue these commands:
```
$sudo mount /dev/sda10 /mnt
$sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by andy1983 on 2010-01-04
> **Leppie said:**
> issue these commands:
```
$sudo mount /dev/sda10 /mnt
$sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

It gives the below result

[B]ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda[/B]

---

### Post by Leppie on 2010-01-04
ok, try rebooting now.

---

### Post by andy1983 on 2010-01-04
YOU R :KS:KS:KS:KS:KS

It worked as it should be

Millions of thanks=D>\\:D/

Could you Pls tell me what was the problem and how to learn ubuntu?

---

### Post by Leppie on 2010-01-04
i am not 100% sure what happened exactly. it looks like grub stores the link to the partition hosting it's configuration files as a physical address on the disk. by resizing the partition, this address would obviously become incorrect, but this is just a guess.

i am glad that your system is working properly again.
you can find a lot of information on the ubuntu system searching this forum for arguments. also, if you keep a close eye on this particular section (general help) you will see a lot of issues other users may have, but could be very useful for you too.

one of the most important things is, if a trusted source (like ubuntuforums) suggest to try something don't be afraid to do it. as you can see ubuntu is very different from windows, and most things that get broken can be fixed with some guidance. read a lot, make google your best friend ;)

---

