---
title: "problem? - /boot is using 93.8% of 227MB"
date: 2012-10-03
forum: General Help
---

### Post by wlraider70 on 2012-10-03
when I log on I get this message.
Is this a problem, what should I do?

 

* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Wed Oct  3 11:25:55 EDT 2012

  System load:  0.01              Processes:           78
  Usage of /:   4.9% of 72.63GB   Users logged in:     0
  Memory usage: 32%               IP address for eth0: 10.10.10.2
  Swap usage:   0%

  => /boot is using 93.8% of 227MB

---

### Post by Wim Sturkenboom on 2012-10-03
Yep that's a problem when the next kernel upgrade comes along.

Clean it out :)

---

### Post by wlraider70 on 2012-10-03
so what can I get rid of?

```

server@philo:/boot$ ls
abi-3.0.0-12-generic-pae     config-3.0.0-22-generic-pae      memtest86+.bin                   vmcoreinfo-3.0.0-20-generic-pae
abi-3.0.0-16-generic-pae     config-3.0.0-24-generic-pae      memtest86+_multiboot.bin         vmcoreinfo-3.0.0-21-generic-pae
abi-3.0.0-17-generic-pae     config-3.0.0-25-generic-pae      System.map-3.0.0-12-generic-pae  vmcoreinfo-3.0.0-22-generic-pae
abi-3.0.0-19-generic-pae     config-3.0.0-26-generic-pae      System.map-3.0.0-16-generic-pae  vmcoreinfo-3.0.0-24-generic-pae
abi-3.0.0-20-generic-pae     grub                             System.map-3.0.0-17-generic-pae  vmcoreinfo-3.0.0-25-generic-pae
abi-3.0.0-21-generic-pae     initrd.img-3.0.0-12-generic-pae  System.map-3.0.0-19-generic-pae  vmcoreinfo-3.0.0-26-generic-pae
abi-3.0.0-22-generic-pae     initrd.img-3.0.0-16-generic-pae  System.map-3.0.0-20-generic-pae  vmlinuz-3.0.0-12-generic-pae
abi-3.0.0-24-generic-pae     initrd.img-3.0.0-17-generic-pae  System.map-3.0.0-21-generic-pae  vmlinuz-3.0.0-16-generic-pae
abi-3.0.0-25-generic-pae     initrd.img-3.0.0-19-generic-pae  System.map-3.0.0-22-generic-pae  vmlinuz-3.0.0-17-generic-pae
abi-3.0.0-26-generic-pae     initrd.img-3.0.0-20-generic-pae  System.map-3.0.0-24-generic-pae  vmlinuz-3.0.0-19-generic-pae
config-3.0.0-12-generic-pae  initrd.img-3.0.0-21-generic-pae  System.map-3.0.0-25-generic-pae  vmlinuz-3.0.0-20-generic-pae
config-3.0.0-16-generic-pae  initrd.img-3.0.0-22-generic-pae  System.map-3.0.0-26-generic-pae  vmlinuz-3.0.0-21-generic-pae
config-3.0.0-17-generic-pae  initrd.img-3.0.0-24-generic-pae  vmcoreinfo-3.0.0-12-generic-pae  vmlinuz-3.0.0-22-generic-pae
config-3.0.0-19-generic-pae  initrd.img-3.0.0-25-generic-pae  vmcoreinfo-3.0.0-16-generic-pae  vmlinuz-3.0.0-24-generic-pae
config-3.0.0-20-generic-pae  initrd.img-3.0.0-26-generic-pae  vmcoreinfo-3.0.0-17-generic-pae  vmlinuz-3.0.0-25-generic-pae
config-3.0.0-21-generic-pae  lost+found                       vmcoreinfo-3.0.0-19-generic-pae  vmlinuz-3.0.0-26-generic-pae
server@philo:/boot$ cd grub
server@philo:/boot/grub$ ls
915resolution.mod  crypto.lst                   gcry_md5.mod        iorw.mod        msdospart.mod        raid5rec.mod        udf.mod
acpi.mod           crypto.mod                   gcry_rfc2268.mod    iso9660.mod     multiboot2.mod       raid6rec.mod        ufs1.mod
affs.mod           cs5536.mod                   gcry_rijndael.mod   jfs.mod         multiboot.mod        raid.mod            ufs2.mod
afs_be.mod         datehook.mod                 gcry_rmd160.mod     jpeg.mod        nilfs2.mod           read.mod            uhci.mod
afs.mod            date.mod                     gcry_seed.mod       kernel.img      normal.mod           reboot.mod          usb_keyboard.mod
aout.mod           datetime.mod                 gcry_serpent.mod    keylayouts.mod  ntfscomp.mod         regexp.mod          usb.mod
ata.mod            diskboot.img                 gcry_sha1.mod       keystatus.mod   ntfs.mod             reiserfs.mod        usbms.mod
ata_pthru.mod      dm_nv.mod                    gcry_sha256.mod     legacycfg.mod   ntldr.mod            relocator.mod       usbserial_common.mod
at_keyboard.mod    drivemap.mod                 gcry_sha512.mod     linux16.mod     ohci.mod             scsi.mod            usbserial_ftdi.mod
befs_be.mod        echo.mod                     gcry_tiger.mod      linux.mod       part_acorn.mod       search_fs_file.mod  usbserial_pl2303.mod
befs.mod           efiemu32.o                   gcry_twofish.mod    lnxboot.img     part_amiga.mod       search_fs_uuid.mod  usbtest.mod
biosdisk.mod       efiemu64.o                   gcry_whirlpool.mod  loadenv.mod     part_apple.mod       search_label.mod    vbe.mod
bitmap.mod         efiemu.mod                   gettext.mod         locale          part_bsd.mod         search.mod          vga.mod
bitmap_scale.mod   elf.mod                      gfxblacklist.txt    loopback.mod    part_gpt.mod         sendkey.mod         vga_text.mod
blocklist.mod      example_functional_test.mod  gfxmenu.mod         lsacpi.mod      partmap.lst          serial.mod          video_bochs.mod
boot.img           ext2.mod                     gfxterm.mod         lsapm.mod       part_msdos.mod       setjmp.mod          video_cirrus.mod
boot.mod           extcmd.mod                   gptsync.mod         lsmmap.mod      part_sun.mod         setpci.mod          video_fb.mod
bsd.mod            fat.mod                      grldr.img           ls.mod          part_sunpc.mod       sfs.mod             videoinfo.mod
btrfs.mod          font.mod                     grub.cfg            lspci.mod       parttool.lst         sleep.mod           video.lst
bufio.mod          fshelp.mod                   grubenv             lvm.mod         parttool.mod         squash4.mod         video.mod
cat.mod            fs.lst                       gzio.mod            mdraid09.mod    password.mod         tar.mod             videotest.mod
cdboot.img         functional_test.mod          halt.mod            mdraid1x.mod    password_pbkdf2.mod  terminal.lst        xfs.mod
chain.mod          g2hdr.img                    hashsum.mod         memdisk.mod     pbkdf2.mod           terminal.mod        xnu.mod
cmostest.mod       gcry_arcfour.mod             hdparm.mod          memrw.mod       pci.mod              terminfo.mod        xnu_uuid.mod
cmp.mod            gcry_blowfish.mod            hello.mod           menu.lst        play.mod             test_blockarg.mod   xzio.mod
command.lst        gcry_camellia.mod            help.mod            minicmd.mod     png.mod              testload.mod        zfsinfo.mod
configfile.mod     gcry_cast5.mod               hexdump.mod         minix2.mod      probe.mod            test.mod            zfs.mod
core.img           gcry_crc.mod                 hfs.mod             minix.mod       pxeboot.img          tga.mod
cpio.mod           gcry_des.mod                 hfsplus.mod         mmap.mod        pxecmd.mod           trig.mod
cpuid.mod          gcry_md4.mod                 hwmatch.mod         moddep.lst      pxe.mod              true.mod
server@philo:/boot/grub$

```

---

### Post by snowpine on 2012-10-03
Easiest is use Synaptic Package Manager to remove some of the older kernels.

---

### Post by wlraider70 on 2012-10-03
I'm using a CLI

here the guide I used

[http://askubuntu.com/questions/153185/how-to-remove-kernels-from-previous-release](http://askubuntu.com/questions/153185/how-to-remove-kernels-from-previous-release)

---

### Post by Statia on 2012-10-03
This:

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

is also very concise.

---

### Post by bowtiev8 on 2013-01-20
> **wlraider70 said:**
> I'm using a CLI

here the guide I used

[http://askubuntu.com/questions/153185/how-to-remove-kernels-from-previous-release](http://askubuntu.com/questions/153185/how-to-remove-kernels-from-previous-release)

Thanks. I have had the same problem and will just say it helped for me.

---

