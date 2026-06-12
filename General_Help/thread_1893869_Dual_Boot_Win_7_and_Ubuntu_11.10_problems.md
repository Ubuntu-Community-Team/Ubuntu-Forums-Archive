---
title: "Dual Boot Win 7 and Ubuntu 11.10 problems"
date: 2011-12-11
forum: General Help
---

### Post by boanda on 2011-12-11
Hello,
I`m new to linux and everything regarding, so I decided to install Ubuntu, because it  camed with my EEpc...   
I installed it and repartitioned my HDD :
1 105 mb system reserved - ntfs 
2. 98 gb - windows 7
3 335 gb - data
4 20gb ext4 - root linux
5 2 gb - swap
6 24 gb - home - ext4
Install was ok , ubuntu booted .
when I try to boot windows 7 it shows a blank screen with a cursor and comes back to ubuntu screen to select operating system.?
I tried windows repair and it shows me windows on D:
What can I do to repair WIN7

---

### Post by editheraven on 2011-12-11
First, try this
```

sudo bash
update-grub
grub-mkconfig

```

---

### Post by boanda on 2011-12-11
Tried it,
it does the same thing when trying to boot... cursor on black backgroung..

---

### Post by boanda on 2011-12-11
Another thing to tell:
I have an asus f3e - the one with the problem... and a EEpc 1011px..
On my EEPC on ubunto boot screen when to select OS it shows me : Windows 7 (loader) (on dev/sda1)
on f3e shows me: Windows 7 (loader) without the dev/sda... could that be the problem????
On eepc ubuntu was installed  today also, but I resized from Win 7 partition d with 20gb less and at  ubunt install i just selected dualboot and it made the partitions for me...

---

### Post by oldfred on 2011-12-11
The 100mb partition is a hidden in Windows boot/repair partition. F8 may get you into repair but from grub you have to be very quick, some say try several times.

Did you resize Windows using the Windows partition tools or gparted/installer? It works best with the Windows partition tools, but never create partitions with the Windows partition tools as it may convert from basic to dynamic which does not work with Linux.

You may need chkdsk or fixBoot to repair Windows.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
# is comment do not copy or type comments
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  #(have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd


You should have a current version liveCD or repairCD for every system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

