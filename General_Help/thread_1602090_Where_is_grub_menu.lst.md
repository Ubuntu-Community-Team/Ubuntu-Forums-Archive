---
title: "Where is grub menu.lst?"
date: 2010-10-21
forum: General Help
---

### Post by JesterDev on 2010-10-21
Sadly I have to install windows XP in order to play Ultima Online via Razor. Razor wont work with wine, nor crossover for some reason, even with .NET installed. And, my virtual box windows keeps locking up the game after I login.. So there is some weird issue going on. 

So anyway, I need to install Windows XP, and cannot find /boot/grub/menu.lst - wanting to backup grub, has it moved?

Any tutorial on how to do this would also make my life easier. I haven't done this sort of thing in years, but I need my UO fix!

---

### Post by uRock on 2010-10-21
No /boot/grub/menu.lst sincethe release of 9.10. I am not sure how to back it up other than copying the whole /boot folder to external media. Not sure that would work being you'll be changing the partition table when you install Windows. The sda numbering would have to stay the same. I haven't had grub2 fail me yet when reinstalling it from the LiveCD.

---

### Post by JesterDev on 2010-10-21
Yeah, no I can't find it in there for some reason. gedit loads a blank file also. This is going to be interesting.

---

### Post by wojox on 2010-10-21
What version Ubuntu are you using? Check out [GRUB 2]("https://help.ubuntu.com/community/Grub2")

---

### Post by JesterDev on 2010-10-21
/boot/grub$ sudo ls -a >> ~/Files

