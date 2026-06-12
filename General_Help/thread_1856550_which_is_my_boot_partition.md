---
title: "which is my boot partition??"
date: 2011-10-08
forum: General Help
---

### Post by F.G. on 2011-10-08
hi,
so I was just partitioning another disk, when i noticed this, I've got a boot partition (sda1) right at the front of my master HDD, which i think was created when i installed Arch to sda3 and is not being used.
 
Ubuntu is installed on an extended partition in sda5 and sda6. 

As far as i'm aware ubuntu doesn't create a boot partition, therefore my computer (which boots from the grub installed by Ubuntu) should boot from sda5. but can computers boot from extended partitions?

so I should be able to get rid of the boot partition and add it to the swap (and then reconfigure the swap)?

so my question is how can i tell if my computer boots from that partition? (without just deleting it and finding out).

this isn't particulary urgent, but seems like a waste of a partition. i've attached a gparted pic. thanks for any help.

---

### Post by stlsaint on 2011-10-08
It looks like sda1 being the boot is being used by sda3 which according to you is your arch install. Ubuntu does not create a seperate /boot unless specified by the user at install so again i think its a safe deal to say that the /boot is from arch although i am not a arch user so i cant say for sure if arch makes a seperate /boot by default. Though something is using it as it has space being used up and its not from ubuntu.

---

### Post by F.G. on 2011-10-08
thanks for your reply.
they both boot from the ubuntu installed grub now, but originally it just had archbang installed which then used the sda1 partition (and automatically makes a boot, '/' and '/home' on seperate partitions).  my concern is that i don't really understand if/how a computer can boot from an extended partition, so i just need a way to check (which wont just tell me the type of patition).

---

### Post by stlsaint on 2011-10-08
IIRC, (and it has been some time since i had to manipulate some partitions) /boot can be on a extended partition. To check my only solution would be to google the issue. I tried for ya but im at work and anything involving "wiki" in the url is blocked....government....go figure!!:popcorn: Also grub is not actually handling booting per say. It is merely the bootloader that points to the partition so even if it still shows up in grub, arch can still be using that seperate /boot.

---

### Post by viperdvman on 2011-10-08
As far as I know, you can make whatever partition you want the boot partition. It just has to be done when you install Ubuntu. Just be careful where you put the MBR (it's usually best to put that in your boot partition)

---

### Post by ajgreeny on 2011-10-08
Linux has no problem booting from a logical partition inside an extended partition;  it's Windows that refuses to boot in that situation.

I also think that linux can manage to boot even without a boot flag on the partition, but that may be my misunderstanding the information I haver read elsewhere.

Contrary to what viperdvman said, the MBR (grub in the case of ubuntu) is actually best not put in a partition at all, but on the root of a disk,  ie, not on /dev/sda1 or /dev/sda2, but simply on /dev/sda (or sdb if there are reasons for that)

---

### Post by F.G. on 2011-10-08
> **stlsaint said:**
> IIRC, (and it has been some time since i had to manipulate some partitions) /boot can be on a extended partition. To check my only solution would be to google the issue. I tried for ya but im at work and anything involving "wiki" in the url is blocked....government....go figure!!:popcorn: Also grub is not actually handling booting per say. It is merely the bootloader that points to the partition so even if it still shows up in grub, arch can still be using that seperate /boot.

hmm, so your saying even if it's listed in one grub it may still be booting from sda1? in that case i should probably leave it. I guess i need to do some more research, I suppose the worst that would happen would be that i'd have to reconfigure the bootloader. I was hopeing someone might know a command (+options) which would give me enough info to know for sure what is actually happening, rather than just a description of the partitioning setup.

i'm curious about the gov't and wiki, as your profile mentions texas and as far as i'm aware (apart from folks who think wikki means wicca) the states is pretty unrestricted (i spent sometime in Beijing where this was an issue, you couldn't get bbc).

---

### Post by Quackers on 2011-10-08
It's possible to see what is where.
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by F.G. on 2011-10-08
...one minute, can't seem to get the code tags working properly.

---

