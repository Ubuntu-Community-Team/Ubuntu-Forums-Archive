---
title: "grub frustration when installing on an external hard drive"
date: 2009-10-31
forum: General Help
---

### Post by ghostier on 2009-10-31
I installed 9.10 on my 1TB external hard drive using the live cd, during this process, I selected to erase and install on my external hard drive, not selecting the internal harddrive for anything. However, after I finished installing, and when it was time to reboot, booting from my external hard drive (which had the 9.10 installed) just drops me into this command line saying something along the lines of "GRUB press TAB to see commands". When I tried to boot into my internal hard drive (windows 7) it says "Grub error cannot find disk" apparently it was looking for the external hard drive with the grub. I tried windows recovery but it didn't detect any problems. Now I can't get into ubuntu or windows.

---

### Post by Herman on 2009-10-31
:D Well you should have pressed 'Advanced' in step 7 of the installation and selected your USB drive's MBR and not the MBR of your first hard drive for where to install the GRUB.

It's okay though, it's very simple to fix your MBRs with the boot loaders you want again.

First, to fix Ubuntu, boot your Ubuntu 9.10 Live CD and open a terminal and go 'Places'-->'Removable Media' or just 'Places' and look under 'Computer' for the partition you want to mount in your USB disk, (your Ubuntu partition),  and click on it.
You should see an icon for it on your desktop, but what you may not see is the 'mount point', which will normally be located in your /media directory.

You need to find out the name of the mount point for your Ubuntu partition by taking a look in your /media directory or by running 'ls /media',
```
ls /media
```Then edit the following command by replacing the word 'disk' with whatever the name of the mount point is that you just found out (above). 
When ready, run the following command ,
```
sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sdb
```Where: /dev/sdb is your USB disk. If you have more hard dirves inside your computer you should check first by looking with a partition editor to make sure your USB disk is really /dev/sdb. If not, please change this number to whatever you need.

That should fix your USB drive to boot your Ubuntu and probably your Windows too. :D

---

### Post by ghostier on 2009-10-31
Thanks for the reply. Just one question, is the mount point a directory? Because I got this really long serial-number-like code when I typed in ls /media into the command line. When I checked the media directory of my external hard drive it has two folders in it, cdrom and cdrom0. and the directory of it is /media/"long serial number"

I tried the above command replacing disk with the long serial number and it gives an error saying "Invalid device 'dev/sdb'"

---

### Post by ghostier on 2009-10-31
I just looked over my external hard drive's media directory and both folders (cdrom and cdrom0) are empty cdrom being a shortcut.

---

### Post by Herman on 2009-10-31
> Thanks for the reply. Just one question, is the mount point a directory? Because I got this really long serial-number-like code when I typed in ls /media into the command line. When I checked the media directory of my external hard drive it has two folders in it, cdrom and cdrom0. and the directory of it is /media/"long serial number"
Yes, the 'mount point' is a directory.
When another file system is 'mounted', we usually open that (mount point) directory to see the files inside. 
To make it easier for users, we have an icon on our desktops which is a 'symlink', (shortcut) to the mount point, but the real ' mount point' is actually located in /media.

The big long ugly, cumbersome number you're seeing is a file system UUID number.
It's showing you that because it doesn't know what else you want to call it but it wants to be specific about exactly what file system is in there.
You can easily set a user-freindly 'label' for your file system with GParted.
Just right-click on the partition in GParted and you'll see' Label' in the right-click menu.
I like to label my Karmic partitions as 'KARMIC' and any data partitions as 'DATA', and so on. Makes things easier in lots of ways. ;)

I don't know why it would say 'invalid device', maybe it's unmounted or disconnected or something, or it's some other device number.
Try running 'sudo blkid' with it plugged in to see what /dev/ number it is,
```
sudo blkid
```Actually, you should be able to see that by looking at it with GParted as well.

---