```

-rw-r--r-- 1 root root    8208 2010-10-08 18:59 915resolution.mod
-rw-r--r-- 1 root root   10488 2010-10-08 18:59 acpi.mod
-rw-r--r-- 1 root root    4536 2010-10-08 18:59 affs.mod
-rw-r--r-- 1 root root    4896 2010-10-08 18:59 afs_be.mod
-rw-r--r-- 1 root root    4872 2010-10-08 18:59 afs.mod
-rw-r--r-- 1 root root    1048 2010-10-08 18:59 aout.mod
-rw-r--r-- 1 root root    8036 2010-10-08 18:59 ata.mod
-rw-r--r-- 1 root root    2228 2010-10-08 18:59 ata_pthru.mod
-rw-r--r-- 1 root root    2672 2010-10-08 18:59 at_keyboard.mod
-rw-r--r-- 1 root root    4792 2010-10-08 18:59 befs_be.mod
-rw-r--r-- 1 root root    4776 2010-10-08 18:59 befs.mod
-rw-r--r-- 1 root root    4288 2010-10-08 18:59 biosdisk.mod
-rw-r--r-- 1 root root    2400 2010-10-08 18:59 bitmap.mod
-rw-r--r-- 1 root root    2904 2010-10-08 18:59 bitmap_scale.mod
-rw-r--r-- 1 root root    2020 2010-10-08 18:59 blocklist.mod
-rw-r--r-- 1 root root     512 2010-10-08 18:59 boot.img
-rw-r--r-- 1 root root    2568 2010-10-08 18:59 boot.mod
-rw-r--r-- 1 root root   19612 2010-10-08 18:59 bsd.mod
-rw-r--r-- 1 root root    1964 2010-10-08 18:59 bufio.mod
-rw-r--r-- 1 root root    2388 2010-10-08 18:59 cat.mod
-rw-r--r-- 1 root root     512 2010-10-08 18:59 cdboot.img
-rw-r--r-- 1 root root    2476 2010-10-08 18:59 chain.mod
-rw-r--r-- 1 root root    1340 2010-10-08 18:59 cmostest.mod
-rw-r--r-- 1 root root    2144 2010-10-08 18:59 cmp.mod
-rw-r--r-- 1 root root    2033 2010-10-08 18:59 command.lst
-rw-r--r-- 1 root root    1784 2010-10-08 18:59 configfile.mod
-rw-r--r-- 1 root root   23817 2010-10-08 18:59 core.img
-rw-r--r-- 1 root root    2864 2010-10-08 18:59 cpio.mod
-rw-r--r-- 1 root root    1608 2010-10-08 18:59 cpuid.mod
-rw-r--r-- 1 root root    1784 2010-10-08 18:59 crc.mod
-rw-r--r-- 1 root root     825 2010-10-08 18:59 crypto.lst
-rw-r--r-- 1 root root    4428 2010-10-08 18:59 crypto.mod
-rw-r--r-- 1 root root    4052 2010-10-08 18:59 cs5536.mod
-rw-r--r-- 1 root root    1824 2010-10-08 18:59 datehook.mod
-rw-r--r-- 1 root root    2316 2010-10-08 18:59 date.mod
-rw-r--r-- 1 root root    1241 2010-10-08 18:59 datetime.mod
-rw-r--r-- 1 root root     512 2010-10-08 18:59 diskboot.img
-rw-r--r-- 1 root root    1896 2010-10-08 18:59 dm_nv.mod
-rw-r--r-- 1 root root    5488 2010-10-08 18:59 drivemap.mod
-rw-r--r-- 1 root root    1920 2010-10-08 18:59 echo.mod
-rw-r--r-- 1 root root    6452 2010-10-08 18:59 efiemu32.o
-rw-r--r-- 1 root root   11018 2010-10-08 18:59 efiemu64.o
-rw-r--r-- 1 root root   24168 2010-10-08 18:59 efiemu.mod
-rw-r--r-- 1 root root    4404 2010-10-08 18:59 elf.mod
-rw-r--r-- 1 root root    1636 2010-10-08 18:59 example_functional_test.mod
-rw-r--r-- 1 root root    5500 2010-10-08 18:59 ext2.mod
-rw-r--r-- 1 root root    3976 2010-10-08 18:59 extcmd.mod
-rw-r--r-- 1 root root    5932 2010-10-08 18:59 fat.mod
-rw-r--r-- 1 root root   11992 2010-10-08 18:59 font.mod
-rw-r--r-- 1 root root    2800 2010-10-08 18:59 fshelp.mod
-rw-r--r-- 1 root root     128 2010-10-08 18:59 fs.lst
-rw-r--r-- 1 root root    2508 2010-10-08 18:59 functional_test.mod
-rw-r--r-- 1 root root    1768 2010-10-08 18:59 gcry_arcfour.mod
-rw-r--r-- 1 root root    8144 2010-10-08 18:59 gcry_blowfish.mod
-rw-r--r-- 1 root root   35040 2010-10-08 18:59 gcry_camellia.mod
-rw-r--r-- 1 root root   17568 2010-10-08 18:59 gcry_cast5.mod
-rw-r--r-- 1 root root    2996 2010-10-08 18:59 gcry_crc.mod
-rw-r--r-- 1 root root   19280 2010-10-08 18:59 gcry_des.mod
-rw-r--r-- 1 root root    3268 2010-10-08 18:59 gcry_md4.mod
-rw-r--r-- 1 root root    4008 2010-10-08 18:59 gcry_md5.mod
-rw-r--r-- 1 root root    2636 2010-10-08 18:59 gcry_rfc2268.mod
-rw-r--r-- 1 root root   19204 2010-10-08 18:59 gcry_rijndael.mod
-rw-r--r-- 1 root root    9116 2010-10-08 18:59 gcry_rmd160.mod
-rw-r--r-- 1 root root   16652 2010-10-08 18:59 gcry_seed.mod
-rw-r--r-- 1 root root   18016 2010-10-08 18:59 gcry_serpent.mod
-rw-r--r-- 1 root root    8848 2010-10-08 18:59 gcry_sha1.mod
-rw-r--r-- 1 root root    3484 2010-10-08 18:59 gcry_sha256.mod
-rw-r--r-- 1 root root    5620 2010-10-08 18:59 gcry_sha512.mod
-rw-r--r-- 1 root root   11980 2010-10-08 18:59 gcry_tiger.mod
-rw-r--r-- 1 root root   39736 2010-10-08 18:59 gcry_twofish.mod
-rw-r--r-- 1 root root   24792 2010-10-08 18:59 gcry_whirlpool.mod
-rw-r--r-- 1 root root    3984 2010-10-08 18:59 gettext.mod
-rw-r--r-- 1 root root   38628 2010-10-08 18:59 gfxmenu.mod
-rw-r--r-- 1 root root   11280 2010-10-08 18:59 gfxterm.mod
-rw-r--r-- 1 root root    3720 2010-10-08 18:59 gptsync.mod
-rw-r--r-- 1 root root   10240 2010-10-08 18:59 grldr.img
-r--r--r-- 1 root root    3723 2010-10-13 02:58 grub.cfg
-rw-r--r-- 1 root root    1024 2010-10-19 23:27 grubenv
-rw-r--r-- 1 root root    7828 2010-10-08 18:59 gzio.mod
-rw-r--r-- 1 root root    1460 2010-10-08 18:59 halt.mod
-rw-r--r-- 1 root root       0 2010-10-08 18:59 handler.lst
-rw-r--r-- 1 root root    4632 2010-10-08 18:59 hashsum.mod
-rw-r--r-- 1 root root    7440 2010-10-08 18:59 hdparm.mod
-rw-r--r-- 1 root root    1216 2010-10-08 18:59 hello.mod
-rw-r--r-- 1 root root    2488 2010-10-08 18:59 help.mod
-rw-r--r-- 1 root root    3244 2010-10-08 18:59 hexdump.mod
-rw-r--r-- 1 root root    6028 2010-10-08 18:59 hfs.mod
-rw-r--r-- 1 root root    5896 2010-10-08 18:59 hfsplus.mod
-rw-r--r-- 1 root root    2856 2010-10-08 18:59 iorw.mod
-rw-r--r-- 1 root root    6248 2010-10-08 18:59 iso9660.mod
-rw-r--r-- 1 root root    5844 2010-10-08 18:59 jfs.mod
-rw-r--r-- 1 root root    5944 2010-10-08 18:59 jpeg.mod
-rw-r--r-- 1 root root   29028 2010-10-08 18:59 kernel.img
-rw-r--r-- 1 root root    1980 2010-10-08 18:59 keystatus.mod
-rw-r--r-- 1 root root    5012 2010-10-08 18:59 linux16.mod
-rw-r--r-- 1 root root    8732 2010-10-08 18:59 linux.mod
-rw-r--r-- 1 root root    1024 2010-10-08 18:59 lnxboot.img
-rw-r--r-- 1 root root    5560 2010-10-08 18:59 loadenv.mod
drwxr-xr-x 2 root root    4096 2010-10-04 16:13 locale
-rw-r--r-- 1 root root    3032 2010-10-08 18:59 loopback.mod
-rw-r--r-- 1 root root    1300 2010-10-08 18:59 lsmmap.mod
-rw-r--r-- 1 root root    4168 2010-10-08 18:59 ls.mod
-rw-r--r-- 1 root root    4932 2010-10-08 18:59 lspci.mod
-rw-r--r-- 1 root root    6060 2010-10-08 18:59 lvm.mod
-rw-r--r-- 1 root root    2652 2010-10-08 18:59 mdraid.mod
-rw-r--r-- 1 root root    2080 2010-10-08 18:59 memdisk.mod
-rw-r--r-- 1 root root    2876 2010-10-08 18:59 memrw.mod
-rw-r--r-- 1 root root    4132 2010-10-08 18:59 minicmd.mod
-rw-r--r-- 1 root root    4336 2010-10-08 18:59 minix.mod
-rw-r--r-- 1 root root    8508 2010-10-08 18:59 mmap.mod
-rw-r--r-- 1 root root    2773 2010-10-08 18:59 moddep.lst
-rw-r--r-- 1 root root    2372 2010-10-08 18:59 msdospart.mod
-rw-r--r-- 1 root root   11436 2010-10-08 18:59 multiboot2.mod
-rw-r--r-- 1 root root   10488 2010-10-08 18:59 multiboot.mod
-rw-r--r-- 1 root root    6648 2010-10-08 18:59 nilfs2.mod
-rw-r--r-- 1 root root   98312 2010-10-08 18:59 normal.mod
-rw-r--r-- 1 root root    3536 2010-10-08 18:59 ntfscomp.mod
-rw-r--r-- 1 root root    9992 2010-10-08 18:59 ntfs.mod
-rw-r--r-- 1 root root   10556 2010-10-08 18:59 ohci.mod
-rw-r--r-- 1 root root    1688 2010-10-08 18:59 part_acorn.mod
-rw-r--r-- 1 root root    1672 2010-10-08 18:59 part_amiga.mod
-rw-r--r-- 1 root root    2112 2010-10-08 18:59 part_apple.mod
-rw-r--r-- 1 root root    2004 2010-10-08 18:59 part_bsd.mod
-rw-r--r-- 1 root root    2284 2010-10-08 18:59 part_gpt.mod
-rw-r--r-- 1 root root      82 2010-10-08 18:59 partmap.lst
-rw-r--r-- 1 root root    2096 2010-10-08 18:59 part_msdos.mod
-rw-r--r-- 1 root root    1792 2010-10-08 18:59 part_sun.mod
-rw-r--r-- 1 root root    1704 2010-10-08 18:59 part_sunpc.mod
-rw-r--r-- 1 root root      17 2010-10-08 18:59 parttool.lst
-rw-r--r-- 1 root root    4488 2010-10-08 18:59 parttool.mod
-rw-r--r-- 1 root root    1904 2010-10-08 18:59 password.mod
-rw-r--r-- 1 root root    2976 2010-10-08 18:59 password_pbkdf2.mod
-rw-r--r-- 1 root root    1328 2010-10-08 18:59 pbkdf2.mod
-rw-r--r-- 1 root root    1184 2010-10-08 18:59 pci.mod
-rw-r--r-- 1 root root    2472 2010-10-08 18:59 play.mod
-rw-r--r-- 1 root root    6620 2010-10-08 18:59 png.mod
-rw-r--r-- 1 root root    2664 2010-10-08 18:59 probe.mod
-rw-r--r-- 1 root root    1024 2010-10-08 18:59 pxeboot.img
-rw-r--r-- 1 root root    1332 2010-10-08 18:59 pxecmd.mod
-rw-r--r-- 1 root root    5588 2010-10-08 18:59 pxe.mod
-rw-r--r-- 1 root root    1400 2010-10-08 18:59 raid5rec.mod
-rw-r--r-- 1 root root    2812 2010-10-08 18:59 raid6rec.mod
-rw-r--r-- 1 root root    6216 2010-10-08 18:59 raid.mod
-rw-r--r-- 1 root root    1564 2010-10-08 18:59 read.mod
-rw-r--r-- 1 root root    1120 2010-10-08 18:59 reboot.mod
-rw-r--r-- 1 root root   38636 2010-10-08 18:59 regexp.mod
-rw-r--r-- 1 root root    9796 2010-10-08 18:59 reiserfs.mod
-rw-r--r-- 1 root root    4104 2010-10-08 18:59 relocator.mod
-rw-r--r-- 1 root root    4128 2010-10-08 18:59 scsi.mod
-rw-r--r-- 1 root root    2168 2010-10-08 18:59 search_fs_file.mod
-rw-r--r-- 1 root root    2336 2010-10-08 18:59 search_fs_uuid.mod
-rw-r--r-- 1 root root    2256 2010-10-08 18:59 search_label.mod
-rw-r--r-- 1 root root    2356 2010-10-08 18:59 search.mod
-rw-r--r-- 1 root root    4920 2010-10-08 18:59 serial.mod
-rw-r--r-- 1 root root     690 2010-10-08 18:59 setjmp.mod
-rw-r--r-- 1 root root    5524 2010-10-08 18:59 setpci.mod
-rw-r--r-- 1 root root    4104 2010-10-08 18:59 sfs.mod
-rw-r--r-- 1 root root    2220 2010-10-08 18:59 sleep.mod
-rw-r--r-- 1 root root    2888 2010-10-08 18:59 tar.mod
-rw-r--r-- 1 root root     124 2010-10-08 18:59 terminal.lst
-rw-r--r-- 1 root root    3476 2010-10-08 18:59 terminal.mod
-rw-r--r-- 1 root root   12740 2010-10-08 18:59 terminfo.mod
-rw-r--r-- 1 root root    5188 2010-10-08 18:59 test.mod
-rw-r--r-- 1 root root    2884 2010-10-08 18:59 tga.mod
-rw-r--r-- 1 root root    1675 2010-10-08 18:59 trig.mod
-rw-r--r-- 1 root root    1276 2010-10-08 18:59 true.mod
-rw-r--r-- 1 root root    5484 2010-10-08 18:59 udf.mod
-rw-r--r-- 1 root root    4672 2010-10-08 18:59 ufs1.mod
-rw-r--r-- 1 root root    4988 2010-10-08 18:59 ufs2.mod
-rw-r--r-- 1 root root    5800 2010-10-08 18:59 uhci.mod
-rw-r--r-- 1 root root 2560080 2010-10-08 18:59 unicode.pf2
-rw-r--r-- 1 root root    3428 2010-10-08 18:59 usb_keyboard.mod
-rw-r--r-- 1 root root    7876 2010-10-08 18:59 usb.mod
-rw-r--r-- 1 root root    5440 2010-10-08 18:59 usbms.mod
-rw-r--r-- 1 root root    3624 2010-10-08 18:59 usbtest.mod
-rw-r--r-- 1 root root    2736 2010-10-08 18:59 vbeinfo.mod
-rw-r--r-- 1 root root    6676 2010-10-08 18:59 vbe.mod
-rw-r--r-- 1 root root    3048 2010-10-08 18:59 vbetest.mod
-rw-r--r-- 1 root root    4788 2010-10-08 18:59 vga.mod
-rw-r--r-- 1 root root    2288 2010-10-08 18:59 vga_text.mod
-rw-r--r-- 1 root root    5500 2010-10-08 18:59 video_bochs.mod
-rw-r--r-- 1 root root    5744 2010-10-08 18:59 video_cirrus.mod
-rw-r--r-- 1 root root   18716 2010-10-08 18:59 video_fb.mod
-rw-r--r-- 1 root root      33 2010-10-08 18:59 video.lst
-rw-r--r-- 1 root root    5388 2010-10-08 18:59 video.mod
-rw-r--r-- 1 root root    3876 2010-10-08 18:59 videotest.mod
-rw-r--r-- 1 root root    5856 2010-10-08 18:59 xfs.mod
-rw-r--r-- 1 root root   31396 2010-10-08 18:59 xnu.mod
-rw-r--r-- 1 root root    1936 2010-10-08 18:59 xnu_uuid.mod
-rw-r--r-- 1 root root    6208 2010-10-08 18:59 zfsinfo.mod
-rw-r--r-- 1 root root   24384 2010-10-08 18:59 zfs.mod
```

---

### Post by uRock on 2010-10-21
This is the one you want,```
-r--r--r-- 1 root root    3723 2010-10-13 02:58 grub.cfg 
```

---

### Post by JesterDev on 2010-10-21
> **uRock said:**
> This is the one you want,```
-r--r--r-- 1 root root    3723 2010-10-13 02:58 grub.cfg 
```

Thank you!

---

