---
title: "Dual boot, lost windows on Kubuntu 9.1 install"
date: 2009-10-26
forum: General Help
---

### Post by yoshimitsuspeed on 2009-10-26
My computer had kind of a ghetto boot setup. 
At one point I had two installs of XP and a couple of linux. 
Then I installed Vista which started up to it's boot manager then let me select vista or either XP. 
Once I got linux working again it would load to grub where I could select kubuntu or load the vista boot manager. 
Then I got rid of vista cause I didn't like it but still used the same boot manager setup.

So I installed Kubuntu 9.1 on my computer. Wrapping up the install it said it saw windows as a bootable partition.
Once the install was complete and I restarted grub only had the new Kubuntu install listed. 
When I started up kubuntu none of my other partitions were even visible.
After a brief moment of panic I busted out testdisk and found and restored my partitions.
Once I updated grub it recognized my windows partitions as bootable but when I tried to boot them nothing happened. 
I used test disk to write to MBR thinking that would do it but nothing changed. 
Then I came across MS-sys and a how to telling me to use it to fix the boot sectors of the win partitions. 
I was able to run it on the drive and it says it updated the MBR but when I try on the individual partition like the how to says it says
 /dev/sdb1 seems to be a disk partition device
I wonder if this is a  problem from having testdisk write to the MBR?

Ok so in my old Version of XP which is a nearly usless nearly worthless OS on my system I found Boot.ini and other boot related files in the main dir that didn't exist in the folder for my current partition of windows. 
So just for S and giggles I copied and pasted those files into the new XP main dir and renamed it so I would recognize it then updated grub which recognized the change. 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect 

When I tried to boot that partition windows loaded normally till it got to the   blue windows splash screen just before you log in then it froze. Retried a few times. 
here are the files I copied over 


boot.ini
boot.ini~
bootmgr
BOOTSECT.BAK
BOOTSECT.DOS
CONFIG.SYS
IO.SYS
MSDOS.sys
NTDETECT.com
NTLDR
ntuser.dat
ntuser.dat.LOG
pagefile.sys
I didn't overwrite anything. If I copied it over it wasn't there before. 
I am almost positive that list is right but I wasn't paying a lot of attention when I did it. It occured to me later it would be a really good idea to know exactly what files I had moved lol. 
Anyway what now?

---

### Post by Zimmer on 2009-10-26
No idea :( 
but there may be a clue as to how to proceed somewhere from here
[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

Vista may have scrambled the other Win install's  .ini files with regard to the partition info.

see
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I hope this may be of use...

---

### Post by yoshimitsuspeed on 2009-10-26
Wow this is crazy.
last post 3 hours ago and already on the 5th page. 
Thanks for the links. 
Checked it out. There might be some helpful tidbits there with lots of research.
I'd hate to have to learn a lot about an OS I never plan on using again lol.
More input would be much appreciated.

---

### Post by arrrghhh on 2009-10-26
I'm not sure what you want/need at this point... Based on that kludge you listed above tho, you probably need to start from square one... and I mean ONE!

As in, backup any docs, pics, vids, etc that you need - and just wipe.  Reinstall Windows first, then do Ubuntu.  You s/b good then... It sounds like all that MBR work you did has now left your system unusable.

---

### Post by oldfred on 2009-10-26
When you installed Vista it took over your XP install. You need to run fixboot and fixmbr from a XP boot disk repair and see if XP boots then reinstall grub to the partition which should overwrite only what fixmbr did. The contents of fixboot is the second part of windows boot that is in the windows partition kinda like when grub is installed into a partition for chainbooting.

These are the files in my XP, the rest must be from Vista:

boot.ini

CONFIG.SYS
IO.SYS
MSDOS.sys
NTDETECT.com
ntldr

pagefile.sys


Also:
autoexec.bat
inf.log
service.log
logfile
The old msdos config.sys and autoexec.bat are 0 bytes but may be required 


boot.ini:

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

I copied these instruction from someone here:
seems your MBR is damage. but you can repair it if only you can boot in windows cd and entering in the recovery console.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by clhsharky on 2009-10-26
HI

Kubuntu 9.10 uses grub2.0 and its new, check out
Karmic Koala Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)
other people have same problem and some solutions.

---

