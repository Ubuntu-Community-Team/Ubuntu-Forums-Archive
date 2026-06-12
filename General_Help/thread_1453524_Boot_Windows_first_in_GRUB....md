---
title: "Boot Windows first in GRUB..."
date: 2010-04-13
forum: General Help
---

### Post by dtrot55 on 2010-04-13
I have looked through some other forum posts and everyone is saying to edit the menu.lst file and just swap the order.  I have looked in the /boot/grub folder and I do not see this file.  Has it been moved to a different location in 9.10 with the newest GRUB installed?

Here is my terminal showing all files:

```

root@Ubuntu-Acer-Laptop:/boot/grub# ls -la
total 2712
drwxr-xr-x 2 root root    4096 2010-03-21 22:50 .
drwxr-xr-x 3 root root    4096 2010-03-21 23:04 ..
-rw-r--r-- 1 root root    8320 2010-03-21 22:50 915resolution.mod
-rw-r--r-- 1 root root   10632 2010-03-21 22:50 acpi.mod
-rw-r--r-- 1 root root    4684 2010-03-21 22:50 affs.mod
-rw-r--r-- 1 root root    5144 2010-03-21 22:50 afs_be.mod
-rw-r--r-- 1 root root    4916 2010-03-21 22:50 afs.mod
-rw-r--r-- 1 root root    1136 2010-03-21 22:50 aout.mod
-rw-r--r-- 1 root root    7952 2010-03-21 22:50 ata.mod
-rw-r--r-- 1 root root    2352 2010-03-21 22:50 ata_pthru.mod
-rw-r--r-- 1 root root    2324 2010-03-21 22:50 at_keyboard.mod
-rw-r--r-- 1 root root    5036 2010-03-21 22:50 befs_be.mod
-rw-r--r-- 1 root root    4808 2010-03-21 22:50 befs.mod
-rw-r--r-- 1 root root    4264 2010-03-21 22:50 biosdisk.mod
-rw-r--r-- 1 root root    2528 2010-03-21 22:50 bitmap.mod
-rw-r--r-- 1 root root    2116 2010-03-21 22:50 blocklist.mod
-rw-r--r-- 1 root root     512 2010-03-21 22:50 boot.img
-rw-r--r-- 1 root root    2652 2010-03-21 22:50 boot.mod
-rw-r--r-- 1 root root   19384 2010-03-21 22:50 bsd.mod
-rw-r--r-- 1 root root    2048 2010-03-21 22:50 bufio.mod
-rw-r--r-- 1 root root    2036 2010-03-21 22:50 cat.mod
-rw-r--r-- 1 root root     512 2010-03-21 22:50 cdboot.img
-rw-r--r-- 1 root root    2420 2010-03-21 22:50 chain.mod
-rw-r--r-- 1 root root    2212 2010-03-21 22:50 cmp.mod
-rw-r--r-- 1 root root    1558 2010-03-21 22:50 command.lst
-rw-r--r-- 1 root root    1904 2010-03-21 22:50 configfile.mod
-rw-r--r-- 1 root root   25105 2010-03-21 22:50 core.img
-rw-r--r-- 1 root root    2872 2010-03-21 22:50 cpio.mod
-rw-r--r-- 1 root root    1660 2010-03-21 22:50 cpuid.mod
-rw-r--r-- 1 root root    1824 2010-03-21 22:50 crc.mod
-rw-r--r-- 1 root root    1912 2010-03-21 22:50 datehook.mod
-rw-r--r-- 1 root root    2360 2010-03-21 22:50 date.mod
-rw-r--r-- 1 root root    1333 2010-03-21 22:50 datetime.mod
-rw-r--r-- 1 root root      15 2010-03-21 18:22 device.map
-rw-r--r-- 1 root root     512 2010-03-21 22:50 diskboot.img
-rw-r--r-- 1 root root    1932 2010-03-21 22:50 dm_nv.mod
-rw-r--r-- 1 root root    5620 2010-03-21 22:50 drivemap.mod
-rw-r--r-- 1 root root    2008 2010-03-21 22:50 echo.mod
-rw-r--r-- 1 root root    6436 2010-03-21 22:50 efiemu32.o
-rw-r--r-- 1 root root   11003 2010-03-21 22:50 efiemu64.o
-rw-r--r-- 1 root root   25024 2010-03-21 22:50 efiemu.mod
-rw-r--r-- 1 root root    4476 2010-03-21 22:50 elf.mod
-rw-r--r-- 1 root root    5544 2010-03-21 22:50 ext2.mod
-rw-r--r-- 1 root root    3916 2010-03-21 22:50 extcmd.mod
-rw-r--r-- 1 root root    5812 2010-03-21 22:50 fat.mod
-rw-r--r-- 1 root root    7296 2010-03-21 22:50 font.mod
-rw-r--r-- 1 root root    2284 2010-03-21 22:50 fs_file.mod
-rw-r--r-- 1 root root    2852 2010-03-21 22:50 fshelp.mod
-rw-r--r-- 1 root root     121 2010-03-21 22:50 fs.lst
-rw-r--r-- 1 root root    2220 2010-03-21 22:50 fs_uuid.mod
-rw-r--r-- 1 root root    8624 2010-03-21 22:50 gfxterm.mod
-rw-r--r-- 1 root root    3816 2010-03-21 22:50 gptsync.mod
-r--r--r-- 1 root root    3617 2010-03-21 22:50 grub.cfg
-rw-r--r-- 1 root root    1024 2010-04-12 17:13 grubenv
-rw-r--r-- 1 root root    7816 2010-03-21 22:50 gzio.mod
-rw-r--r-- 1 root root    1552 2010-03-21 22:50 halt.mod
-rw-r--r-- 1 root root     272 2010-03-21 22:50 handler.lst
-rw-r--r-- 1 root root    2144 2010-03-21 22:50 handler.mod
-rw-r--r-- 1 root root    7400 2010-03-21 22:50 hdparm.mod
-rw-r--r-- 1 root root    1308 2010-03-21 22:50 hello.mod
-rw-r--r-- 1 root root    2200 2010-03-21 22:50 help.mod
-rw-r--r-- 1 root root    3196 2010-03-21 22:50 hexdump.mod
-rw-r--r-- 1 root root    5996 2010-03-21 22:50 hfs.mod
-rw-r--r-- 1 root root    5876 2010-03-21 22:50 hfsplus.mod
-rw-r--r-- 1 root root    6080 2010-03-21 22:50 iso9660.mod
-rw-r--r-- 1 root root    5676 2010-03-21 22:50 jfs.mod
-rw-r--r-- 1 root root    5988 2010-03-21 22:50 jpeg.mod
-rw-r--r-- 1 root root   31004 2010-03-21 22:50 kernel.img
-rw-r--r-- 1 root root    2092 2010-03-21 22:50 keystatus.mod
-rw-r--r-- 1 root root    4952 2010-03-21 22:50 linux16.mod
-rw-r--r-- 1 root root    8716 2010-03-21 22:50 linux.mod
-rw-r--r-- 1 root root    1024 2010-03-21 22:50 lnxboot.img
-rw-r--r-- 1 root root    5664 2010-03-21 22:50 loadenv.mod
-rw-r--r-- 1 root root    3172 2010-03-21 22:50 loopback.mod
-rw-r--r-- 1 root root    1388 2010-03-21 22:50 lsmmap.mod
-rw-r--r-- 1 root root    4196 2010-03-21 22:50 ls.mod
-rw-r--r-- 1 root root    4272 2010-03-21 22:50 lspci.mod
-rw-r--r-- 1 root root    5580 2010-03-21 22:50 lvm.mod
-rw-r--r-- 1 root root    1856 2010-03-21 22:50 mdraid.mod
-rw-r--r-- 1 root root    2176 2010-03-21 22:50 memdisk.mod
-rw-r--r-- 1 root root    2272 2010-03-21 22:50 memrw.mod
-rw-r--r-- 1 root root    4116 2010-03-21 22:50 minicmd.mod
-rw-r--r-- 1 root root    4456 2010-03-21 22:50 minix.mod
-rw-r--r-- 1 root root    8656 2010-03-21 22:50 mmap.mod
-rw-r--r-- 1 root root    1657 2010-03-21 22:50 moddep.lst
-rw-r--r-- 1 root root    2468 2010-03-21 22:50 msdospart.mod
-rw-r--r-- 1 root root   15112 2010-03-21 22:50 multiboot.mod
-rw-r--r-- 1 root root   34764 2010-03-21 22:50 normal.mod
-rw-r--r-- 1 root root    3352 2010-03-21 22:50 ntfscomp.mod
-rw-r--r-- 1 root root    8584 2010-03-21 22:50 ntfs.mod
-rw-r--r-- 1 root root    4576 2010-03-21 22:50 ohci.mod
-rw-r--r-- 1 root root    2196 2010-03-21 22:50 part_acorn.mod
-rw-r--r-- 1 root root    2400 2010-03-21 22:50 part_amiga.mod
-rw-r--r-- 1 root root    2776 2010-03-21 22:50 part_apple.mod
-rw-r--r-- 1 root root    2840 2010-03-21 22:50 part_gpt.mod
-rw-r--r-- 1 root root      62 2010-03-21 22:50 partmap.lst
-rw-r--r-- 1 root root    3552 2010-03-21 22:50 part_msdos.mod
-rw-r--r-- 1 root root    2376 2010-03-21 22:50 part_sun.mod
-rw-r--r-- 1 root root      22 2010-03-21 22:50 parttool.lst
-rw-r--r-- 1 root root    4608 2010-03-21 22:50 parttool.mod
-rw-r--r-- 1 root root    2052 2010-03-21 22:50 password.mod
-rw-r--r-- 1 root root     928 2010-03-21 22:50 pci.mod
-rw-r--r-- 1 root root    2144 2010-03-21 22:50 play.mod
-rw-r--r-- 1 root root    6580 2010-03-21 22:50 png.mod
-rw-r--r-- 1 root root    2752 2010-03-21 22:50 probe.mod
-rw-r--r-- 1 root root    1024 2010-03-21 22:50 pxeboot.img
-rw-r--r-- 1 root root    2512 2010-03-21 22:50 pxecmd.mod
-rw-r--r-- 1 root root    3620 2010-03-21 22:50 pxe.mod
-rw-r--r-- 1 root root    1472 2010-03-21 22:50 raid5rec.mod
-rw-r--r-- 1 root root    2920 2010-03-21 22:50 raid6rec.mod
-rw-r--r-- 1 root root    5960 2010-03-21 22:50 raid.mod
-rw-r--r-- 1 root root    1632 2010-03-21 22:50 read.mod
-rw-r--r-- 1 root root    1212 2010-03-21 22:50 reboot.mod
-rw-r--r-- 1 root root    9948 2010-03-21 22:50 reiserfs.mod
-rw-r--r-- 1 root root    3340 2010-03-21 22:50 scsi.mod
-rw-r--r-- 1 root root    3604 2010-03-21 22:50 search.mod
-rw-r--r-- 1 root root    5692 2010-03-21 22:50 serial.mod
-rw-r--r-- 1 root root     778 2010-03-21 22:50 setjmp.mod
-rw-r--r-- 1 root root    4228 2010-03-21 22:50 sfs.mod
-rw-r--r-- 1 root root   12132 2010-03-21 22:50 sh.mod
-rw-r--r-- 1 root root    2296 2010-03-21 22:50 sleep.mod
-rw-r--r-- 1 root root    2904 2010-03-21 22:50 tar.mod
-rw-r--r-- 1 root root    9624 2010-03-21 22:50 terminfo.mod
-rw-r--r-- 1 root root    5248 2010-03-21 22:50 test.mod
-rw-r--r-- 1 root root    2976 2010-03-21 22:50 tga.mod
-rw-r--r-- 1 root root    1356 2010-03-21 22:50 true.mod
-rw-r--r-- 1 root root    5156 2010-03-21 22:50 udf.mod
-rw-r--r-- 1 root root    4796 2010-03-21 22:50 ufs1.mod
-rw-r--r-- 1 root root    5116 2010-03-21 22:50 ufs2.mod
-rw-r--r-- 1 root root    4972 2010-03-21 22:50 uhci.mod
-rw-r--r-- 1 root root 1716019 2010-03-21 22:50 unicode.pf2
-rw-r--r-- 1 root root    3356 2010-03-21 22:50 usb_keyboard.mod
-rw-r--r-- 1 root root    4268 2010-03-21 22:50 usb.mod
-rw-r--r-- 1 root root    3876 2010-03-21 22:50 usbms.mod
-rw-r--r-- 1 root root    3052 2010-03-21 22:50 usbtest.mod
-rw-r--r-- 1 root root    2824 2010-03-21 22:50 vbeinfo.mod
-rw-r--r-- 1 root root    6236 2010-03-21 22:50 vbe.mod
-rw-r--r-- 1 root root    3136 2010-03-21 22:50 vbetest.mod
-rw-r--r-- 1 root root    3756 2010-03-21 22:50 vga.mod
-rw-r--r-- 1 root root    2780 2010-03-21 22:50 vga_text.mod
-rw-r--r-- 1 root root   16316 2010-03-21 22:50 video_fb.mod
-rw-r--r-- 1 root root    5352 2010-03-21 22:50 video.mod
-rw-r--r-- 1 root root    3912 2010-03-21 22:50 videotest.mod
-rw-r--r-- 1 root root    6168 2010-03-21 22:50 xfs.mod
-rw-r--r-- 1 root root   24792 2010-03-21 22:50 xnu.mod
-rw-r--r-- 1 root root    4312 2010-03-21 22:50 xnu_uuid.mod
-rw-r--r-- 1 root root    6416 2010-03-21 22:50 zfsinfo.mod
-rw-r--r-- 1 root root   24360 2010-03-21 22:50 zfs.mod



```

