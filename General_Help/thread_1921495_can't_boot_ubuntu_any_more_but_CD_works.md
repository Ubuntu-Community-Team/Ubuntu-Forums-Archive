---
title: "can't boot ubuntu any more but CD works"
date: 2012-02-06
forum: General Help
---

### Post by improvent363 on 2012-02-06
I installed ubuntu 10.4 after installing windows 7 64-bit. [I had to install nvidia driver first since I was getting a  blank purple screen than a blank black screen.  After that sometimes ubuntu freezes up or mouse stop working so I had to restart the PC every time it did that.] 


Now all I get a blank black screen when trying to boot in ubuntu normally. I tried booting in manual by tying "nomodeset" [since I was able to boot into unbuntu this way before] but I get this error: "alloc magic is broken at 0xcacfa610 aborted. Press any key to exit"

[So I have no idea what to do now. I think it might happened because in windows 7, nvidia driver was rolled backed into previous version and I had to reinstall nvidia driver again.]


So, can someone tell me what to do next?

---

### Post by overcast on 2012-02-06
I'm not sure if this is because of Nvidia driver because every OS has it's own driver for managing graphics card. So i don't think this could be because of nvidia driver.

You can try reinstalling GRUB to see if dual boot is properly set, just in case. I'm not sure about this error too. Hope someone else come up with more info on this one.

---

### Post by varunendra on 2012-02-07
Try booting into "Recovery mode", then select "dpkg" (repair broken packages). Reboot and see if it improves things.

And as *overcast* already said, any change in windows drivers or any applications can not affect drivers/applications in Ubuntu. Each OS has its own drivers, programs and settings to handle the hardware.

---

### Post by improvent363 on 2012-02-07
> **varunendra said:**
> Try booting into "Recovery mode", then select "dpkg" (repair broken packages). Reboot and see if it improves things.

Can't boot in recovery mode either so I think I have to reinstall GRUB, so how do i make that happen.

---

### Post by improvent363 on 2012-02-07
> **overcast said:**
> You can try reinstalling GRUB to see if dual boot is properly set, just in case. I'm not sure about this error too. Hope someone else come up with more info on this one.


HOw do I reinstall GRUB for ubuntu 10.04?

---

### Post by varunendra on 2012-02-07
> **improvent363 said:**
> HOw do I reinstall GRUB for ubuntu 10.04?
Using the same cd that you used for installation, and following this guide: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

But if you get grub menu, but can't boot even in Recovery mode, then combining this with your description of the problem in your first post, I doubt if reinstalling grub is going to do any good. It seems to me a filesystem problem now. Accordingly, I would suggest to boot from the live cd, and run fsck on the partition on which Ubuntu is installed:
```
sudo fsck /dev/sd***xy***
```where "xy" is to be replaced by the relevant partition number (e.g. sda1, sda2, sdb1 etc.)

---

