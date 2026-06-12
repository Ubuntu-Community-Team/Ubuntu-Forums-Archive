---
title: "ALERT! /dev/disk/by-uuid/.... does not exist. Dr. opping to a shell"
date: 2012-07-07
forum: General Help
---

### Post by BEaSTFX on 2012-07-07
After compiling my new kernel (i tried both 2.4.4 and 3.5-rc) and I try to boot my kernel I got the error in the subject:

> ALERT! /dev/disk/by-uuid/5a86a3b5-3bb8-461c-b60f-0b89753d3b78 does not exist. Dropping to shell

This happens only to my new kernel (the old 3.2 boots ). I tried recompiling with more scsi and ata options but no luck. I guess there is some module i need that i missed to check, but i am not sure what.

This is the output of:

> cat /proc/partitions
major minor  #blocks  name

   8        0  976762584 sda
   8        1     473915 sda1
   8        2   41984000 sda2
   8        3          1 sda3
   8        4    6806528 sda4
   8        5  871020205 sda5
   8        6   55078821 sda6
   8       16  244198584 sdb
   8       17  244196001 sdb1
 251        0     489672 zram0
 251        1     489672 zram1
 251        2     489672 zram2
 251        3     489672 zram3



> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=007a9e26-3c7b-4642-ba34-b58b3de915b2 none            swap    sw              0       0

> ls -l /dev/disk/by-id
&#1086;&#1073;&#1097;&#1086; 0
lrwxrwxrwx 1 root root  9 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U -> ../../sda
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-Hitachi_HDS721010CLA332_JP9960HZ0TNZ4U-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 &#1102;&#1083;&#1080;  7 08:56 ata-ST3250624AS_9ND15CXH -> ../../sdb
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 ata-ST3250624AS_9ND15CXH-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U -> ../../sda
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_Hitachi_HDS7210_JP9960HZ0TNZ4U-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_ST3250624AS_9ND15CXH -> ../../sdb
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 scsi-SATA_ST3250624AS_9ND15CXH-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2 -> ../../sda
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 wwn-0x5000cca375cb37a2-part6 -> ../../sda6


>  ls -l /dev/disk/by-uuid
&#1086;&#1073;&#1097;&#1086; 0
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 007a9e26-3c7b-4642-ba34-b58b3de915b2 -> ../../sda4
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 0628550D2854FD5D -> ../../sdb1
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 5a86a3b5-3bb8-461c-b60f-0b89753d3b78 -> ../../sda2
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 6A12F68C12F65C8F -> ../../sda6
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 B6E86EB7E86E7591 -> ../../sda5
lrwxrwxrwx 1 root root 10 &#1102;&#1083;&#1080;  7 08:56 FAF404F2F404B2C5 -> ../../sda1


> lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0ca5 (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)


> cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
  set locale_dir=($root)/boot/grub/locale
  set lang=bg_BG
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.5.0-rc5' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	linux	/boot/vmlinuz-3.5.0-rc5 root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro   crashkernel=384M-2G:64M,2G-:128M 
	initrd	/boot/initrd.img-3.5.0-rc5
}
menuentry 'Ubuntu, with Linux 3.5.0-rc5 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	echo	'Loading Linux 3.5.0-rc5 ...'
	linux	/boot/vmlinuz-3.5.0-rc5 root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.5.0-rc5
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.4.4' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	linux	/boot/vmlinuz-3.4.4 root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro   crashkernel=384M-2G:64M,2G-:128M 
	initrd	/boot/initrd.img-3.4.4
}
menuentry 'Ubuntu, with Linux 3.4.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	echo	'Loading Linux 3.4.4 ...'
	linux	/boot/vmlinuz-3.4.4 root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.4.4
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro   crashkernel=384M-2G:64M,2G-:128M 
	initrd	/boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	echo	'Loading Linux 3.2.0-26-generic ...'
	linux	/boot/vmlinuz-3.2.0-26-generic root=UUID=5a86a3b5-3bb8-461c-b60f-0b89753d3b78 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-26-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 5a86a3b5-3bb8-461c-b60f-0b89753d3b78
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root FAF404F2F404B2C5
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 0628550D2854FD5D
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###


This are the modules in the loaded old 3.2 kernel:

