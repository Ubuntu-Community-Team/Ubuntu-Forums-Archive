---
title: "Accidentally installed LILO on my ubuntu partition"
date: 2011-10-10
forum: General Help
---

### Post by w201 on 2011-10-10
Hey all. I accidentally installed LILO on the wrong partition now ubuntu won't boot up. All I get is a blank screen that starts with L 04 04 04 04...

Help!

---

### Post by oldfred on 2011-10-10
I do not know all the details of lilo but boot script should show what is installed where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by garvinrick4 on 2011-10-10
Put grub2 back in mbr:
use the same live cd you used to install lilo.
I am using sda5 as my Ubuntu partition[COLOR=Red] you use yours.[/COLOR]

```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
```
sudo reboot
```
Boot into Ubuntu.
```
sudo update-grub
```
Just to make a new config file.
##Below is link to bookmark and in drs305 signature you will find links to all things grub.
Keep them and study them as time permits.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by garvinrick4 on 2011-10-10
Oldfred has asked for a bootscript which tells him all there is to know about your
boot process and config file. Would be nice in all cases. He is looking to see why
you chose to install Lilo at all and where it installed. (nice user to have diagnose your bootscript while you got him)

---

### Post by w201 on 2011-10-10
Here you go. I think it's worth noting that I have Ubuntu on my primary drive /dev/sda and slackware on /dev/sdb. I was trying to install LILO in slackware when this happened. 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  LILO
    Boot sector info:   LILO is installed in boot sector of /dev/sdb1 and 
                       looks at sector 142942454 of /dev/sdb for the "map" 
                       file, and the "map" file was found at this location.
    Operating System:  Slackware 13.37.0
    Boot files:        /etc/fstab /etc/lilo.conf /boot/map

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   210,772,799   210,772,737  83 Linux
/dev/sdb2         210,772,800   234,493,055    23,720,256  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a97e6722-7e13-4f56-a96f-e46a841a29c6   ext4       
/dev/sda5        12c0222b-4b77-45f6-a894-a7c9acf868ff   swap       
/dev/sdb1        54915623-8ff7-4b43-8c41-94485063590f   ext4       
/dev/sdb2        63d34583-5a18-4273-b786-eb3d2ab4a833   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ee6628e-c69e-4925-8adf-3c4804acd33b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  48.152854919 = 51.703734272   boot/grub/core.img                             1
   4.499397278 = 4.831191040    boot/grub/grub.cfg                             1
   1.149414062 = 1.234173952    boot/initrd.img-2.6.35-22-generic              2
  44.909702301 = 48.221425664   boot/initrd.img-2.6.35-30-generic              1
  48.140518188 = 51.690487808   boot/vmlinuz-2.6.35-22-generic                 1
  48.255027771 = 51.813441536   boot/vmlinuz-2.6.35-30-generic                 1
  44.909702301 = 48.221425664   initrd.img                                     1
   1.149414062 = 1.234173952    initrd.img.old                                 2
  48.255027771 = 51.813441536   vmlinuz                                        1
  48.140518188 = 51.690487808   vmlinuz.old                                    1

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sdb1        /                ext4        defaults         1   1
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0
--------------------------------------------------------------------------------

============================= sdb1/etc/lilo.conf: ==============================

--------------------------------------------------------------------------------
# LILO configuration file
# generated by 'liloconfig'
#
# Start LILO global section
# Append any additional kernel parameters:
append=" vt.default_utf8=0"
boot = /dev/sda

# Boot BMP Image.
# Bitmap in BMP format: 640x480x8
  bitmap = /boot/slack.bmp
# Menu colors (foreground, background, shadow, highlighted
# foreground, highlighted background, highlighted shadow):
  bmp-colors = 255,0,255,0,255,0
# Location of the option table: location x, location y, number of
# columns, lines per column (max 15), "spill" (this is how many
# entries must be in the first column before the next begins to
# be used.  We don't specify it here, as there's just one column.
  bmp-table = 60,6,1,16
# Timer location x, timer location y, foreground color,
# background color, shadow color.
  bmp-timer = 65,27,0,255

# Standard menu.
# Or, you can comment out the bitmap menu above and 
# use a boot message with the standard menu:
#message = /boot/boot_message.txt

# Wait until the timeout to boot (if commented out, boot the
# first entry immediately):
prompt
# Timeout before the first entry boots.
# This is given in tenths of a second, so 600 for every minute:
timeout = 1200
# Override dangerous defaults that rewrite the partition table:
change-rules
  reset
# Normal VGA console
vga = normal
# Ask for video mode at boot (time out to normal in 30s)
#vga = ask
# VESA framebuffer console @ 1024x768x64k
#vga=791
# VESA framebuffer console @ 1024x768x32k
#vga=790
# VESA framebuffer console @ 1024x768x256
#vga=773
# VESA framebuffer console @ 800x600x64k
#vga=788
# VESA framebuffer console @ 800x600x32k
#vga=787
# VESA framebuffer console @ 800x600x256
#vga=771
# VESA framebuffer console @ 640x480x64k
#vga=785
# VESA framebuffer console @ 640x480x32k
#vga=784
# VESA framebuffer console @ 640x480x256
#vga=769
# End LILO global section
# Linux bootable partition config begins
image = /boot/vmlinuz
  root = /dev/root
  label = Linux
  read-only
# Linux bootable partition config ends
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  54.135020733 = 58.127035904   boot/vmlinuz                                   1
  54.129554272 = 58.121166336   boot/vmlinuz-generic-2.6.37.6                  1
  54.135020733 = 58.127035904   boot/vmlinuz-huge-2.6.37.6                     1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  80 7b d0 fb a0 47 96 59  30 17 7a 88 80 4b 8d b0  |.{...G.Y0.z..K..|
00000010  45 13 f4 bb 45 21 19 91  d0 b8 fd c8 e9 f0 5c b9  |E...E!........\.|
00000020  d0 7f f5 5c 4a ba 00 22  e9 93 36 54 0a 17 ed 00  |...\J.."..6T....|
00000030  1b af 0d 90 ff c5 c8 af  00 72 b3 95 bc 9d ae dc  |.........r......|
00000040  b3 00 1b b7 15 b7 d6 6f  6a 74 00 fd 04 31 8a 9a  |.......ojt...1..|
00000050  dc ec 1b 00 e7 25 90 b8  e6 c8 af 79 00 f3 95 bc  |.....%.....y....|
00000060  dd af dd b3 1a 00 2c de  bc 80 7b fd 73 23 00 98  |......,...{.s#..|
00000070  fa 8b 96 df ec 1a af 80  00 90 b8 ed d9 af 79 00  |..............y.|
00000080  7a 04 dd ae 00 3c b6 16  b7 4c a4 00 25 a8 22 98  |z....<...L..%.".|
00000090  fb 8a 96 dc 00 76 d0 a4  c1 4f 24 26 c9 02 a2 00  |.....v...O$&....|
000000a0  3c be dd ae dc b2 1a 80  b6 15 f3 5c a4 61 b9 00  |<..........\.a..|
000000b0  7a 00 11 5d d7 20 c4 33  c6 91 a0 bb fd d8 af 7a  |z..]. .3.......z|
000000c0  00 3d df 00 7b 00 5a b6  15 b7 4c a5 61 b8 4e 22  |.=..{.Z...L.a.N"|
000000d0  01 5c 00 7b 00 9a b8 e9  00 7b b4 01 00 7b ee dc  |.\.{.....{...{..|
000000e0  b3 1a b7 14 b7 00 4c 3e  aa b3 ee 47 66 40 40 97  |......L>...Gf@@.|
000000f0  db ec 1b af 08 00 7b c3  0f 04 7b 02 5c 00 7b 05  |......{...{.\.{.|
00000100  3d d1 33 af 0d 20 91 a8  ed c8 ef 00 7b bd dc 00  |=.3.. ......{...|
00000110  ae dc 29 d1 bd d9 68 d0  08 6f 60 ad 04 5c 56 af  |..)...h..o`..\V.|
00000120  64 90 00 db ed ba af 16  b3 e6 bc 00 b2 ae ba b3  |d...............|
00000130  6e b6 35 b7 00 08 a4 22  b8 6d 98 b7 8b 00 b6 dc  |n.5....".m......|
00000140  af 1b c3 0d f9 b8 00 88  c8 c1 79 c7 95 82 f5 41  |..........y....A|
00000150  80 5c 0a b6 15 f7 4c 8b  5c ad 06 ed 00 4d 80 5c  |.\....L.\....M.\|
00000160  90 ae b5 b3 79 00 b6 67  b7 23 a4 12 b8 4d 00 98  |....y..g.#...M..|
00000170  9c 8b e2 dc cc 1b eb 00  0d d3 b8 a2 c8 e2 79 93  |..............y.|
00000180  00 95 ff dd c2 dc da 1a  d3 00 15 d9 4c d0 61 87  |............L.a.|
00000190  0a 98 00 fa 81 96 dc ec  5b bf 0d 00 90 b9 ec c8  |........[.......|
000001a0  af e3 78 9e 40 70 02 32  17 b2 1e 80 7b 0c 10 8c  |..x.@p.2....{...|
000001b0  61 b8 2a 80 7b d6 cc ec  00 1b ae 0c 90 b8 00 fe  |a.*.{...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by w201 on 2011-10-10
@[garvinrick4]("http://ubuntuforums.org/member.php?u=899097")

THANK YOU! Your solution worked. Back up and running!

---

### Post by garvinrick4 on 2011-10-10
=> [COLOR=Red]Lilo[/COLOR] is installed in the MBR of [COLOR=Red]/dev/sda.[/COLOR]  
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 
of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos1)/boot/grub on this drive. 

Just so you know the why of it, see in red where lilo was installed in sda not in
sdb where you wanted it. sda is your Ubuntu drive and we just put grub2 back
in mbr (master boot record) of sda so it can find the boot files in sda1 your
Ubuntu install and boot in proper fashion. Welcome to the Forums w201

---

### Post by oldfred on 2011-10-10
Boot script does not always show grub in a seond drive booting correct drive. Your install of grub2's boot loader in sdb may have worked.

As garvinrick4 points out you have Lilo in sda and you can add it to sdb. Then in BIOS you can directly boot it. You can also add a chainload entry if grub2's os-prober does not find your slackware.

From Ubuntu:
```
sudo update-grub
```

Restore basic windows or lilo boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

You can also add a chain load just like a chainload to windows as both lilo & windows have boot code in the partition boot sector.

gksudo gedit /etc/grub.d/40_custom
```
menuentry "Slackware on sdb1" {
    set root=(hd1,1)
    insmod chain
    chainloader +1 
}
```
sudo update-grub

---

### Post by w201 on 2011-10-10
Hey oldfred, originally my problem was not being able to boot slackware. Actually, I'm still having that problem. I can only get in with a bootable usb thumb drive. 

I'm going to try some of the solutions in your last post to see if I can get slackware to boot. All this is still quite new to me, so it might take me hours or days to digest all these commands. What's the easier option here as far as booting slackware is concerned, grub2 or lilo?

---

### Post by oldfred on 2011-10-10
Try the update- grub first. 

Grub2 runs the os-prober as part of that and it is good at finding other installs, not sure about slackware. Installing lilo to sdb is easy, as is adding the boot stanza to 40_custom as you can just copy & paste the boot stanza above.

---

### Post by w201 on 2011-10-10
Sounds good. Thanks for all your assistance guys.

---

### Post by w201 on 2011-10-11
I executed your instructions above. When I try to configure LILO in Ubuntu I get this error message:

> WARNING!

 Your /etc/fstab configuration file gives device 
 UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 as the root filesystem device. 
 This doesn't look to me like an "ordinary" block device. Either your 
 fstab is broken and you should fix it, or you are using hardware (such 
 as a RAID array) which this simple configuration program does not 
 handle.

 You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
 again to retry the configuration process. Documentation for LILO can be
 found in /usr/share/doc/lilo/.

 <Ok>
 I also uninstalled lilo- don't want to get locked out of my system again- but I ran all your other commands. Now when I boot up, I get the grub splash screen, but if I choose slackware on /dev/sdb1 as my option, I get a blank screen starting with L followed by long string of 04 04 04 etc... and nothing else happens

I'm starting to think there's something mechanically wrong with the /dev/sdb hard drive.

---

### Post by oldfred on 2011-10-11
I do not understand your uninstalling lilo, you want it on sdb and grub on sda. Then in BIOS you can choose which to boot.

The UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 is your sda1 partition per script. So why is it giving an error? Did you do something else to your Ubuntu in sda1? Or did you uninstall the whole system?

Rerun script so we can see where you are at. Be sure to post the new verison. If you cannot boot use liveCD.

---

### Post by drs305 on 2011-10-11
> **w201 said:**
> I executed your instructions above. When I try to configure LILO in Ubuntu I get this error message:


Re the warning you are getting from lilo about the UUID. I believe if you actually run the lilo configuration commands it looks at the designation for / in /etc/fstab. If it finds a UUID instead of a device name (e.g. /dev/sda3) it complains. The solution is to change the fstab entry.

As has been mentioned, don't install lilo to the Ubuntu drive, and leave the Ubuntu /etc/fstab alone. There is reason Grub 2 and Ubuntu's fstab use UUIDs, so you should keep whenever possible. I think if you change only the fstab of your other OS lilo will be happy.

---

### Post by w201 on 2011-10-11
Not sure why I uninstalled LILO, but I reinstalled it. It's very frustrating, but the hard drive device names keep switching up on me whenever I reboot. I think that's part of the problem. Here's the new script. 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Lilo is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  LILO
    Boot sector info:   LILO is installed in boot sector of /dev/sdb1 and 
                       looks at sector 142942454 of /dev/sdb for the "map" 
                       file, and the "map" file was found at this location.
    Operating System:  Slackware 13.37.0
    Boot files:        /etc/fstab /etc/lilo.conf /boot/map

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   149,843,967   149,841,920  83 Linux
/dev/sda2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sda5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   210,772,799   210,772,737  83 Linux
/dev/sdb2         210,772,800   234,493,055    23,720,256  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a97e6722-7e13-4f56-a96f-e46a841a29c6   ext4       
/dev/sda5        12c0222b-4b77-45f6-a894-a7c9acf868ff   swap       
/dev/sdb1        54915623-8ff7-4b43-8c41-94485063590f   ext4       LinuxSlack
/dev/sdb2        63d34583-5a18-4273-b786-eb3d2ab4a833   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media                   ext4       (rw,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a97e6722-7e13-4f56-a96f-e46a841a29c6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 54915623-8ff7-4b43-8c41-94485063590f
    linux /boot/vmlinuz root=/dev/root ro  vt.default_utf8=0 vga = normal
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
menuentry "Slackware on sdb1" {
    set root=(hd1,1)
    insmod chain
    chainloader +1 
}
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a97e6722-7e13-4f56-a96f-e46a841a29c6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3ee6628e-c69e-4925-8adf-3c4804acd33b none            swap    sw              0       0
# linuxSlack on /dev/sdb1
UUID=54915623-8ff7-4b43-8c41-94485063590f    /media    ext4    defaults    0    0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  48.151115417 = 51.701866496   boot/grub/core.img                             1
   6.677894592 = 7.170334720    boot/grub/grub.cfg                             1
   1.149414062 = 1.234173952    boot/initrd.img-2.6.35-22-generic              2
   9.773399353 = 10.494107648   boot/initrd.img-2.6.35-30-generic              2
  48.140518188 = 51.690487808   boot/vmlinuz-2.6.35-22-generic                 1
  48.453193665 = 52.026220544   boot/vmlinuz-2.6.35-30-generic                 1
   9.773399353 = 10.494107648   initrd.img                                     2
   1.149414062 = 1.234173952    initrd.img.old                                 2
  48.453193665 = 52.026220544   vmlinuz                                        1
  48.140518188 = 51.690487808   vmlinuz.old                                    1

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sdb1        /                ext4        defaults         1   1
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0
--------------------------------------------------------------------------------

============================= sdb1/etc/lilo.conf: ==============================

--------------------------------------------------------------------------------
# LILO configuration file
# generated by 'liloconfig'
#
# Start LILO global section
# Append any additional kernel parameters:
append=" vt.default_utf8=0"
boot = /dev/sda

# Boot BMP Image.
# Bitmap in BMP format: 640x480x8
  bitmap = /boot/slack.bmp
# Menu colors (foreground, background, shadow, highlighted
# foreground, highlighted background, highlighted shadow):
  bmp-colors = 255,0,255,0,255,0
# Location of the option table: location x, location y, number of
# columns, lines per column (max 15), "spill" (this is how many
# entries must be in the first column before the next begins to
# be used.  We don't specify it here, as there's just one column.
  bmp-table = 60,6,1,16
# Timer location x, timer location y, foreground color,
# background color, shadow color.
  bmp-timer = 65,27,0,255

# Standard menu.
# Or, you can comment out the bitmap menu above and 
# use a boot message with the standard menu:
#message = /boot/boot_message.txt

# Wait until the timeout to boot (if commented out, boot the
# first entry immediately):
prompt
# Timeout before the first entry boots.
# This is given in tenths of a second, so 600 for every minute:
timeout = 1200
# Override dangerous defaults that rewrite the partition table:
change-rules
  reset
# Normal VGA console
vga = normal
# Ask for video mode at boot (time out to normal in 30s)
#vga = ask
# VESA framebuffer console @ 1024x768x64k
#vga=791
# VESA framebuffer console @ 1024x768x32k
#vga=790
# VESA framebuffer console @ 1024x768x256
#vga=773
# VESA framebuffer console @ 800x600x64k
#vga=788
# VESA framebuffer console @ 800x600x32k
#vga=787
# VESA framebuffer console @ 800x600x256
#vga=771
# VESA framebuffer console @ 640x480x64k
#vga=785
# VESA framebuffer console @ 640x480x32k
#vga=784
# VESA framebuffer console @ 640x480x256
#vga=769
# End LILO global section
# Linux bootable partition config begins
image = /boot/vmlinuz
  root = /dev/root
  label = Linux
  read-only
# Linux bootable partition config ends
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  54.135020733 = 58.127035904   boot/vmlinuz                                   1
  54.129554272 = 58.121166336   boot/vmlinuz-generic-2.6.37.6                  1
  54.135020733 = 58.127035904   boot/vmlinuz-huge-2.6.37.6                     1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  80 7b d0 fb a0 47 96 59  30 17 7a 88 80 4b 8d b0  |.{...G.Y0.z..K..|
00000010  45 13 f4 bb 45 21 19 91  d0 b8 fd c8 e9 f0 5c b9  |E...E!........\.|
00000020  d0 7f f5 5c 4a ba 00 22  e9 93 36 54 0a 17 ed 00  |...\J.."..6T....|
00000030  1b af 0d 90 ff c5 c8 af  00 72 b3 95 bc 9d ae dc  |.........r......|
00000040  b3 00 1b b7 15 b7 d6 6f  6a 74 00 fd 04 31 8a 9a  |.......ojt...1..|
00000050  dc ec 1b 00 e7 25 90 b8  e6 c8 af 79 00 f3 95 bc  |.....%.....y....|
00000060  dd af dd b3 1a 00 2c de  bc 80 7b fd 73 23 00 98  |......,...{.s#..|
00000070  fa 8b 96 df ec 1a af 80  00 90 b8 ed d9 af 79 00  |..............y.|
00000080  7a 04 dd ae 00 3c b6 16  b7 4c a4 00 25 a8 22 98  |z....<...L..%.".|
00000090  fb 8a 96 dc 00 76 d0 a4  c1 4f 24 26 c9 02 a2 00  |.....v...O$&....|
000000a0  3c be dd ae dc b2 1a 80  b6 15 f3 5c a4 61 b9 00  |<..........\.a..|
000000b0  7a 00 11 5d d7 20 c4 33  c6 91 a0 bb fd d8 af 7a  |z..]. .3.......z|
000000c0  00 3d df 00 7b 00 5a b6  15 b7 4c a5 61 b8 4e 22  |.=..{.Z...L.a.N"|
000000d0  01 5c 00 7b 00 9a b8 e9  00 7b b4 01 00 7b ee dc  |.\.{.....{...{..|
000000e0  b3 1a b7 14 b7 00 4c 3e  aa b3 ee 47 66 40 40 97  |......L>...Gf@@.|
000000f0  db ec 1b af 08 00 7b c3  0f 04 7b 02 5c 00 7b 05  |......{...{.\.{.|
00000100  3d d1 33 af 0d 20 91 a8  ed c8 ef 00 7b bd dc 00  |=.3.. ......{...|
00000110  ae dc 29 d1 bd d9 68 d0  08 6f 60 ad 04 5c 56 af  |..)...h..o`..\V.|
00000120  64 90 00 db ed ba af 16  b3 e6 bc 00 b2 ae ba b3  |d...............|
00000130  6e b6 35 b7 00 08 a4 22  b8 6d 98 b7 8b 00 b6 dc  |n.5....".m......|
00000140  af 1b c3 0d f9 b8 00 88  c8 c1 79 c7 95 82 f5 41  |..........y....A|
00000150  80 5c 0a b6 15 f7 4c 8b  5c ad 06 ed 00 4d 80 5c  |.\....L.\....M.\|
00000160  90 ae b5 b3 79 00 b6 67  b7 23 a4 12 b8 4d 00 98  |....y..g.#...M..|
00000170  9c 8b e2 dc cc 1b eb 00  0d d3 b8 a2 c8 e2 79 93  |..............y.|
00000180  00 95 ff dd c2 dc da 1a  d3 00 15 d9 4c d0 61 87  |............L.a.|
00000190  0a 98 00 fa 81 96 dc ec  5b bf 0d 00 90 b9 ec c8  |........[.......|
000001a0  af e3 78 9e 40 70 02 32  17 b2 1e 80 7b 0c 10 8c  |..x.@p.2....{...|
000001b0  61 b8 2a 80 7b d6 cc ec  00 1b ae 0c 90 b8 00 fe  |a.*.{...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 80 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by drs305 on 2011-10-11
Is everything working now? 

The 'drive name switching' may cause a problem with a lilo boot if it continues since the / partition is defined as 'sdb1' rather than by UUID, but I don't know if you can do anything about that as far as lilo is concerned. Hopefully the system will boot now with more consistency and the drive designations won't switch.

---

### Post by w201 on 2011-10-11
No, it's still not working. Slackware is not booting.

I get a grub splash screen, and from there I can boot ubuntu just fine. But when I select slackware I get errors.

the fstabs fro ubuntu and slackware are different. Ubuntu uses UUIDs and slackware uses /dev/sdb. Does that cause a conflict? I honestly don't know what to do anymore.

oldfred, to answer your question- the only other thing I did was to add the UUID for my second harddrive to the ubuntu fstab.

---

### Post by drs305 on 2011-10-11
In your Grub menu, there should be two Slackware entries - the one Grub found automatically and the custom entry you added.

> "Linux (on /dev/sdb1)"
"Slackware on sdb1" 
Did you try both of them? The entries go about trying to find Slackware in different ways.

I don't know how Slackware is presented in Grub, but I'll try to find an example and compare it to your entries. In the meantime, hopefully someone else will be able to shed some light on Slackware.

Added:
Back in a bit.

---

### Post by drs305 on 2011-10-11
At the Grub menu, highlight the first Slackware entry and press "e" to edit it. Go to the 'linux' line and change
> linux /boot/vmlinuz root=**/dev/root** ...
to
linux /boot/vmlinuz root=**/dev/sdb1** ...
Leave the rest of the line as is.
Then press CTRL-x to see if it boots.

There is also no 'initrd' line in your menuentry. For a normal Linux menuentry, there should be a line:
> initrd /boot/initrd.img
Neither the Boot Info Script nor Grub found an initrd image.  Sorry but I just don't know enough about how Slackware works to know if it's missing or that's just how Slackware works.

I have no idea if this is the proper formatting or not. It looks odd to me.:
> vt.default_utf8=0 vga = normal

---

### Post by w201 on 2011-10-11
Hey drs305, yes, I've tried both slackware entries. Neither one works.

I tried your suggestion of changing /dev/root to /dev/sdb1 and it returned an "error: out of disk"

I just can't seem to get the damn thing to boot. I really appreciate you trying to help.

---

### Post by drs305 on 2011-10-11
[s]If you give me a link I can try to install your version of slackware to see what I get. I leave on a business trip tomorrow but if I can figure anything out I'll try to post before leaving.[/s]
Sorry. Just saw how large Slackware is (6 CDs or DVD). I won't have the time to do this tonight unless I can get away with just CD 1.

It might also be worthwhile to change the BIOS boot order to sdb and see if lilo boots Slackware. Sometimes we spend a lot of effort trying to get Grub to boot a system that won't run on it's own, thinking that it's a Grub problem when in fact it isn't.

---

### Post by w201 on 2011-10-11
Go to this page and scroll to the bottom of the page and you'll see the torrent for my verson[SIZE=1], Torrent for Slackware 13.37, 64-bit x86_64[/SIZE]:
[http://www.slackware.com/getslack/torrents.php](http://www.slackware.com/getslack/torrents.php)

I've tried changing the boot priority before but I'm going to give it another try because I've been making lots of changes. 

I'm new to linux, so I'm sure somewhere in there something is not configured correctly, bios, grub, fstab, etc...

---

### Post by drs305 on 2011-10-11
I installed Slackware 13.37, using only CD 1. I chose a very basic installation and did not install lilo. There is no 'initrd' file in the /boot folder, where the vmlinuz kernels are stored.

I then ran update-grub from Ubuntu. It found 4 slackware kernels but failed to boot from any of the automated entries. Each left me hanging at a kernel panic.

I then experimented from the Grub command line and the following worked. It allowed me to enter the username and password and left me at a terminal. I couldn't get farther than the terminal since I'm not sure I installed the necessary packages.

From the Grub menu, I pressed 'c' to get to the grub prompt. I then typed the following:

> 
set root=(hd1,1)
linux (hd1,1)/boot/vmlinuz root=/dev/sdb1 ro
boot
and it booted to the 'darkstar' login prompt.

---

### Post by w201 on 2011-10-11
> **drs305 said:**
> set root=(hd1,1)
linux (hd1,1)/boot/vmlinuz root=/dev/sdb1 ro
boot 			 		

I was hopeful that would do it, but I got:

[B]out of disk
& 
no kernel loaded[/B]

I also tried by changing the boot priority and got:

**L 04 04 04 04 04 04 04....**

I have to crtl+alt+del out of that

---

### Post by oldfred on 2011-10-11
Your lilo.conf has this line. If drive is sdb should it not be sdb?

boot = /dev/sda

---

### Post by w201 on 2011-10-12
I corrected the error. I don't know how it got that way, it may have something to do with my drives randomly swapping device names. Anyway, still can't get slackware to boot up.

It's very frustrating not being able to do more but I've only been messing with linux systems less than a month. You guys are awesome for helping me out but half these commands I'm running are just going right over my head and I'm afraid of doing more damage than good.

I've edited half dozen files so far here and there, I don't even know what half of those files do. If I can at least pinpoint one problem area, that would be great.

Still willing to try but it seems like we're running out of options here.

To compact an already complicated issue, I think my uninstalling LILO earlier messed things up even further, because now I can't even get liloconfig to work. Slackware doesn't recognize the command.

---

### Post by oldfred on 2011-10-12
If BIOS is not consistently bringing up the drives in the same order then it makes it very difficult. Grub/Ubuntu changed to UUIDs just for that but more with removeable drives that can become different device numbers.

Is one drive SATA and the other PATA?  We have seen similar issues with mixed drives.

---

### Post by w201 on 2011-10-12
> **oldfred said:**
> 
Is one drive SATA and the other PATA?  We have seen similar issues with mixed drives.

Yup! So that's it then? Is there anything that can be done to fix that? 

It's going to be pointless tackling this slackware issue until I can solve this drive problem.

---

### Post by oldfred on 2011-10-12
I have not seen an answer. 

It may be a difference between warm boot & cold boot. Is PATA have jumpers set correctly or cable select set correctly. Often PATA is promoted to sda since it has the old jumpers set to primary master or boot drive.

Is BIOS updated to current version?

---

### Post by w201 on 2011-10-12
When I added the second drive, I think i set everything correctly, but I guess you just never know. Same goes for the BIOS.

I guess now is a good time to check. I'll post back what I find...

---

### Post by w201 on 2011-10-12
Okay, so my bios is not current. I've never updated my bios in linux systems before. Looks complicated. I'm looking into it...

---

### Post by w201 on 2011-10-12
My BIOS is not current, but I don't feel terribly confident with the update process in linux.

oldfred, what do you recommend here? I don't want to burn my BIOS and I'd hate to think all the problems I'm experiencing are due to an out-of-date bios because everything else seems to be working fine, so isn't it better to just leave it alone?

---

### Post by oldfred on 2011-10-12
I would suggest not to update BIOS unless you have specific issues that the BIOS update reportedly fixes.

I updated mine several times but it directly reads the update from a FAT32 flash drive, so it is easy to update.

---

### Post by w201 on 2011-10-12
hmmm, I have some flash drives formatted with FAT32 that I could possibly use to do the update. 

Sounds tempting.

---

### Post by dcstar on 2011-10-13
Your BIOS should allow you to select which drive is the boot drive, change it to the one with Slackware on it.

---

### Post by w201 on 2011-10-13
That's one of the first things I tried when I noticed the problem. I put the problem on the back burner for now. That drive had bad blocks in it anyway, but because I was using SATA and PATA drives in different slots, device names kept switching on me, and that's the deeper issue. Can't really get anywhere like that. I'm ditching that PATA drive for a new SATA drive into which I'll reinstall slackware.

---

