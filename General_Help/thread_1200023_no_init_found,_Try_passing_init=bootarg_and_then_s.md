---
title: "no init found, Try passing init=bootarg and then some"
date: 2009-06-29
forum: General Help
---

### Post by AINTEZ86 on 2009-06-29
I am having a problem simular to apperrently alot of people in here however none of the solutions anyone else provides seem to work. When I boot I get several error messages:
 
mount: mounting /dev/mapper/ubuntu-root on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootrag
 
 
Then when I have run a live cd and tried following several different advice I get the following:
 
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root
 
mount: unknown filesystem type 'LVM2_member' (I have tried installing lvm2 and this command still doesn't work)
 
sudo fdisk /dev/sda1
 
The number of cylinders for this disk is set to 36449.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)
(It then comes up to a command prompt....I have been running this server for about a month before now without problems)
 
sudo e2fsck /dev/sda1
 
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid , trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
efsck2 -b 8193 <device>
 
sudo e2fsck -b 8193 /dev/sda1
 
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Superblock invalid , trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
 
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
efsck2 -b 8193 <device>
 
 
I am obviously in way over my head here because a) I am really new to ubuntu and b) I have no idea what in the world a super block is. 
 
Someone please help... if you need anymore info please let me know (I am going to need step by step direction).

---

### Post by night dash on 2010-05-22
I am having the same problem on Ubuntu 10.04, can anyone help?

---

### Post by jasonlearninglinux on 2010-06-03
also having this problem w/ 10.04.

---

### Post by djtarki on 2010-06-04
Hi.

Same problem here after today's update using Ubuntu Lucid 10.04 64 bits

Any idea?

Thanks very much.

---

### Post by andddlay on 2010-06-11
Has there been a solution to this problem yet?  I am also getting this error.

---

### Post by djtarki on 2010-06-11
My hard disk died at the end, so all the problems came from bad sectors, etc.

Good luck!

---

### Post by andddlay on 2010-06-11
This post led me to the answer:

