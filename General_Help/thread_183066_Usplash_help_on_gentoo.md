---
title: "Usplash help on gentoo"
date: 2006-05-27
forum: General Help
---

### Post by ivik on 2006-05-27
Hello ubuntu users. 
I'm trying to install usplash on my gentoo box. The reason is because fbsplash doesnt work with new initng system which really speedup boot. My system now boots in 45 sec. from grub to KDE 3.5.2. And this is and old laptop with k6-2CPU@400MHz and 160MB of memory.
 I compiled usplash but i cant create initramfs because i don't know what is in there. So, if sameone could be so kind to send my his initramfs or if at least post directory structure and files. The dpgk-reconfigure linux-image-(kernel version) doesnt exist on gentoo. 
Thank you very much.

---

### Post by [S|G] on 2006-05-27
I'm not sure this'll help, but take a look here:
[https://wiki.ubuntu.com/USplashCustomizationHowto](https://wiki.ubuntu.com/USplashCustomizationHowto)

EDIT: Forgot to address part of your post... To create an Initramfs, at least in debian-based distros, you need the initramfs-tools package

---

### Post by ivik on 2006-05-27
Thanks for quick replay. But the problem that sudo dpkg-reconfigure linux-image-$(uname -r) doesn't exist on gentoo and i don't even need it. I know how to create initramfs but don't know what files are in needed by usplash.
For example in initramfs for fbsplash the directory and files are:
/dev/, /etc /proc... I have to know the right directory structure and files to usplash work.

---

### Post by [S|G] on 2006-05-27
I'm afraid I don't really know enough about the gentoo system to help you, but have you tried [http://gentoo-wiki.com/HOWTO_fbsplash](http://gentoo-wiki.com/HOWTO_fbsplash) ?

---

### Post by ivik on 2006-05-27
Could you please post me the contents of:
zcat /boot/youriniramfs | cpio --list?
Thanks.

---

### Post by [S|G] on 2006-05-27
Sorry, I might have misunderstood your question. You need to know the basic debian system layout? Here is a quick ls from my root:

```

bin
boot
cdrom
debootstrap
dev
etc
home
initrd
initrd.img
initrd.img.old
lib
media
mnt
opt
proc
root
sbin
srv
sys
tftpboot
tmp
usplash_fifo
usr
var
vmlinuz
vmlinuz.old

```

---

### Post by [S|G] on 2006-05-27
```

diego@SnowGust:/$ ls /boot/
abi-2.6.15-22-386     grub                      System.map-2.6.15-22-386
abi-2.6.15-23-386     initrd.img-2.6.15-22-386  System.map-2.6.15-23-386
config-2.6.15-22-386  initrd.img-2.6.15-23-386  vmlinuz-2.6.15-22-386
config-2.6.15-23-386  memtest86+.bin            vmlinuz-2.6.15-23-386

```

---

### Post by ivik on 2006-05-27
I know the linux directory structure. I only need the contents of your initramfs image. Could you please send it to me by mail? Thanks

---

### Post by [S|G] on 2006-05-27
Well, here goes content from initrd.img-2.6.15-23-386
```

.
bin
bin/dd
bin/ln
bin/sh
bin/cat
bin/gzip
bin/nuke
bin/true
bin/zcat
bin/sh.shared
bin/ipconfig
bin/false
bin/kinit
bin/mkdir
bin/mount
bin/sleep
bin/uname
bin/run-init
bin/chroot
bin/fstype
bin/gunzip
bin/insmod
bin/minips
bin/mkfifo
bin/pivot_root
bin/umount
bin/nfsmount
bin/busybox
etc
etc/udev
etc/udev/rules.d
etc/udev/rules.d/90-modprobe.rules
etc/udev/rules.d/65-persistent-disk.rules
etc/udev/rules.d/20-names.rules
etc/udev/rules.d/00-init.rules
etc/udev/udev.conf
etc/modprobe.d
etc/modprobe.d/apm
etc/modprobe.d/arch
etc/modprobe.d/arch/i386
etc/modprobe.d/bluez
etc/modprobe.d/ibm_acpi.modprobe
etc/modprobe.d/nvidia-kernel-nkc
etc/modprobe.d/blacklist-modem
etc/modprobe.d/arch-aliases
etc/modprobe.d/blacklist-watchdog
etc/modprobe.d/isapnp
etc/modprobe.d/blacklist-framebuffer
etc/modprobe.d/aliases
etc/modprobe.d/options
etc/modprobe.d/toshiba_acpi.modprobe
etc/modprobe.d/alsa-base
etc/modprobe.d/ipw3945
etc/modprobe.d/blacklist-oss
etc/modprobe.d/blacklist
etc/evms.conf
lib
lib/evms
lib/evms/2.5.4
lib/evms/2.5.4/multipath-1.0.4.so
lib/evms/2.5.4/drivelink-3.0.6.so
lib/evms/2.5.4/dos-1.1.15.so
lib/evms/2.5.4/bbr_seg-1.1.12.so
lib/evms/2.5.4/gpt-1.1.11.so
lib/evms/2.5.4/mac-1.0.8.so
lib/evms/2.5.4/bbr-1.1.14.so
lib/evms/2.5.4/bsd-1.0.8.so
lib/evms/2.5.4/lvm2-1.0.4.so
lib/evms/2.5.4/disk-1.2.12.so
lib/evms/2.5.4/md-1.1.19.so
lib/udev
lib/udev/dasd_id
lib/udev/vio_type
lib/udev/usb_device_name
lib/udev/scsi_id
lib/udev/ata_id
lib/udev/edd_id
lib/udev/pnp_modules
lib/udev/ide_media
lib/udev/usb_id
lib/udev/vol_id
lib/udev/path_id
lib/udev/dvb_device_name
lib/libreadline.so.5
lib/libncurses.so.5
lib/klibc-t2jM36h7OcxUNTDzncfER2p7kd4.so
lib/modules
lib/modules/2.6.15-23-386
lib/modules/2.6.15-23-386/kernel
lib/modules/2.6.15-23-386/kernel/fs
lib/modules/2.6.15-23-386/kernel/fs/jbd
lib/modules/2.6.15-23-386/kernel/fs/jbd/jbd.ko
lib/modules/2.6.15-23-386/kernel/fs/jfs
lib/modules/2.6.15-23-386/kernel/fs/jfs/jfs.ko
lib/modules/2.6.15-23-386/kernel/fs/nfs
lib/modules/2.6.15-23-386/kernel/fs/nfs/nfs.ko
lib/modules/2.6.15-23-386/kernel/fs/xfs
lib/modules/2.6.15-23-386/kernel/fs/xfs/xfs.ko
lib/modules/2.6.15-23-386/kernel/fs/ext2
lib/modules/2.6.15-23-386/kernel/fs/ext2/ext2.ko
lib/modules/2.6.15-23-386/kernel/fs/ext3
lib/modules/2.6.15-23-386/kernel/fs/ext3/ext3.ko
lib/modules/2.6.15-23-386/kernel/fs/exportfs
lib/modules/2.6.15-23-386/kernel/fs/exportfs/exportfs.ko
lib/modules/2.6.15-23-386/kernel/fs/reiserfs
lib/modules/2.6.15-23-386/kernel/fs/reiserfs/reiserfs.ko
lib/modules/2.6.15-23-386/kernel/fs/isofs
lib/modules/2.6.15-23-386/kernel/fs/isofs/isofs.ko
lib/modules/2.6.15-23-386/kernel/fs/lockd
lib/modules/2.6.15-23-386/kernel/fs/lockd/lockd.ko
lib/modules/2.6.15-23-386/kernel/lib
lib/modules/2.6.15-23-386/kernel/lib/crc-ccitt.ko
lib/modules/2.6.15-23-386/kernel/net
lib/modules/2.6.15-23-386/kernel/net/packet
lib/modules/2.6.15-23-386/kernel/net/packet/af_packet.ko
lib/modules/2.6.15-23-386/kernel/net/sunrpc
lib/modules/2.6.15-23-386/kernel/net/sunrpc/sunrpc.ko
lib/modules/2.6.15-23-386/kernel/drivers
lib/modules/2.6.15-23-386/kernel/drivers/md
lib/modules/2.6.15-23-386/kernel/drivers/md/dm-mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid0.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid1.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid5.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid6.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid10.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/dm-snapshot.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/linear.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/xor.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/md-mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/serverworks.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/via82cxxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/sis5513.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/amd74xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cy82c693.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/ns87415.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/opti621.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/pdc202xx_new.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/pdc202xx_old.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/atiixp.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/triflex.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/sc1200.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cs5520.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cs5530.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/generic.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/slc90e66.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/rz1000.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/piix.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cmd64x.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/hpt366.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/hpt34x.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/alim15x3.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/trm290.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/aec62xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/siimage.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-disk.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-generic.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-cd.ko
lib/modules/2.6.15-23-386/kernel/drivers/net
lib/modules/2.6.15-23-386/kernel/drivers/net/8139too.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/dl2k.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sungem.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/starfire.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sunhme.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/e1000
lib/modules/2.6.15-23-386/kernel/drivers/net/e1000/e1000.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/fealnx.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/dmfe.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/xircom_cb.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/de2104x.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/xircom_tulip_cb.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/tulip.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/winbond-840.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/de4x5.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/ne2k-pci.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/skge.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/slhc.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/epic100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/b44.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/e100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tlan.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/eql.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/yellowfin.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/defxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/s2io.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/mii.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sundance.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/r8169.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tg3.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/hp100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/natsemi.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/via-velocity.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sungem_phy.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/ns83820.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/pcnet32.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/netconsole.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sis900.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/bnx2.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/8390.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/via-rhine.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/3c59x.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/8139cp.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb
lib/modules/2.6.15-23-386/kernel/drivers/usb/core
lib/modules/2.6.15-23-386/kernel/drivers/usb/core/usbcore.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/ehci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/ohci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/uhci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/input
lib/modules/2.6.15-23-386/kernel/drivers/usb/input/usbhid.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/storage
lib/modules/2.6.15-23-386/kernel/drivers/usb/storage/usb-storage.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi
lib/modules/2.6.15-23-386/kernel/drivers/acpi/thermal.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi/processor.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi/fan.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla1280.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_sas.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/lpfc
lib/modules/2.6.15-23-386/kernel/drivers/scsi/lpfc/lpfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2100.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2200.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2300.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2322.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla6312.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_spi.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sil.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sis.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sx4.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_svw.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_uli.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dmx3191d.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_via.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_vsc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ch.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/eata.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qlogicfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/BusLogic.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_fc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_spi2.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/3w-9xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_nv.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dc395x.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/tmscsim.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/fdomain.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/arcmsr
lib/modules/2.6.15-23-386/kernel/drivers/scsi/arcmsr/arcmsr.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/gdth.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/initio.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/3w-xxxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ipr.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ips.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aacraid
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aacraid/aacraid.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/nsp32.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_iscsi.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ahci.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx/aic79xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/atp870u.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sd_mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_promise.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sym53c8xx_2
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_qstor.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/osst.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ata_piix.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qlogicfas408.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid/megaraid_mm.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dpt_i2o.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/libata.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/advansys.ko
lib/modules/2.6.15-23-386/kernel/drivers/block
lib/modules/2.6.15-23-386/kernel/drivers/block/cpqarray.ko
lib/modules/2.6.15-23-386/kernel/drivers/block/cciss.ko
lib/modules/2.6.15-23-386/kernel/drivers/cdrom
lib/modules/2.6.15-23-386/kernel/drivers/cdrom/cdrom.ko
lib/modules/2.6.15-23-386/kernel/drivers/video
lib/modules/2.6.15-23-386/kernel/drivers/video/console
lib/modules/2.6.15-23-386/kernel/drivers/video/console/fbcon.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/font.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/softcursor.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/tileblit.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/bitblit.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vga16fb.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vgastate.ko
lib/modules/2.6.15-23-386/kernel/drivers/message
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o/i2o_block.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o/i2o_core.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptscsih.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptbase.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptsas.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptspi.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/sbp2.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/ohci1394.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/ieee1394.ko
lib/modules/2.6.15-23-386/kernel/security
lib/modules/2.6.15-23-386/kernel/security/commoncap.ko
lib/libdevmapper.so.1.02
lib/libselinux.so.1
lib/libevms-2.5.so.0
lib/libsepol.so.1
lib/ld-linux.so.2
lib/libdl.so.2
lib/libuuid.so.1
lib/libpthread.so.0
lib/libc.so.6
usr
usr/lib
usr/lib/usplash
usr/lib/usplash/usplash-artwork.so
conf
conf/arch.conf
conf/initramfs.conf
conf/conf.d
conf/conf.d/resume
conf/modules
init
sbin
sbin/mdadm
sbin/mdrun
sbin/rmmod
sbin/udevd
sbin/usplash_write
sbin/modprobe
sbin/depmod
sbin/vgchange
sbin/udevplug
sbin/usplash
sbin/evms_activate
scripts
scripts/nfs
scripts/init-premount
scripts/init-premount/udev
scripts/init-premount/thermal
scripts/local
scripts/nfs-premount
scripts/local-premount
scripts/local-premount/suspend
scripts/nfs-top
scripts/nfs-top/udev
scripts/functions
scripts/init-bottom
scripts/init-bottom/udev
scripts/local-top
scripts/local-top/md
scripts/local-top/lvm
scripts/local-top/evms
scripts/local-top/udev
scripts/nfs-bottom
scripts/casper-premount
scripts/casper-premount/udev
scripts/local-bottom
scripts/init-top
scripts/init-top/usplash
scripts/init-top/framebuffer
modules
lib/modules/2.6.15-23-386/kernel/security/capability.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vesafb.ko

```

---

### Post by ivik on 2006-05-27
Could ypu please do:
zcat /boot/initrd.img-2.6.15-23-386 | cpio --list?
Thanks

EDIT: Thanks. I'll try create one now only for usplash.

---

### Post by [S|G] on 2006-05-27
I posted that above... but here it goes again (sorry for taking so long to understand what you were asking... kinda doing too many things at once)
```

.
bin
bin/dd
bin/ln
bin/sh
bin/cat
bin/gzip
bin/nuke
bin/true
bin/zcat
bin/sh.shared
bin/ipconfig
bin/false
bin/kinit
bin/mkdir
bin/mount
bin/sleep
bin/uname
bin/run-init
bin/chroot
bin/fstype
bin/gunzip
bin/insmod
bin/minips
bin/mkfifo
bin/pivot_root
bin/umount
bin/nfsmount
bin/busybox
etc
etc/udev
etc/udev/rules.d
etc/udev/rules.d/90-modprobe.rules
etc/udev/rules.d/65-persistent-disk.rules
etc/udev/rules.d/20-names.rules
etc/udev/rules.d/00-init.rules
etc/udev/udev.conf
etc/modprobe.d
etc/modprobe.d/apm
etc/modprobe.d/arch
etc/modprobe.d/arch/i386
etc/modprobe.d/bluez
etc/modprobe.d/ibm_acpi.modprobe
etc/modprobe.d/nvidia-kernel-nkc
etc/modprobe.d/blacklist-modem
etc/modprobe.d/arch-aliases
etc/modprobe.d/blacklist-watchdog
etc/modprobe.d/isapnp
etc/modprobe.d/blacklist-framebuffer
etc/modprobe.d/aliases
etc/modprobe.d/options
etc/modprobe.d/toshiba_acpi.modprobe
etc/modprobe.d/alsa-base
etc/modprobe.d/ipw3945
etc/modprobe.d/blacklist-oss
etc/modprobe.d/blacklist
etc/evms.conf
lib
lib/evms
lib/evms/2.5.4
lib/evms/2.5.4/multipath-1.0.4.so
lib/evms/2.5.4/drivelink-3.0.6.so
lib/evms/2.5.4/dos-1.1.15.so
lib/evms/2.5.4/bbr_seg-1.1.12.so
lib/evms/2.5.4/gpt-1.1.11.so
lib/evms/2.5.4/mac-1.0.8.so
lib/evms/2.5.4/bbr-1.1.14.so
lib/evms/2.5.4/bsd-1.0.8.so
lib/evms/2.5.4/lvm2-1.0.4.so
lib/evms/2.5.4/disk-1.2.12.so
lib/evms/2.5.4/md-1.1.19.so
lib/udev
lib/udev/dasd_id
lib/udev/vio_type
lib/udev/usb_device_name
lib/udev/scsi_id
lib/udev/ata_id
lib/udev/edd_id
lib/udev/pnp_modules
lib/udev/ide_media
lib/udev/usb_id
lib/udev/vol_id
lib/udev/path_id
lib/udev/dvb_device_name
lib/libreadline.so.5
lib/libncurses.so.5
lib/klibc-t2jM36h7OcxUNTDzncfER2p7kd4.so
lib/modules
lib/modules/2.6.15-23-386
lib/modules/2.6.15-23-386/kernel
lib/modules/2.6.15-23-386/kernel/fs
lib/modules/2.6.15-23-386/kernel/fs/jbd
lib/modules/2.6.15-23-386/kernel/fs/jbd/jbd.ko
lib/modules/2.6.15-23-386/kernel/fs/jfs
lib/modules/2.6.15-23-386/kernel/fs/jfs/jfs.ko
lib/modules/2.6.15-23-386/kernel/fs/nfs
lib/modules/2.6.15-23-386/kernel/fs/nfs/nfs.ko
lib/modules/2.6.15-23-386/kernel/fs/xfs
lib/modules/2.6.15-23-386/kernel/fs/xfs/xfs.ko
lib/modules/2.6.15-23-386/kernel/fs/ext2
lib/modules/2.6.15-23-386/kernel/fs/ext2/ext2.ko
lib/modules/2.6.15-23-386/kernel/fs/ext3
lib/modules/2.6.15-23-386/kernel/fs/ext3/ext3.ko
lib/modules/2.6.15-23-386/kernel/fs/exportfs
lib/modules/2.6.15-23-386/kernel/fs/exportfs/exportfs.ko
lib/modules/2.6.15-23-386/kernel/fs/reiserfs
lib/modules/2.6.15-23-386/kernel/fs/reiserfs/reiserfs.ko
lib/modules/2.6.15-23-386/kernel/fs/isofs
lib/modules/2.6.15-23-386/kernel/fs/isofs/isofs.ko
lib/modules/2.6.15-23-386/kernel/fs/lockd
lib/modules/2.6.15-23-386/kernel/fs/lockd/lockd.ko
lib/modules/2.6.15-23-386/kernel/lib
lib/modules/2.6.15-23-386/kernel/lib/crc-ccitt.ko
lib/modules/2.6.15-23-386/kernel/net
lib/modules/2.6.15-23-386/kernel/net/packet
lib/modules/2.6.15-23-386/kernel/net/packet/af_packet.ko
lib/modules/2.6.15-23-386/kernel/net/sunrpc
lib/modules/2.6.15-23-386/kernel/net/sunrpc/sunrpc.ko
lib/modules/2.6.15-23-386/kernel/drivers
lib/modules/2.6.15-23-386/kernel/drivers/md
lib/modules/2.6.15-23-386/kernel/drivers/md/dm-mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid0.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid1.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid5.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid6.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/raid10.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/dm-snapshot.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/linear.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/xor.ko
lib/modules/2.6.15-23-386/kernel/drivers/md/md-mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/serverworks.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/via82cxxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/sis5513.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/amd74xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cy82c693.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/ns87415.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/opti621.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/pdc202xx_new.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/pdc202xx_old.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/atiixp.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/triflex.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/sc1200.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cs5520.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cs5530.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/generic.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/slc90e66.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/rz1000.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/piix.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/cmd64x.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/hpt366.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/hpt34x.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/alim15x3.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/trm290.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/aec62xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/pci/siimage.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-disk.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-generic.ko
lib/modules/2.6.15-23-386/kernel/drivers/ide/ide-cd.ko
lib/modules/2.6.15-23-386/kernel/drivers/net
lib/modules/2.6.15-23-386/kernel/drivers/net/8139too.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/dl2k.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sungem.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/starfire.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sunhme.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/e1000
lib/modules/2.6.15-23-386/kernel/drivers/net/e1000/e1000.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/fealnx.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/dmfe.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/xircom_cb.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/de2104x.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/xircom_tulip_cb.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/tulip.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/winbond-840.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tulip/de4x5.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/ne2k-pci.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/skge.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/slhc.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/epic100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/b44.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/e100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tlan.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/eql.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/yellowfin.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/defxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/s2io.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/mii.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sundance.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/r8169.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/tg3.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/hp100.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/natsemi.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/via-velocity.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sungem_phy.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/ns83820.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/pcnet32.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/netconsole.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/sis900.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/bnx2.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/8390.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/via-rhine.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/3c59x.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/8139cp.ko
lib/modules/2.6.15-23-386/kernel/drivers/net/forcedeth.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb
lib/modules/2.6.15-23-386/kernel/drivers/usb/core
lib/modules/2.6.15-23-386/kernel/drivers/usb/core/usbcore.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/ehci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/ohci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/host/uhci-hcd.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/input
lib/modules/2.6.15-23-386/kernel/drivers/usb/input/usbhid.ko
lib/modules/2.6.15-23-386/kernel/drivers/usb/storage
lib/modules/2.6.15-23-386/kernel/drivers/usb/storage/usb-storage.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi
lib/modules/2.6.15-23-386/kernel/drivers/acpi/thermal.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi/processor.ko
lib/modules/2.6.15-23-386/kernel/drivers/acpi/fan.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla1280.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_sas.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/lpfc
lib/modules/2.6.15-23-386/kernel/drivers/scsi/lpfc/lpfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2100.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2200.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2300.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2322.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qla2xxx/qla6312.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_spi.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sil.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sis.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_sx4.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_svw.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_uli.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dmx3191d.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_via.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_vsc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ch.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/eata.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qlogicfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/BusLogic.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_fc.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_spi2.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/3w-9xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_nv.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dc395x.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/tmscsim.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/fdomain.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/arcmsr
lib/modules/2.6.15-23-386/kernel/drivers/scsi/arcmsr/arcmsr.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/gdth.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/initio.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/3w-xxxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ipr.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ips.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aacraid
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aacraid/aacraid.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/nsp32.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_transport_iscsi.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ahci.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/aic7xxx/aic79xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/scsi_mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/atp870u.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sd_mod.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_promise.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sym53c8xx_2
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/sata_qstor.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/osst.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/ata_piix.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/qlogicfas408.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid/megaraid_mm.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/dpt_i2o.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/libata.ko
lib/modules/2.6.15-23-386/kernel/drivers/scsi/advansys.ko
lib/modules/2.6.15-23-386/kernel/drivers/block
lib/modules/2.6.15-23-386/kernel/drivers/block/cpqarray.ko
lib/modules/2.6.15-23-386/kernel/drivers/block/cciss.ko
lib/modules/2.6.15-23-386/kernel/drivers/cdrom
lib/modules/2.6.15-23-386/kernel/drivers/cdrom/cdrom.ko
lib/modules/2.6.15-23-386/kernel/drivers/video
lib/modules/2.6.15-23-386/kernel/drivers/video/console
lib/modules/2.6.15-23-386/kernel/drivers/video/console/fbcon.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/font.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/softcursor.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/tileblit.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/console/bitblit.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vga16fb.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vgastate.ko
lib/modules/2.6.15-23-386/kernel/drivers/message
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o/i2o_block.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/i2o/i2o_core.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptscsih.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptbase.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptsas.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptspi.ko
lib/modules/2.6.15-23-386/kernel/drivers/message/fusion/mptfc.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/sbp2.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/ohci1394.ko
lib/modules/2.6.15-23-386/kernel/drivers/ieee1394/ieee1394.ko
lib/modules/2.6.15-23-386/kernel/security
lib/modules/2.6.15-23-386/kernel/security/commoncap.ko
lib/libdevmapper.so.1.02
lib/libselinux.so.1
lib/libevms-2.5.so.0
lib/libsepol.so.1
lib/ld-linux.so.2
lib/libdl.so.2
lib/libuuid.so.1
lib/libpthread.so.0
lib/libc.so.6
usr
usr/lib
usr/lib/usplash
usr/lib/usplash/usplash-artwork.so
conf
conf/arch.conf
conf/initramfs.conf
conf/conf.d
conf/conf.d/resume
conf/modules
init
sbin
sbin/mdadm
sbin/mdrun
sbin/rmmod
sbin/udevd
sbin/usplash_write
sbin/modprobe
sbin/depmod
sbin/vgchange
sbin/udevplug
sbin/usplash
sbin/evms_activate
scripts
scripts/nfs
scripts/init-premount
scripts/init-premount/udev
scripts/init-premount/thermal
scripts/local
scripts/nfs-premount
scripts/local-premount
scripts/local-premount/suspend
scripts/nfs-top
scripts/nfs-top/udev
scripts/functions
scripts/init-bottom
scripts/init-bottom/udev
scripts/local-top
scripts/local-top/md
scripts/local-top/lvm
scripts/local-top/evms
scripts/local-top/udev
scripts/nfs-bottom
scripts/casper-premount
scripts/casper-premount/udev
scripts/local-bottom
scripts/init-top
scripts/init-top/usplash
scripts/init-top/framebuffer
modules
lib/modules/2.6.15-23-386/kernel/security/capability.ko
lib/modules/2.6.15-23-386/kernel/drivers/video/vesafb.ko

```

---

### Post by ivik on 2006-05-27
I'm still having problems... Can someone with custom kernel show me the contents of initramfs? There are lots of unneeded things in generic ubuntu kernel. I just need files that usplash is depending on.
Thanks

---

### Post by ivik on 2006-05-28
Please, could someone send me and intrd from a custom kernel with working usplash. Thanks.
Preety please

---

### Post by halfvolle melk on 2006-05-28
edit: nevermind. Nothing custom about my kernel.

---

### Post by ivik on 2006-05-30
OMG.... Ubuntu kernel is such a mess. So much unneeded modules and software in initramfs. That kernel is only usefull for first booting and installation. Can't believe that nobody with custom kernel and working usplash is here... 
BUMP:rolleyes: :confused:

---

### Post by matiit on 2008-01-06
ivik
I'm interested in run usplash on gentoo.
Have you done it?
Please answer.

---