### Post by F.G. on 2011-10-08
ok, something in this output is acting like an escape character and making the code tags not work so i put it in > s. 
anyway, thanks for that script, its given a massive output, here it is:
[QUOTE]
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    31370192 of the same hard drive for core.img. core.img is at this location 
    and looks for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /syslinux/syslinux.cfg

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              1       144,584       144,584  83 Linux
/dev/sda2             144,585     1,204,874     1,060,290  82 Linux swap / Solaris
/dev/sda3           1,204,875    21,687,749    20,482,875  83 Linux
/dev/sda4          21,688,318   488,396,799   466,708,482   5 Extended
/dev/sda5          21,688,320    41,218,047    19,529,728  83 Linux
/dev/sda6          41,220,096   488,396,799   447,176,704  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        cd1e73d2-3054-4f74-9604-21df97556104   ext2       
/dev/sda2        a2a303c6-d932-4822-920e-7bbcef93631a   swap       
/dev/sda3        8689830c-cd61-4ced-8408-4153b87c201f   ext4       
/dev/sda5        61847cd1-74cd-4ff9-be04-6eaa70b52527   ext4       
/dev/sda6        64c3bd28-0288-42b4-afd3-931cab31b351   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


============================= sda1/grub/menu.lst: ==============================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  [https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution](https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution)

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) ArchBang Linux
title  ArchBang Linux
root   (hd0,0)
kernel /vmlinuz-linux root=/dev/disk/by-uuid/6e2e8b30-eba5-4b80-a836-7930ac7cd1d7 loglevel=3 ro quiet resume=/dev/disk/by-uuid/fb671bcb-2648-461e-b808-ec693c3617ba   
initrd /initramfs-linux.img

# (1) ArchBang Linux fallback (useful if you change your hard disk/mainboard)
title  ArchBang Linux Fallback
root   (hd0,0)
kernel /vmlinuz-linux root=/dev/disk/by-uuid/6e2e8b30-eba5-4b80-a836-7930ac7cd1d7 loglevel=3 ro quiet
initrd /initramfs-linux-fallback.img