### Post by ghostier on 2009-10-31
Again, your reply is much appreciated. It turns out that my internal hard drive (windows 7) was /dev/sda and my 1TB external hard drive (ubuntu) was /dev/sdb1. I can't seem to change the label, the right click menu is mostly disabled other than unmount, information and manage flags. I tried the grub-setup using the long serial code and /dev/sdb1 but it said that /dev/sdb1 is also an invalid device. btw, is karmic suppose to take up 16 gb? My 1TB hard drive which i formatted while installing karmic apparently used up 16 gb


EDIT: I was able to change the label after unmounting the partition (i named it karmic sorry for being unoriginal heh). i've confirmed that the partition is /dev/sdb1 yet it still says invalid device. I've also used ```
mount /dev/sdb1
``` to confirm it is mounted on /media/karmic

---

### Post by Herman on 2009-10-31
> Again, your reply is much appreciated. It turns out that my internal hard drive (windows 7) was /dev/sda and my 1TB external hard drive (ubuntu) was /dev/sdb1. :D Okay, good, that is as expected, thanks for confirming.
That means  /dev/sdb should be the correct device to re-install the code for pointing to GRUB to, (the MBR of /dev/sdb).
> I can't seem to change the label, the right click menu is mostly disabled other than unmount, information and manage flags.You might need to unmount it first, then those options should become usable instead of greyed out. Just click 'unmount'. You can always mount it again later.
>  I tried the grub-setup using the long serial code and /dev/sdb1 but it said that /dev/sdb1 is also an invalid device.:-k Hmm, I wonder why that might be?
> btw, is karmic suppose to take up 16 gb? My 1TB hard drive which i formatted while installing karmic apparently used up 16 gb A new Karmic install I have only takes up about 2.1 GB. Try right-clicking on it in GParted and click 'Check', then confirm that twice by clicking 'apply' in tow differnet buttons, wait a while and GParted will run a file system check in it for you. It might help and other than taking a few minutes, it won't do any harm.

---

### Post by Herman on 2009-10-31
> EDIT: I was able to change the label after unmounting the partition (i named it karmic sorry for being unoriginal heh). i've confirmed that the partition is /dev/sdb1 yet it still says invalid device.Okay, good, file system labels will make lots of things easier for you in lots of ways. :D

Okay, but you're trying to install GRUB to /dev/sdb right?
You can install GRUB to /dev/sdb1 alright too, that's the boot sector at the start of the partition, but the BIOS won't look there for boot code, it will only look at the MBR, so you need to install GRUB to /dev/sdb.

---

### Post by ghostier on 2009-10-31
Hmmm... it still says invalid device '/dev/sdb' 
i tried "mount /dev/sdb" but "can't find /dev/sdb in /etc/fstab or /etc/mtab"

---

### Post by Herman on 2009-10-31
:D Okay, let's change tack and try a different approach then.

You can download a Super Grub Disk for free from [supergrubdisk.org]("http://www.supergrubdisk.org/"), burn it to a CD and use it for lots of jobs, for example it can boot Windows for you and/or restore your Windows boot in the MBR of your first hard disk. (It installs syslinux).

You can also use it to boot into Ubuntu directly and then once you have Ubuntu running you'll be able to easily run grub-install to /dev/sdb and that should fix your USB drive's MBR. 
It's easier to boot Ubuntu and fix GRUBII from within compared with the other way which is also doable, chroot from the Live CD and run grub-install, [Recover GRUB 2 Via LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") - ubuntu wiki - you can do it that way if you want to.

Another idea would be to go download the latest [Parted Magic]("http://partedmagic.com/") Live CD, it has Super Grub Disk included in it now, plus it has all the other disc utility tools you'll ever need, all in the one CD and it's still only a small download, and free. :D

---

### Post by ghostier on 2009-10-31
Is it okay to burn? I mean the only cd drive i have available is the one im running the live cd on.

---

