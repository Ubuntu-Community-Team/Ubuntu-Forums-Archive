---
title: "Kernel Panic ?!?!"
date: 2011-05-12
forum: General Help
---

### Post by Gr72 on 2011-05-12
Ok, so I am a newby at Linux but I have learned quickly, I have been runnung Ubuntu on my Sattelite C655 laptop for almost a month now. The other day I tried installing Fedora onto another partition. WEll, when I try to change the grub.cfg to boot to fedora it doesn't work. Then I tried to boot back into Ubuntu and I recieve a
##Start##
[4.436614] kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[4.436660] Pid: 1, comm: swapper Not tainted 2.6.35-28-generic #50-Ubuntu
[4.436701] Call Trace:
[4.436742] [<ffffffff815885ce>] panic+0x90/0X113
[4.436783] [<ffffffff81aee2b3>] mount_block_root+0x1ea/0x29e
[4.436823] [<ffffffff81aee3bd>] mount_root+0x56/0x5a
[4.436863] [<ffffffff81aee531>] prepare_namespace+0x170/0x1a9
[4.436904] [<ffffffff81aed8c2>] kernel_init+0x1a6/0x1b6
[4.436945] [<ffffffff8100aee4>] kernel_thread_helper+0x4/0x10
[4.436986] [<ffffffff81aed71c>] ? kernel_init+0x1a6/0x1b6
[4.437025]  [<ffffffff8100aee0>] ? kernel_thread_helper+0x4/0x10
##End##

Any help here would be hot thanks sooo much. I already checked and put the grub.cfg file back to it's original state and am still getting this error. 
Thanks!!!

---

### Post by Gr72 on 2011-05-12
Hey Drs, 
I'm having the same problem, here;s what I get when I do the BIS