### Post by improvent363 on 2012-02-08
> **varunendra said:**
> Using the same cd that you used for installation, and following this guide: [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

But if you get grub menu, but can't boot even in Recovery mode, then combining this with your description of the problem in your first post, I doubt if reinstalling grub is going to do any good. It seems to me a filesystem problem now. Accordingly, I would suggest to boot from the live cd, and run fsck on the partition on which Ubuntu is installed:
```
sudo fsck /dev/sd***xy***
```where "xy" is to be replaced by the relevant partition number (e.g. sda1, sda2, sdb1 etc.)

I am a complete newbie, so how do I figure out what my partition # is?

---

### Post by elliotn on 2012-02-08
if when u boot to rescue mode and u see text scrolling then it isn't grub it could be graphic related

---

### Post by varunendra on 2012-02-08
> **improvent363 said:**
> I am a complete newbie, so how do I figure out what my partition # is?
One of the many other ways (including GUI ones, but you need to identify it in terms of "sdxy"..) is to run the command:
```
sudo fdisk -l
```(it is small "L" after fdisk)
and in the output, look for the lines that say "Linux" in the last column. The first column of this line(s) contains the partition address that you have to use with fsck. If unsure, just post the output here.

---

### Post by improvent363 on 2012-02-13
> **varunendra said:**
> One of the many other ways (including GUI ones, but you need to identify it in terms of "sdxy"..) is to run the command:
```
sudo fdisk -l
```(it is small "L" after fdisk)
and in the output, look for the lines that say "Linux" in the last column. The first column of this line(s) contains the partition address that you have to use with fsck. If unsure, just post the output here.


Okay I did what you said and got this:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb2b1c8ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       58230   467626216    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           58230       60802    20655105    5  Extended
/dev/sda5           58230       59768    12351488   83  Linux
/dev/sda6           59768       60802     8302592   82  Linux swap / Solaris

Disk /dev/sdb: 3869 MB, 3869544448 bytes
32 heads, 63 sectors/track, 3748 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x649459a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3748     3777952+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$
```




Therefore, their is two linux in their and I don't know which one I should use? So please tell me :)

---

### Post by varunendra on 2012-02-13
> **improvent363 said:**
> 
```
ubuntu@ubuntu:~$ sudo fdisk -l
..*<snip>*..
**/dev/sda5**           58230       59768    12351488   83 ** Linux**
/dev/sda6           59768       60802     8302592   82 ** Linux swap / Solaris**
..*<snip>*..
```
It is **/dev/sda5**. The other one is Linux-Swap partition.

Accordingly, boot into live session, run **sudo fdisk -l **again to make sure that partition is again listed as sda5, then run:
```
sudo fsck -f /dev/sda5
```


**_PS_:**
Please always wrap your output codes within 'CODE' tags by clicking on **#** on the top of edit box (in which you create new posts) to generate those tags, then copy-paste the output in-between those tags. This preserves the output formatting and makes the post look tidy and easily readable.

You can edit your above post to add those tags now. Just type [noparse]```
 in the beginning of the output part, and 
```[/noparse] at the end.

---

### Post by improvent363 on 2012-02-21
> **varunendra said:**
> It is **/dev/sda5**. The other one is Linux-Swap partition.

Accordingly, boot into live session, run **sudo fdisk -l **again to make sure that partition is again listed as sda5, then run:
```
sudo fsck -f /dev/sda5
```
****

Okay I ran "fsck /dev/sda5" and it passed all 5 test [did the test 3 times at different times].

So, what can I do next in order to boot into ubuntu again?

---

### Post by varunendra on 2012-02-28
> **improvent363 said:**
> Okay I ran "fsck /dev/sda5" and it passed all 5 test [did the test 3 times at different times].

So, what can I do next in order to boot into ubuntu again?
Sorry it took me so long to reply, some office work kept me on toes.

I did a quick search about the original error message you get ("alloc magic is broken..."), and found that it maybe related with either a bad memory stick, or a memory management problem in grub-pc. It makes sense (considering the 'malloc' function in 'C' programming) to run memtest from grub menu, for at least 4+ hours, to check if the RAM is okay. Additionally, you may try to reinstall grub as per the guide I linked to in [post #6]("http://ubuntuforums.org/showpost.php?p=11672244&postcount=6") earlier.

For reference:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882) (an explanation in [post #12]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/498882/comments/12"))

[http://www.linuxforums.org/forum/mint-linux/170539-what-does-alloc-magic-broken-mean.html#post813574](http://www.linuxforums.org/forum/mint-linux/170539-what-does-alloc-magic-broken-mean.html#post813574)

---

### Post by improvent363 on 2012-02-28
> **varunendra said:**
> I did a quick search about the original error message you get ("alloc magic is broken..."), and found that it maybe related with either a bad memory stick, or a memory management problem in grub-pc. It makes sense (considering the 'malloc' function in 'C' programming) to run memtest from grub menu, for at least 4+ hours, to check if the RAM is okay. Additionally, you may try to reinstall grub as per the guide I linked to in [post #6]("http://ubuntuforums.org/showpost.php?p=11672244&postcount=6") earlier.

Okay, I will run the memtest from grub menu and post the results when I am done with it.

---

### Post by improvent363 on 2012-03-08
> **varunendra said:**
>  run memtest from grub menu, for at least 4+ hours

okay I tried running memtest and it doesn't do anything and thats because I have ubuntu 11.04 whose memtest 86 does not have support for intel "sandy bridge" cpu. So, I cannot run that.

However, I did try try the basic and standard memory test on windows 7 and they work fine, EXCEPT it gets stuck on extended Memory test. I also am getting blue screen every 2-3 days [and it is almost always when watching youtube videos]. So, does that mean my Ram is bad [I have 2 4gb ram installed]?

---

### Post by varunendra on 2012-03-11
> **improvent363 said:**
> ....However, I did try try the basic and standard memory test on windows 7 and they work fine, [COLOR=Red]**EXCEPT it gets stuck on extended Memory test. I also am getting blue screen every 2-3 days**[/COLOR] [and it is almost always when watching youtube videos]. So, does that mean my Ram is bad [I have 2 4gb ram installed]?Not certainly, but it certainly does make the RAM look more suspicious. Try the same tests with only one module at a time and see if it makes any difference.

---

