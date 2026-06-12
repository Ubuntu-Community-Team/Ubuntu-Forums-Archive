---
title: "No init found.  Try passing init=bootarg."
date: 2010-01-20
forum: General Help
---

### Post by CaitlinJ on 2010-01-20
Ubuntu 9.10 will not boot!  System froze this morning, I restarted and it is now failing to boot.  Starts loading grub and I get this message:

-----------------------------------------------------------------
mount: mounting /dev/disk/by-uuid/04aa3697-7bc0-45b5-b86a-77a1e6534bd5 on  /root failed: invalid argument
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount.  Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
--------------------------------------------------------------

I booted with 9.04 LiveCD discovered the drive could not be mounted-ran fsck -ln and it told me the drive has no valid partition table.  I have had intermittent problems mounting flash drives before this, so I'm kind of worried it might be a hardware issue.  

Also have files on that drive I would rather not lose, so reinstalling is hopefully a last resort.

I'm something of a n00b and still trying to learn, any help would be much appreciated!

---

### Post by johnerskine2010 on 2010-01-22
I'm having a similar problem, although the performance of my system has been flakey for a few days; with lock-outs particularly when I'm watching online video.

---

### Post by bazio101 on 2010-01-25
> **johnerskine2010 said:**
> I'm having a similar problem, although the performance of my system has been flakey for a few days; with lock-outs particularly when I'm watching online video.

Hi, I'm new to ubuntu 9.10 (about a month) and I have the same problem. I was watching live sports video on myp2p and after this computer started not responding well (couldn't open firefox and other programs) and when I restart I saw the screen with the (**initramfs**) at the bottom. I tried use the fsck command (fixed a problem at the past) but seems not right. Search on google but only thing I found -and understand- was that computer can't find the proper file to boot, I think this is /dev/sda1. Says that there is no such file or directory. Maybe a grub problem? Try to fix this using live CD and terminal by giving commands found on internet to restore or update grub but nothing happened. Don't want to format and re-install ubuntu so any advice? :confused:

---

### Post by bazio101 on 2010-01-25
> **johnerskine2010 said:**
> I'm having a similar problem, although the performance of my system has been flakey for a few days; with lock-outs particularly when I'm watching online video.

Hey, I used terminal on liveCD and command: **sudo fsck /dev/sda1** a couple of times. First time said something about an error or problem - I don't remember- but the second time it started fix things -pushed (y) button a lot of times- and now I'm about to restart. Hope everything is all right. I'll be back to post the results. :D

---

### Post by kingjm on 2010-01-26
I am having the same problem. I have used the blkid command and notice that the UUID's listed in the grub menu are the same as those used for sda1.

I do not understand. The initial install was fine. When i did the upgrade and rebooted this is when the problems as listed above started.

I have deleted and reinstalled several times. The first upgrade and boot is when it starts for me.

I am not sure what else I can do.

I have been doing some reading.... ACPI is now used on newer ubuntu distributions I needed to edit my bios so that all is well. ACPI needs to be turned on and set to S3 (suspend to Ram). Before was on S1

---

### Post by dobbod on 2010-01-30
> **bazio101 said:**
> Hey, I used terminal on liveCD and command: **sudo fsck /dev/sda1** a couple of times. First time said something about an error or problem - I don't remember- but the second time it started fix things -pushed (y) button a lot of times- and now I'm about to restart. Hope everything is all right. I'll be back to post the results. :D
Thanks for the tips bazio.

I have had the same problem, but it solved just now. What I did was:

Boot into Live-CD, open terminal and run:

```
sudo fsck /dev/sda3
sudo fsck /dev/sda4
```Where my /Root is in sda3, and /Home is in sda4. There was a few issuse while fsck checking, and I just press 'Y' for yes, for it to fix the problems.

---

### Post by ForgivenByJC on 2010-02-03
Opening with LiveCD and running *(See Note)```
fsck -y /dev/sda1
```would likely work best here and did for me.

I used SystemRescueCD because I have both i386 & amd64 architectures and Ubuntu LiveCD must match the architecture requiring two separate CDs for me.  SystemRescueCD does not require two separate CDs for different architectures.

