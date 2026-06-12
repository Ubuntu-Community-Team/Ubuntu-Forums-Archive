---
title: "Grub a Grub Grub?"
date: 2011-01-20
forum: General Help
---

### Post by Tnt8902 on 2011-01-20
Hello Readers/Scanners!! Well this is my first post and new to Linux[ubuntu]. Im Dual booting with windows Xp pro and Ubuntu 10.10, so my question is; When I boot my lappy after it shows the dell screen im prompted by the grub screen, i dunno if it is grub legacy or gub 2 atm, but it gives me options like

Linux generic kernel 4#
Linux generic kernel 4# recovery
Linux generic kernel 2#
Linux generic kernel 2# recovery
memory test
memory test
Microsoft Windows XP pro blah blah blah

and it is standard black and white no nice logo or anything flashy.

Second is that i tried to see what version i have under terminal it says;
tnt8902@tnt8902-Latitude-D820:~$ grub --version
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

what should i do?
how can i make the grub look nice
how can i remove the extra linux kernals
i need help!!!!!
:popcorn:

---

### Post by Quackers on 2011-01-20
Welcome to UF
Have a look here
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Tnt8902 on 2011-01-20
Wow now I done it, I did something wrong under the grub customizer and I lost grub start up and it sends me strait into grub terminal, what can I do now LOL

---

### Post by Quackers on 2011-01-20
What did you do? It's not safe for me to guess :wink:

---

### Post by Tnt8902 on 2011-01-20
> **Quackers said:**
> What did you do? It's not safe for me to guess :wink:

when i installed the grub customizer, i started the application, i when it listed the OS I unchecked everything . i also removed them............. with the - minus sign ,except the linux and the microsoft oses, i clicked save and install to mbr... do you have gtalk btw?

---

### Post by Tnt8902 on 2011-01-20
i also tried to install grub2 thru livecd/usb  but it is giving me this


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007070c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5561    44662474+   7  HPFS/NTFS
/dev/sda2            5561       14594    72557569    5  Extended
/dev/sda5            5561       14220    69555200   83  Linux
/dev/sda6           14220       14594     3001344   82  Linux swap / Solaris

Disk /dev/sdb: 1999 MB, 1999634432 bytes
16 heads, 32 sectors/track, 7628 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16        7628     1948736    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ grub-install --root-directory=/mnt/ /dev/sda5
rm: cannot remove `/mnt//boot/grub/915resolution.mod': Permission denied
ubuntu@ubuntu:~$

---

### Post by Quackers on 2011-01-20
No sir, I don't.
It's not good to take the "bull in a china shop" routine :-)
One thing at a time is safer!
What does your screen say, exactly please, when you try to boot?

Edit; you don't install grub to a partition (sda5) but to the mbr of sda, in your case.

---

### Post by Tnt8902 on 2011-01-20
> **Quackers said:**
> No sir, I don't.
It's not good to take the "bull in a china shop" routine :-)
One thing at a time is safer!
What does your screen say, exactly please, when you try to boot?

Edit; you don't install grub to a partition (sda5) but to the mbr of sda, in your case.

hrmm its not gonna be word for word but i can give you a hint.

it says something about bash commands

then below that it says 

Grub >


right now im using my livecd and also using my phone as a teether so i can fully use the ubuntu forum site

---

### Post by Quackers on 2011-01-20
Have a look here
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)
your /root partition is /dev/sda5

---

### Post by Tnt8902 on 2011-01-20
> **Quackers said:**
> Have a look here
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)
your /root partition is /dev/sda5


ubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ 


this showed up when i typed ls

To help locate or verify the correct system partition is selected, use the *ls* command. First use the *ls* command to find the known partitions; then expand it's use to verify the location and contents of the *grub* folder. Examples:  
***ls***  returns drives and partitions located by Grub 2:  (hd0) (hd0,1) (hd0,5) (hd1) (hd1,1) 
***ls (hd0,5)/boot*** returns the files and folders in *sda5's* /boot folder. If the path correctly points to Ubuntu's */boot* folder the result should include the kernel and initrd images and the *grub* folder. If the command does not find the correc 
***ls (hd0,5)/boot/grub*** returns the files and folders in the */boot/grub* folder of *sda5*. If the path correctly points to Ubuntu's */boot/grub* folder the result should include numerous *.mod files.

---

### Post by drs305 on 2011-01-20
Grub Customizer can rename and move some of the Grub2 files so it might be hard for us to help you put it back together.

An easier method would be to boot the LiveCD and then purge and reinstall Grub2 using the chroot method described in this guide:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
It will remove all the normal Grub2 files and reinstall them to their original condition.

/dev/sda5 is the partition you should mount to start the chroot procedure.

---

### Post by Tnt8902 on 2011-01-20
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ 


ok i figure its better to reinstall grub2 sence all the other methods arent really helping and really confusing the pretzels out of me, so apparently im lost at this point any ideas?

windows is sda1
linux is sda5

---

### Post by Quackers on 2011-01-20
This is an ongoing question at the moment. For the last command try
```
sudo grub-install --root-directory=/mnt /dev/sda
```
In other words no extra / after /mnt, and to sda, not sda5

---

### Post by Tnt8902 on 2011-01-20
> **Quackers said:**
> This is an ongoing question at the moment. For the last command try
```
sudo grub-install --root-directory=/mnt /dev/sda
```In other words no extra / after /mnt, and to sda, not sda5


Awesome it here is output


ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.

---

### Post by Quackers on 2011-01-20
Reboot and see how it goes :-)

---

### Post by Tnt8902 on 2011-01-20
Thank you and Thank you!!!! You helped me restore my Grub2.

now sense i installed the grub2 customizer i changed the background and the color texts but they are still the same color as before. any ideas?

the background is a jpg format that i used from the background directory.

---

### Post by Quackers on 2011-01-20
Is a .jpg allowed? I'm not sure. And take it easy - you just fixed it :wink: :-)

---

### Post by libssd on 2011-01-20
Essential informatioun about grub/grub2 **here**: _[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)_

More than you ever wanted to know **here**: _[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)_

**Edit**: If you're truly determined to muck about with grub, use Remastersys (or similar tool) to create a restorable backup image of your system. It's such a relief to know that if you screw something up, it's possible to be back in business in 15 minutes with your system restored exactly as it was before you borked it. 

Been there, done that, don't want to go there again. After several unsatisfactory experiences with burg, I decided a functional system was more important to me than a pretty grub screen. That said, I have probably learned more by breaking things than from reading. Just have a backup in place.

---

### Post by drs305 on 2011-01-20
You can use a jpg image (8-bit) but some experienced Ubuntu users have reported problems with the Grub Customizer (GC) and boot backgrounds. 

I haven't had time to troubleshoot them but there have been some large changes to the files that Grub uses to include the background image information. It's possible that Grub Customizer hasn't caught up to these changes yet. 

I don't want to blame GC since I don't know, but that's a possibility. As *Quackers* suggests, getting the system to boot is a major hurdle. While it would be nice to get the background image, don't do anything, ah ... rash ...., while trying to fix it. (*Quackers* didn't say that last part, I did.)   ;-) 

If I find out the reason it doesn't work I'll post my findings.

---