```

Boot Info Script 0.55    dated February 15th, 2010                    
    
    [LEFT]============================= Boot Info Summary: ==============================[/LEFT]
    
    [LEFT] => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in [/LEFT]
    [LEFT]    partition #2 for (,msdos2)/boot/grub.[/LEFT]
    
    [LEFT]sda1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows Vista/7[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows 7[/LEFT]
    [LEFT]    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe[/LEFT]
    
    [LEFT]sda2: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       ext2[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    [LEFT]    Operating System:  Ubuntu 10.10[/LEFT]
    [LEFT]    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/LEFT]
    
    [LEFT]=========================== Drive/Partition Info: =============================[/LEFT]
    
    [LEFT]Drive: sda ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sda: 250.1 GB, 250059350016 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sda1    *             63   244,711,423   244,711,361   7 HPFS/NTFS[/LEFT]
    [LEFT]/dev/sda2         310,138,880   488,392,703   178,253,824  83 Linux[/LEFT]
    
    
    [LEFT]blkid -c /dev/null: ____________________________________________________________[/LEFT]
    
    [LEFT]Device           UUID                                   TYPE       LABEL                         [/LEFT]
    
    [LEFT]/dev/loop0                                              squashfs                                 [/LEFT]
    [LEFT]/dev/loop2                                              squashfs                                 [/LEFT]
    [LEFT]/dev/loop3       e432b045-0778-46d3-8975-921660d07caf   ext4       _Fedora-14-x86_6              [/LEFT]
    [LEFT]/dev/loop4                                              DM_snapshot_cow                               [/LEFT]
    [LEFT]/dev/mapper/live-osimg-min e432b045-0778-46d3-8975-921660d07caf   ext4       _Fedora-14-x86_6              [/LEFT]
    [LEFT]/dev/mapper/live-rw e432b045-0778-46d3-8975-921660d07caf   ext4       _Fedora-14-x86_6              [/LEFT]
    [LEFT]/dev/sda1        0EE7A39866165E60                       ntfs                                     [/LEFT]
    [LEFT]/dev/sda2        641d772c-f0bd-404d-be42-17fa82a02cc8   ext2       Ubuntu                        [/LEFT]
    [LEFT]/dev/sda: PTTYPE="dos" [/LEFT]
    
    [LEFT]=============================== "ls -R /dev/mapper/" output: ===============================[/LEFT]
    [LEFT]/dev/mapper:[/LEFT]
    [LEFT]control[/LEFT]
    [LEFT]live-osimg-min[/LEFT]
    [LEFT]live-rw[/LEFT]
    
    [LEFT]============================ "mount | grep ^/dev  output: ===========================[/LEFT]
    
    [LEFT]Device           Mount_Point              Type       Options[/LEFT]
    
    [LEFT]/dev/mapper/live-rw /                        ext4       (rw,noatime)[/LEFT]
    
    
    [LEFT]=========================== sda2/boot/grub/grub.cfg: ===========================[/LEFT]
    
    #
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    #
    [LEFT]# It is automatically generated by grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    #
    
    [LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s $prefix/grubenv ]; then[/LEFT]
    [LEFT]  set have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ "${prev_saved_entry}" ]; then[/LEFT]
    [LEFT]  set saved_entry="${prev_saved_entry}"[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  set prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]  set boot_once=true[/LEFT]
    [LEFT]fi[/LEFT]
    
    [LEFT]function savedefault {[/LEFT]
    [LEFT]  if [ -z "${boot_once}" ]; then[/LEFT]
    [LEFT]    saved_entry="${chosen}"[/LEFT]
    [LEFT]    save_env saved_entry[/LEFT]
    [LEFT]  fi[/LEFT]
    }
    
    [LEFT]function recordfail {[/LEFT]
    [LEFT]  set recordfail=1[/LEFT]
    [LEFT]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/LEFT]
    }
    
    [LEFT]function load_video {[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  insmod vga[/LEFT]
    }
    
    [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd0,msdos2)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=640x480[/LEFT]
    [LEFT]  load_video[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]terminal_output gfxterm[/LEFT]
    [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd0,msdos2)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]set locale_dir=($root)/boot/grub/locale[/LEFT]
    [LEFT]set lang=en[/LEFT]
    [LEFT]insmod gettext[/LEFT]
    [LEFT]if [ "${recordfail}" = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/light-gray[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos2)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=641d772c-f0bd-404d-be42-17fa82a02cc8 ro   quiet splash[/LEFT]
    [LEFT]	initr	/boot/initrd.img-2.6.35-28-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos2)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]	echo	'Loading Linux 2.6.35-28-generic ...'[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=641d772c-f0bd-404d-be42-17fa82a02cc8 ro single [/LEFT]
    [LEFT]	echo	'Loading initial ramdisk ...'[/LEFT]
    [LEFT]	initr	/boot/initrd.img-2.6.35-28-generic[/LEFT]
    }
    
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/20_linux_xen ###[/LEFT]
    [LEFT]### END /etc/grub.d/20_linux_xen ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos2)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin[/LEFT]
    }
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd0,msdos2)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 641d772c-f0bd-404d-be42-17fa82a02cc8[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    }
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]menuentry "Windows 7 (loader) (on /dev/sda1)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ntfs[/LEFT]
    [LEFT]	set root='(hd0,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 0ee7a39866165e60[/LEFT]
    [LEFT]	chainloader +1[/LEFT]
    }
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]menuentry "Fedora"[/LEFT]
    [LEFT]set root = (hd0,1)[/LEFT]
    [LEFT]chainloader +1[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/41_custom ###[/LEFT]
    [LEFT]if [ -f  $prefix/custom.cfg ]; then[/LEFT]
    [LEFT]  source $prefix/custom.cfg;[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/41_custom ###[/LEFT]
    
    [LEFT]=============================== sda2/etc/fstab: ===============================[/LEFT]
    
    [LEFT]# /etc/fstab: static file system information.[/LEFT]
    #
    [LEFT]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/LEFT]
    [LEFT]# for a device; this may be used with UUID= as a more robust way to name[/LEFT]
    [LEFT]# devices that works even if disks are added and removed. See fstab(5).[/LEFT]
    #
    [LEFT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/LEFT]
    [LEFT]proc            /proc           proc    nodev,noexec,nosuid 0       0[/LEFT]
    [LEFT]# / was on /dev/sda2 during installation[/LEFT]
    [LEFT]UUID=641d772c-f0bd-404d-be42-17fa82a02cc8 /               ext2    errors=remount-ro 0       1[/LEFT]
    
    [LEFT]=================== sda2: Location of files loaded by Grub: ===================[/LEFT]
    
    
    [LEFT] 236.8GB: boot/grub/core.img[/LEFT]
    [LEFT] 236.8GB: boot/grub/grub.cfg[/LEFT]
    [LEFT] 236.7GB: boot/initrd.img-2.6.35-28-generic[/LEFT]
    [LEFT] 236.7GB: boot/vmlinuz-2.6.35-28-generic[/LEFT]
    [LEFT] 236.7GB: initrd.img[/LEFT]
    [LEFT] 236.7GB: vmlinuz[/LEFT]
    [LEFT]=============================== StdErr Messages: ===============================[/LEFT]
    
    [LEFT]  No volume groups found[/LEFT]
    [LEFT]mdadm: No arrays found in config file or automatically
##End##

```

