---
title: "Formatting external hard drive"
date: 2011-09-17
forum: General Help
---

### Post by moorhead98 on 2011-09-17
I have a Iomega 1TB external hard drive. It is formatted on NTFS, and there are some windows files on it. I want to format about 100 gigabytes of it to ext4, but i cant seem to find out how without destroying the whole windows partition (I only need like ten percent of the hard drive)
Is there any way to do it? Preferably graphically, and on ubunut (but its fine if i have to do it on windows)
I'm open to suggestions

---

### Post by oldfred on 2011-09-17
With a Windows boot drive we usually suggest Windows MMC, but it is very limited and we only suggest it for shrinking and nothing else.

Gparted will work on NTFS partitions and we use it for XP or data partitions without issue. Just be sure to use the latest available some (now pretty old) did have issues but only on Windows 7 system partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by DukeBoxer on 2011-09-17
How many files are on it? Or really how much size? if it's not a lot, move the files to your hard drive, then open disk utility and create all the partitions you need and format them and then move the files back to the external. That would be the easiest route I think

---

### Post by moorhead98 on 2011-09-17
I tried using gparted but this is what happens.
it shows icons that are suggesting that i cant do anything with it (see picture 1)
then when i hit properties it shows an error. (see picture 2)
is there any way to solve it?

---

### Post by moorhead98 on 2011-09-17
> **DukeBoxer said:**
> How many files are on it? Or really how much size? if it's not a lot, move the files to your hard drive, then open disk utility and create all the partitions you need and format them and then move the files back to the external. That would be the easiest route I think
A copy of the windows c drive (backup wont work on it for some reason) and its like 60 gigs.
And if it matters, the files are not defragged. should i just partition it with disk utility?
Also, how would i do it? sorry im not familiar with partitioning tools

---

### Post by DukeBoxer on 2011-09-17
Well first make sure you install that "ntfsprogs" or whatever it is that gparted says you need, then make sure the drive is not mounted.  I'm pretty sure you can just go into disk utility and partition it there without even moving the files off of it

---

### Post by moorhead98 on 2011-09-17
> **DukeBoxer said:**
> Well first make sure you install that "ntfsprogs" or whatever it is that gparted says you need, then make sure the drive is not mounted.  I'm pretty sure you can just go into disk utility and partition it there without even moving the files off of it

I checked on synaptic and it says that ntfsprogs is instaled. and it is the same choices when i unmount it

---

### Post by DukeBoxer on 2011-09-17
have you gone into disk utility? What happen in there if you did?

---

### Post by moorhead98 on 2011-09-17
> **DukeBoxer said:**
> have you gone into disk utility? What happen in there if you did?
ok i have disk utility open. it shows the drive in its entirety, but i see no option for resizing. where would this be?

---

### Post by DukeBoxer on 2011-09-17
hang on so I can check

---

### Post by moorhead98 on 2011-09-17
ok

---

### Post by DukeBoxer on 2011-09-17
Forget it, I'm pretty sure you need to format it first, on top where it says format drive, right underneath the information about the drive, then you can partition it

---

### Post by moorhead98 on 2011-09-17
> **DukeBoxer said:**
> Forget it, I'm pretty sure you need to format it first, on top where it says format drive, right underneath the information about the drive, then you can partition it
so just go where it says format drive? i have it circled in the picture

---

### Post by DukeBoxer on 2011-09-17
I'm pretty sure it's the one on the top that you need to click first, the one right above benchmark

---

### Post by moorhead98 on 2011-09-17
> **DukeBoxer said:**
> I'm pretty sure it's the one on the top that you need to click first, the one right above benchmark
And what do I format it to? the choices it gives is Master boot record, GUID partition table, don't partiton, and Apple partition map

---

### Post by oldfred on 2011-09-17
If you reformat it, it will erase everything.

You probably want MBR(msdos). The partitioning that has been used since the PC came out in the 1980's.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

gpt is the new partitioning method used by Macs and drives over 2TiB. You can use gpt as it is slight better and you will never install Windows on an external drive. Ubuntu will work with gpt but you have to create a bios_grub partition if you want to boot a gpt drive with Ubuntu and BIOS.

Often when gparted or Ubuntu have issues with a NTFS partition you need to run chkdsk on the partition. I had a XP install that worked but gparted would not even see it. After a chkdsk XP worked better and gparted saw it just fine.

---

### Post by moorhead98 on 2011-09-17
> **oldfred said:**
> If you reformat it, it will erase everything.

You probably want MBR(msdos). The partitioning that has been used since the PC came out in the 1980's.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

gpt is the new partitioning method used by Macs and drives over 2TiB. You can use gpt as it is slight better and you will never install Windows on an external drive. Ubuntu will work with gpt but you have to create a bios_grub partition if you want to boot a gpt drive with Ubuntu and BIOS.

Often when gparted or Ubuntu have issues with a NTFS partition you need to run chkdsk on the partition. I had a XP install that worked but gparted would not even see it. After a chkdsk XP worked better and gparted saw it just fine.

ok, how do i chkdsk an external hard drive? and there is no way to split it, ntfs and ext4, 50/50?

---

### Post by oldfred on 2011-09-18
You use your Windows repair CD to run chkdsk or run it from your windows install. Just specify d: or whatever the Windows sees it as.

Gparted should then let you split it any way you want.

You should have a liveCD or repair CD/USB for every system you have installed. Some of us also have other Linux versions or repair CDs, just in case. But chkdsk can only be run from a Windows CD/USB.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by moorhead98 on 2011-09-18
> **oldfred said:**
> You use your Windows repair CD to run chkdsk or run it from your windows install. Just specify d: or whatever the Windows sees it as.

Gparted should then let you split it any way you want.

You should have a liveCD or repair CD/USB for every system you have installed. Some of us also have other Linux versions or repair CDs, just in case. But chkdsk can only be run from a Windows CD/USB.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

The system has a recovery cd built in. When it boots up and something goes wrong, it shows an error, then a recovery manager pops up giving some options. Since I dual boot it with Ubuntu, it goes to that every time, so i put it in windows recovery mode. I have no idea what service pack is installed. 
So my questions are: 
1) Should I go with the first or second method to make the repair cd
2) does it have to be a cd or can it be a dvd
3) (off topic question that I've been meaning to ask the forums) Should windows only run in recovery mode because of Ubuntu/any Linux distro, or is that a sign i did something wrong?

---

### Post by oldfred on 2011-09-18
The Windows repair is tiny, I made a Flash drive and it used only 200-300MB. Do not know about DVDs, but some writers may not work as well. Some making Ubuntu install disks have had issues with DVDs. You should also make the vendor recovery which is multiple DVDs and just an image of your install as purchased and/or a full backup.

You should not be getting recovery mode every time. Have you run chkdsk on your install until there are no errors. Not sure what else may be an issue. All grub does is chainload into Windows and after that it is just like any Windows boot.

If you run the auto repair in Windows it will write the Windows boot loader back into the MBR, so either use manual commands or be prepared to reinstall grub2's boot loader to the MBR.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ottosykora on 2011-09-18
just one general question: is this not some of the hardware encrypted drives or so?

---

### Post by moorhead98 on 2011-10-01
No, I do not believe it is encrypted

---

### Post by moorhead98 on 2011-10-01
Ok, I solved my problem. For whatever reason, Gparted failed at unmounting the drive. I used the regular disk utility to unmount it, and i was all set

---