[http://ubuntuforums.org/showpost.php?p=9411005&postcount=2](http://ubuntuforums.org/showpost.php?p=9411005&postcount=2)

I ran a live CD, opened terminal, and typed in "sudo fsck /dev/sda7" (where my ubuntu partition was located)

---

### Post by smbaloo on 2010-06-24
Thanks man
 after booting through live DVD i did
sudo e2fsck -C0 -p -f -v /dev/sda1

then it asked for a manual fsck i did
fsck /dev/sda1 and now it is ok.

Any way i have decided to backup the Disk and throw this one

---

### Post by miststlkr on 2010-07-16
I know the thread is a month dead, but I thought perhaps it was better  to keep it here than start a new one.    I get this every time I reboot.  I boot into the liveCD and "fix" it by scanning with gparted, then boot to the hard drive, everything works like a charm till I reboot and have to do it again.    Could someone point out what may be the actual CAUSE that I can look into rather than just how to work around it??  Thanks.
 
[edit=add] The issue is on 10.04 and the partition in question is ext4, if wither of those points are relevant.  [/edit]

---

### Post by gabak on 2010-07-27
have u tried to report the bug??
press alt F2 then write ubuntu-bug or go to their website and report ur case.

> **miststlkr said:**
> I know the thread is a month dead, but I thought perhaps it was better  to keep it here than start a new one.    I get this every time I reboot.  I boot into the liveCD and "fix" it by scanning with gparted, then boot to the hard drive, everything works like a charm till I reboot and have to do it again.    Could someone point out what may be the actual CAUSE that I can look into rather than just how to work around it??  Thanks.
 
[edit=add] The issue is on 10.04 and the partition in question is ext4, if wither of those points are relevant.  [/edit]

---

### Post by miststlkr on 2010-07-28
I haven't.   I'm wondering if it might not be an issue with the boot sector on the drive perhaps?  I just tried a fresh install of a different liveCD and got the same result the first time I rebooted.    Thinking it may not be directly OS-related...   Going to try another hard drive when I get some more time and find another spare.

---

### Post by buzucan on 2010-09-06
i`m having this problem too,i tried to install ubuntu 10.10 beta 1 and it gives me "no init found"...

---

### Post by mindaslab on 2010-09-08
> **miststlkr said:**
> I haven't.   I'm wondering if it might not be an issue with the boot sector on the drive perhaps?  I just tried a fresh install of a different liveCD and got the same result the first time I rebooted.    Thinking it may not be directly OS-related...   Going to try another hard drive when I get some more time and find another spare.

Thats true, looks like there is a issue with OS. This must be a major bug. None like to wake up and see a cashed machine!

---

### Post by miststlkr on 2010-09-08
Sorry I haven't updated, I forgot all about this thread.  I installed on a different hard drive and haven't had an issue since, so I guess for the time being I am going to stand by my previous assumption that it was an issue with the drive and not the OS.

This, of course, doesn't help in fixing the issue for others...

---

### Post by shashikasaragodu on 2010-09-08
it worked!
there were solutions like holding shift key while booting, and to select the kernel and to do fix.
i tried it and my system is normal now.

---

### Post by wkhasintha on 2010-09-08
I seem to have this prob too

---

### Post by DryChili on 2010-09-09
Hi!

I had the problem too, but it was my fault. My computer hung, so I switched it off. Afterwards I got this error.

To fix it is easy. Just boot from a USB-stick or CD and do fsck.

Some instructions:

List your partitions:
```

 ls /dev/sd*

```If you haven't got an encrypted disk just do (where sda5 is the corrupted partition):
```

fsck /dev/sda5 

```If you are using an encrypted hard-disk (i do) do

```

sudo cryptsetup luksOpen /dev/sda5 something

```where sda5 is the encrypted partition and someting is the name under which you will find the partition (/dev/mapper/something).

The install  Lvm and look for volumes :

```

sudo apt-get install lvm2
sudo pvscan
sudo vgscan

```The last command should list the at least one volume-group
Enable it or the ones you're interested in

```

sudo vgchange -a y groupname

```Now list the logical volumens

```

sudo lvscan

```Your drive you're interested in should now appear under /dev/mapper

do a fsck

```

sudo fsck /dev/mapper/logical-volume

```Lots of errors! Off course you want to have them all fixed. REBOOT!
This worked for me!

Best regards!

---

### Post by der.brain on 2010-12-29
Hi guys,

i had to ad -f for force. Without fsck does not find any errors. 

```
sudo fsck -f /dev/mapper/logical-volume
```

if you get a lot of errors you can add -y for silent mode:

```
sudo fsck -f -y /dev/mapper/logical-volume
```

For more infomation: [http://adminschoice.com/repairing-unix-file-system-fsck]("http://adminschoice.com/repairing-unix-file-system-fsck")

---

### Post by rezanabavi on 2011-01-05
Dear friends, I had same problem with ubuntu 10.10. I run many cods

in terminal but they did not work. finaly I try with slax. I run slax live CD and run its terminal the following code:

```
e2fsck -y -f -v /dev/sda1
```

sda1 is the partition where my ubuntu was installed.

then rest slax and I could login to ubuntu again.

So great slax, :p

slax link:

[http://www.slax.org/get_slax.php]("http://www.slax.org/get_slax.php")

---

### Post by Carmellotruffles on 2011-01-22
I put the install disk in now how do I get it to boot? It doesn't do It automatically.
My screen says:
No init found. Try passing init= bootarg.

BusyBox v1.13.3 ( ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by Meltey on 2011-02-15
Hello, I have the same problem with "try passing init=bootarg".
I managed to fix it by booting into liveUSB and using e2fsck command but the problem always appear a few days later. I really dont know why this is happening and I dont want to use liveUSB every second day...could someone help me please? :)

---

### Post by Meltey on 2011-02-15
just hit the F2 or F12 button (Boot setup or something like that) ,choose BOOT options and choose CD or USB as 1st boot priority :)

---

### Post by pyrial on 2011-04-03
So I just resolved that crappy problem and heres what I did:
 
First I installed ubuntu on a seperate hard drive and ran that as primary hard drive. then I opened terminal and entered:
 
*sudo fdisk -l*
 
The errored hard drive was sdb1. I then entered:
 
*sudo fsck /dev/sdb1*
 
There were questions i answered yes to then booted normally after it finished. everything was normal exccept I have to choose a different version of ubuntu at startup. I havent had any problems so far but this was just an hour ago. Good luck and hope this helps.

---

### Post by alyaba on 2011-04-30
Any other fixes that dont require a second hard drive?

---

### Post by gemrico on 2011-05-01
i to have gotten mount: mounting/devon/root/dev failed:no such file or directory  then TARGET filesystem doesnt have requested /sbin/init 
Busybox v1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) enter help for a list of commands
initramfs 
 
 
PLEASE HELP ME WHAT DO I DO  ITS DRIVING ME CRAZY I COMMUNICATEWITH MY PARENTS THREW SKYPE MY FATHER IS ILL SO IF SOMEOME COULD PLEASE HELP ME THANK YOU

---

### Post by deadlytackler on 2011-05-03
Same No init found problem, using Ubuntu 10.04 LTS, tried 
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
     417 inodes used (0.86%)
       1 non-contiguous file (0.2%)
       0 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 407
   73815 blocks used (37.94%)
       0 bad blocks
       0 large files

     401 regular files
       7 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
     408 files
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
e2fsck: Device or resource busy while trying to open /dev/sda3
Filesystem mounted or opened exclusively by another program?
I suppose problem is with sda3, what is the solution? because of this sda3 even boot_info_script is not working it hangs when it starts working on sda3.

---

### Post by timstewart on 2011-05-09
Today I moved a computer across a desk and changed the monitor. On boot I got the 'no init found' etc. DryChilli's post sorted my encrypted volume error out. BTW fs is ext4 as I have seen posted elsewhere.

Thanks a lot. Top man.

Tim.



> **DryChili said:**
> Hi!

I had the problem too, but it was my fault. My computer hung, so I switched it off. Afterwards I got this error.

To fix it is easy. Just boot from a USB-stick or CD and do fsck.

Some instructions:

List your partitions:
```

 ls /dev/sd*

```If you haven't got an encrypted disk just do (where sda5 is the corrupted partition):
```

fsck /dev/sda5 

```If you are using an encrypted hard-disk (i do) do

```

sudo cryptsetup luksOpen /dev/sda5 something

```where sda5 is the encrypted partition and someting is the name under which you will find the partition (/dev/mapper/something).

The install  Lvm and look for volumes :

```

sudo apt-get install lvm2
sudo pvscan
sudo vgscan

```The last command should list the at least one volume-group
Enable it or the ones you're interested in

```

sudo vgchange -a y groupname

```Now list the logical volumens

```

sudo lvscan

```Your drive you're interested in should now appear under /dev/mapper

do a fsck

```

sudo fsck /dev/mapper/logical-volume

```Lots of errors! Off course you want to have them all fixed. REBOOT!
This worked for me!

Best regards!

---

### Post by Gemba on 2011-09-17
> **andddlay said:**
> This post led me to the answer:

[http://ubuntuforums.org/showpost.php?p=9411005&postcount=2](http://ubuntuforums.org/showpost.php?p=9411005&postcount=2)

I ran a live CD, opened terminal, and typed in "sudo fsck /dev/sda7" (where my ubuntu partition was located)


Thanks so much for this! Worked a treat.

---

