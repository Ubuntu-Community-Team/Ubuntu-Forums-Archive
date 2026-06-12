---
title: "I think I broke my computer. HELP NOW!!!"
date: 2011-03-03
forum: General Help
---

### Post by DDarkusTriforce on 2011-03-03
I installd Ubuntu on my computer thta hadWindows 7. It was aside by side install. When I start my computer, it goes to a weird black screen with severa things on it. There are two for windows 7 and 1 for vista (idk why). Whe I start one of them, it just reboots my computer! Please, help!!! D':
I DONT KNOW ANYTHING ABOUT UBUNTU AT ALL, SO DONT USE ANY BIG WORDS ABOU IT. Sorry if i seem ignorant, but I am freaking out right now!!

---

### Post by mmsmc on 2011-03-03
what are the error codes(the words that pop up when you get your black screen

---

### Post by Quackers on 2011-03-03
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by DDarkusTriforce on 2011-03-03
```
 An error has been encountered in accessing this page. 
1. **Server:** bootscript.sourceforge.net 
2. **URL path:** / 
3. **Error notes:** NONE 
4. **Error type:** 404 
5. **Request method:** GET 
6. **Request query string:** NONE 
7. **Time:** 2011-03-03 22:25:26 UTC (1299191126) 
**Reporting this problem:** The problem you have encountered  is with a project web site hosted by SourceForge.net.  This issue should  be reported to the SourceForge.net-hosted project (not to  SourceForge.net). 
*If this is a severe or recurring/persistent problem,* please do one of the following, and provide the error text (numbered 1 through 7, above): 

[LIST=1]
[*]Contact the project via their [designated support resources]("http://sourceforge.net/support/prweb-lookup.php?host=bootscript.sourceforge.net&support=1").
[*]Contact the project administrators of this project via email (see the upper right-hand corner of the [Project Summary page]("http://sourceforge.net/support/prweb-lookup.php?host=bootscript.sourceforge.net") for their usernames) at *user-name*@users.sourceforge.net
[/LIST]
  If you are a maintainer of this web content, please refer to the [Site Documentation regarding web services]("http://sourceforge.net/apps/trac/sourceforge/wiki/WikiStart#HostingwithSourceForge.net") for further assistance.  
NOTE: As of 2008-10-23 directory index display has been disabled  by default. This option may be re-enabled by the project by placing a  file with the name ".htaccess" with this line: 
Options +Indexes   
```

---

### Post by DDarkusTriforce on 2011-03-03
nevermind, i made a typo. let me get the code.

---

### Post by DDarkusTriforce on 2011-03-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   404,220,124   401,146,077   7 HPFS/NTFS
/dev/sda3         600,561,664   625,141,759    24,580,096  17 Hidden HPFS/NTFS
/dev/sda4         404,221,950   600,561,663   196,339,714   5 Extended
/dev/sda5         404,221,952   592,486,399   188,264,448  83 Linux
/dev/sda6         592,488,448   600,561,663     8,073,216  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        80E4A52FE4A5287C                       ntfs       System                        
/dev/sda2        C85ACC635ACC503C                       ntfs       TI106033W0C                   
/dev/sda3        9E08F41008F3E565                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        fd6e97f6-be9b-4d9e-8088-40539a0c3264   ext4                                     
/dev/sda6        91d164df-a124-4202-8355-10d91ae70c94   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D035-6A43                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fd6e97f6-be9b-4d9e-8088-40539a0c3264 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fd6e97f6-be9b-4d9e-8088-40539a0c3264 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set fd6e97f6-be9b-4d9e-8088-40539a0c3264
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 80e4a52fe4a5287c
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c85acc635acc503c
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 9e08f41008f3e565
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fd6e97f6-be9b-4d9e-8088-40539a0c3264 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=91d164df-a124-4202-8355-10d91ae70c94 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 297.2GB: boot/grub/core.img
 265.0GB: boot/grub/grub.cfg
 207.9GB: boot/initrd.img-2.6.35-22-generic
 297.2GB: boot/vmlinuz-2.6.35-22-generic
 207.9GB: initrd.img
 297.2GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 38 0b 00 fe  |............8...|
000001d0  ff ff 05 fe ff ff 02 b0  38 0b 00 38 7b 00 00 00  |........8..8{...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 01 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 ef 00  3f 00 40 00 81 00 00 00  |........?.@.....|
00000020  3f 9d 3b 00 80 00 29 43  6a 35 d0 4e 4f 20 4e 41  |?.;...)Cj5.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 fa fc 31 c9 8e d1  |U."..~..N...1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 ff 01 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by Quackers on 2011-03-03
Which Windows 7 entry are you trying to boot? The first one (that ends with /dev/sda1) should be the bootable one. For some reason you have 2 hidden Windows type partitions. One will be a recovery parition (probably the one marked as Vista). I have no idea what the other one is :-)  Do you?