If your Ubuntu LiveCD boots on your computer, then just go to terminal and type *(See Note)```
fsck -y /dev/sda1
```> *** Note:** Change "/dev/sda1" for your appropriate root partition.  Cannot track down how best to ID your root partition, but some commands are:
[LIST]
[*]cfdisk
[*]sfdisk -l
[*]fdisk -l
[/LIST]These commands need to be run as sudo under normal Ubuntu (without LiveCD), but may or may not need to be run with LiveCD.

Does anyone know of a good page which explains simply to locate someone's root partition?

---

### Post by plavery on 2010-10-15
Thanks Every one!

 For some reason my Ubuntu 10.04 lost the option to reboot or shut down, when I clicked the little box with shutdown or restart it popped up blank.So after doing the cardinal computer sin of just pressing the off button for 4 seconds, it would not reboot and had the error [B]"No init found.  Try passing init=bootarg."
**Followed: **[/B]fsck -y /dev/sda1[B]
After booting to 10.04 cd, went to terminal and typed sudo -s then the command above. Only had to type "yes" once the terminal screen filled up with "Y" 's re-booted and all was good. Thanks everyone so much, had the problem fixed in approx 30 minutes. 

Pete:guitar: 
Rock On!
[/B]

---

### Post by manuganji on 2010-10-29
Please help me too. My thread is at [http://ubuntuforums.org/showthread.php?t=1606975]("http://ubuntuforums.org/showthread.php?t=1606975") . I have no clue about how to fix this.

---

### Post by Michae Marie on 2010-10-30
Hi, 
 
Well, Im using Ubuntu for few months, everything was goign very smoothly until this morning...this message appeared : 
 
 
Target filesystem doesn't have /sbin/init.
No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
 
 
..No idea how it happend, or what to do. The sytem wont just launch, I do not have the copy of Ubuntu CD, my friend installed a clean legal version for me, but went back to USA with original CD. 
 
Anyway can it be fixed without CD ?
 
Thank you.
 
Michael

---

### Post by aliozkan on 2010-10-30
Hi,
I m using Ubuntu 10.10.
While i was working, some programs gave "couldn't write to disk" error and i tried to restart. Computer shut down but i got the same error above while starting Ubuntu.

I started my computer with a live CD and tried to run
sudo fsck /dev/sda6 
(sda6 is my ext4 filesystem that ubuntu installed)

and i got:

fsck.ext4: Device or resource busy while trying to open /dev/sda6
Filesystem mounted or opened exclusively by another program?

I m sure disk is not mounted to anywhere. I cannot reinstall Ubuntu, i have to get my projects in there. What can i do?

Ali ÖZKAN

---

### Post by aliozkan on 2010-10-30
I have copied my files with testdrive and i will reinstall Ubuntu.

This was the last solution, but i had nothing to do...

---

### Post by SatishJL on 2010-11-07
Hi folks,
Even im facing the same problem of no init found. Is there any option to resolve this without using cd.......?:confused:

---

### Post by azurehi on 2010-11-12
I had the same issue with 10.04 (32bit) not booting.  When I attempted to use the live cd to reach a terminal, it would not boot into desktop.

What I did was boot from gparted 0.6.0.4.  I saw the correct partitions and selected to repair sda1.  I then rebooted and 10.04 booted normally.  I have no idea why this worked but it did...so far anyway.

---

### Post by PPOY on 2010-11-14
> **azurehi said:**
> I had the same issue with 10.04 (32bit) not booting.  When I attempted to use the live cd to reach a terminal, it would not boot into desktop.

What I did was boot from gparted 0.6.0.4.  I saw the correct partitions and selected to repair sda1.  I then rebooted and 10.04 booted normally.  I have no idea why this worked but it did...so far anyway.

And how did you boot from gparted 0.6.0.4 if i might ask?

---

### Post by azurehi on 2010-11-14
> **PPOY said:**
> And how did you boot from gparted 0.6.0.4 if i might ask?
 I should have clarified:  I removed the gparted disc and re-booted the computer.  The graphical logon screen appeared, as usual, and I have had no trouble since.

---

### Post by tk189 on 2010-11-15
To everyone in this thread so far, the problem will most likely return and as it does increase in regularity.

It is cropping up all over this forum under various threads and so far the best solution is to use this excellent walkthrough guide and [purge and reinstall grub]("http://ubuntuforums.org/showthread.php?t=1581099") on your installed copy using chroot from a liveCD session :

It is a big problem and in my cases crashes and freeze ups are occurring daily (3 or 4 times before I shut my PC down and give up for the day), most often the reboot results in the Try passing init=bootarg error text and the busybox thing.

10.10 will occasionally allow me to see the grub menu and select rescue version or whatever it's called in which case I can select the update grub option, then sudo reboot after the non gui login prompt.

More often than not the system just looks up forcing a hard restart which always results in "Try passing init=bootarg" and the whole thing begins again.

I've read so far it is to do with less than 2GB of RAM, I've read it affects dual core or quad core PCs, I've read alsorts of things from random kernel downgrades (and crossing your fingers) to uninstalling loads of things (and crossing your fingers) to disabling a second monitor and compiz (again whilst crossing your fingers) but no fixes as yet ](*,)

ubuntu rocks :guitar: but this problem sucks! #-o

---

### Post by patse on 2010-11-17
hello,

I can confirm having the same problems when I try to boot Ubuntu10.10 on my netbook: No init found. Try passing init=bootarg.

The other problem is, that I'm not even able to mount the root partition when using a live system. When I run the command: sudo mount /dev/sda5 /mnt , which is my root partition, I don't get any error message but from then on the terminal from which I executed the command hangs and doesn't respond to anything!? All the other partition on the disk, /home for example, mount properly!

---

### Post by trentd on 2010-11-24
I have a similar problem. I have tried to boot off a usb and cd, but it just goes back to the initial error message noted above. 

In other words, I cannot get to the terminal window to type in the correction to make it right. Any suggestions?

Thanks in advance.

---

### Post by samuelranta on 2010-12-12
Also got my system working following the instructions above. Thank you =)

