---
title: "Partitions?"
date: 2010-11-04
forum: General Help
---

### Post by Yezinki on 2010-11-04
Hi there,

While installing Ubuntu, how many partitions in total should I create, there approx sizes, file systems etc.

Will they be created automatically or do I need to create them manually?


Regards!

---

### Post by Quackers on 2010-11-04
If you just install into free space on the disc Ubuntu will create the minimum amount of partitions (root and swap) by default.
If you want to do it manually you can create a root partition of at least 6GB (mine is 12GB) with a mount point / and ext3 or ext4 file system.
Then a swap partition of type swap and no mount point of a size slightly bigger than the amount of ram your machine has (if you use hibernation).
Then a separate /home partition with a mount point /home of whatever size you want (eg the rest of the disc) in either ext3 or ext4

---

### Post by Yezinki on 2010-11-05
Thanks for sharing your views.

Do you have a dual boot or just Ubuntu on your Vaio machine.

Regards!

---

### Post by Quackers on 2010-11-05
You're welcome :-)
I usually have 3 systems (or so) running at the same time. I have W7 and Natty-testing on the first HDD and Maverick occupying the whole of the second HDD.

---

### Post by Yezinki on 2010-11-05
1. root partition/ with a mount point, ext4 = 12 GB

2. swap = 2 GB.

3. Separate home/with out a mount point ext4 = the rest.


a. What exactly is the purpose of root & home?

b. Should the drive be encrypted?

c. Which of the 2 can be shared with another OS/Linux distro?


Regards!

---

### Post by Quackers on 2010-11-05
No, item 3 the mount point for the /home partition is /home
It's the swap partition that doesn't have a mount point.

The root partition is what holds your basic operating system files.
The home partition is for your user settings and installed programs etc.
The advantage of having a separate home partition is that if you upgrade the system you update only the root partition, leaving your home partition alone.

I suppose encryption is a decision you will have to make. I don't but some do.

I can't be specific as to which partitions can be shared as it's not something I use. I would imagine swap and any data partitions you may make could be shared if using a compatible file system.

---

### Post by rob.arntfield on 2010-11-05
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Useful information from ubuntu. 

Three partitions is a good setup (personally speaking). Root, Swap and home. 