---

### Post by DDarkusTriforce on 2011-03-03
I don't know what it is. And when I select the first one, it gives me a choice of Startup Repair, or Start Windows Normally. When I choose to do it normally, it has the "Starting Windows" logo, then restarts. SHould I use the startup repair?

---

### Post by Quackers on 2011-03-03
That could definitely be worth trying :-)
Did you shrink a Windows partition before you installed Ubuntu?

---

### Post by DDarkusTriforce on 2011-03-03
I gave Ubuntu 100 gigs, and gave windows the other 200. Ill try recovery. Thanks! But you may wanna keep watching this thread in case it dosn't work.

---

### Post by Quackers on 2011-03-03
Good luck :-)

---

### Post by DDarkusTriforce on 2011-03-03
THANK YOU SO MUCH!!! It works again! You sir, are amazing! You saved my 500 dollar laptop! :D
Thank so much, dude! :D :D :D

But, can you please answer this? How do I start Ubuntu? When I select the Ubuntu option on the black screen, all it does is let me log in to a black screen with white text. I tried "start" and "startx", but neither worked. Any ideas? Thanks!

---

### Post by Quackers on 2011-03-03
You're welcome.
When did the black screen problem start in Ubuntu? Did you run updates or install a graphics driver first?

---

### Post by DDarkusTriforce on 2011-03-03
It was a black screen since forever. It has white text that has the command prompt font. I log in (password text is hidden, but it works), and it then has tells me to enter a command. It says *COmputerName*@*Scrren Name* and then some other stuff. I don't know why it does that. And no, the only thing I installed/downloaded on Ubuntu was that file you told me to see the error report.

---

### Post by mmsmc on 2011-03-03
does it say tty1 anywhere?

---

### Post by DDarkusTriforce on 2011-03-03
Yeah, it says tty1 in the same thing as the computername@username.

---

### Post by Quackers on 2011-03-03
So Ubuntu has never booted to a desktop?

---

### Post by mmsmc on 2011-03-03
yeah, youve got a graphics problem, what kind of graphics card do you have?

---

### Post by DDarkusTriforce on 2011-03-03
only time it boots to desktop is when I boot it via USB and select Try Ubuntu.

---

### Post by mmsmc on 2011-03-03
had the same problem, i just reinstalled. you will not be able to use nvidia on that computer

---

### Post by DDarkusTriforce on 2011-03-03
It's Intel(R) HD Graphics.

---

### Post by mmsmc on 2011-03-03
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9954224](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9954224) follow this

---

### Post by DDarkusTriforce on 2011-03-03
Yea, that just made my brain explode. Sorry... Can you summarize it for a n00b?

---

### Post by mmsmc on 2011-03-03
sudo dpkg-reconfigure xserver-xorg try entering that, then restart

---

### Post by DDarkusTriforce on 2011-03-03
I don't know how to restart from that command area. By the way, a message appeared when i tried startx. It said that my CPU security settings wern't effective, or something to that effect.

---

### Post by mmsmc on 2011-03-03
does it say any where "fatal error: no screens found"

---

### Post by DDarkusTriforce on 2011-03-03
not that i can see. ill check.

---

### Post by mmsmc on 2011-03-03
it should say it after you enter startx, i have a plan b if it doesnt work

---