---

### Post by clbaines on 2011-01-08
You got this one right on. I just fixed the same problem using your solution. Thanks

---

### Post by dirtydevil on 2011-01-14
Hey,
I had the same problem with my 10.04 ubuntu. Tried using above steps but My system is not even booting from live CD. I tried latest Unetbootin to make my pendrive bootable. My system is Dual boot not using wubi. When I tried to run Live CD , It got stuck at the screen ubuntu in the start-up. Can't process further. Please I don't want to loose my data. Help needed.

---

### Post by xdunlapx on 2011-01-14
I'm currently running Windows 7 64-bit. I decided again that I want ubuntu on my laptop so I downloaded and burnt the iso for 10.10 desktop edition. I keep coming up with it needing a command such as "init= bootarg" Why doesn't it just boot into the live cd?? This is so frustrating. I checked the md5sum and it's correct. I have no idea what to do and nobody would help me in the ubuntu IRC chat. They ignored me. So I'm coming here. I don't want to burn and try 10.04 as I like to have the latest version. 

Can someone help me figure this out??

---

### Post by teciman on 2011-02-14
Hi friends,

sudo e2fsck -c0 -p -f -v /dev/sda3


this command solved my problem.

i used this link   ;

[http://askubuntu.com/questions/18101/after-grub-loads-linux-no-init-found](http://askubuntu.com/questions/18101/after-grub-loads-linux-no-init-found)

---

### Post by LeiaLeaf on 2011-03-07
> **azurehi said:**
> I had the same issue with 10.04 (32bit) not booting. When I attempted to use the live cd to reach a terminal, it would not boot into desktop.
 
What I did was boot from gparted 0.6.0.4. I saw the correct partitions and selected to repair sda1. I then rebooted and 10.04 booted normally. I have no idea why this worked but it did...so far anyway.
 
I'm having this exact problem, but my noobism does not allow me to understand how you fixed this. Could you elaborate?

---

### Post by aad on 2011-03-13
Time to bump this thread up.  I was sitting on this issue for almost a month blaming myself when it surfaced suddenly without warning.  I assumed that I accidently deleted an important boot file(s) as I was using a new ubuntu file clean up program and thought I went overkill, LOL.  My worst fear was that I had lost all my valuable data.  Desperate for a quickfix and wanting to avoid drastic time consuming format and reinstall measures,  I decided to Google the issue and came across this awesome thread. 

Thanks to everyone here, I am back up and running with all my data intact.  The solutions that worked for my were the ones posted by dobbod and ForgivenByJc.  You guys are awesome, many thanks!  I am going to keep my fingers crossed and hope it does not resurface  [-o<  if it does I at least have a quick fix.  On second thought,  I suspect this may be related to some newly released update as it seemed to coincide with the last update I did before it surfaced.

---

### Post by SometimesJane on 2011-04-17
> **ForgivenByJC said:**
> Opening with LiveCD and running *(See  Note)```
fsck -y /dev/sda1
```would likely work best here and did  for me.

I used SystemRescueCD because I have both i386 & amd64 architectures  and Ubuntu LiveCD must match the architecture requiring two separate  CDs for me.  SystemRescueCD does not require two separate CDs for  different architectures.

If your Ubuntu LiveCD boots on your computer, then just go to terminal  and type *(See Note)```
fsck -y /dev/sda1
```

You can see what your partitions are by opening gparted (I think). Easier than using the commands from terminal.

So very glad I found this thread. I'm a **total**  newbie, and had no idea what I was doing..still not sure. I just spent  the last 6 hours trying to fix this issue, while learning a bit about  basic ubuntu functions/things. A friend originally partitioned my laptop  so it could dual load Vista (yuck) and Lucid Lynx, unfortunately, he  isn't available to help.

From the last 6 hours: I have Ubuntu  10.04 Lucid Lynx (32 bit). I have 4 partitions (sda1 a ntfs with 21.92  gigs; sda2 ntfs 4.68 gigs; sda3 ext4 476mb; sda4 **crypt-luks** 44.46gigs)

I  made a LiveCD, but didn't boot properly (probably didn't burn right,  didn't use the slowest speed, etc.) Anyway, ended up using a USB LiveCD  from Windows...fixed boot order from BIOS to USB, and the second time  was able to open terminal and run some commands from sudo/root: "sudo  -s" "fsck -y /dev/sda1" "fsck -y /dev/sda2" "fsck -y /dev/sda3" "fsck -y  /dev/sda4"

No problems were found on sda3, entered "yes" got a  list of y's. But there were errors on sda4, and sometimes 1 and 2 as  well. Is is because sda4 is encrypted? I rebooted to ubuntu and still  got the same "no init found" message...

[COLOR=Navy]Botton line: how do you run fsck with an encrypted drive?[/COLOR]

---

### Post by dreado on 2011-05-09
Hi. I'm getting the same error, but I'm getting it when booting from the CD (for the first time). Any solutions?

---

### Post by Alchemist27 on 2011-05-09
My problem started quite similarly; I use Ubuntu 10.10 on an Asus Eee 1000ha notebook, and some months ago I installed MacBuntu, which I fell in love with!!!
My netbook worked perfectly until this last weekend; when I tried to boot up last Friday night, I kept getting the 'no init found, try init=bootarg', and couldn't get past it. 

I followed some advice from this forum before registering and tried to run some commands from the terminal, having booted up from the LiveCD, nevertheless I think my problems just got bigger, for I burned the iso file from the Ubuntu download site for Windows XP (which is in one of the 4 partitions - 3 regular and 1 hidden for rollback to factory settings), I tried it first on my job laptop which is a Dell and booted, ran and worked like a dream! Whereas when I try to boot up from the LiveCD from my netbook, I get a message like this: 

'unable to mount /dev/sda1', 'no init found' - where /dev/sda1 is the partition Ubuntu is installed on. 

And this happens every time I try to boot up my netbook from the LiveCD, it just won't work and it just won't mount the partition Ubuntu is allocated on. 

Just 2 things: My WinXP works just fine (oddly enough, it even loads up faster now (!?), and I use an external CD-DVD USB combo from Samsung to boot up from the LiveCD. 

Can anyone please provide any advice???

Many thanks in advance, Best Regards!

---

### Post by dreado on 2011-05-09
> **dreado said:**
> Hi. I'm getting the same error, but I'm getting it when booting from the CD (for the first time). Any solutions?
I tried turning it off and on again, now it just hangs on the red dots..

---

### Post by SometimesJane on 2011-06-29
> **SometimesJane said:**
> You can see what your partitions are by opening gparted (I think). Easier than using the commands from terminal.

So very glad I found this thread. I'm a **total**  newbie, and had no idea what I was doing..still not sure. I just spent  the last 6 hours trying to fix this issue, while learning a bit about  basic ubuntu functions/things. A friend originally partitioned my laptop  so it could dual load Vista (yuck) and Lucid Lynx, unfortunately, he  isn't available to help.

From the last 6 hours: I have Ubuntu  10.04 Lucid Lynx (32 bit). I have 4 partitions (sda1 a ntfs with 21.92  gigs; sda2 ntfs 4.68 gigs; sda3 ext4 476mb; sda4 **crypt-luks** 44.46gigs)

I  made a LiveCD, but didn't boot properly (probably didn't burn right,  didn't use the slowest speed, etc.) Anyway, ended up using a USB LiveCD  from Windows...fixed boot order from BIOS to USB, and the second time  was able to open terminal and run some commands from sudo/root: "sudo  -s" "fsck -y /dev/sda1" "fsck -y /dev/sda2" "fsck -y /dev/sda3" "fsck -y  /dev/sda4"

No problems were found on sda3, entered "yes" got a  list of y's. But there were errors on sda4, and sometimes 1 and 2 as  well. Is is because sda4 is encrypted? I rebooted to ubuntu and still  got the same "no init found" message...

[COLOR=Navy]Botton line: how do you run fsck with an encrypted drive?[/COLOR]
Btw, a friend helped me solve this Luks encrypt problem using this: [http://blog.bitengine.ca/?p=72](http://blog.bitengine.ca/?p=72)

Another friend helped enter all the commands but it crashed again. Doing this over by myself. Wish me luck :-)

---

### Post by quantumcop on 2011-06-29
> **tk189 said:**
> 
It is cropping up all over this forum under various threads and so far the best solution is to use this excellent walkthrough guide and [purge and reinstall grub]("http://ubuntuforums.org/showthread.php?t=1581099") on your installed copy using chroot from a liveCD session : 

I am having the same problem that many on this thread are. When I try using fsck at the terminal of a Live CD session, I get the same error message

"fsck.ext4: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?"

I tried the solution quoted above, but I find that I am not even able to mount the Ubuntu partition (in my case, /dev/sdb1). If I try a command like

```
sudo mount /dev/sdb1 /mnt/tmp
```

the terminal simply hangs. I have no Idea what to do; as others have said, I really want to reinstall *only* as a last resort.

Thank you for your help,
A semi-noob.

---

### Post by SometimesJane on 2011-06-30
I also got "Filesystem mounted or opened exclusively by another program?" when I tried it the first few times. Luckily my friend called me back. I just pulled the plug/shut down and re-ran from the LiveCD. Here's what I did after opening up a terminal (unedited):
> 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo su-
sudo: su-: command not found
ubuntu@ubuntu:~$ sudo su -
root@ubuntu:~# apt-get update
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)/ lucid/restricted Translation-en_US
Get:1 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:2 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release [44.7kB]
Get:3 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid Release          
Get:4 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates Release [44.7kB]             
Get:5 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages [197kB]
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Packages     
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Packages
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/main Sources       
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid/restricted Sources 
Get:6 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Packages [504kB]
Get:7 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages [14B]   
Get:8 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources [59.6kB]       
Get:9 [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources [14B]   
Get:10 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Packages [3,240B]   
Get:11 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/main Sources [196kB]
Get:12 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") lucid-updates/restricted Sources [1,443B]
Fetched 1,052kB in 4s (220kB/s)                    
Reading package lists... Done
root@ubuntu:~# apt-get install cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 134 not upgraded.
root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a182a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2862    22988983+   7  HPFS/NTFS
/dev/sda2            8728        9729     8048565    7  HPFS/NTFS
/dev/sda3   *        2863        2923      487424   83  Linux
/dev/sda4            2923        8727    46621696   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1012 MB, 1012924416 bytes
11 heads, 42 sectors/track, 4282 cylinders
Units = cylinders of 462 * 512 = 236544 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96e34ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4283      989152    c  W95 FAT32 (LBA)
root@ubuntu:~# cryptsetup -v luksDump /dev/sda4
LUKS header information for /dev/sda4

Version:           1
Cipher name:       aes
Cipher mode:       cbc-essiv:sha256
Hash spec:         sha1
Payload offset:    2056
MK bits:           256
MK digest:         d9 60 56 d4 c7 cc 28 d3 97 46 14 ef e2 83 5d 5d 33 1c da 20 
MK salt:           d9 46 7d dc ab 81 a8 76 c8 9f 23 04 e2 f8 b6 49 
                   e9 10 30 62 17 64 78 e1 99 cd ca 97 3c a2 de 46 
MK iterations:     10
UUID:              9354764a-c13e-4b17-9b8d-0da2fbbeab71

Key Slot 0: ENABLED
    Iterations:             99527
    Salt:                   f6 ef 72 37 ad 4e 38 3e 08 c1 6e a8 ef 3f 9f f8 
                              66 4c 96 33 c6 9d e7 15 13 2e d2 8c 42 91 a2 e9 
    Key material offset:    8
    AF stripes:                4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED
Command successful.
root@ubuntu:~# cryptsetup -v luksOpen /dev/sda4 sda4_crypt
Enter passphrase for /dev/sda4: 
Key slot 0 unlocked.
Command successful.
root@ubuntu:~# lvdisplay
The program 'lvdisplay' is currently not installed.  You can install it by typing:
apt-get install lvm2
root@ubuntu:~# apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdevmapper-event1.02.1 watershed
The following NEW packages will be installed:
  libdevmapper-event1.02.1 lvm2 watershed
0 upgraded, 3 newly installed, 0 to remove and 134 not upgraded.
Need to get 447kB of archives.
After this operation, 1,282kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main watershed 5 [10.7kB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libdevmapper-event1.02.1 2:1.02.39-1ubuntu4.1 [27.5kB]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main lvm2 2.02.54-1ubuntu4.1 [409kB]
Fetched 447kB in 2s (158kB/s)
Selecting previously deselected package libdevmapper-event1.02.1.
(Reading database ... 128790 files and directories currently installed.)
Unpacking libdevmapper-event1.02.1 (from .../libdevmapper-event1.02.1_2%3a1.02.39-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package watershed.
Unpacking watershed (from .../archives/watershed_5_i386.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.54-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Setting up libdevmapper-event1.02.1 (2:1.02.39-1ubuntu4.1) ...

Setting up watershed (5) ...
update-initramfs: deferring update (trigger activated)

Setting up lvm2 (2.02.54-1ubuntu4.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
root@ubuntu:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/Jacob/Swappy
  VG Name                Jacob
  LV UUID                zL6VCe-XCZH-ml3N-J8b6-mDNR-roOO-tDuUtX
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                1.86 GiB
  Current LE             476
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/Jacob/Rooty
  VG Name                Jacob
  LV UUID                yV2yk0-sCkW-x2WX-uXHb-tqLl-nsaO-5wVwJE
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                42.60 GiB
  Current LE             10905
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
root@ubuntu:~# fsck -y /dev/Jacob/Rooty
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/Jacob/Rooty

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:~# vgchange -a y Rooty
  Volume group "Rooty" not found
root@ubuntu:~# vgchange -a y dev/Jacob/Rooty
  Invalid volume group name: dev/Jacob/Rooty
  Run `vgchange --help' for more information.
root@ubuntu:~# vgchange -a y Jacob
  2 logical volume(s) in volume group "Jacob" now active
root@ubuntu:~# fsck -y /dev/Jacob/Rooty
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/mapper/Jacob-Rooty: recovering journal
Clearing orphaned inode 2365873 (uid=0, gid=0, mode=0100644, size=125032)
Clearing orphaned inode 2392208 (uid=0, gid=0, mode=0100644, size=59008)
Clearing orphaned inode 2398224 (uid=0, gid=0, mode=0100644, size=79708)
Clearing orphaned inode 2398113 (uid=0, gid=0, mode=0100644, size=116728)
Clearing orphaned inode 2363542 (uid=0, gid=0, mode=0100644, size=26152)
Clearing orphaned inode 2363538 (uid=0, gid=0, mode=0100644, size=719540)
Clearing orphaned inode 2360773 (uid=0, gid=0, mode=0100644, size=191280)
Clearing orphaned inode 2391478 (uid=0, gid=0, mode=0100644, size=140828)
Clearing orphaned inode 135735 (uid=0, gid=0, mode=0100755, size=415516)
Clearing orphaned inode 2097500 (uid=0, gid=0, mode=0100600, size=163)
Clearing orphaned inode 543841 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 543725 (uid=1000, gid=1000, mode=0100600, size=40656)
/dev/mapper/Jacob-Rooty: clean, 488763/2793472 files, 4764501/11166720 blocks
root@ubuntu:~# 


After this, I pulled out my LiveCD USB, restarted to computer and it is now working. Hope this helps!

---

### Post by ACCS on 2011-07-21
> **tk189 said:**
> I've read so far it is to do with less than 2GB of RAM
I'm sorry to be the bearer of bad news, but we just saw this issue on a system with 4GB of memory.
 
The good news is that we've been running ~30 systems (mostly physical, but some virtual) on 10.4 for several months, and this is the first time we've seen this issue.  The only significant difference I've seen is that this system uses EXT4, while all the other systems use EXT3 (network install).

---

### Post by crotale on 2011-07-24
Thanks, this thread helped me get a Ubuntu Server 10.04 back to life.

```
sudo fsck /dev/sda1
```Was the only thing needed.

---

### Post by angelxdlv on 2011-07-25
> **plavery said:**
> Thanks Every one!

 For some reason my Ubuntu 10.04 lost the option to reboot or shut down, when I clicked the little box with shutdown or restart it popped up blank.So after doing the cardinal computer sin of just pressing the off button for 4 seconds, it would not reboot and had the error [B]"No init found.  Try passing init=bootarg."
**Followed: **[/B]fsck -y /dev/sda1[B]
After booting to 10.04 cd, went to terminal and typed sudo -s then the command above. Only had to type "yes" once the terminal screen filled up with "Y" 's re-booted and all was good. Thanks everyone so much, had the problem fixed in approx 30 minutes. 

Pete:guitar: 
Rock On!
[/B]

this worked perfectly for me, only took a few minutes! thanks!

---

### Post by cc_in_oh on 2011-08-18
> **dreado said:**
> Hi. I'm getting the same error, but I'm getting it when booting from the CD (for the first time). Any solutions?

Same issue here.

Downloaded 11.04 yesterday.
Used Infrarecorder to burn to CD. 
System was WinXP - new HD to replace crashed drive. 2.8 ghz Pentium, 2GB RAM.

CD boots to command prompt after the "no init found" message.

Is there a way to run the install from commend prompt?

Thanks,
CC

---

### Post by lambengolmor on 2011-08-20
I've just experienced the same problem on a Pentium 4 with 1,7Gb RAM (so I don't think it's hardware-dependent) on an Ubuntu 11.04 32 bit desktop.

I also fear this message appears for a various number of problems. In my case it doesn't seem to be a file system problem:
-- fsck reports 0 errors
-- the root partition mounts perfectly from live
-- i find the root partition mounted in /root/ in the emergency environment ubuntu offers my after the "no init found" error.
-- the installation worked fine, it broke just after a kernel upgrade
BUT: it can always be fs-related since I'm using btrfs

Does anyone has ideas on how to investigate further the causes of this error? Thanks a lot!

---

### Post by lambengolmor on 2011-08-20
> **tk189 said:**
> so far the best solution is to use this excellent walkthrough guide and [purge and reinstall grub]("http://ubuntuforums.org/showthread.php?t=1581099") on your installed copy using chroot from a liveCD session

This, surprisingly (grub boot entry seemed fine), worked for me! Thanks A LOT!

---

### Post by ravish_36 on 2011-10-13
Thanx to every one...same problem but solved.....
Run ubuntu live cd 9.04 open terminal....enter the command as my frnd say above...
sudo -s
fsck -y /dev/sdaX

X is any no. where ur ubuntu root ....
:D

---

### Post by parvathi.did on 2011-11-28
"For some reason my Ubuntu 10.04 lost the option to reboot or shut down,  when I clicked the little box with shutdown or restart it popped up  blank.So after doing the cardinal computer sin of just pressing the off  button for 4 seconds, it would not reboot and had the error [B]"No init found.  Try passing init=bootarg."
**Followed: **[/B]fsck -y /dev/sda1[B]
After booting to 10.04 cd, went to terminal and typed sudo -s then the  command above. Only had to type "yes" once the terminal screen filled up  with "Y" 's re-booted and all was good. Thanks everyone so much, had  the problem fixed in approx 30 minutes."


I followed the same thing, it was printing "y" 's but never ending.... could you please suggest a solution.. its urgent
[/B]

---

### Post by ludi567 on 2012-02-08
Hi,

I have encountered the same problem on my machine. I tried running the fsck solution posted above but all I got was something like the following:

fsck from util-linux-ng2.17.2
dos fsck 3.0.7,24 dec 2009,fat32,LFN
/dev/sda1 1 files, 1/12016403 clusters

What does this mean? Does it mean there is only 1 file on that partition? Why is it not scanning the whole partition? After these three lines I just get a new line in terminal. How can I check that it is still running and doing something?

I say it is "something like this" because I am actually trying to fix this issue over the phone with somebody who isnt exactly familiar with computers.

Thanks a lot in advance.

---

### Post by odophyagoca on 2012-02-08
ïðàâäà, åñòü èñêëþ÷åíèÿ ïî÷òà õîðîõîðäèí ðîññèóñ

---

### Post by ownx0rz on 2012-02-08
I am having the same problem. I am running an Acer Aspire One Netbook D255. I have attempted to fix it with Gparted, but it will not boot. I do not believe it is the flash drive I am using as I tried another one in conjunction with creating the bootable stick in both Unetbootin and Pendrivelinux. I have attempted to install distros other than Ubuntu, too. I am at a black screen with the 
"No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13-31ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)"

any updates on alternative solutions? I cannot even reach the Live CD installation menu so I cannot open a terminal.

---

### Post by buzzjn on 2012-05-15
Thanks to everyone!
fsck "root directory"

worked perfect for me

---

### Post by duuchung on 2012-11-27
Mine is 10.04 LTS and LVM.
I finally solved by following the thread BusyBox bug# 646284 debian. I just copied the steps below. The original author would not sue me for copyright infringement.  
"BusyBox bug# 646284.

You'll have to boot from a cd-rom or using other alternative way,
eg, using an installation CD-rom, or some rescue-linux - anything
will do that lets you to mount chroot to your existing system.

Once there, update busybox package and regenerate initramfs images,
by running

 update-initramfs -k <yourkernelversion> -u

next umount (or just sync) and reboot."

---

### Post by maulynvia on 2013-02-01
I solved this  in a different way on the eeepc. This is my understanding which may not be 100% correct, but it worked

The eeepc stores some of the bootup data on a special part of the disk this is the "boot booster". I was getting the same error as others but fdisk and gparted (run from live usb) could not 'see' the partition in question (sda4 in my case). 

The solution is actually easy:

1. Disable boot booster at startup (F2)
2. System boots OK now, no error message
3. Reboot  and enable the boot boster (I think at this point the boot booster partition is re-written by the eeepc) a bit slow, but boots ok.
4. Reboot, and we are now back to normal quick boot (Lubuntu).

:)

More info on boot booster here [https://help.ubuntu.com/community/EeePC/Using#Enabling_Bootbooster](https://help.ubuntu.com/community/EeePC/Using#Enabling_Bootbooster)

---

