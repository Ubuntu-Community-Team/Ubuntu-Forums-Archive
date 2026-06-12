---
title: "menu.lst file is missing"
date: 2010-09-01
forum: General Help
---

### Post by acidblue on 2010-09-01
I no longer have a menu.lst file in /boot/grub.
What the hell happened to it??
Using 10.04

Here is a file list of /boot/grub:

rocko@darkstar:/boot/grub$ ls -l
total 4372
-rw-r--r-- 1 root root    8208 2010-07-23 10:33 915resolution.mod
-rw-r--r-- 1 root root   10536 2010-07-23 10:33 acpi.mod
-rw-r--r-- 1 root root    4556 2010-07-23 10:33 affs.mod
-rw-r--r-- 1 root root    4844 2010-07-23 10:33 afs_be.mod
-rw-r--r-- 1 root root    4828 2010-07-23 10:33 afs.mod
-rw-r--r-- 1 root root    1048 2010-07-23 10:33 aout.mod
-rw-r--r-- 1 root root    8052 2010-07-23 10:33 ata.mod
-rw-r--r-- 1 root root    2252 2010-07-23 10:33 ata_pthru.mod
-rw-r--r-- 1 root root    2676 2010-07-23 10:33 at_keyboard.mod
-rw-r--r-- 1 root root    4740 2010-07-23 10:33 befs_be.mod
-rw-r--r-- 1 root root    4716 2010-07-23 10:33 befs.mod
-rw-r--r-- 1 root root    4300 2010-07-23 10:33 biosdisk.mod
-rw-r--r-- 1 root root    2412 2010-07-23 10:33 bitmap.mod
-rw-r--r-- 1 root root    2904 2010-07-23 10:33 bitmap_scale.mod
-rw-r--r-- 1 root root    2012 2010-07-23 10:33 blocklist.mod
-rw-r--r-- 1 root root     512 2010-07-23 10:33 boot.img
-rw-r--r-- 1 root root    2568 2010-07-23 10:33 boot.mod
-rw-r--r-- 1 root root   19740 2010-07-23 10:33 bsd.mod
-rw-r--r-- 1 root root    1960 2010-07-23 10:33 bufio.mod
-rw-r--r-- 1 root root    1988 2010-07-23 10:33 cat.mod
-rw-r--r-- 1 root root     512 2010-07-23 10:33 cdboot.img
-rw-r--r-- 1 root root    2416 2010-07-23 10:33 chain.mod
-rw-r--r-- 1 root root    1948 2010-07-23 10:33 charset.mod
-rw-r--r-- 1 root root    2144 2010-07-23 10:33 cmp.mod
-rw-r--r-- 1 root root    1950 2010-07-23 10:33 command.lst
-rw-r--r-- 1 root root    1784 2010-07-23 10:33 configfile.mod
-rw-r--r-- 1 root root   25367 2010-07-23 10:33 core.img
-rw-r--r-- 1 root root    2808 2010-07-23 10:33 cpio.mod
-rw-r--r-- 1 root root    1608 2010-07-23 10:33 cpuid.mod
-rw-r--r-- 1 root root    1784 2010-07-23 10:33 crc.mod
-rw-r--r-- 1 root root     825 2010-07-23 10:33 crypto.lst
-rw-r--r-- 1 root root    4384 2010-07-23 10:33 crypto.mod
-rw-r--r-- 1 root root    1824 2010-07-23 10:33 datehook.mod
-rw-r--r-- 1 root root    2316 2010-07-23 10:33 date.mod
-rw-r--r-- 1 root root    1241 2010-07-23 10:33 datetime.mod
-rw-r--r-- 1 root root     512 2010-07-23 10:33 diskboot.img
-rw-r--r-- 1 root root    1864 2010-07-23 10:33 dm_nv.mod
-rw-r--r-- 1 root root    5524 2010-07-23 10:33 drivemap.mod
-rw-r--r-- 1 root root    1920 2010-07-23 10:33 echo.mod
-rw-r--r-- 1 root root    6444 2010-07-23 10:33 efiemu32.o
-rw-r--r-- 1 root root   11010 2010-07-23 10:33 efiemu64.o
-rw-r--r-- 1 root root   24400 2010-07-23 10:33 efiemu.mod
-rw-r--r-- 1 root root    4428 2010-07-23 10:33 elf.mod
-rw-r--r-- 1 root root    1664 2010-07-23 10:33 example_functional_test.mod
-rw-r--r-- 1 root root    5448 2010-07-23 10:33 ext2.mod
-rw-r--r-- 1 root root    4004 2010-07-23 10:33 extcmd.mod
-rw-r--r-- 1 root root    5912 2010-07-23 10:33 fat.mod
-rw-r--r-- 1 root root    9732 2010-07-23 10:33 font.mod
-rw-r--r-- 1 root root    2764 2010-07-23 10:33 fshelp.mod
-rw-r--r-- 1 root root     121 2010-07-23 10:33 fs.lst
-rw-r--r-- 1 root root    2608 2010-07-23 10:33 functional_test.mod
-rw-r--r-- 1 root root    1768 2010-07-23 10:33 gcry_arcfour.mod
-rw-r--r-- 1 root root    8144 2010-07-23 10:33 gcry_blowfish.mod
-rw-r--r-- 1 root root   35040 2010-07-23 10:33 gcry_camellia.mod
-rw-r--r-- 1 root root   17568 2010-07-23 10:33 gcry_cast5.mod
-rw-r--r-- 1 root root    2992 2010-07-23 10:33 gcry_crc.mod
-rw-r--r-- 1 root root   19280 2010-07-23 10:33 gcry_des.mod
-rw-r--r-- 1 root root    3272 2010-07-23 10:33 gcry_md4.mod
-rw-r--r-- 1 root root    4016 2010-07-23 10:33 gcry_md5.mod
-rw-r--r-- 1 root root    2636 2010-07-23 10:33 gcry_rfc2268.mod
-rw-r--r-- 1 root root   19204 2010-07-23 10:33 gcry_rijndael.mod
-rw-r--r-- 1 root root    9136 2010-07-23 10:33 gcry_rmd160.mod
-rw-r--r-- 1 root root   16652 2010-07-23 10:33 gcry_seed.mod
-rw-r--r-- 1 root root   18040 2010-07-23 10:33 gcry_serpent.mod
-rw-r--r-- 1 root root    8924 2010-07-23 10:33 gcry_sha1.mod
-rw-r--r-- 1 root root    3492 2010-07-23 10:33 gcry_sha256.mod
-rw-r--r-- 1 root root    5676 2010-07-23 10:33 gcry_sha512.mod
-rw-r--r-- 1 root root   11996 2010-07-23 10:33 gcry_tiger.mod
-rw-r--r-- 1 root root   39616 2010-07-23 10:33 gcry_twofish.mod
-rw-r--r-- 1 root root   24824 2010-07-23 10:33 gcry_whirlpool.mod
-rw-r--r-- 1 root root    3980 2010-07-23 10:33 gettext.mod
-rw-r--r-- 1 root root   37316 2010-07-23 10:33 gfxmenu.mod
-rw-r--r-- 1 root root   10952 2010-07-23 10:33 gfxterm.mod
-rw-r--r-- 1 root root    3720 2010-07-23 10:33 gptsync.mod
-rw-r--r-- 1 root root   10240 2010-07-23 10:33 grldr.img
-r--r--r-- 1 root root    5922 2010-08-31 10:26 grub.cfg
-rw-r--r-- 1 root root    1024 2010-09-01 15:38 grubenv
-rw-r--r-- 1 root root    7740 2010-07-23 10:33 gzio.mod
-rw-r--r-- 1 root root    1464 2010-07-23 10:33 halt.mod
-rw-r--r-- 1 root root      16 2010-07-23 10:33 handler.lst
-rw-r--r-- 1 root root    1688 2010-07-23 10:33 handler.mod
-rw-r--r-- 1 root root    4720 2010-07-23 10:33 hashsum.mod
-rw-r--r-- 1 root root    7420 2010-07-23 10:33 hdparm.mod
-rw-r--r-- 1 root root    1216 2010-07-23 10:33 hello.mod
-rw-r--r-- 1 root root    2412 2010-07-23 10:33 help.mod
-rw-r--r-- 1 root root    3244 2010-07-23 10:33 hexdump.mod
-rw-r--r-- 1 root root    5984 2010-07-23 10:33 hfs.mod
-rw-r--r-- 1 root root    5844 2010-07-23 10:33 hfsplus.mod
-rw-r--r-- 1 root root    6204 2010-07-23 10:33 iso9660.mod
-rw-r--r-- 1 root root    5748 2010-07-23 10:33 jfs.mod
-rw-r--r-- 1 root root    5900 2010-07-23 10:33 jpeg.mod
-rw-r--r-- 1 root root   29784 2010-07-23 10:33 kernel.img
-rw-r--r-- 1 root root    2000 2010-07-23 10:33 keystatus.mod
-rw-r--r-- 1 root root    4972 2010-07-23 10:33 linux16.mod
-rw-r--r-- 1 root root    8652 2010-07-23 10:33 linux.mod
-rw-r--r-- 1 root root    1024 2010-07-23 10:33 lnxboot.img
-rw-r--r-- 1 root root      87 2010-07-23 10:33 load.cfg
-rw-r--r-- 1 root root    5544 2010-07-23 10:33 loadenv.mod
drwxr-xr-x 2 root root    4096 2010-06-04 04:13 locale
-rw-r--r-- 1 root root    3080 2010-07-23 10:33 loopback.mod
-rw-r--r-- 1 root root    1300 2010-07-23 10:33 lsmmap.mod
-rw-r--r-- 1 root root    4140 2010-07-23 10:33 ls.mod
-rw-r--r-- 1 root root    4944 2010-07-23 10:33 lspci.mod
-rw-r--r-- 1 root root    5496 2010-07-23 10:33 lvm.mod
-rw-r--r-- 1 root root    1792 2010-07-23 10:33 mdraid.mod
-rw-r--r-- 1 root root    2104 2010-07-23 10:33 memdisk.mod
-rw-r--r-- 1 root root    2876 2010-07-23 10:33 memrw.mod
-rw-r--r-- 1 root root    4212 2010-07-23 10:33 minicmd.mod
-rw-r--r-- 1 root root    4296 2010-07-23 10:33 minix.mod
-rw-r--r-- 1 root root    8544 2010-07-23 10:33 mmap.mod
-rw-r--r-- 1 root root    2629 2010-07-23 10:33 moddep.lst
-rw-r--r-- 1 root root    2376 2010-07-23 10:33 msdospart.mod
-rw-r--r-- 1 root root   11176 2010-07-23 10:33 multiboot2.mod
-rw-r--r-- 1 root root   11172 2010-07-23 10:33 multiboot.mod
-rw-r--r-- 1 root root   42060 2010-07-23 10:33 normal.mod
-rw-r--r-- 1 root root    3548 2010-07-23 10:33 ntfscomp.mod
-rw-r--r-- 1 root root    9948 2010-07-23 10:33 ntfs.mod
-rw-r--r-- 1 root root    4484 2010-07-23 10:33 ohci.mod
-rw-r--r-- 1 root root    2088 2010-07-23 10:33 part_acorn.mod
-rw-r--r-- 1 root root    2192 2010-07-23 10:33 part_amiga.mod
-rw-r--r-- 1 root root    2632 2010-07-23 10:33 part_apple.mod
-rw-r--r-- 1 root root    2736 2010-07-23 10:33 part_gpt.mod
-rw-r--r-- 1 root root      62 2010-07-23 10:33 partmap.lst
-rw-r--r-- 1 root root    3448 2010-07-23 10:33 part_msdos.mod
-rw-r--r-- 1 root root    2320 2010-07-23 10:33 part_sun.mod
-rw-r--r-- 1 root root      22 2010-07-23 10:33 parttool.lst
-rw-r--r-- 1 root root    4484 2010-07-23 10:33 parttool.mod
-rw-r--r-- 1 root root    1908 2010-07-23 10:33 password.mod
-rw-r--r-- 1 root root    3008 2010-07-23 10:33 password_pbkdf2.mod
-rw-r--r-- 1 root root    1332 2010-07-23 10:33 pbkdf2.mod
-rw-r--r-- 1 root root     900 2010-07-23 10:33 pci.mod
-rw-r--r-- 1 root root    2496 2010-07-23 10:33 play.mod
-rw-r--r-- 1 root root    6652 2010-07-23 10:33 png.mod
-rw-r--r-- 1 root root    2664 2010-07-23 10:33 probe.mod
-rw-r--r-- 1 root root    1024 2010-07-23 10:33 pxeboot.img
-rw-r--r-- 1 root root    1332 2010-07-23 10:33 pxecmd.mod
-rw-r--r-- 1 root root    5548 2010-07-23 10:33 pxe.mod
-rw-r--r-- 1 root root    1380 2010-07-23 10:33 raid5rec.mod
-rw-r--r-- 1 root root    2828 2010-07-23 10:33 raid6rec.mod
-rw-r--r-- 1 root root    5856 2010-07-23 10:33 raid.mod
-rw-r--r-- 1 root root    1544 2010-07-23 10:33 read.mod
-rw-r--r-- 1 root root    1124 2010-07-23 10:33 reboot.mod
-rw-r--r-- 1 root root    9836 2010-07-23 10:33 reiserfs.mod
-rw-r--r-- 1 root root    4148 2010-07-23 10:33 relocator.mod
-rw-r--r-- 1 root root    3260 2010-07-23 10:33 scsi.mod
-rw-r--r-- 1 root root    2164 2010-07-23 10:33 search_fs_file.mod
-rw-r--r-- 1 root root    2312 2010-07-23 10:33 search_fs_uuid.mod
-rw-r--r-- 1 root root    2264 2010-07-23 10:33 search_label.mod
-rw-r--r-- 1 root root    2356 2010-07-23 10:33 search.mod
-rw-r--r-- 1 root root    6092 2010-07-23 10:33 serial.mod
-rw-r--r-- 1 root root     690 2010-07-23 10:33 setjmp.mod
-rw-r--r-- 1 root root    5532 2010-07-23 10:33 setpci.mod
-rw-r--r-- 1 root root    4056 2010-07-23 10:33 sfs.mod
-rw-r--r-- 1 root root   12124 2010-07-23 10:33 sh.mod
-rw-r--r-- 1 root root    2220 2010-07-23 10:33 sleep.mod
-rw-r--r-- 1 root root    2836 2010-07-23 10:33 tar.mod
-rw-r--r-- 1 root root     134 2010-07-23 10:33 terminal.lst
-rw-r--r-- 1 root root    5020 2010-07-23 10:33 terminal.mod
-rw-r--r-- 1 root root    9760 2010-07-23 10:33 terminfo.mod
-rw-r--r-- 1 root root    5156 2010-07-23 10:33 test.mod
-rw-r--r-- 1 root root    2912 2010-07-23 10:33 tga.mod
-rw-r--r-- 1 root root    1675 2010-07-23 10:33 trig.mod
-rw-r--r-- 1 root root    1276 2010-07-23 10:33 true.mod
-rw-r--r-- 1 root root    5060 2010-07-23 10:33 udf.mod
-rw-r--r-- 1 root root    4636 2010-07-23 10:33 ufs1.mod
-rw-r--r-- 1 root root    4952 2010-07-23 10:33 ufs2.mod
-rw-r--r-- 1 root root    5180 2010-07-23 10:33 uhci.mod
-rw-r--r-- 1 root root 2968057 2010-07-23 10:33 unicode.pf2
-rw-r--r-- 1 root root    3420 2010-07-23 10:33 usb_keyboard.mod
-rw-r--r-- 1 root root    3832 2010-07-23 10:33 usb.mod
-rw-r--r-- 1 root root    3816 2010-07-23 10:33 usbms.mod
-rw-r--r-- 1 root root    3488 2010-07-23 10:33 usbtest.mod
-rw-r--r-- 1 root root    2736 2010-07-23 10:33 vbeinfo.mod
-rw-r--r-- 1 root root    7912 2010-07-23 10:33 vbe.mod
-rw-r--r-- 1 root root    3048 2010-07-23 10:33 vbetest.mod
-rw-r--r-- 1 root root    3804 2010-07-23 10:33 vga.mod
-rw-r--r-- 1 root root    2824 2010-07-23 10:33 vga_text.mod
-rw-r--r-- 1 root root   17168 2010-07-23 10:33 video_fb.mod
-rw-r--r-- 1 root root       4 2010-07-23 10:33 video.lst
-rw-r--r-- 1 root root    5604 2010-07-23 10:33 video.mod
-rw-r--r-- 1 root root    3828 2010-07-23 10:33 videotest.mod
-rw-r--r-- 1 root root    5792 2010-07-23 10:33 xfs.mod
-rw-r--r-- 1 root root   31348 2010-07-23 10:33 xnu.mod
-rw-r--r-- 1 root root    1936 2010-07-23 10:33 xnu_uuid.mod
-rw-r--r-- 1 root root    6208 2010-07-23 10:33 zfsinfo.mod
-rw-r--r-- 1 root root   24080 2010-07-23 10:33 zfs.mod
rocko@darkstar:/boot/grub$

---

### Post by PRC09 on 2010-09-01
Ubuntu 10.04 uses Grub2 and not Grub Legacy......


[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by acidblue on 2010-09-01
Thanks. I had no idea it had been changed.

---

### Post by wojox on 2010-09-01
After you edit 

```
/etc/default/grub
```

And run 

```
sudo update-grub
```


This is what is read

```
-r--r--r-- 1 root root 5922 2010-08-31 10:26 grub.cfg
```

---

