---
title: "Bootloader is Always Shown in Ubuntu 11.04"
date: 2011-05-28
forum: General Help
---

### Post by multisystem on 2011-05-28
Hi all,

I don't have any OS installed besides my beloved Ubuntu. So I want bootloader to choose the default OS automatically. I want to hide the menu asking me to choose an OS.

I've tried StartUp-Manager and set timeout to 0. Surprisingly, it's the same. Actually there is no timeout until it loads the default OS. the menu is here until I choose what to load myself.


Thanks very much.
Regards.

---

### Post by linuxinstalledfromhdd on 2011-05-28
Try installing Grub Customizer 2.1.2 and you can quickly change it to whatever you need.

From terminal:

sudo apt-get install grub-customizer

Cheers:mad:

---

### Post by sikander3786 on 2011-05-28
It would be even better to let us see the output of this command.

```
cat /etc/default/grub
```

GUI tools that are used to tweak boot settings can hurt at times.

---

### Post by multisystem on 2011-05-28
Thanks for your reply.

I've updated settings through Edit->Preferences, and unchecked both "show menu" and "look for other operating systems" options, and finally set timeout to 0 seconds, but it also doesn't work. The menu is still here :S:S:S

---

### Post by multisystem on 2011-05-28
> **sikander3786 said:**
> It would be even better to let us see the output of this command.

```
cat /etc/default/grub
```

GUI tools that are used to tweak boot settings can hurt at times.


Here you are
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"

```

---

### Post by sikander3786 on 2011-05-28
Ok, edit your /etc/default/grub:

```
gksudo gedit /etc/default/grub
```

Change the line:

```
GRUB_TIMEOUT="0"
```

To:

```
GRUB_TIMEOUT="3"
```

Save and close the file.

Run:

```
sudo update-grub
```

Reboot and let us know if that helps.

---

### Post by multisystem on 2011-05-28
The same. It doesn't even go after 3 seconds. :(

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"


```

---

### Post by sikander3786 on 2011-05-28
The /etc/default/grub looks ok to me for now. It would be better to post the output of bootinfoscript in these circumstances.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

I've also requested some senior member to take a look at your problems. So, stay tuned.

---

### Post by multisystem on 2011-05-28
Thank you very much for your great efforts :)
 
Here is the output

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *            124   625,137,344   625,137,221   5 Extended
/dev/sda5                 126    41,945,714    41,945,589  83 Linux
/dev/sda6          41,945,778    51,375,869     9,430,092  82 Linux swap / Solaris
/dev/sda7          51,375,933   261,088,379   209,712,447   7 NTFS / exFAT / HPFS
/dev/sda8         261,088,443   449,836,064   188,747,622   7 NTFS / exFAT / HPFS
/dev/sda9         449,836,128   583,063,109   133,226,982   7 NTFS / exFAT / HPFS
/dev/sda10        583,063,173   625,137,344    42,074,172   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda10       1817C6740B804C23                       ntfs       WinXP
/dev/sda5        2a939663-27cf-4226-960b-f4e06d1507b2   ext4       
/dev/sda6        e5705a9e-1360-4521-b181-acbb891fe27b   swap       Swap
/dev/sda7        3C89B68C3CF9D3B6                       ntfs       Work
/dev/sda8        057D1FA31AD851B0                       ntfs       Stuff
/dev/sda9        618BE51844C6C7D7                       ntfs       Programs

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /media/WinXP             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/Work              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /media/Stuff             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda9        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
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
	search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2a939663-27cf-4226-960b-f4e06d1507b2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2a939663-27cf-4226-960b-f4e06d1507b2 ro single 
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
	search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2a939663-27cf-4226-960b-f4e06d1507b2
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