### Post by Herman on 2009-10-31
:( No, cancel that, we'll need to think of some other idea, I'm trying out SGD in Parted Magic and it's not able to handle the ext4 file system, at least not the version of Super Grub Disk I have now, in  Parted Magic.

---

### Post by Herman on 2009-10-31
[Recover GRUB 2 Via LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") - ubuntu wiki

I guess you'll have to do it the official way, it will take you a few more commands, but it should work, just remember to install GRUBII to /dev/sdb not /dev/sda, then you should be able to boot both operating systems with GRUBII.
Then your CD drive will be freed.
 Right after that well look into restoring your Windows boot loader to MBR in /dev/sda.

---

### Post by exploder on 2009-10-31
I came across this today. 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The information you need is in the guide.

---

### Post by ghostier on 2009-10-31
Thanks herman, trying the "official way" right now.

Whoa. I think I found what was wrong. When I tried "grub-update" it says that it cannot find a grub drive. Here's the full text:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-14-generic-pae
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done

```


Hmm... /dev/sdb isn't in my device.map, there is only /dev/sda and /dev/sdc

btw, if I install grub on /dev/sda (my internal hard drive with windows) would that allow me to access windows?

---

### Post by Herman on 2009-10-31
Well I think try skipping the update-grub command and go right to grub-install because grub-install runs grub-probe and grub-mkdevicemap again anyway, as well as grub-mkimage and grub-setup, (which was what we were trying to run earlier, without bothering to chroot first).
You can always run update-grub or  grub-mkconfig -o /boot/grub/grub.cfg later, (they both do the same thing, generate a new grub.cfg file).

---

### Post by Herman on 2009-10-31
> btw, if I install grub on /dev/sda (my internal hard drive with windows) would that allow me to access windows?What you're really doing is just installing a small code, less than 446 bytes, in the first half of the MBR.
That code is just a pointer, to make the MBR point somewhere else. It can be to the next few sectors right after the MBR, or it could be to a partition (boot sector), or it could be to some other sector, where the files for a boot loader may be located.

If you only have the Windows boot loader in your computer's internal ahrd disk and you install code to make the MBR point to GRUB in Ubuntu in your USB, it will work as long as your USB drive is plugged in and you should be able to boot either operating system. So 'Yes', that should give you access to Windows. It's kind of a relay setup.
If you don't plug your USB drive in before trying to boot though, you'll only get an error message and no boot. You MBR will be trying to point to GRUB in your USB but since your USB isn't there it won't be able to find GRUB.

It would be better for you to have a code in your internal hard disk's MBR that points to a boot  loader in the same hard disk so you won't need to worry about plugging your USB drive in every time.
It would be better for you also to have a pointer to GRUB installed in your USB so you can get it to boot in other computers in case you need the USB to work in someone else's computer.

---

### Post by ghostier on 2009-10-31
Alright, all the patience has finally payed off. I've installed grub on to my external hard drive (karmic) and now I can successfully boot into it. Right now I dont have my live CD in the drive and I'm using karmic. Now on to fixing the internal hard drive (windows). I'll reboot again without my external hard drive and see what happens to windows.

---

### Post by Herman on 2009-10-31
:D Okay, cool!

Can you boot into Windows via GRUB?
You should have a Windows entry in GRUB that you can select and you should be able to boot into Windows.
GRUB chainloads Windows by it's boot sector, (the first sector of the Windows partition, which has another small code with sector number pointing to the Windows boot loader).

I forgot to ask you which version of Windows you have, XP or Vista/Windows7?

There are lots of ways to fix the MBR and make it point to Windows's boot sector again, but choosing the best one to pick depends on what Windows version you have.

---

### Post by Herman on 2009-10-31
Here's a method you can use from Ubuntu which doesn't matter what Windows version, (after all, it's only a code to relay the boot to the boot sector), we can fix it with ms-sys.You can install the ms-sys program in Ubuntu or your Ubuntu Live CD with this command,
[FONT=Bitstream Vera Sans Mono][/FONT]```
sudo apt-get install ms-sys
```
Before you run ms-sys, you will probably want to check first and see which hard disk is which, so you can work on the right MBR, run 'sudo fdisk -lu' for that,  I expect it to be /dev/sda, but just to make sure ...
```
sudo fdisk -lu
```
From the output from the above command, you should be able to tell which of your hard drives are  called '/dev/sda', and which one is '/dev/sdb' and so on.
```
sudo ms-sys -m  /dev/sda
```
That's it, it should be all fixed! :D

---

### Post by ghostier on 2009-10-31
I have windows 7 and no, grub does not have an entry for windows. I think it only detects the boot from my external hard drive. I'm gonna try ms-sys now.

---

### Post by mechro on 2009-10-31
@ Herman

_Off Topic_

I didn't realise you posted here. Your Grub pages have been an indispensable guide over the past couple of years. Thanks. :D

---

### Post by ghostier on 2009-10-31
I can't install ms-sys somehow, it says that it couldn't find the package. Should I download a package from sourceforge?

---

### Post by tpjk on 2009-10-31
hey everyone!

i'm not trying to hijack this thread but i'm having pretty much the exact same problem.

i created a karmic live cd, booted from it, tried out karmic from the cd for a bit, decided i liked it enough to put it on my 16gb external usb stick/pendrive, went through the installation process without clicking the 'advanced' button in step 7 and now i can only boot if the stick is plugged in. that is what i would like to fix.

on my internal hd i'm dual booting win xp and intrepid with win as the boot partition.

here's the output of sudo fdisk -lu:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc51bc51b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2       486287550   488392064     1052257+   c  W95 FAT32 (LBA)
/dev/sda3        81915435   183574754    50829660    5  Extended
/dev/sda4       183574755   486287549   151356397+   b  W95 FAT32
/dev/sda5        81915498   179670959    48877731   83  Linux
/dev/sda6       179671023   183574754     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00021b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          52    31283909    15641929   83  Linux

```EDIT: does that mean that in order to be able to boot without the stick i would have to run the following: sudo ms-sys -m  /dev/sda[B]1  
[/B] 

> Here's a method you can use from Ubuntu which doesn't matter what Windows version, (after all, it's only a code to relay the boot to the boot sector), we can fix it with ms-sys.trying to install ms-sys i got the following error:

```
E: Couldn't find package ms-sys
```do i need to enable any special repos for this to work?


thanks herman for all of your help so far, and ghostier, i hope you'll get it to work:]

peace

---

### Post by ghostier on 2009-10-31
What problems do you get when you try to boot?

My problem was that I did a bad install of grub. By bad install I mean incomplete install (i think installing grub on external hard drive is the source of the problem) so I had to install grub manually from Live CD (you can read previous posts on this thread to follow what I did). Now, grub is successfully installed on my external hard disk (the hard disk with karmic), I still need to make my windows booting work by replacing grub with mbr. 

As for you, I don't know if my problem is the same as yours. Did you install 9.10 on your 16gb drive? How come you can't boot into windows or intrepid?

---

### Post by Herman on 2009-10-31
:D To have GRUBII scan your disks for other operating systems and add then automatically to your GRUB Menu, you should run 'sudo grub-mkconfig -o /boot/grub/grub.cfg'. 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by tpjk on 2009-10-31
> **ghostier said:**
> What problems do you get when you try to boot?

My problem was that I did a bad install of grub. By bad install I mean incomplete install (i think installing grub on external hard drive is the source of the problem) so I had to install grub manually from Live CD (you can read previous posts on this thread to follow what I did). Now, grub is successfully installed on my external hard disk (the hard disk with karmic), I still need to make my windows booting work by replacing grub with mbr. 

As for you, I don't know if my problem is the same as yours. Did you install 9.10 on your 16gb drive? How come you can't boot into windows or intrepid?

i didn't do a bad install of grub: as long as the stick is plugged in i have no problem booting into any of the systems. if i remove it and then try to boot it goes to grub-rescue right away.

---

### Post by ghostier on 2009-10-31
I've installed an early version of ms-sys because I am having trouble installing tar.gz package. And I made a windows 2000/xp/2003 master boot record. But I have windows 7, does this matter?


Just tried and it works! Posting now from windows 7

---

### Post by Herman on 2009-10-31
I can't find ms-sys in Karmic either, sorry about that, it mustn't have been included in the repositories, I don't know why not, it has always been available unti now. Sorry for the inconvenience.

There are lots of ways to change the MBR listed in my [Uninstall Page]("http://members.iinet.net.au/%7Eherman546/p18.html"). 

:-k Lets see now ...

Even if you can't boot Windows, now that your CD drive is free, you might like a nice Windows Vista/Windows 7 recovery disk, from NeoSmart, (the makers of EasyBCD), **See lswest's and bodhi.zazen's thread**, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")

Another way, if you can boot Windows would be to go download MBRfix, from Sysint.
Download a small utility called MbrFix.exe here, [http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)
      Read about MbrFix.exe here, [http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)
1. Paste the file to the root of drive C:
2. boot windows
3. Click 'Start'->'Run', type CMD (for a Command Prompt).
4.type: cd \ , then press 'Enter', (to change directories to the root of drive C:\
5. after the C:\> prompt: MbrFix /drive 0 fixmbr /yes

Nothing much will appear to happen, your monitor may blink slightly, that's all. You will see the plain C:\>_ prompt again. Type 'exit'.
6. reboot and see if it worked.

---

### Post by tpjk on 2009-10-31
> **ghostier said:**
> I've installed an early version of ms-sys because I am having trouble installing tar.gz package. And I made a windows 2000/xp/2003 master boot record. But I have windows 7, does this matter?


Just tried and it works! Posting now from windows 7


congrats! so that means you can now boot from your internal hard drive without your external hd being connected? 

if so, what exactly did you do?:]

---

### Post by Herman on 2009-10-31
> Just tried and it works! Posting now from windows 7:D Ah -Good! Well done!

---

### Post by Herman on 2009-10-31
> @ Herman
_Off Topic_
I didn't realise you posted here. Your Grub pages have been an indispensable guide over the past couple of years. Thanks. :D :D Thanks for your kind remarks there, mechro. I'm always happy to hear when find my website helpful, that makes it all seem worthwhile. I used to spend a lot more time here helping in the Ubuntu Forums than I do now, but there are lots of other good Ubuntu and GRUB helpers around who also are doing a great job and who I'm thankful to have here as well. My life has become busier lately so I don't always have as much time to help as I'd like. I still look in on Ubuntu Web Forums at least once  day.  I'm still here and I still think it's fun to try to help someone, especially when they turn out to be successful in solving their problem.

---

### Post by ghostier on 2009-10-31
You're a very good man. I am truly grateful for your help today. Problem solved.

---

### Post by Herman on 2009-10-31
:D Thanks ghostier.
> congrats! so that means you can now boot from your internal hard drive without your external hd being connected?   if so, what exactly did you do?:]:D Hello tpjk,
I think ghostier downloaded a tar.gz file from syslinux's website and installed it. Normally it's easier to deal with software downloaded from Ubuntu's reopsitories in .deb files when the software we need  is available, and normally that's the better way to do things.
The recommended procedure is to search for it in Synaptic Package Manager or in the new Ubuntu Software Center, or install with apt-get commands.

You also might consider one of the other methods I outlined in [post#29]("http://ubuntuforums.org/showpost.php?p=8209441&postcount=29").

Just do whatever you think will be easiest.
Let us know how you go and I or someone will help if you need it. :D

---

### Post by ghostier on 2009-11-01
I did download the tar.gz from the official site of ms-sys on sourceforge, but I wasn't able to install it successfully. So I downloaded an earlier version from ubuntu's site.

---

