---
title: "Can't find /boot/grub/menu.lst"
date: 2010-02-05
forum: General Help
---

### Post by JetSirus on 2010-02-05
I primarily need to remove several listings from my boot menu.  After many updates and upgrades the list is HUGE.  I know you can edit the grub menu.lst file, but I don't have one...  

ls /boot/grub/ result:
```
915resolution.mod  efiemu64.o     lspci.mod       reiserfs.mod
acpi.mod           efiemu.mod     lvm.mod         scsi.mod
affs.mod           elf.mod        mdraid.mod      search.mod
afs_be.mod         ext2.mod       memdisk.mod     serial.mod
afs.mod            extcmd.mod     memrw.mod       setjmp.mod
aout.mod           fat.mod        minicmd.mod     sfs.mod
ata.mod            font.mod       minix.mod       sh.mod
ata_pthru.mod      fs_file.mod    mmap.mod        sleep.mod
at_keyboard.mod    fshelp.mod     moddep.lst      tar.mod
befs_be.mod        fs.lst         msdospart.mod   terminfo.mod
befs.mod           fs_uuid.mod    multiboot.mod   test.mod
biosdisk.mod       gfxterm.mod    normal.mod      tga.mod
bitmap.mod         gptsync.mod    ntfscomp.mod    true.mod
blocklist.mod      grub.cfg       ntfs.mod        udf.mod
boot.img           grubenv        ohci.mod        ufs1.mod
boot.mod           gzio.mod       part_acorn.mod  ufs2.mod
bsd.mod            halt.mod       part_amiga.mod  uhci.mod
bufio.mod          handler.lst    part_apple.mod  unicode.pf2
cat.mod            handler.mod    part_gpt.mod    usb_keyboard.mod
cdboot.img         hdparm.mod     partmap.lst     usb.mod
chain.mod          hello.mod      part_msdos.mod  usbms.mod
cmp.mod            help.mod       part_sun.mod    usbtest.mod
command.lst        hexdump.mod    parttool.lst    vbeinfo.mod
configfile.mod     hfs.mod        parttool.mod    vbe.mod
core.img           hfsplus.mod    password.mod    vbetest.mod
cpio.mod           iso9660.mod    pci.mod         vga.mod
cpuid.mod          jfs.mod        play.mod        vga_text.mod
crc.mod            jpeg.mod       png.mod         video_fb.mod
datehook.mod       kernel.img     probe.mod       video.mod
date.mod           keystatus.mod  pxeboot.img     videotest.mod
datetime.mod       linux16.mod    pxecmd.mod      xfs.mod
device.map         linux.mod      pxe.mod         xnu.mod
diskboot.img       lnxboot.img    raid5rec.mod    xnu_uuid.mod
dm_nv.mod          loadenv.mod    raid6rec.mod    zfsinfo.mod
drivemap.mod       loopback.mod   raid.mod        zfs.mod
echo.mod           lsmmap.mod     read.mod
efiemu32.o         ls.mod         reboot.mod
```

whereis menu.lst result:
```
menu: /usr/share/menu
```

And the menu.lst in /usr/share/ is empty....  Normally I would just uninstall some of the old kernels with synaptic to get rid of them, but I also want to exclude certain installed OSs without uninstalling them.

EDIT-UPDATE:
I am using Ubuntu 9.10. When I type, "grub --version" it gives the error:
The program 'grub' is currently not installed. You can install it by typing:
sudo apt-get install grub

And, I did read the guide on removing entries from grub 2. The problem is, some of the kernels in the current grub menu are no longer in synaptic on this install. Currently I have WinXP, Ubuntu 8.10, and Ubuntu 9.10 installed. I want to leave 8.10 installed, but not have it available in the Grub menu. How can this be accomplished? Grub 2 seems quite obtuse compared to earlier versions where there was a simple menu file.

Thanks in advance for any help.

---

### Post by rcayea on 2010-02-05
Are you using Ubuntu 9.10? If so, I don't believe there is a menu.1st file any longer. I think it is grub.cfg or something similar to that.

---

### Post by howefield on 2010-02-05
What version of grub do you have.

There is no menu.lst in grub.

```
grub --version
```

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by 2hot6ft2 on 2010-02-05
See the link in my sig called **Grub 2 Guide**.
There is no menu.lst file to edit with Grub 2.
To make changes with grub 2 is completely different.

---

### Post by lykwydchykyn on 2010-02-05
If you have a large amount of kernel entries, you want to actually uninstall the old kernels, not just remove them from the grub menu.

Open synaptic, search for "linux-image" and remove all but the newest 2-3 kernels. (make sure you know which one you're currently using, and don't remove it).

---

### Post by JetSirus on 2010-02-05
I am using Ubuntu 9.10.  When I type, "grub --version" it gives the error:
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

And, I did read the guide on removing entries from grub 2.  The problem is, some of the kernels in the current grub menu are no longer in synaptic on this install.  Currently I have WinXP, Ubuntu 8.10, and Ubuntu 9.10 installed.  I want to leave 8.10 installed, but not have it available in the Grub menu.  How can this be accomplished?  Grub 2 seems quite obtuse compared to earlier versions where there was a simple menu file.

Thanks in advnace for any help. :)

---

### Post by rcayea on 2010-02-05
First I would suggest you reinstall, via synaptic, "grub-Pc". Once that is reinstalled your grub file will be as up-to-date as possible.

---

### Post by SoupFlies on 2010-07-01
To find the version of grub you must now do
```
grub-installer -v
```

---

### Post by Vimmander on 2010-07-22
> **SoupFlies said:**
> To find the version of grub you must now do
```
grub-installer -v
```

I've been trying to find menu.lst, or whatever it is now, and using your command, I got:

```
joe@Rose:~$ grub-installer -v
grub-installer: command not found
```

And thus, the search continues.  I wish the developers didn't change things that need not be changed...
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Edit:  Looks like I didn't need the "er", "install" works.  My previous developer comment still holds, though.

---

### Post by muteXe on 2010-07-22
Just read that guide at the bottom of post#4. it explains everything about grub2.

---

### Post by krimzonstarr on 2010-07-22
```
grub-install --version
```

If the result is > grub-install (GNU GRUB 1.98-1ubuntu7) then you are using grub2, not legacy and must follow the grub2 instructions linked in the previous post.

As for your issue on how to leave 8.04 installed on your HD, but not listed in grub, there are advanced grub2 editing methods that allow you to build custom menus. I think that would be your best bet.

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275") Is a great place to start.

---