### BEGIN /etc/grub.d/30_os-prober.bak1 ###
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
### END /etc/grub.d/30_os-prober.bak1 ###

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
UUID=2a939663-27cf-4226-960b-f4e06d1507b2 /               ext4    errors=remount-ro 0       1
# /media/Programs was on /dev/sda9 during installation
UUID=618BE51844C6C7D7 /media/Programs ntfs    defaults,umask=007,gid=46 0       0
# /media/Stuff was on /dev/sda8 during installation
UUID=057D1FA31AD851B0 /media/Stuff    ntfs    defaults,umask=007,gid=46 0       0
# /media/WinXP was on /dev/sda10 during installation
UUID=1817C6740B804C23 /media/WinXP    ntfs    defaults,umask=007,gid=46 0       0
# /media/Work was on /dev/sda7 during installation
UUID=3C89B68C3CF9D3B6 /media/Work     ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=e5705a9e-1360-4521-b181-acbb891fe27b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  12.129977226 = 13.024463872   boot/grub/core.img                             1
   7.216811180 = 7.748992000    boot/grub/grub.cfg                             1
   9.215888023 = 9.895484416    boot/initrd.img-2.6.38-8-generic               2
  12.635981560 = 13.567781888   boot/vmlinuz-2.6.38-8-generic                  1
   9.215888023 = 9.895484416    initrd.img                                     2
  12.635981560 = 13.567781888   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by drs305 on 2011-05-28
If the Grub menu always displays and doesn't automatically count down and then boot, it could be Grub is (correctly or not) finding something it doesn't like. It designates a 'recordfail' flag and won't let the OS boot until the user manually selects something.

We can see if that is what is causing the problem by making a temporary change in /boot/grub/grub.cfg. Normally we don't edit this file since it will be updated by various automated scripts, but we can do it for testing.

Open grub.cfg for editing as root:
```
gksu gedit /boot/grub/grub.cfg
```

Find this section and change the **-1** value to 3 (you could set it to 0 but this will give you the chance to interrupt it for now):
> 
if [ "${recordfail}" = 1 ]; then
[s][COLOR="Red"]  set timeout=-1[/COLOR][/s]
  set timeout=**7**
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###


Save the file. Do NOT update-grub, which would erase the change. Reboot and see if the menu displays for 3 seconds or 7 seconds and then boots automatically.

---

### Post by multisystem on 2011-05-28
Yes, it works fine. Thanks very much.

So, what do you think about
```

it could be Grub is (correctly or not) finding something it doesn't like. 

```

What may I do?

Thanks again very much. :)

---

### Post by drs305 on 2011-05-28
Early on after G2's introduction I tried unsuccessfully to determine what exactly was triggering the recordfail event for many users. I finally ended up just having them purge and reinstall G2. From a running system, it's very easy as long as an Internet connection is available. 

By purging Grub2, all the files are removed and replaced, which guarantees any corrupted files are repaired (which isn't the case with a simple reinstall). Sometimes it worked, sometimes it didn't. The actual commands if you want to try follow. Explanations can be found in the 'Chroot' link in my signature line.
```
sudo apt-get update # Confirm you have an Internet connection. Don't continue if not.
sudo apt-get purge grub-common # Removes grub-common and grub-pc
sudo apt-get install grub-pc # Installs grub-common and grub-pc
# Tab to OK on the first screen, press the SPACEBAR to select the proper DRIVE only then TAB to OK on the second.
```

If that doesn't fix it, you can make the recordfail timeout edit more permanent (so it survives an 'update-grub') by making the change to /etc/grub.d/00_header:
```
gksu gedit +229 /etc/grub.d/00_header
```

> make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
[COLOR="Red"][s]  set timeout=-1[/s][/COLOR]
  set timeout=**3**
else
  set timeout=${2}
fi
EOF
}
I put "3" as an example. "0" would never show the screen, but I'd recommend at least "1" so you can interrupt the boot if necessary. Of course you can also use "0" and hold down the SHIFT key to call up the menu if necessary. The SHIFT option is available if you have os-prober enabled, which you do.

One final note about 'recordfail': Grub 2 is designed to force the user to manually select an option if G2 thinks there may be or there actually was a problem booting the previous attempt. This post provides a way to bypass the recordfail stoppage. It's not ideal, and in an unattended operation it's possible the computer would continually try to reboot if it finds a problem (rather than wait for your input).

---