# (2) Optional entry for the system on sda1
#title sda1
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: [https://wiki.archlinux.org/index.php/Syslinux](https://wiki.archlinux.org/index.php/Syslinux)
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to [http://syslinux.zytor.com/wiki/index.php/Doc/menu](http://syslinux.zytor.com/wiki/index.php/Doc/menu)
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
	MENU LABEL Arch Linux
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.029300213 = 0.031460864    grub/menu.lst                                  1
   0.028058529 = 0.030127616    grub/stage2                                    2
   0.018716335 = 0.020096512    initramfs-linux-fallback.img                  44
   0.008869648 = 0.009523712    initramfs-linux.img                           11
   0.009180546 = 0.009857536    vmlinuz-linux                                 11

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

   0.017095089 = 0.018355712    syslinux/syslinux.cfg                          1

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  [https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution](https://wiki.archlinux.org/index.php/GRUB#Framebuffer_resolution)

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux  [/boot/vmlinuz-linux]
root   (hd0,0)
kernel /vmlinuz-linux root=/dev/sda3 ro
initrd /initramfs-linux.img

# (1) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
tmpfs		/tmp	tmpfs	nodev,nosuid	0	0
UUID=8689830c-cd61-4ced-8408-4153b87c201f / ext4 defaults 0 1
UUID=a2a303c6-d932-4822-920e-7bbcef93631a swap swap defaults 0 0
--------------------------------------------------------------------------------

======================= sda3/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: [https://wiki.archlinux.org/index.php/Syslinux](https://wiki.archlinux.org/index.php/Syslinux)
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Change to 1 if you do not want to use a menu
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to [http://syslinux.zytor.com/wiki/index.php/Doc/menu](http://syslinux.zytor.com/wiki/index.php/Doc/menu)
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
	MENU LABEL Arch Linux
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.699532986 = 2.898601472    boot/grub/menu.lst                             1
   2.874314785 = 3.086272000    boot/grub/stage2                               1
   2.904019833 = 3.118167552    boot/initramfs-linux-fallback.img              1
   2.892961025 = 3.106293248    boot/initramfs-linux.img                       1
   2.889848232 = 3.102950912    boot/vmlinuz-linux                             1

================= sda3: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

   2.699693203 = 2.898773504    boot/syslinux/syslinux.cfg                     1

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="4"
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=61847cd1-74cd-4ff9-be04-6eaa70b52527 ro  splash vga=773  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=61847cd1-74cd-4ff9-be04-6eaa70b52527 ro single  splash vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 61847cd1-74cd-4ff9-be04-6eaa70b52527
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 8689830c-cd61-4ced-8408-4153b87c201f
	linux /boot/vmlinuz-linux root=/dev/sda3
	initrd /boot/initramfs-linux.img
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=61847cd1-74cd-4ff9-be04-6eaa70b52527 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=64c3bd28-0288-42b4-afd3-931cab31b351 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=fb671bcb-2648-461e-b808-ec693c3617ba none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.958499908 = 16.061566976   boot/grub/core.img                             1
  14.962974548 = 16.066371584   boot/grub/grub.cfg                             1
  13.400909424 = 14.389116928   boot/initrd.img-2.6.38-8-generic               2
  14.956802368 = 16.059744256   boot/vmlinuz-2.6.38-8-generic                  1
  13.400909424 = 14.389116928   initrd.img                                     2
  14.956802368 = 16.059744256   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error



so, that's all quite long and messy, my guess would be that this bit is relevant:
> 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 8689830c-cd61-4ced-8408-4153b87c201f
	linux /boot/vmlinuz-linux root=/dev/sda3
	initrd /boot/initramfs-linux.img
}
### END /etc/grub.d/30_os-prober ###



i'm not sure what '(/dev/sda,msdos3)' means, but might it be relevant. also it looks like 'linux /boot/vmlinuz-linux root=/dev/sda3' might mean that it boots directly, and doesn't use sda1? 

anyway, thanks for the script. I look forwared to hearing what anyone has to say (if they don't mind wading through the ouput).

---

### Post by QLee on 2011-10-09
[QUOTE=F.G.]...
i'm not sure what '(/dev/sda,msdos3)' means, but might it be relevant. also it looks like 'linux /boot/vmlinuz-linux root=/dev/sda3' might mean that it boots directly, and doesn't use sda1? [/QUOTE]
It means sda3, just like you thought.

[QUOTE=F.G.]anyway, thanks for the script. I look forwared to hearing what anyone has to say (if they don't mind wading through the ouput).[/QUOTE]
OK, I don't mind putting on my hip waders for a little while. It sure is harder to read the thread with such a long quote. If you ask a moderator to fix it, someone will probably add the code tags.

Here's what I have to say:

[QUOTE=F.G.]so I was just partitioning another disk, when i noticed this, I've got a  boot partition (sda1) right at the front of my master HDD, which i  think was created when i installed Arch to sda3 and is not being used.
 
Ubuntu is installed on an extended partition in sda5 and sda6. 

As far as i'm aware ubuntu doesn't create a boot partition, therefore my  computer (which boots from the grub installed by Ubuntu) should boot  from sda5. but can computers boot from extended partitions?[/QUOTE]
That all seems both reasonable and it appears to fit the rest of the information we have.

[QUOTE=F.G.]so I should be able to get rid of the boot partition and add it to the swap (and then reconfigure the swap)?[/QUOTE]
Yes, since it is adjacent you could easily delete one, combine them, however, now partition 1 and 2 would now be combined and I'm not sure which number gparted would asign and sda1 is a pretty small amount of storage space to choose to waste if your system is working well as it is. 

Definitely have a good backup of any important files before you start trying things. There are lots of threads in the forum about moving partitions around. If you post what steps you propose to take someone will look them over and make suggestions if necessary.

---

### Post by F.G. on 2011-10-10
ok, so I think for now i'm going to do nothing. particularly as my machine works, and i need it right now and don't want to break it/have to fix it. my main reason for wanting to change it was to free-up a physical partition (rather than the space issue), but i don't need the use of an extra physical partition right now either.

In due course (when i;m brave enough, and don't need the use of this netbook so much), i'll probably delete that partition, resize the swap, re-reference the swap in ubuntu / arch and pray that it still works.

my thoughts on the labeling is that sda1 would just disappear during the resizing and then on reboot all the numbers would be shuffled down one, the naming of disk drives (at least the physical names: sda, sdb etc) has always seemed 'on-the-fly', or 'dynamic' to me (at least with external disks.)
hmm, although then surely nothing with named references would work?

---

### Post by PayPaul on 2011-10-10
I have a similar question related to where my boot partition is. I currently use a Wubi install for my Ubuntu. Opening up gparted for the first time I wanted to see all my partitions and their labels. I'm going to post 4 screenshots and hope someone knows more of what to make of them than I do. It seems to me that I don't have but one sda1 device which is an external drive. The majority of the devices listed are SDE devices. I thought all my drives were sda/?

---

### Post by F.G. on 2011-10-14
hi paypaul,

so, first a disclaimer, I've never used wubi, and have no idea how it works.

looking at your screenshots, it looks like /dev/sde1 is a boot partition, this is going to be your windows boot partition (i gather ntfs has to boot from the begining of a disk). now i figured that using wubi, the windows bootloader is used??
either way, i think the names (eg /dev/sd*) are just names, and change for devices depending on the order they're attached, so not particularly important.

hope this was some help.

---