> cat /proc/modules
pci_stub 12622 1 - Live 0x0000000000000000
vboxpci 23200 0 - Live 0x0000000000000000 (O)
vboxnetadp 25670 0 - Live 0x0000000000000000 (O)
vboxnetflt 23441 0 - Live 0x0000000000000000 (O)
vboxdrv 287130 3 vboxpci,vboxnetadp,vboxnetflt, Live 0x0000000000000000 (O)
zram 18642 4 - Live 0x0000000000000000 (C)
rfcomm 47604 0 - Live 0x0000000000000000
bnep 18281 2 - Live 0x0000000000000000
bluetooth 180104 10 rfcomm,bnep, Live 0x0000000000000000
snd_hda_codec_hdmi 32474 4 - Live 0x0000000000000000
ppdev 17113 0 - Live 0x0000000000000000
snd_hda_intel 33773 2 - Live 0x0000000000000000
snd_hda_codec 127706 2 snd_hda_codec_hdmi,snd_hda_intel, Live 0x0000000000000000
snd_hwdep 13668 1 snd_hda_codec, Live 0x0000000000000000
ip6t_LOG 16974 4 - Live 0x0000000000000000
xt_hl 12521 6 - Live 0x0000000000000000
ip6t_rt 12558 3 - Live 0x0000000000000000
snd_ice1712 75629 2 - Live 0x0000000000000000
snd_ice17xx_ak4xxx 13315 1 snd_ice1712, Live 0x0000000000000000
snd_ak4xxx_adda 18904 2 snd_ice1712,snd_ice17xx_ak4xxx, Live 0x0000000000000000
snd_cs8427 14297 1 snd_ice1712, Live 0x0000000000000000
snd_ac97_codec 134826 1 snd_ice1712, Live 0x0000000000000000
snd_pcm 97188 5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_ice1712,snd_ac97_codec, Live 0x0000000000000000
nf_conntrack_ipv6 13906 7 - Live 0x0000000000000000
nf_defrag_ipv6 13368 1 nf_conntrack_ipv6, Live 0x0000000000000000
ac97_bus 12730 1 snd_ac97_codec, Live 0x0000000000000000
snd_i2c 14191 2 snd_ice1712,snd_cs8427, Live 0x0000000000000000
snd_mpu401_uart 14169 1 snd_ice1712, Live 0x0000000000000000
snd_seq_midi 13324 0 - Live 0x0000000000000000
ipt_REJECT 12576 1 - Live 0x0000000000000000
ipt_LOG 12919 5 - Live 0x0000000000000000
snd_rawmidi 30748 2 snd_mpu401_uart,snd_seq_midi, Live 0x0000000000000000
xt_multiport 12597 4 - Live 0x0000000000000000
snd_seq_midi_event 14899 1 snd_seq_midi, Live 0x0000000000000000
nvidia 10888310 30 - Live 0x0000000000000000 (P)
asus_atk0110 18078 0 - Live 0x0000000000000000
snd_seq 61896 2 snd_seq_midi,snd_seq_midi_event, Live 0x0000000000000000
parport_pc 32866 1 - Live 0x0000000000000000
xt_limit 12711 12 - Live 0x0000000000000000
k10temp 13166 0 - Live 0x0000000000000000
sp5100_tco 13791 0 - Live 0x0000000000000000
xt_tcpudp 12603 42 - Live 0x0000000000000000
edac_core 53746 0 - Live 0x0000000000000000
edac_mce_amd 23709 0 - Live 0x0000000000000000
i2c_piix4 13301 0 - Live 0x0000000000000000
xt_addrtype 12713 4 - Live 0x0000000000000000
snd_timer 29990 2 snd_pcm,snd_seq, Live 0x0000000000000000
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x0000000000000000
xt_state 12578 14 - Live 0x0000000000000000
ip6table_filter 12815 1 - Live 0x0000000000000000
snd 78855 23 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x0000000000000000
ip6_tables 27864 3 ip6t_LOG,ip6t_rt,ip6table_filter, Live 0x0000000000000000
mac_hid 13253 0 - Live 0x0000000000000000
wmi 19256 0 - Live 0x0000000000000000
nf_conntrack_netbios_ns 12665 0 - Live 0x0000000000000000
nf_conntrack_broadcast 12589 1 nf_conntrack_netbios_ns, Live 0x0000000000000000
nf_nat_ftp 12704 0 - Live 0x0000000000000000
nf_nat 25891 1 nf_nat_ftp, Live 0x0000000000000000
nf_conntrack_ipv4 19716 9 nf_nat, Live 0x0000000000000000
nf_defrag_ipv4 12729 1 nf_conntrack_ipv4, Live 0x0000000000000000
nf_conntrack_ftp 13452 1 nf_nat_ftp, Live 0x0000000000000000
nf_conntrack 81926 8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp, Live 0x0000000000000000
soundcore 15091 1 snd, Live 0x0000000000000000
iptable_filter 12810 1 - Live 0x0000000000000000
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm, Live 0x0000000000000000
ip_tables 27473 1 iptable_filter, Live 0x0000000000000000
x_tables 29846 14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables, Live 0x0000000000000000
lp 17799 0 - Live 0x0000000000000000
parport 46562 3 ppdev,parport_pc,lp, Live 0x0000000000000000
pata_atiixp 13204 0 - Live 0x0000000000000000
usbhid 47199 0 - Live 0x0000000000000000
r8169 62099 0 - Live 0x0000000000000000
hid 99559 1 usbhid, Live 0x0000000000000000


