---
title: "how to run chkdsk from ubuntu live CD"
date: 2012-01-11
forum: General Help
---

### Post by cybermecano on 2012-01-11
Hello,

Since I couldn't access neither my windows nor the recovery console by booting from windows installation CD ROM, the only way to start my laptop and go to my files is now the ubuntu live CD. So, I used the 'gedit' tool to check my drive up and here is the informations I get :

```
ERROR: This software has detected that the disk has at least one bad serctor.
##########################################################
WARNING: The disk has bad sector. This means physical damage on the disk surface 
caused by deterioration, manufacturing faults or other reason. The reliability 
of the disk may stay stable or degrade fast. We suggest making a full backup by 
running 'ntfs clone --rescue...' then run CHKDSK /F /R on windows and reboot it 
twice ! then you can resize NTFS safely by additionally using the bad sectors 
option of ntfsresize.
##########################################################
```

Now, my only wish is to rum CHKDSK but unfortunately I can't do it because I don't have any access to any command shell under windows so can I run an equivalent to CHKDSK from my ubuntu live CD ??? Anyone have any suggestion ?

Thx

---

### Post by Double.J on 2012-01-11
Hi there!

Sorry to hear about your problem. I was unclear whether you had windows and ubuntu file systems to check or just windows ones?

Both can be checked from the terminal on the live CD - boot it up and open gparted (on the desktop) to work out what each of the partitions you want to scan are - and what file system they are, for example /dev/sda1 - ntfs, /dev/sda2 - ext4

then open a terminal by pressing ctrl+alt+t

For scanning of Linux filesystems
```

sudo fsck -t ext4 /dev/sdaX -[COLOR="Red"]set X as the number of the Linux partition in gparted.[/COLOR]

```
It'll ask you to repair any errors it makes - it you want to just say yes to all add '-y' between '4' and '/'

For scanning NTFS (Windows)
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdaX - [COLOR="Green"]set X as the number of the Windows (NTFS) partition in gparted[/COLOR]

```

Hope it helps

---

### Post by oldfred on 2012-01-11
The ntfsfix only does minor fixes and sets the chkdsk flag so Windows will run chkdsk on next reboot.

You can run chkdsk from any Windows repairCD/USB. I used a Windows 7 repairUSB to run chkdsk on my XP install.

If you know anyone with Windows 7.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by cybermecano on 2012-01-12
Hi,

Acutually I pulled the HDD of my laptop and set it as slave on my desktop and turn it on. CHKDSK was run automatically at the start of the windows and it repaired all errors... and voila ! Everything is all right.

Thanks for all of you.

Regards

---