---

### Post by oldfred on 2010-04-13
grub2 does not use menu.lst.

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by dtrot55 on 2010-04-13
> **oldfred said:**
> grub2 does not use menu.lst.

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I installed startupmanager and made windows the default and now anytime i try to load ubuntu i get a vga=795 depriciated and then a blank screen.  I have tried to follow this from the Grub2 Basics post but still getting blank screen

"VGA Deprecated" Message on Boot
Symptom: A blank screen appears with a message concerning VGA being deprecated after the menu item is selected (manually or by default). The message will be a variation of: "VGA=792 is deprecated. Use set GFX payload=1024x768x24, 1024x768 using the linux command instead."

The message probably is informing the user that there is a vga entry on either the "GRUB_CMDLINE_LINUX_DEFAULT=" or "GRUB_CMDLINE_LINUX=" line of /etc/default/grub. "Deprecated" means that there is a newer, preferred way to convey this instruction in GRUB 2. (Note the "vga=" method will still work, despite the message. It is advisory only.) 

In the example above, the line would probably look something like:

Quote:
GRUB_CMDLINE_LINUX_DEFAULT=quiet splash vga=792"
GRUB_CMDLINE_LINUX=""  

To conform to the desired format and eliminate the message, change the above lines in /etc/default/grub to look like the following, using the "vga" value, and translated value, found in your current default file:

Quote:
GRUB_GFXMODE=1024x768
GRUB_CMDLINE_LINUX_DEFAULT=quiet splash"
GRUB_CMDLINE_LINUX=""  

Save the file and run "sudo update-grub" for the changes to be incorporated in the menu.
There is a vga conversion table located at: [http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash) From the GRUB 2 command line, you can run "vbeinfo" to see resolutions supported by your system.

---

### Post by oldfred on 2010-04-13
Did running SUM add an entry into your grub file for VGA=792??

You can manually edit it out.

gksudo gedit /etc/default/grub
sudo update-grub

---

### Post by dtrot55 on 2010-04-13
> **oldfred said:**
> Did running SUM add an entry into your grub file for VGA=792??

You can manually edit it out.

gksudo gedit /etc/default/grub
sudo update-grub

I went in and manually removed all references of vga=xxx in the grub.cfg and etc/default/grub file

---