I read the most similar topics and i tried adding the rootdelay= to the grub.cfg and changing the uuid to sda2 but it does not help. I need some more advice. Thank you

Regards 
-BEaSTFX

---

### Post by hal8000 on 2012-07-07
As your / filesystem is not mounted and you have made the filesystem ext4, then in your newly compiled kernel, under filesystems, you need to compile ext4 support either as a module or built into the kernel.

I do not see ext4 listed in the output of cat /proc/modules so perhaps this is why it fails to boot.

You can also post
blkid

in future, gives UUID and partition in one command.
Hope that helps.

---

### Post by BEaSTFX on 2012-07-07
I checked the The Extended 4 (ext4) filesystem (EXT4_FS) in the kernel it is supposed to be there i guess

Here is the blkid
> sudo blkid
/dev/sda1: UUID="FAF404F2F404B2C5" TYPE="ntfs" 
/dev/sda2: UUID="5a86a3b5-3bb8-461c-b60f-0b89753d3b78" TYPE="ext4" 
/dev/sda4: UUID="007a9e26-3c7b-4642-ba34-b58b3de915b2" TYPE="swap" 
/dev/sda5: UUID="B6E86EB7E86E7591" TYPE="ntfs" 
/dev/sda6: UUID="6A12F68C12F65C8F" TYPE="ntfs" 
/dev/sdb1: UUID="0628550D2854FD5D" TYPE="ntfs" 
/dev/zram0: UUID="71a40e10-9215-40ea-a9c2-a30fb3ee5af3" TYPE="swap" 
/dev/zram1: UUID="f631b2f4-8760-4415-a4ff-37e875b0c155" TYPE="swap" 
/dev/zram2: UUID="e7518a2b-be54-4ee7-ac16-f1c66b7047b5" TYPE="swap" 
/dev/zram3: UUID="2eacb99e-be39-4162-b2e6-1e0e864ca0c5" TYPE="swap" 


---

### Post by BEaSTFX on 2012-07-08
I added ext4dev to /etc/initramfs-tools/modules and then updated the initramfs. Can you tell me what else I should of done to load ext4 to initrd so i can boot properly?

---

### Post by dino99 on 2012-07-08
the error  show "by-uiid" which is wrong, its "by-uuid"
so update /etc/fstab

maybe also check blkid

---

### Post by BEaSTFX on 2012-07-08
> **dino99 said:**
> the error  show "by-uiid" which is wrong, its "by-uuid"
so update /etc/fstab

maybe also check blkid

The error is "by-uuid" typo mistake. Im sorry about that.

I posted the blkid result in the original post.

---

### Post by Rexilion on 2012-07-08
You said you tried changing the 'uuid' line to 'sda2' (or whatever) 'but that didn't work'.

Try the below fstab, should be kernel agnostic. Might help us narrow down what is going wrong.

Furthermore, it's not a matter of the fact whether you have EXT4 enabled or not. The error says:

ALERT! /dev/disk/by-uuid/.... does not exist.

Which means your initramfs is incapable of finding the block device. Filesystem detection and mounting is *after* that. It could be an issue, but it's not the issue right *now*.

P.S. Keep a rescue disk at hand!

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda2 during installation
/dev/sda2 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda4 during installation
/dev/sda4 none swap sw 0 0 
```

---