### Post by DDarkusTriforce on 2011-03-03
the screen just goes black. a bunch of code appears for asplit second, but i can't read even a single word before it all dissapears. It dosn't say the missing screen error message.

---

### Post by mmsmc on 2011-03-03
ok, go to the recovery mode(it is in the grub menu when you pick wich operating system to boot up) then go to failsafe graphics mode

---

### Post by DDarkusTriforce on 2011-03-03
failsafe graphics work! But is there a way for t to be in failsafe graphics mode permanantly? I don't want to have to go to recovery mode everytime I use Ubuntu. ANd (I know I'mn a real n00b for saying this) how do I connect to my DSL network? I can't figure it out at all.

---

### Post by mmsmc on 2011-03-03
i belive so, when you press the login button and are about to type in your password(dont login yet just get to this point). on the very bottom of the screen there should be a bar that lets you choose your language and so on, on that bar there is a version choice, i have no clue which one it is but look through them, one of the choices is to use desktop edition, click on that login and restart(hopefully you got all that)

---

### Post by mmsmc on 2011-03-03
is it wireless?

---

### Post by DDarkusTriforce on 2011-03-03
it's wireless

---

### Post by mmsmc on 2011-03-03
ok, lets get you logged in first then we'll deal with the wireless stuff

---

### Post by DDarkusTriforce on 2011-03-03
that bar you told me about, it was there. But i was already on Ubuntu Desktop according to it. ANd im on a laptop, btw.

---

### Post by mmsmc on 2011-03-03
ok hold on a second

---

### Post by mmsmc on 2011-03-03
try the desktop edition safe mode, then if that doesnt work try netbook edition, when you checked that were you on recovery mode?

---

### Post by DDarkusTriforce on 2011-03-03
I don't understand. How do I do that? ANd yes, it's a laptop, not a netbook.

---

### Post by mmsmc on 2011-03-03
that does not matter, switch it from desktop edition to each of the others, restart and try to boot up normally, if that does not work we'll have to try something drastic, but may fix it

---

### Post by DDarkusTriforce on 2011-03-03
i know tht, but is there a way to get to ubuntu without going to recovery mode everytime?

---

### Post by mmsmc on 2011-03-03
by doing this, you are changing the graphics mode, if this works it will affect your entire system, allowing you to boot up normally

---

### Post by mmsmc on 2011-03-03
since you can boot into recovery mode, it wont be as difficult if you were stuck in tty

---

### Post by DDarkusTriforce on 2011-03-03
fine. i guess ill be happy if it can boot at all. THanks! :)

---

### Post by DDarkusTriforce on 2011-03-03
Sorry for the double post, but IS there a way to autoboot in low graphics mode?

---

### Post by Niedzwiedz on 2011-03-03
This may be a little long.
I not really have an answer, but, am experiencing the same problem. 
I installed 10.04 LTS about 3 days ago with Vista. HP G60-445DX Laptop
I still trying to figure it out but, here what I have learned.
First I stop trying any windows recovery or anything and went with the attitude, if, it works don't fix it. Well it kinda works?
First; I found Booting to Windows I get a Start Windows then the screen may dim dark and go blank then reboot.
It goes back to the original Screen to select OS.
I can keep going to; Windows Vista (Loader) on/dev/Sda1 and after 3-4 tries it will Startup! :-)
I can easily select the first Ubuntu OS (Not recovery) and get it going. I did stop trying to do updates until I could do some basic tweaks, like my Graphics, Wireless internet/printer etc.
I mainly wanted Vista as a backup until I know Ubuntu work with this laptop as I could not find where it had been specifically used.
So, as I got Ubuntu working I really not using Windows, but, I am finding it seem to be fixing itself! When I seen your first post I went to Windows to get a screen-shot of the Partitions from a windows perspective. Windows began to Boot and did a little of the dimming screen thing and started! So, it seem, with time, to be doing better. This why I say I not have the answer and am still wanting to know.

I did want to add, it seemed to be something with Grub and if it changed during an update that may be why it seem to Boot to Windows better.

---

### Post by mmsmc on 2011-03-03
plug your ethernet cable into your computer, you will get internet, if you still want help with wireless there are dozens of threads about that here

---