---

### Post by drs305 on 2011-05-12
Things look normal for your setup as well. 

You can try the following from the Grub 2 menu just to see if it boots. From the menu, press 'c' to get to the grub prompt. Then:
Note you can use TAB completion to help - as you type the vmlinuz and initrd filenames you can press TAB to partially complete the name.
```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
insmod (hd0,2)/boot/grub/linux.mod # May report already loaded
linux (hd0,2)/boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 ro nomodeset
initrd (hd0,2)/boot/initrd.img-2.6.35-28-generic
boot
```
If it boots, run these two commands (not from a LiveCD boot):
```
sudo grub-install /dev/sda  # Do not include the partition number
sudo update-grub
```

---

### Post by Gr72 on 2011-05-12
ok, I'll try it.

---

### Post by Gr72 on 2011-05-12
It is saying that those commands are "not an assignment"

---

### Post by drs305 on 2011-05-12
> **Gr72 said:**
> It is saying that those commands are "not an assignment"

Are you running these commands from either the grub> or grub rescue> prompt? I haven't seen that before.

To get to the grub prompt, from the main Grub menu (hold SHIFT during boot if you don't see it), press 'c'.

---

### Post by Gr72 on 2011-05-12
i'm using grub> command

---

### Post by Gr72 on 2011-05-12
wait, I was able to do the commands, wrong Syntax. But when reboot it stopped with [5.850743] sd1:0:0:0 [sda] Attached SCSI disk

---

### Post by drs305 on 2011-05-12
All those other errors you reported in your first post concerned me but I'm not sure how to fix them.

From the LiveCD, I'd try running fsck on the Ubuntu partition to see if it will fix any errors. You need to run this check with the Ubuntu partition unmounted. If it won't unmount with the first command (busy error), you will have to reboot the CD first:
```

sudo umount /dev/sda2
sudo e2fsck -f -y -v /dev/sda2
```

Then try rebooting (first via the menu, then via the commands if it still fails).

That's probably about all the advice I can offer. If you are still having problems, I'd try googling the main part of the error messages or await someone else's inputs.


**ADDED:** Simultaneous posts. I'm not familiar with that problem. There may be a kernel option you can add or a setting in BIOS, but I'm not sure. Grub has passed control so I don't think it's a Grub problem (although there may be a kernel option you can add to the 'linux' line).

---

### Post by Gr72 on 2011-05-12
Ok, I'll try it

---

### Post by Gr72 on 2011-05-12
nothing was bad, or changed.

---

### Post by Gr72 on 2011-05-12
Nope, still not booting

---

### Post by Gr72 on 2011-05-12
Is there anyway to update Kernel from a liveCD??

---

### Post by drs305 on 2011-05-12
> **Gr72 said:**
> Is there anyway to update Kernel from a liveCD??

You can chroot into sda2. I don't know if you can purge the kernel, but you can add an additional kernel or update the initrd file with  "update-initramfs -c -k <kernel version>". 

Although it's for a different problem, there are chroot instructions in the 'Chroot' link in my signature line.

I think I'd first try to address the disk error messages - looking for posts with similar errors to see if you can find a solution that addresses the same type of problem.

---

### Post by Gr72 on 2011-05-12
Already Tried..... didn't really find much.

---

### Post by Gr72 on 2011-05-12
I am just going to re-install.

---