Swap partitions are shared between different linux distros. As well, you can have complete access to files on other partitions of your drive. (for example, right now i'm pulling something off of my openSUSE partition)

---

### Post by mastablasta on 2010-11-05
that and you can easilly partition more later if you feell the need.
 
i don't have separate home partition at the moment but i might do it in the future after i decide to remove WinXP.

---

### Post by Yezinki on 2010-11-05
Which is a better partitioning tool...gparted CD, Partimagic CD?

Thanks

---

### Post by WorMzy on 2010-11-05
gparted uses the same utilities to create/modify partitions that are used by Ubuntu to read/write to the partitions. I'm unsure about Partimagic, I can't find any information about it. I recommend that you use gparted, it's a standard utility that comes on most LiveCDs these days, and works just fine.

As for partitions, I find that a /home partition is unnecessary; but a data partition, formatted as NTFS, is ideal for storing all your documents and media, as you can then access it from Windows (if you ever need to use it). I currently multi-boot with Ubuntu 9.10 and 10.04, Debian 5.04, Arch Linux (32 and 64 bit installs), Windows Vista, and Windows XP Pro. I allocate 40GB for each Linux partition, and 100GB for each Windows partition. But I have two terabyte drives in my PC, so I have space to burn. :P

---

### Post by Yezinki on 2010-11-05
WorMzy......... Personally I like Kubuntu it's rock solid, great layout & better than XP, Vista or even W7Ult.

I don't even wanna install any windows on this machine having a 230 GB HDD.

I feel that can do all with Kubuntu... why would I need 7, Vista or XP...... but what would you care to answer 2 questions?

1. How would you make a plan to partition a drive for a dual boot of XP & Kubuntu.........size 230 GB?

2. What are the salient feature of wine & its utility?

Best Regards!

---

### Post by WorMzy on 2010-11-05
I assumed you were using Windows, since you mentioned CHKDSK in your other thread. If not, then don't bother with a NTFS partition -- you can't defrag it from Linux, and NTFS really aught to be defragged periodically.

I use Windows for playing graphically intensive computer games. Things like Fallout 3, Team Fortress, Crysis, etc. You can play these games on Linux, using wine as a compatibility layer, but the display drivers for Linux don't work nearly as well as they do in Windows, meaning that you don't get the same texture quality or number FPS on Linux. Wine is better suited for 2D applications designed for Windows, such as Photoshop, Microsoft Office, etc.

If I was dual booting with those two OS', I'd allocate 100GB for Windows, 40GB for Kubuntu, 5GB Swap space, and the rest as shared NTFS storage (Documents, Music, Videos, etc).

---

### Post by Yezinki on 2010-11-05
1. 100 GB for windows fine.

2. 40 GB for Kubuntu.........could you be specific regarding root, home  allocations individually?

3. 5 GB for swap ok.

4. approx 80 GB Data NTFS.

I don't play games on either computer or on my Nokia N8 lol.

Can I use wine to run windows apps like windows yahoo messenger .......cause I do video conferencing & Kopete doesn't support audio video only Skype does & not all my clients have Skype??

Regards!

---

### Post by Yezinki on 2010-11-05
Besides games what other pros can you give to convince for a dual boot.........I have Windows Only running on my laptop.

Regards!

---

### Post by Yezinki on 2010-11-05
Can i run windows live & yahoo messenger using wine?

---

### Post by WorMzy on 2010-11-05
Unfortunately, it doesn't look as though WLM or YIM work too well with wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=127]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=127") [http://appdb.winehq.org/objectManager.php?sClass=application&iId=29]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=29") which may be another reason to dual-boot.

Though, the WLM page suggests using [aMSN]("http://amsn.sourceforge.net/index.php"), a Linux alternative which apparently has integrated webcam features which may suit your needs. Not sure about audio support for this app though. The YIM page also suggests Yahoo! Messenger for Unix, but that doesn't seem to have webcam support.


As for the partitions, I'd just use the 40GB as / and not bother with a /home partition. I'd store all my documents in the shared partition anyway, so all that'd be in the /home partition would be config files and such. If you create specific folders inside the storage partition, you can mount --bind or symlink them into your home area, making it so that your ~/Documents folder is actually the shared folder. You'd need to edit /etc/fstab to set this up, but once it's done, you'll never need to think about it again. If you decide to go down this path, let me know and I'll give you instructions on how to set it all up.

---

### Post by Yezinki on 2010-11-05
Thanks WorMzy for the search about the messengers using wine.

I'll go by your plan for a dual boot of XP & Kubuntu.

Am grateful to you big time.

Just take it easy with me cause as said many times am a retired old MD new to the world of Linux & windows.

Looking forward to seeing your custom install dual boot plan.

The legit copy of XP MCE Pro 2005 that I got with this Vaio desktop is bundled with drivers, 3rd party trial softwares....The XP MCE DVDs manufactured by MS for Sony wont install like default XP.........with options to create, resize format partitions.

If I want to install XP than it shall be a OEM/Sony install. After that using any disk partition bootable CD for which I have been using Disk Director CD to resize ,create , delete partitions/HDD. Only than can I install another OS like had Vista running.....dual boot of XP & Vitsa.

Just for your info I like to create a Full back image of the machine at various steps just in case & later if I experiment try some thing new have a peace of mind that have a backup & wont have to install all from scratch.

Regarding fsck.......I boot from a LiveCD & type it in the terminal?

How can I check the integrity of a k3b burnt ISO with out installing.....though the burn was successful?

Man Kubuntu supports my desktop hardware as if it was made for it lol.

---

### Post by WorMzy on 2010-11-05
There should be an option to check the disk for errors during the boot-up stage, but in order to see this option you need to press the arrow keys immediately after the screen turns purple, otherwise it'll be skipped.
[[IMG]http://img703.imageshack.us/img703/4892/ubuntubootsplashbeforei.th.png[/IMG]]("http://img703.imageshack.us/img703/4892/ubuntubootsplashbeforei.png")

---

You said you're installing by OEM, so it shouldn't matter too much which order you install the operating systems; though if you're planning on wiping the hard drive and starting again, I'd install XP first, and *then* install Kubuntu. Doing it in that order saves having to reinstall grub (since Windows always installs it's own bootloader, which breaks grub). If you do it the other way, and install XP after installing Kubuntu (or if you're keeping the existing installation), then you'll need to reinstall grub, follow this tutorial for that: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

I posted the fsck command in the other thread. Just boot into the LiveCD and run the command (editing it as necessary; e.g. use "fsck.ext3" if your partition is formatted as ext3 -- run "sudo blkid -c /dev/null" if you're unsure)

---

Setting up the shared folders is pretty simple, but you need to have created the shared partition and the folders first.

You just need to set the shared partition to automount under your ownership ([see this HOWTO]("http://ubuntuforums.org/showthread.php?t=1604251") for info on how to do that), and then specify which folders you want bound and where.

e.g.
```
#mount the shared partition:
UUID=7A5C94995C94522D                     /media/Terastore        ntfs auto,uid=1000,gid=100,utf8,umask=002 0 0
#bind the folders:
/media/Terastore/Collection/              /home/wormzy/Collection none bind                                 0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none bind                                 0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none bind                                 0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none bind                                 0 0
/media/Terastore/Videos/                  /home/wormzy/Videos     none bind                                 0 0
```

---

### Post by Yezinki on 2010-11-05
Thanks WorMzy.

1. Both burnt ISO were checked according to your method were error free.
2. I booted e LiveCD & typed sudo blkid -c/dev/null>fsck.ext4


it displayed various parameters/command like -p, -c etc but none worked?

3. I would simply say Kubuntu suits me the best better than any windows or Mac OS X.

Best Regards!

---

### Post by Yezinki on 2010-11-05
```
**[SIZE="3"]"Do I really need XP on this desktop?"[/SIZE]**
```

---

### Post by Yezinki on 2010-11-05
WorMzy these are the screen shots captured of the disk errors.

For your expert opinion.

Regards!

---

### Post by Yezinki on 2010-11-05
How do I get em fixed.......service the desktop or .........??

---

### Post by WorMzy on 2010-11-05
> **Yezinki said:**
> 2. I booted e LiveCD & typed sudo blkid -c/dev/null>fsck.ext4


Whoa, don't type that! They're separate commands. The blkid command tells you about all the partitions on your system, telling you such information as what they're identified as (e.g. /dev/sda1) and type they are (e.g. ext4); use the information that gives you to figure out which partition is your root partition, and which filesystem it's formatted as, then use that information to modify the fsck command (if necessary). Also, note the space between "-c" and "/dev/null", correct whitespace is essential when using terminal commands, missing out a space can stop a command from working, and may even cause problems -- especially when sudo is involved. Make sure you write out commands perfectly, or copy-paste then from here, if possible, to avoid mistakes.

I don't like the look of that Reallocated Sector reading, that's a dangerously high number of bad sectors; your hard drive might not remain operational for much longer. You may want to consider buying a new hard drive for your machine, and scrapping this one before it gives up the ghost. However, SMART readings have been known to be wrong before, so if you don't mind taking a risk, then it's up to you if you want to keep using it.

The temperature reading doesn't worry me so much.

> "Do I really need XP on this desktop?"

Only you can answer that. Having two Operating Systems leaves less space for file storage, but sometimes you can't do everything with just one OS. If that aMSN program does what you were planning on using wine+Yahoo Messenger for, then do you need XP for anything? If not, don't install it. But if aMSN doesn't work, then can you convince your clients to use Skype instead?

---

### Post by Yezinki on 2010-11-05
Thanks WorMzy.

1. What other tests can I perform to confirm a HDD failure if any?

2. Which drives & what options do I have to replace this WD 250JS since the machine is very compact?

Regards!

---

### Post by Yezinki on 2010-11-05
[http://support.wdc.com/product/download.asp?groupid=606&lang=en](http://support.wdc.com/product/download.asp?groupid=606&lang=en)

---

### Post by Yezinki on 2010-11-05
Some more screen shots of the Disk Utility.

---

### Post by WorMzy on 2010-11-05
Okay, blkid confirmed that your partition is /dev/sda1, and it's filesystem is ext4. So you don't need to make any changes to the command I wrote in the previous thread:
```
fsck.ext4 -fpc /dev/sda1
```

Just running fsck.ext4 without any arguments doesn't work because you haven't told it what to check. The other arguments (-fpc) stand for (f)orce check, which means that even if the partition has only just been checked recently, check it again anyway, (p)reen the filesystem [fix any easily fixable problems], and (c)heck for, and report any bad blocks.

---

I don't know of any other disk diagnostic tools for Linux; but any that exist probably use the same data (SMART) to diagnose the drive. And that website only has a specialist diagnostic tool for Windows, you can either accept the SMART diagnosis as accurate, install Windows and run the specialist diagnostic, or run the diagnostic with wine. But I wouldn't trust wine to run the diagnostic, since it's dealing with hardware. It might work fine, it might not work at all, or might cause more damage. I'm not sure about that one.

---

Those screenshots show that you're booted into your Ubuntu installation, and not a LiveCD. The partition is mounted as "/", and cannot be unmounted, and therefore cannot have fsck run on it. You have to boot into a LiveCD (or USB).

---

### Post by Yezinki on 2010-11-05
Wont allow to run command fsck.ext4 -fc /dev/sda1

Displayed an error saved to desktop, but cannot find it?

---

### Post by Yezinki on 2010-11-05
Typed  ```
fsck.ext4 -fpc /dev/sda1
```

Displayed a warning firstly, entered Y..........than " You dont have the rights"

?

---

### Post by WorMzy on 2010-11-05
Sorry, ```
*sudo* fsck.ext4 -fpc /dev/sda1
```

What was the warning? If was anything like "This partition is mounted, running fsck will bugger it up completely" then **don't** run fsck, unless you're a masochist. ;)

Seriously, I can't emphasise enough that you shouldn't run fsck on a mounted partition. You need to be in a LiveCD environment (or another Linux installation) to fsck your root partition.

---

### Post by Yezinki on 2010-11-05
It has 199 bad sectors..........why could'nt windows pick em up, despite I did regular defrag, CHKDSK with option checked to automatically fix bad sectors........should I install run Kubuntu on my laptop to check it;s HDD status........though Hitachi Drive Boot Fitness CD ran all the test & found it to fine?

Which HDDs could replace this one.......what options do I have?

Sony Vaio VGC-LS1..........945 GM Chipset.

What are the do's & dont's while installing HDDs & to take care drive health fitness.

My machines chipset wont support a SSD?

USBs are fine but won't be bootable.

Can excessive defrag & low formats decrease a HDD life? 

I shall run this new command using LiveCD & let ya kn  the results.

Regards!

---

### Post by Yezinki on 2010-11-05
I am in using Live CD this is the output what should I do now?

ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

---

### Post by Yezinki on 2010-11-05
with out sudo:

ubuntu@ubuntu:~$ fsck.ext4 -fpc /dev/sda1
fsck.ext4: Permission denied while trying to open /dev/sda1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$

---

### Post by Yezinki on 2010-11-05
ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

---

### Post by oldfred on 2010-11-06
When you started the liveCD did you click on sda1 to see if it worked. That mounted it. You need to umount it.

---

### Post by Yezinki on 2010-11-06
I didn't see an option of sda1 on starting the Live CD?

---

### Post by Yezinki on 2010-11-06
I am again using Live CD..........same out put:

ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

---

### Post by Yezinki on 2010-11-06
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ fsck.ext4: Device or resource busy while trying to open /dev/sda1
No command 'fsck.ext4:' found, did you mean:
 Command 'fsck.ext4' from package 'e2fsprogs' (main)
fsck.ext4:: command not found
ubuntu@ubuntu:~$ Filesystem mounted or opened exclusively by another program?
Filesystem: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo fsck.ext4 -fpc /dev/sda1
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ fsck.ext4: Device or resource busy while trying to open /dev/sda1
No command 'fsck.ext4:' found, did you mean:
 Command 'fsck.ext4' from package 'e2fsprogs' (main)
fsck.ext4:: command not found
ubuntu@ubuntu:~$ Filesystem mounted or opened exclusively by another program?
Filesystem: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$

---

### Post by Yezinki on 2010-11-06
No luck despite unmount.

---

### Post by WorMzy on 2010-11-06
I don't know what to tell you then. If fsck refuses to run, then there's not much you can do about it.

> It has 199 bad sectors..........why could'nt windows pick em up, despite I did regular defrag, CHKDSK with option checked to automatically fix bad sectors........should I install run Kubuntu on my laptop to check it;s HDD status........though Hitachi Drive Boot Fitness CD ran all the test & found it to fine?
You can't 'fix' bad sectors, the hard drive just makes a note of where they are, and then redirects any data to be written to a bad sector to a specially reserved area.

> Which HDDs could replace this one.......what options do I have?

You should be able to replace the drive with another 3.5" SATA hard drive. I dunno about where you are, but over here you can pick up a 250GB one for £25 (or a 1TB on for £40).

> What are the do's & dont's while installing HDDs & to take care drive health fitness.

Obviously be gentle, hard drives are very robust, but they contain moving parts and so can be damaged by impacts and violent shaking. Clean out your fans and vents, so that heat can be blown out, keeping the drive cool.

> My machines chipset wont support a SSD?

SSD is overpriced anyway. I'm sure you can live without it. :P

> Can excessive defrag & low formats decrease a HDD life?

Of course. But anything that uses the hard drive decreases it's life. Nothing lasts forever. ;)

---

### Post by Yezinki on 2010-11-06
Hi WorMzy I gotta cheap 350 GB 16 MB buffer to replace the 250 GB 8 MB WD Cavier SATA II HDD.

But what I am gonna do when I need Kubuntu or may be XP & Kubuntu.

I am confused whether to dual boot or simply install XP.

Just to run Yahoo & Windows Live audio video features install XP?

Vs 350 GB for Kubuntu?

Hope you could guide me,

Regards

---

### Post by WorMzy on 2010-11-06
The choice is yours. If you need XP, then you don't have much choice there; as for Kubuntu, well, do you want to keep using it or not? How much time have you been using it recently? If it's been your primary OS for a while, then it's clearly been working for you, would giving up using it now be a good choice for you?

At the end of the day, I can't tell you what to, and what not to install; it's your PC, and you're the one that'll have to use it, so you'll have to make the decisions for yourself.

Allocating 350GB for Kubuntu seems a little over the top to me, but if you'll be using it as storage as well as for the OS, then maybe; but in that case I'd probably create a separate /home partition (since there's no other OS' to share with), that way, if something goes wrong with Kubuntu, you can reinstall it without losing all your personal files.

In this case, I'd allocate 40GB for Kubuntu, 5GB for Swap, and the rest for /home.

If you go with a dual boot: 40GB for Kubuntu, 100GB for Windows, 5GB for Swap, and the rest for a shared partition.

If you go for windows only: 100GB for Windows, and the rest for storage.

Again, these figures are just what I'd use. You can use what ever values you want (within reason - you can't install Windows to a 3GB partition :P).

---

### Post by Yezinki on 2010-11-06
Thanks WorMzy,

I am going with a dual boot...at this moment firstly installing XP MCE after that Kubuntu.

Previously XP MCE e Off 07 took 13 GB of disk space & allocated the rest for Data/Images/softwares etc.

After the install OEM XP MCE & all related windows things shall use DD CD to resize the HDD, defrag, CHKDSK & create a NTFS partition. 

What should be its size, type/logical/primary & could it be shared with Kubuntu?

As to Kubuntu how many partitions, root, home, swap, shared/data & there sizes?

Best Regards!

Btw is would a 16 MB buffer cache  vs 8 MB makes a difference?

---

### Post by Yezinki on 2010-11-06
What's this command used for  sudo shutdown now -R  ?

---

### Post by Yezinki on 2010-11-06
Do tell me the intricate details regarding Kubuntu install....which partitions to mount etc.

Regards!

---

### Post by WorMzy on 2010-11-06
Yes, the NTFS partition can be used by Kubuntu for storage. You can only have four primary partitions on a hard drive, but if I understand correctly, four is all you need: 1) Windows, 2) Software/storage, 3) Kubuntu, 4) Swap. If you wanted any more than four partitions, or if you think that you *might* need more partitions in the future, then you'll need to use one of the four primary partitions as an extended partition:

1) Windows, 2) Software/storage, 3) Kubuntu, 4) Extended: [ 5) Swap ]

If your disk is 250GB, Windows is content with 16GB, you plan to use 40GB for Kubuntu and 5GB for Swap, then your storage partition can potentially be 189MB. But disk manufacturers distort the truth, so you've probably only got about 240GB of usable space to start with, so I'd make the storage partition 180MB big.

For Kubuntu partitions, I'd just create a root (/) partition. Personal files and media can be stored on the NTFS partition, so a /home partition wouldn't be necessary. A 5GB swap should be sufficient.

There's no such flag as -R for the shutdown command, but a lower case "r" means (r)estart. So "sudo shutdown -r now" makes Ubuntu restart the PC now.

---

### Post by Yezinki on 2010-11-06
Thanks. True the HDD size on the box is 350 & after XP install displays 292 GB. Previously was 250 & 230 GB.

Fresh XP MCE install is 5.60 GB.

Kubuntu is rock solid windows is a security risk.

Shall keep you updated.

Regards!

---

