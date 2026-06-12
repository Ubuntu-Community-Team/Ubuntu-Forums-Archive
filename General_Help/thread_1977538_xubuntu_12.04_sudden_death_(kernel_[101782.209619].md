---
title: "xubuntu 12.04 sudden death (kernel: [101782.209619] BUG: unable to handle kernel...)"
date: 2012-05-10
forum: General Help
---

### Post by Forux on 2012-05-10
Each 1-2 day system die without any reason.

Everything not work - ctrl + alt + F1 do not work, mouse do not work, keyboard do not work, at monitor "freezed" image

syslog:

```
May 10 15:17:02 forux-Work CRON[11761]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 10 15:17:18 forux-Work kernel: [101782.209619] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 10 15:17:18 forux-Work kernel: [101782.209627] IP: [<ffffffffa01f8291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.209700] PGD 0 
May 10 15:17:18 forux-Work kernel: [101782.209703] Oops: 0002 [#1] SMP 
May 10 15:17:18 forux-Work kernel: [101782.209707] CPU 0 
May 10 15:17:18 forux-Work kernel: [101782.209708] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc ppdev vesafb binfmt_misc nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep fglrx(P) snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device mac_hid snd soundcore snd_page_alloc lp parport usbhid hid r8169
May 10 15:17:18 forux-Work kernel: [101782.209737] 
May 10 15:17:18 forux-Work kernel: [101782.209740] Pid: 1094, comm: Xorg Tainted: P           O 3.2.0-24-generic #37-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 10 15:17:18 forux-Work kernel: [101782.209745] RIP: 0010:[<ffffffffa01f8291>]  [<ffffffffa01f8291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.209789] RSP: 0018:ffff8801351dd960  EFLAGS: 00010297
May 10 15:17:18 forux-Work kernel: [101782.209791] RAX: ffff8801354b2008 RBX: ffffc900116f9150 RCX: 0000000000000000
May 10 15:17:18 forux-Work kernel: [101782.209793] RDX: 0000000000000000 RSI: ffffc900116f9018 RDI: ffff8801354b2e30
May 10 15:17:18 forux-Work kernel: [101782.209795] RBP: 0000000000000002 R08: ffffffffa0228eb0 R09: ffff8801354b2008
May 10 15:17:18 forux-Work kernel: [101782.209798] R10: ffffc900116f9090 R11: ffff8801354b2008 R12: ffff8801354b2e30
May 10 15:17:18 forux-Work kernel: [101782.209800] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 10 15:17:18 forux-Work kernel: [101782.209803] FS:  00007f882884c880(0000) GS:ffff88013fc00000(0000) knlGS:0000000000000000
May 10 15:17:18 forux-Work kernel: [101782.209805] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 10 15:17:18 forux-Work kernel: [101782.209807] CR2: 0000000000000008 CR3: 00000001351c0000 CR4: 00000000000406f0
May 10 15:17:18 forux-Work kernel: [101782.209809] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 10 15:17:18 forux-Work kernel: [101782.209812] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 10 15:17:18 forux-Work kernel: [101782.209814] Process Xorg (pid: 1094, threadinfo ffff8801351dc000, task ffff880135b3dbc0)
May 10 15:17:18 forux-Work kernel: [101782.209816] Stack:
May 10 15:17:18 forux-Work kernel: [101782.209818]  ffffffffa01f7cb6 0000000000000000 ffff8801354b2e30 ffff8801354b2ec8
May 10 15:17:18 forux-Work kernel: [101782.209823]  0000000000000200 0000000000000000 ffffffffa0190c55 0000000000080000
May 10 15:17:18 forux-Work kernel: [101782.209827]  ffff8801354b2e30 ffffffffa0228eb0 ffffffffa0190fb8 ffff880028c2cb58
May 10 15:17:18 forux-Work kernel: [101782.209831] Call Trace:
May 10 15:17:18 forux-Work kernel: [101782.209875]  [<ffffffffa01f7cb6>] ? _ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj+0xb6/0xc0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.209931]  [<ffffffffa0190c55>] ? _ZN20CMMHeap_SystemMemory10obtainPoolEv+0x85/0xc0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.209981]  [<ffffffffa0190fb8>] ? _ZN16CMMHeap_PAGEABLE10expandHeapEm+0x18/0xb0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210023]  [<ffffffffa01f7aaa>] ? _ZN7CMMHeap10expandHeapEmRmPv+0xa/0x10 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210071]  [<ffffffffa018f9af>] ? _ZN7CMMHeap21allocateMorePoolSpaceEmPv+0x8f/0x1b0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210121]  [<ffffffffa018e37e>] ? _ZN14CMMHeapManager13allocPageableEjR14CMM_ALLOCATION+0xbe/0x100 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210171]  [<ffffffffa01988b7>] ? _ZN9CMMObjectnwEmP8CMM_CORE+0x37/0x70 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210222]  [<ffffffffa019c462>] ? _ZN8MSF_CORE21get_surface_structureEv+0xc2/0xe0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210271]  [<ffffffffa018663f>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x1f/0x1c0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210319]  [<ffffffffa0186d10>] ? _ZN3MSF10alloc_surfEP9CMMClientP9CMMDriverP21MEMHEAP_ADDR_RESTRICTjP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x530/0x580 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210367]  [<ffffffffa018447d>] ? _ZN17SegmentMapManager11FindMappingEbP4AsicP10CMMProcess+0xad/0xe0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210417]  [<ffffffffa0196f8b>] ? CMMAllocSurface1D_WA+0x3fb/0x470 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210424]  [<ffffffff81162d5d>] ? __kmalloc+0x13d/0x190
May 10 15:17:18 forux-Work kernel: [101782.210472]  [<ffffffffa01936ea>] ? _Z8uCWDDEQCmjjPvjS_+0x9aa/0x10c0 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210478]  [<ffffffff810903fe>] ? down+0x2e/0x50
May 10 15:17:18 forux-Work kernel: [101782.210509]  [<ffffffffa0132b6f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210541]  [<ffffffffa01312de>] ? firegl_cmmqs_CWDDE32+0x6e/0x100 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210546]  [<ffffffff8129ce01>] ? security_capable+0x21/0x30
May 10 15:17:18 forux-Work kernel: [101782.210577]  [<ffffffffa0131270>] ? firegl_cmmqs_createdriver+0x170/0x170 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210603]  [<ffffffffa010e12d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210623]  [<ffffffffa00fe9be>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210627]  [<ffffffff81189cfa>] ? do_vfs_ioctl+0x8a/0x340
May 10 15:17:18 forux-Work kernel: [101782.210630]  [<ffffffff81177e0d>] ? vfs_read+0x10d/0x180
May 10 15:17:18 forux-Work kernel: [101782.210633]  [<ffffffff8118a041>] ? sys_ioctl+0x91/0xa0
May 10 15:17:18 forux-Work kernel: [101782.210637]  [<ffffffff81664a82>] ? system_call_fastpath+0x16/0x1b
May 10 15:17:18 forux-Work kernel: [101782.210640] Code: 00 00 00 00 00 00 00 00 00 00 48 8d 47 68 c3 00 00 00 00 00 00 00 00 00 00 00 31 c9 48 8b 97 98 00 00 00 83 7e 18 02 48 0f 44 ce <48> 89 51 08 ff 87 a0 00 00 00 48 89 8f 98 00 00 00 c3 00 00 00 
May 10 15:17:18 forux-Work kernel: [101782.210672] RIP  [<ffffffffa01f8291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 10 15:17:18 forux-Work kernel: [101782.210715]  RSP <ffff8801351dd960>
May 10 15:17:18 forux-Work kernel: [101782.210717] CR2: 0000000000000008
May 10 15:17:18 forux-Work kernel: [101782.210720] ---[ end trace 536148576144f410 ]---
May 10 15:19:50 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

upd: Any help?

upd:

> **Corporation said:**
> I have exactly the same issue but using Arch Linux.   My thread is [here]("https://bbs.archlinux.org/viewtopic.php?pid=1100375")

we both have multiple monitors

---

### Post by Corporation on 2012-05-11
I have exactly the same issue but using Arch Linux.   My thread is [here]("https://bbs.archlinux.org/viewtopic.php?pid=1100375"), please let me know if you get a solution and I'll do the same for you.  

I've emailed AMD so I'll let you know what they say.  

Edit: Just a couple of quick queries:  

1. Can you output the response to 'lsmod'? For some reason 'radeon' was still loading on my box.  Not sure if I've fixed the problem but I have stopped 'radeon' loading.

2. Can you show me /boot/grub/menu.lst? You may not have added nomodeset to your kernel line.

---

### Post by Forux on 2012-05-14
lsmod
```
lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
vesafb                 13844  1 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
nfsd                  277809  13 
nfs                   356307  5 
lockd                  86161  2 nfsd,nfs
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
fscache                61529  1 nfs
snd_hwdep              13668  1 snd_hda_codec
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
binfmt_misc            17540  1 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
sunrpc                245464  41 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
snd_rawmidi            30748  1 snd_seq_midi                                                               
snd_seq_midi_event     14899  1 snd_seq_midi                                                               
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event                                            
snd_timer              29990  2 snd_pcm,snd_seq                                                            
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq                                           
snd                    78855  24 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd                                                                        
fglrx                3263886  110                                                                          
mac_hid                13253  0                                                                            
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm                                                      
lp                     17799  0                                                                            
parport                46562  3 parport_pc,ppdev,lp                                                        
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0
```

there are no file "/boot/grub/menu.lst"
/boot/grub/grub.cfg
```
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	linux	/boot/vmlinuz-3.2.0-20-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	echo	'Loading Linux 3.2.0-20-generic ...'
	linux	/boot/vmlinuz-3.2.0-20-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-20-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

```

System die again
```
May 14 10:39:01 forux-Work CRON[16313]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
May 14 10:53:14 forux-Work kernel: [329621.491681] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 14 10:53:14 forux-Work kernel: [329621.491689] IP: [<ffffffffa0176291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.491762] PGD 0 
May 14 10:53:14 forux-Work kernel: [329621.491764] Oops: 0002 [#1] SMP 
May 14 10:53:14 forux-Work kernel: [329621.491768] CPU 1 
May 14 10:53:14 forux-Work kernel: [329621.491769] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) rfcomm vesafb bnep bluetooth parport_pc ppdev nfsd nfs lockd binfmt_misc fscache auth_rpcgss nfs_acl sunrpc snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm fglrx(P) snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc mac_hid lp parport usbhid hid r8169
May 14 10:53:14 forux-Work kernel: [329621.491796] 
May 14 10:53:14 forux-Work kernel: [329621.491799] Pid: 1092, comm: Xorg Tainted: P           O 3.2.0-24-generic #37-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 14 10:53:14 forux-Work kernel: [329621.491803] RIP: 0010:[<ffffffffa0176291>]  [<ffffffffa0176291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.491844] RSP: 0018:ffff88011a1219c0  EFLAGS: 00010297
May 14 10:53:14 forux-Work kernel: [329621.491846] RAX: ffff88011a0b6008 RBX: ffffc90011946150 RCX: 0000000000000000
May 14 10:53:14 forux-Work kernel: [329621.491848] RDX: 0000000000000000 RSI: ffffc90011946018 RDI: ffff88011a0b6e30
May 14 10:53:14 forux-Work kernel: [329621.491850] RBP: 0000000000000002 R08: ffffffffa01a6eb0 R09: ffff88011a0b6008
May 14 10:53:14 forux-Work kernel: [329621.491852] R10: ffffc90011946090 R11: ffff88011a0b6008 R12: ffff88011a0b6e30
May 14 10:53:14 forux-Work kernel: [329621.491854] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 14 10:53:14 forux-Work kernel: [329621.491857] FS:  00007f49141f8880(0000) GS:ffff88013fc80000(0000) knlGS:0000000000000000
May 14 10:53:14 forux-Work kernel: [329621.491859] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 14 10:53:14 forux-Work kernel: [329621.491861] CR2: 0000000000000008 CR3: 0000000119169000 CR4: 00000000000406e0
May 14 10:53:14 forux-Work kernel: [329621.491864] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 14 10:53:14 forux-Work kernel: [329621.491866] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 14 10:53:14 forux-Work kernel: [329621.491868] Process Xorg (pid: 1092, threadinfo ffff88011a120000, task ffff8801361a44d0)
May 14 10:53:14 forux-Work kernel: [329621.491870] Stack:
May 14 10:53:14 forux-Work kernel: [329621.491871]  ffffffffa0175cb6 0000000000000000 ffff88011a0b6e30 ffff88011a0b6ec8
May 14 10:53:14 forux-Work kernel: [329621.491876]  0000000000000200 0000000000000000 ffffffffa010ec55 0000000000080000
May 14 10:53:14 forux-Work kernel: [329621.491880]  ffff88011a0b6e30 ffffffffa01a6eb0 ffffffffa010efb8 ffff88011a121a88
May 14 10:53:14 forux-Work kernel: [329621.491884] Call Trace:
May 14 10:53:14 forux-Work kernel: [329621.491925]  [<ffffffffa0175cb6>] ? _ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj+0xb6/0xc0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.491978]  [<ffffffffa010ec55>] ? _ZN20CMMHeap_SystemMemory10obtainPoolEv+0x85/0xc0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa010efb8>] ? _ZN16CMMHeap_PAGEABLE10expandHeapEm+0x18/0xb0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa0175aaa>] ? _ZN7CMMHeap10expandHeapEmRmPv+0xa/0x10 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa010d9af>] ? _ZN7CMMHeap21allocateMorePoolSpaceEmPv+0x8f/0x1b0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa010c37e>] ? _ZN14CMMHeapManager13allocPageableEjR14CMM_ALLOCATION+0xbe/0x100 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa0137aad>] ? _ZN7PM4Ring8PM4queueEPPj+0x3d/0xa0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa01168b7>] ? _ZN9CMMObjectnwEmP8CMM_CORE+0x37/0x70 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa011a462>] ? _ZN8MSF_CORE21get_surface_structureEv+0xc2/0xe0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa010463f>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x1f/0x1c0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa0105d43>] ? _ZN3MSF21handle_shared_surfaceEP9CMMClientP9CMMDriverP10CMMSurfaceP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x113/0x280 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa0100216>] ? CMMAllocSurface_WA+0x656/0xba0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff8106cf56>] ? current_fs_time+0x16/0x60
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa00ae262>] ? firegl_trace+0x72/0x1e0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff81162d5d>] ? __kmalloc+0x13d/0x190
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa0111899>] ? _Z8uCWDDEQCmjjPvjS_+0xb59/0x10c0 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff810903fe>] ? down+0x2e/0x50
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa00b0b6f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa00af2de>] ? firegl_cmmqs_CWDDE32+0x6e/0x100 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff8129ce01>] ? security_capable+0x21/0x30
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa00af270>] ? firegl_cmmqs_createdriver+0x170/0x170 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa008c12d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffffa007c9be>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff81189cfa>] ? do_vfs_ioctl+0x8a/0x340
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff81177e0d>] ? vfs_read+0x10d/0x180
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff8118a041>] ? sys_ioctl+0x91/0xa0
May 14 10:53:14 forux-Work kernel: [329621.492002]  [<ffffffff81664a82>] ? system_call_fastpath+0x16/0x1b
May 14 10:53:14 forux-Work kernel: [329621.492002] Code: 00 00 00 00 00 00 00 00 00 00 48 8d 47 68 c3 00 00 00 00 00 00 00 00 00 00 00 31 c9 48 8b 97 98 00 00 00 83 7e 18 02 48 0f 44 ce <48> 89 51 08 ff 87 a0 00 00 00 48 89 8f 98 00 00 00 c3 00 00 00 
May 14 10:53:14 forux-Work kernel: [329621.492002] RIP  [<ffffffffa0176291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 14 10:53:14 forux-Work kernel: [329621.492002]  RSP <ffff88011a1219c0>
May 14 10:53:14 forux-Work kernel: [329621.492002] CR2: 0000000000000008
May 14 10:53:14 forux-Work kernel: [329621.492814] ---[ end trace 047d2fc73a8d620b ]---
May 14 11:06:26 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

---

### Post by Corporation on 2012-05-14
Have sent you a PM, want to get people talking together on this issue to work out what our hardware similarities etc. are.

Try changing the following in /boot/grub/grub.cfg:

menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {     
recordfail     
gfxmode $linux_gfx_mode     
insmod gzio     
insmod part_msdos     
insmod ext2     
set root='(hd0,msdos1)'     
search --no-floppy --fs-uuid --set=root 1722af9f-adb5-47f2-a3dc-f3b94a6ac90a     
linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro **nomodeset** quiet splash $vt_handoff     
initrd    /boot/initrd.img-3.2.0-24-generic 
}

---

### Post by Forux on 2012-05-16
Add nomodeset.

Replay on private message.

---

### Post by Forux on 2012-05-18
nomodeset do not help

another death:

```
May 18 11:18:27 forux-Work rpc.idmapd[718]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 18 11:28:18 forux-Work kernel: [174743.944187] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 18 11:28:18 forux-Work kernel: [174743.944194] IP: [<ffffffffa0186291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 18 11:28:18 forux-Work kernel: [174743.944260] PGD 0 
May 18 11:28:18 forux-Work kernel: [174743.944263] Oops: 0002 [#1] SMP 
May 18 11:28:18 forux-Work kernel: [174743.944267] CPU 0 
May 18 11:28:18 forux-Work kernel: [174743.944268] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vesafb rfcomm bnep bluetooth parport_pc ppdev snd_hda_codec_hdmi nfsd nfs lockd fscache auth_rpcgss nfs_acl binfmt_misc sunrpc snd_hda_codec_realtek snd_seq_midi snd_hda_intel snd_hda_codec snd_hwdep snd_rawmidi snd_pcm fglrx(P) snd_seq_midi_event snd_seq snd_timer snd_seq_device mac_hid snd soundcore snd_page_alloc lp parport usbhid hid r8169
May 18 11:28:18 forux-Work kernel: [174743.944295] 
May 18 11:28:18 forux-Work kernel: [174743.944298] Pid: 1093, comm: Xorg Tainted: P           O 3.2.0-24-generic #37-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 18 11:28:18 forux-Work kernel: [174743.944302] RIP: 0010:[<ffffffffa0186291>]  [<ffffffffa0186291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 18 11:28:18 forux-Work kernel: [174743.944343] RSP: 0018:ffff88013554b9c0  EFLAGS: 00010297
May 18 11:28:18 forux-Work kernel: [174743.944345] RAX: ffff880120ec2008 RBX: ffffc90011946150 RCX: 0000000000000000
May 18 11:28:18 forux-Work kernel: [174743.944347] RDX: 0000000000000000 RSI: ffffc90011946018 RDI: ffff880120ec2e30
May 18 11:28:18 forux-Work kernel: [174743.944350] RBP: 0000000000000002 R08: ffffffffa01b6eb0 R09: ffff880120ec2008
May 18 11:28:18 forux-Work kernel: [174743.944352] R10: ffffc90011946090 R11: ffff880120ec2008 R12: ffff880120ec2e30
May 18 11:28:18 forux-Work kernel: [174743.944354] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 18 11:28:18 forux-Work kernel: [174743.944356] FS:  00007f650f5b5880(0000) GS:ffff88013fc00000(0000) knlGS:0000000000000000
May 18 11:28:18 forux-Work kernel: [174743.944359] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 18 11:28:18 forux-Work kernel: [174743.944361] CR2: 0000000000000008 CR3: 0000000135685000 CR4: 00000000000406f0
May 18 11:28:18 forux-Work kernel: [174743.944363] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 18 11:28:18 forux-Work kernel: [174743.944365] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 18 11:28:18 forux-Work kernel: [174743.944368] Process Xorg (pid: 1093, threadinfo ffff88013554a000, task ffff880123c1c4d0)
May 18 11:28:18 forux-Work kernel: [174743.944370] Stack:
May 18 11:28:18 forux-Work kernel: [174743.944371]  ffffffffa0185cb6 0000000000000000 May 18 11:29:15 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 18 11:29:15 forux-Work rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="746" x-info="http://www.rsyslog.com"] start
May 18 11:29:15 forux-Work rsyslogd: rsyslogd's groupid changed to 103
May 18 11:29:15 forux-Work rsyslogd: rsyslogd's userid changed to 101
May 18 11:29:15 forux-Work rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 18 11:29:15 forux-Work kernel: [    0.000000] Initializing cgroup subsys cpuset
May 18 11:29:15 forux-Work kernel: [    0.000000] Initializing cgroup subsys cpu
May 18 11:29:15 forux-Work kernel: [    0.000000] Linux version 3.2.0-24-generic (buildd@yellow) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 (Ubuntu 3.2.0-24.37-generic 3.2.14)
May 18 11:29:15 forux-Work kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=1722af9f-adb5-47f2-a3dc-f3b94a6ac90a ro nomodeset quiet splash vt.handoff=7
May 18 11:29:15 forux-Work kernel: [    0.000000] KERNEL supported cpus:
May 18 11:29:15 forux-Work kernel: [    0.000000]   Intel GenuineIntel
May 18 11:29:15 forux-Work kernel: [    0.000000]   AMD AuthenticAMD
```

---

### Post by Forux on 2012-05-22
again

```
May 22 10:00:52 forux-Work AptDaemon: INFO: Quitting due to inactivity
May 22 10:00:52 forux-Work AptDaemon: INFO: Quitting was requested
May 22 10:09:02 forux-Work CRON[20194]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
May 22 10:10:34 forux-Work rpc.idmapd[844]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 22 10:10:39 forux-Work rpc.idmapd[844]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 22 10:11:29 forux-Work kernel: [340943.223406] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 22 10:11:29 forux-Work kernel: [340943.223415] IP: [<ffffffffa01a2291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223502] PGD 0 
May 22 10:11:29 forux-Work kernel: [340943.223505] Oops: 0002 [#1] SMP 
May 22 10:11:29 forux-Work kernel: [340943.223509] CPU 0 
May 22 10:11:29 forux-Work kernel: [340943.223510] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs reiserfs ext2 pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) rfcomm bnep bluetooth parport_pc vesafb ppdev binfmt_misc snd_hda_codec_hdmi nfsd nfs lockd fscache auth_rpcgss nfs_acl snd_hda_codec_realtek snd_hda_intel sunrpc snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) snd soundcore mac_hid snd_page_alloc lp parport usbhid hid r8169
May 22 10:11:29 forux-Work kernel: [340943.223548] 
May 22 10:11:29 forux-Work kernel: [340943.223550] Pid: 1045, comm: Xorg Tainted: P           O 3.2.0-24-generic #37-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 22 10:11:29 forux-Work kernel: [340943.223555] RIP: 0010:[<ffffffffa01a2291>]  [<ffffffffa01a2291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223599] RSP: 0018:ffff88013583f9c0  EFLAGS: 00010297
May 22 10:11:29 forux-Work kernel: [340943.223601] RAX: ffff880135bd8008 RBX: ffffc90011946150 RCX: 0000000000000000
May 22 10:11:29 forux-Work kernel: [340943.223604] RDX: 0000000000000000 RSI: ffffc90011946018 RDI: ffff880135bd8e30
May 22 10:11:29 forux-Work kernel: [340943.223606] RBP: 0000000000000002 R08: ffffffffa01d2eb0 R09: ffff880135bd8008
May 22 10:11:29 forux-Work kernel: [340943.223608] R10: ffffc90011946090 R11: ffff880135bd8008 R12: ffff880135bd8e30
May 22 10:11:29 forux-Work kernel: [340943.223610] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 22 10:11:29 forux-Work kernel: [340943.223613] FS:  00007fed1d1d2880(0000) GS:ffff88013fc00000(0000) knlGS:0000000000000000
May 22 10:11:29 forux-Work kernel: [340943.223615] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 22 10:11:29 forux-Work kernel: [340943.223617] CR2: 0000000000000008 CR3: 0000000135912000 CR4: 00000000000406f0
May 22 10:11:29 forux-Work kernel: [340943.223619] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 22 10:11:29 forux-Work kernel: [340943.223621] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 22 10:11:29 forux-Work kernel: [340943.223624] Process Xorg (pid: 1045, threadinfo ffff88013583e000, task ffff8801364216f0)
May 22 10:11:29 forux-Work kernel: [340943.223626] Stack:
May 22 10:11:29 forux-Work kernel: [340943.223627]  ffffffffa01a1cb6 0000000000000000 ffff880135bd8e30 ffff880135bd8ec8
May 22 10:11:29 forux-Work kernel: [340943.223632]  0000000000000200 0000000000000000 ffffffffa013ac55 0000000000080000
May 22 10:11:29 forux-Work kernel: [340943.223636]  ffff880135bd8e30 ffffffffa01d2eb0 ffffffffa013afb8 ffff88013583fa88
May 22 10:11:29 forux-Work kernel: [340943.223640] Call Trace:
May 22 10:11:29 forux-Work kernel: [340943.223684]  [<ffffffffa01a1cb6>] ? _ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj+0xb6/0xc0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223739]  [<ffffffffa013ac55>] ? _ZN20CMMHeap_SystemMemory10obtainPoolEv+0x85/0xc0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223789]  [<ffffffffa013afb8>] ? _ZN16CMMHeap_PAGEABLE10expandHeapEm+0x18/0xb0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223830]  [<ffffffffa01a1aaa>] ? _ZN7CMMHeap10expandHeapEmRmPv+0xa/0x10 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223879]  [<ffffffffa01399af>] ? _ZN7CMMHeap21allocateMorePoolSpaceEmPv+0x8f/0x1b0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223929]  [<ffffffffa013837e>] ? _ZN14CMMHeapManager13allocPageableEjR14CMM_ALLOCATION+0xbe/0x100 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.223979]  [<ffffffffa01428b7>] ? _ZN9CMMObjectnwEmP8CMM_CORE+0x37/0x70 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa0146462>] ? _ZN8MSF_CORE21get_surface_structureEv+0xc2/0xe0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa013063f>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x1f/0x1c0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa0131d43>] ? _ZN3MSF21handle_shared_surfaceEP9CMMClientP9CMMDriverP10CMMSurfaceP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x113/0x280 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa012c216>] ? CMMAllocSurface_WA+0x656/0xba0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff8106cf56>] ? current_fs_time+0x16/0x60
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00da262>] ? firegl_trace+0x72/0x1e0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff81162d5d>] ? __kmalloc+0x13d/0x190
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa013d899>] ? _Z8uCWDDEQCmjjPvjS_+0xb59/0x10c0 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff810903fe>] ? down+0x2e/0x50
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00dcb6f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00db2de>] ? firegl_cmmqs_CWDDE32+0x6e/0x100 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff8129ce01>] ? security_capable+0x21/0x30
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00db270>] ? firegl_cmmqs_createdriver+0x170/0x170 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00b812d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffffa00a89be>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff81189cfa>] ? do_vfs_ioctl+0x8a/0x340
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff81177e0d>] ? vfs_read+0x10d/0x180
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff8118a041>] ? sys_ioctl+0x91/0xa0
May 22 10:11:29 forux-Work kernel: [340943.224005]  [<ffffffff81664a82>] ? system_call_fastpath+0x16/0x1b
May 22 10:11:29 forux-Work kernel: [340943.224005] Code: 00 00 00 00 00 00 00 00 00 00 48 8d 47 68 c3 00 00 00 00 00 00 00 00 00 00 00 31 c9 48 8b 97 98 00 00 00 83 7e 18 02 48 0f 44 ce <48> 89 51 08 ff 87 a0 00 00 00 48 89 8f 98 00 00 00 c3 00 00 00 
May 22 10:11:29 forux-Work kernel: [340943.224005] RIP  [<ffffffffa01a2291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 22 10:11:29 forux-Work kernel: [340943.224005]  RSP <ffff88013583f9c0>
May 22 10:11:29 forux-Work kernel: [340943.224005] CR2: 0000000000000008
May 22 10:11:29 forux-Work kernel: [340943.224552] ---[ end trace 0e73cae61579c563 ]---
May 22 10:12:07 forux-Work acpid: client 1045[0:0] has diMay 22 10:12:43 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 22 10:12:43 forux-Work rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="697" x-info="http://www.rsyslog.com"] start
May 22 10:12:43 forux-Work rsyslogd: rsyslogd's groupid changed to 103
May 22 10:12:43 forux-Work rsyslogd: rsyslogd's userid changed to 101
May 22 10:12:43 forux-Work rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
May 22 10:12:43 forux-Work kernel: [    0.000000] Initializing cgroup subsys cpuset
```

---

### Post by Forux on 2012-05-25
another:

```
May 25 10:03:23 forux-Work AptDaemon: INFO: Quitting was requested
May 25 10:09:01 forux-Work CRON[21310]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
May 25 10:09:58 forux-Work rpc.idmapd[784]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 25 10:17:01 forux-Work CRON[21397]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 10:39:01 forux-Work CRON[21732]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
May 25 10:49:16 forux-Work rpc.idmapd[784]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 25 10:50:26 forux-Work kernel: [152323.462605] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 25 10:50:26 forux-Work kernel: [152323.462614] IP: [<ffffffffa0161291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 25 10:50:26 forux-Work kernel: [152323.462696] PGD 0 
May 25 10:50:26 forux-Work kernel: [152323.462698] Oops: 0002 [#1] SMP 
May 25 10:50:26 forux-Work kernel: [152323.462702] CPU 0 
May 25 10:50:26 forux-Work kernel: [152323.462703] Modules linked in: btrfs zlib_deflate libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs reiserfs ext2 pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) rfcomm bnep bluetooth parport_pc ppdev vesafb nfsd nfs binfmt_misc lockd fscache auth_rpcgss nfs_acl sunrpc snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fglrx(P) soundcore snd_page_alloc mac_hid lp parport usbhid hid r8169
May 25 10:50:26 forux-Work kernel: [152323.462740] 
May 25 10:50:26 forux-Work kernel: [152323.462743] Pid: 1118, comm: Xorg Tainted: P           O 3.2.0-24-generic #38-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 25 10:50:26 forux-Work kernel: [152323.462748] RIP: 0010:[<ffffffffa0161291>]  [<ffffffffa0161291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 25 10:50:26 forux-Work kernel: [152323.462792] RSP: 0018:ffff8801361899c0  EFLAGS: 00010297
May 25 10:50:26 forux-Work kernel: [152323.462794] RAX: ffff880138236008 RBX: ffffc90011946150 RCX: 0000000000000000
May 25 10:50:26 forux-Work kernel: [152323.462796] RDX: 0000000000000000 RSI: ffffc90011946018 RDI: ffff880138236e30
May 25 10:50:26 forux-Work kernel: [152323.462798] RBP: 0000000000000002 R08: ffffffffa0191eb0 R09: ffff880138236008
May 25 10:50:26 forux-Work kernel: [152323.462801] R10: ffffc90011946090 R11: ffff880138236008 R12: ffff880138236e30
May 25 10:50:26 forux-Work kernel: [152323.462803] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 25 10:50:26 forux-Work kernel: [152323.462805] FS:  00007fce67401880(0000) GS:ffff88013fc00000(0000) knlGS:0000000000000000
May 25 10:50:26 forux-Work kernel: [152323.462808] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 25 10:50:26 forux-Work kernMay 25 10:51:13 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

strange, always cron is near )

---

### Post by Forux on 2012-05-30
again

```
May 30 11:12:32 forux-Work AptDaemon: INFO: Quitting due to inactivity
May 30 11:12:32 forux-Work AptDaemon: INFO: Quitting was requested
May 30 11:17:01 forux-Work CRON[12566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 30 11:21:12 forux-Work rpc.idmapd[792]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 30 11:27:42 forux-Work kernel: [92091.993845] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 30 11:27:42 forux-Work kernel: [92091.993854] IP: [<ffffffffa0186291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.993933] PGD 0 
May 30 11:27:42 forux-Work kernel: [92091.993936] Oops: 0002 [#1] SMP 
May 30 11:27:42 forux-Work kernel: [92091.993940] CPU 0 
May 30 11:27:42 forux-Work kernel: [92091.993941] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vesafb parport_pc ppdev bnep rfcomm bluetooth nfsd binfmt_misc nfs lockd fscache auth_rpcgss nfs_acl sunrpc snd_hda_codec_hdmi fglrx(P) snd_hda_codec_realtek snd_seq_midi snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep snd_seq_midi_event snd_pcm snd_seq snd_timer snd_seq_device snd mac_hid lp soundcore parport snd_page_alloc usbhid hid r8169
May 30 11:27:42 forux-Work kernel: [92091.993970] 
May 30 11:27:42 forux-Work kernel: [92091.993973] Pid: 1122, comm: Xorg Tainted: P           O 3.2.0-24-generic #39-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
May 30 11:27:42 forux-Work kernel: [92091.993977] RIP: 0010:[<ffffffffa0186291>]  [<ffffffffa0186291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994018] RSP: 0018:ffff88011922b960  EFLAGS: 00010297
May 30 11:27:42 forux-Work kernel: [92091.994020] RAX: ffff8801174a2008 RBX: ffffc90011179150 RCX: 0000000000000000
May 30 11:27:42 forux-Work kernel: [92091.994022] RDX: 0000000000000000 RSI: ffffc90011179018 RDI: ffff8801174a2e30
May 30 11:27:42 forux-Work kernel: [92091.994025] RBP: 0000000000000002 R08: ffffffffa01b6eb0 R09: ffff8801174a2008
May 30 11:27:42 forux-Work kernel: [92091.994027] R10: ffffc90011179090 R11: ffff8801174a2008 R12: ffff8801174a2e30
May 30 11:27:42 forux-Work kernel: [92091.994029] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
May 30 11:27:42 forux-Work kernel: [92091.994031] FS:  00007f2042d6f880(0000) GS:ffff88013fc00000(0000) knlGS:0000000000000000
May 30 11:27:42 forux-Work kernel: [92091.994034] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 30 11:27:42 forux-Work kernel: [92091.994036] CR2: 0000000000000008 CR3: 00000001191e9000 CR4: 00000000000406f0
May 30 11:27:42 forux-Work kernel: [92091.994038] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 30 11:27:42 forux-Work kernel: [92091.994040] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 30 11:27:42 forux-Work kernel: [92091.994043] Process Xorg (pid: 1122, threadinfo ffff88011922a000, task ffff8801191ddbc0)
May 30 11:27:42 forux-Work kernel: [92091.994045] Stack:
May 30 11:27:42 forux-Work kernel: [92091.994046]  ffffffffa0185cb6 0000000000000000 ffff8801174a2e30 ffff8801174a2ec8
May 30 11:27:42 forux-Work kernel: [92091.994051]  0000000000000200 0000000000000000 ffffffffa011ec55 0000000000080000
May 30 11:27:42 forux-Work kernel: [92091.994055]  ffff8801174a2e30 ffffffffa01b6eb0 ffffffffa011efb8 ffff88007ebdc090
May 30 11:27:42 forux-Work kernel: [92091.994059] Call Trace:
May 30 11:27:42 forux-Work kernel: [92091.994103]  [<ffffffffa0185cb6>] ? _ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj+0xb6/0xc0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994156]  [<ffffffffa011ec55>] ? _ZN20CMMHeap_SystemMemory10obtainPoolEv+0x85/0xc0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994205]  [<ffffffffa011efb8>] ? _ZN16CMMHeap_PAGEABLE10expandHeapEm+0x18/0xb0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994246]  [<ffffffffa0185aaa>] ? _ZN7CMMHeap10expandHeapEmRmPv+0xa/0x10 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994294]  [<ffffffffa011d9af>] ? _ZN7CMMHeap21allocateMorePoolSpaceEmPv+0x8f/0x1b0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994342]  [<ffffffffa011c37e>] ? _ZN14CMMHeapManager13allocPageableEjR14CMM_ALLOCATION+0xbe/0x100 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994390]  [<ffffffffa01268b7>] ? _ZN9CMMObjectnwEmP8CMM_CORE+0x37/0x70 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994439]  [<ffffffffa012a462>] ? _ZN8MSF_CORE21get_surface_structureEv+0xc2/0xe0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994486]  [<ffffffffa011463f>] ? _ZN3MSF11create_surfEP9CMMClientP9CMMDriverPvRA4_K14CMM_ALLOCATIONP16MSF_SURF_ATTRIBS+0x1f/0x1c0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994532]  [<ffffffffa0114d10>] ? _ZN3MSF10alloc_surfEP9CMMClientP9CMMDriverP21MEMHEAP_ADDR_RESTRICTjP16MSF_SURF_ATTRIBSP15_CMM_RETURNCODE+0x530/0x580 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994579]  [<ffffffffa011247d>] ? _ZN17SegmentMapManager11FindMappingEbP4AsicP10CMMProcess+0xad/0xe0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994627]  [<ffffffffa0124f8b>] ? CMMAllocSurface1D_WA+0x3fb/0x470 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994635]  [<ffffffff81162e6d>] ? __kmalloc+0x13d/0x190
May 30 11:27:42 forux-Work kernel: [92091.994683]  [<ffffffffa01216ea>] ? _Z8uCWDDEQCmjjPvjS_+0x9aa/0x10c0 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994688]  [<ffffffff8109052e>] ? down+0x2e/0x50
May 30 11:27:42 forux-Work kernel: [92091.994719]  [<ffffffffa00c0b6f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994750]  [<ffffffffa00bf2de>] ? firegl_cmmqs_CWDDE32+0x6e/0x100 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994754]  [<ffffffff8129ceb1>] ? security_capable+0x21/0x30
May 30 11:27:42 forux-Work kernel: [92091.994785]  [<ffffffffa00bf270>] ? firegl_cmmqs_createdriver+0x170/0x170 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994810]  [<ffffffffa009c12d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994830]  [<ffffffffa008c9be>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994834]  [<ffffffff81189e0a>] ? do_vfs_ioctl+0x8a/0x340
May 30 11:27:42 forux-Work kernel: [92091.994837]  [<ffffffff81177f1d>] ? vfs_read+0x10d/0x180
May 30 11:27:42 forux-Work kernel: [92091.994840]  [<ffffffff8118a151>] ? sys_ioctl+0x91/0xa0
May 30 11:27:42 forux-Work kernel: [92091.994844]  [<ffffffff81664d82>] ? system_call_fastpath+0x16/0x1b
May 30 11:27:42 forux-Work kernel: [92091.994846] Code: 00 00 00 00 00 00 00 00 00 00 48 8d 47 68 c3 00 00 00 00 00 00 00 00 00 00 00 31 c9 48 8b 97 98 00 00 00 83 7e 18 02 48 0f 44 ce <48> 89 51 08 ff 87 a0 00 00 00 48 89 8f 98 00 00 00 c3 00 00 00 
May 30 11:27:42 forux-Work kernel: [92091.994878] RIP  [<ffffffffa0186291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
May 30 11:27:42 forux-Work kernel: [92091.994920]  RSP <ffff88011922b960>
May 30 11:27:42 forux-Work kernel: [92091.994922] CR2: 0000000000000008
May 30 11:27:42 forux-Work kernel: [92091.994926] ---[ end trace 2aebf9513211f235 ]---
May 30 11:29:12 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

---

### Post by Forux on 2012-05-31
again, but now log super-short

```
May 31 18:15:37 forux-Work rpc.idmapd[760]: nss_getpwnam: name 'name' not found in domain 'localdomain'
May 31 18:15:48 forux-Work kernel: [110814.240093] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
May 31 18:15:48 forux-Work kernel: [110814.240102] IP: [<ffffffffa0163291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglMay 31 18:16:35 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
May 31 18:16:35 forux-Work rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="779" x-info="http://www.rsyslog.com"] start
```

---

### Post by Forux on 2012-06-08
any help ?

```
Jun  8 12:13:31 forux-Work kernel: [344927.618536] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Jun  8 12:13:31 forux-Work kernel: [344927.618544] IP: [<ffffffffa0164291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Jun  8 12:13:31 forux-Work kernel: [344927.618614] PGD 0 
Jun  8 12:13:31 forux-Work kernel: [344927.618616] Oops: 0002 [#1] SMP 
Jun  8 12:13:31 forux-Work kernel: [344927.618620] CPU 0 
Jun  8 12:13:31 forux-Work kernel: [344927.618621] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc ppdev vesafb nfsd nfs lockd fscache auth_rpcgss nfs_acl binfmt_misc sunrpc snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq mac_hid snd_timer snd_seq_device snd fglrx(P) soundcore snd_page_alloc lp parport usbhid hid r8169
Jun  8 12:13:31 forux-Work kernel: [344927.618648] 
Jun  8 12:13:31 forux-Work kernel: [344927.618651] Pid: 1103, comm: Xorg Tainted: P           O 3.2.0-24-generic #39-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
Jun  8 12:13:31 forux-Work kernel: [344927.618655] RIP: 0010:[<ffffffffa0164291>]  [<ffffffffa0164291>] _ZN20CMMHeap_SystemMemory8pJun  8 12:14:16 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
```

---

### Post by Forux on 2012-06-12
again

```
Jun 12 16:53:50 forux-Work rpc.idmapd[707]: nss_getpwnam: name 'name' not found in domain 'localdomain'
Jun 12 16:59:48 forux-Work kernel: [111361.553687] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Jun 12 16:59:48 forux-Work kernel: [111361.553698] IP: [<ffffffffa0164291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Jun 12 16:59:48 forux-Work kernel: [111361.553778] PGD 0 
Jun 12 16:59:48 forux-Work kernel: [111361.553780] Oops: 0002 [#1] SMP 
Jun 12 16:59:48 forux-Work kernel: [111361.553784] CPU 1 
Jun 12 16:59:48 forux-Work kernel: [111361.553786] Modules linked in: ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) vesafb snd_hda_codec_hdmi parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_realtek nfsd nfs lockd binfmt_misc fscache auth_rpcgss nfs_acl sunrpc snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq fglrx(P) snd_timer snd_seq_device snd mac_hid soundcore snd_page_alloc lp parport usbhid hid r8169
Jun 12 16:59:48 forux-Work kernel: [111361.553816] 
Jun 12 16:59:48 forux-Work kernel: [111361.553819] Pid: 1145, comm: Xorg Tainted: P           O 3.2.0-24-generic #39-Ubuntu BIOSTAR Group G31D-M7/G31D-M7
Jun 12 16:59:48 forux-Work kernel: [111361.553823] RIP: 0010:[<ffffffffa0164291>]  [<ffffffffa0164291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Jun 12 16:59:48 forux-Work kernel: [111361.553864] RSP: 0018:ffff88011cb199c0  EFLAGS: 00010297
Jun 12 16:59:48 forux-Work kernel: [111361.553866] RAX: ffff88011a328008 RBX: ffffc90011475150 RCX: 0000000000000000
Jun 12 16:59:48 forux-Work kernel: [111361.553868] RDX: 0000000000000000 RSI: ffffc90011475018 RDI: ffff88011a328e30
Jun 12 16:59:48 forux-Work kernel: [111361.553870] RBP: 0000000000000002 R08: ffffffffa0194eb0 R09: ffff88011a328008
Jun 12 16:59:48 forux-Work kernel: [111361.553872] R10: ffffc90011475090 R11: ffff88011a328008 R12: ffff88011a328e30
Jun 12 16:59:48 forux-Work kernel: [111361.553874] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
Jun 12 16:59:48 forux-Work kernel: [111361.553877] FS:  00007f2b5ad6a880(0000) GS:ffff88013fc80000(0000) knlGS:0000000000000000
Jun 12 16:59:48 forux-Work kernel: [111361.553880] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jun 12 16:59:48 forux-Work kernel: [111361.553882] CR2: 0000000000000008 CR3: 000000011cbb3000 CR4: 00000000000406e0
Jun 12 16:59:48 forux-Work kernel: [111361.553884] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jun 12 16:59:48 forux-Work kernel: [111361.553886] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jun 12 16:59:48 forux-Work kernel: [111361.553888] Process Xorg (pid: 1145, threadinfo ffff88011cb18000, task ffff880134870000)
Jun 12 16:59:48 forux-Work kernel: [111361.553890] Stack:
Jun 12 16:59:48 forux-Work kernel: [111361.553892]  ffffffffa0163cb6 0000000000000000 ffff88011a328e30 ffff88011a328ec8
Jun 12 16:59:48 forux-Work kernel: [111361.553897]  0000000000000200 0000000000000000 ffffffffa00fcc55 0000000000080000
Jun 12 16:59:48 forux-Work kernel: [111361.553901]  ffff88011a328e30 ffffffffa0194eb0 ffffffffa00fcfb8 ffffc900112b15d8
Jun 12 16:59:48 forux-Work kernel: [111361.553905] Call Trace:
Jun 12 16:59:48 forux-Work kernel: [111361.553947]  [<ffffffffa0163cb6>] ? _ZN7CMMHeap15createPoolSpaceI21CMMPoolAsicAccessibleEEbj+0xb6/0xc0 [fglrx]
Jun 12 16:59:48 forux-Work kernel: [111361.553999]  [<fffffffJun 12 17:00:53 forux-Work kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jun 12 17:00:53 forux-Work rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="771" x-info="http://www.rsyslog.com"] start
```

---

### Post by LV33 on 2012-08-04
Don't know if you're still having this problem, but disabling Xinerama seems to have helped in my case. 

(using ubuntu 12.04, default fglrx from restricted driver manager, 2 video cards, 3 monitors; was having crashes 1-2 times a day with the same "NULL pointer dereference" error messages shown here and at the ArchLinux forums.)

---

### Post by john009 on 2012-12-06
I had a very similar problem running Xubuntu 12.04, running on a 10 year old PC built using the following main components:

MSI KT3 Ultra 2 mb
AMD Athlon XP2600+ processor
ATI Radeon 8500 graphics card
1.5 gb RAM (in 2 DIMMs - 3 slots available).

After searching via google for months without finding anything useful, I removed one other component (e.g. radio card, USB cards) at a time without success. Finally, I removed the 512 mb DIMM, and the problem appears to have gone (touch wood, cross fingers, etc). I had previously checked the RAM using the utility available during boot-up. Don't know what your RAM spec is, but thought it might be off use.

---

### Post by TBcosinus on 2013-01-10
Hello,

I think the latest beta drivers directly from AMD could prevent freezing the machine:

had the same problem with Radeon HD 36xx and HD 54xx with proprietary drivers installed by jockey in Xubuntu 12.04 (precise) x86_64 on an Athlon X2 6000+ Machine and 3 GiB RAM 

Yesterday i just tried the **[latest beta drivers directy from AMD]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip")** and I had no crash with them by playing Assault Cube....I played it for about three hours with no crash. With the other proprietary drivers offered by jockey I had after about 15 minutes, sometimes about 30 minutes a crash => machine freeze, numlock status not changeable on keyboard, other consoles not reachable

Regards
Arne

---

