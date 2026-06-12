---
title: "Dual Boot Windows 7/Ubuntu 10.10 - Ubuntu Not Booting After Partition Resize"
date: 2010-12-29
forum: General Help
---

### Post by Felix1701D on 2010-12-29
Hello,

I am a new Ubuntu user, although I am not completely new to Linux (openSuSE 11.1 x64 has been my primary desktop OS for over two years).  Two weeks ago, I bought a new HP EliteBook 8540w laptop on which I have done a clean install of Windows 7 Pro x64 and Ubuntu 10.10 x64 (_not_ using wubi).  The problem is that, although it used to work, I am now not able to boot into Ubuntu.  Whenever I select Ubuntu I either get an immediate reboot, or the computer hangs with a blinking cursor on the top left of the screen.  Before I try anything drastic, like a reinstall of Ubuntu, I would like to see if there are any other options to fix this problem.

Below is some history on how I got to this point.  

When I did the installation I set things up so that the Windows boot loader allows me to select Windows or Ubuntu.    From my experience dual-booting XP and Linux, Windows is easily offended, so I prefer to keep it happy by using its own boot loader and letting it think it is the master of the universe.  I installed GRUB2 on a separate boot (logical) partition.  This configuration worked nicely; I was able to boot both operating systems without problems.  However, after realizing that Windows 7 plus drivers took up 20 of the 40GB I had allocated for Windows and I still had Office, Flight Simulator X, etc. to install, I decided to resize my Windows system partition.  

I resized the partitions using GParted from the Ubuntu 10.10 live CD.  I doubled the size of the Windows operating system partition by shrinking my Files partition.  I did not explicitly change the number or order of the partitions in an attempt to avoid boot problems.  After resizing was done, I confirmed that Windows booted (it forced a disk check, but booted fine).  Unless I was actually dreaming, I recall confirming that Ubuntu continued to boot after the resize.  I made no further changes other than system updates as required by both operating systems.

I got busy setting things up in Windows (this is my first Windows 7 experience) and did not boot Ubuntu again until this past weekend when I wanted to continue setting things up there.  What I got when I selected Ubuntu in the NTLDR menu was an instant reboot to the HP logo screen, or after several such cycles a blinking cursor on the top left of the screen.   I do not get any indication that GRUB is doing anything and I do not get a rescue prompt.  The only recovery after reaching the blinking cursor is to power cycle the computer.   Windows continues to boot properly and I am able to boot the Ubuntu live CD and see all my partitions.

I ran the boot info script referenced in other threads and got the following results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

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
    Boot file info:     Grub 2 in the file /ubnt1010.lnx looks at sector 
                       84120790 of the same hard drive for core.img, but 
                       core.img can not be found at this location. Grub 2 in 
                       the file /ubnt1010_orig.lnx looks at sector 84120790 
                       of the same hard drive for core.img, but core.img can 
                       not be found at this location.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 84120790 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /ubnt1010.lnx looks at sector 
                       84120790 of the same hard drive for core.img, but 
                       core.img can not be found at this location. Grub 2 in 
                       the file /ubt21010.lnx looks at sector 84120790 of the 
                       same hard drive for core.img, but core.img can not be 
                       found at this location.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   167,786,495   167,579,648   7 HPFS/NTFS
/dev/sda3         167,786,496   976,773,119   808,986,624   5 Extended
/dev/sda5         167,788,544   168,202,239       413,696  83 Linux
/dev/sda6         168,204,288   172,396,543     4,192,256   b W95 FAT32
/dev/sda7         172,398,592   184,979,455    12,580,864  82 Linux swap / Solaris
/dev/sda8         184,981,504   226,922,495    41,940,992  83 Linux
/dev/sda9         226,924,544   892,887,039   665,962,496   7 HPFS/NTFS
/dev/sda10        892,889,088   976,773,119    83,884,032  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       fafc6b13-8963-4f41-8cab-746428a29f8d   ext3                                     
/dev/sda1        B0B691F7B691BDF2                       ntfs       System Reserved               
/dev/sda2        5062A06A62A0570E                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        dc36dc4c-7972-476f-b07a-3f08c43cd156   ext3                                     
/dev/sda6        6F3A-3122                              vfat       DOS                           
/dev/sda7        81a301a5-65bc-4c4e-a21e-258715910910   swap                                     
/dev/sda8        b376dfc3-16fc-4a32-ab36-1f0a6aed44aa   ext3                                     
/dev/sda9        CAA8164EA8163981                       ntfs       Files                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/DOS               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


============================= sda5/grub/grub.cfg: =============================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set b376dfc3-16fc-4a32-ab36-1f0a6aed44aa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    linux    /vmlinuz-2.6.35-23-generic root=UUID=b376dfc3-16fc-4a32-ab36-1f0a6aed44aa ro   quiet splash
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /vmlinuz-2.6.35-23-generic root=UUID=b376dfc3-16fc-4a32-ab36-1f0a6aed44aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b376dfc3-16fc-4a32-ab36-1f0a6aed44aa ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=b376dfc3-16fc-4a32-ab36-1f0a6aed44aa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set dc36dc4c-7972-476f-b07a-3f08c43cd156
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b0b691f7b691bdf2
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

=================== sda5: Location of files loaded by Grub: ===================


  86.0GB: grub/core.img
  86.0GB: grub/grub.cfg
  85.9GB: initrd.img-2.6.35-22-generic
  85.9GB: initrd.img-2.6.35-23-generic
  85.9GB: vmlinuz-2.6.35-22-generic
  85.9GB: vmlinuz-2.6.35-23-generic

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=b376dfc3-16fc-4a32-ab36-1f0a6aed44aa    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda5 :
UUID=dc36dc4c-7972-476f-b07a-3f08c43cd156    /boot    ext3    defaults    0    2
#Entry for /dev/sda10 :
UUID=fafc6b13-8963-4f41-8cab-746428a29f8d    /data    ext3    defaults    0    2
#Entry for /dev/sda6 :
UUID=6F3A-3122    /dos    vfat    utf8,umask=007,gid=46    0    1
#Entry for /dev/sda1 :
#UUID=B0B691F7B691BDF2    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda2 :
UUID=5062A06A62A0570E    /windows/C    ntfs    defaults,umask=007,gid=46    0    0
#Entry for /dev/sda7 :
UUID=81a301a5-65bc-4c4e-a21e-258715910910    none    swap    sw    0    0



```From the results I got, it seems that GRUB is not able to find core.img.  I have confirmed that the file is in the correct path (in sda5 under the grub folder).  Because of the partition resize I do not expect the file to be in the same sector of the hard disk, but I have no idea how to tell GRUB to look for it in a different sector.

I have been tempted to do an 'update-grub' and see what it does, although I do not think the intent of that command applies in my situation.  I could also try reinstalling GRUB, but I do not want to do anything rash and end up messing things up even more.  I would also prefer to keep NTLDR as master and avoid installing GRUB to the MBR.  Any thoughts?

In case it makes a difference, these are my system specifications:
- HP EliteBook 8540w
- Intel Core i7 820QM
- 8GB DDR3 RAM
- ATI FirePro M5800
- 500GB SATA HDD
- DreamColor 2 Display
- Windows 7 Professional x64
- Ubuntu 10.10 x64

Thanks,

Felix

By the way, [this thread]("http://ubuntuforums.org/showthread.php?t=1540694") seems related to my problem, but it is currently flying above my head and the final resolution was a reinstall of Ubuntu...

---

### Post by gordintoronto on 2010-12-29
I would reinstall Ubuntu, it's quicker than solving the problem.

---

### Post by wilee-nilee on 2010-12-29
Your paranoia of the MS needing to have its bootloader has left you where your at. You don't need a separate boot partition.

If you just remove that boot partition and purge and reload grub and load it to the mbr correctly it will work.

---

### Post by Priyantha Bleeker on 2011-01-04
Felix1701D, did you have a successfull installation of Ubuntu already ?
Because I can't even get my graphics up and running.
And I have the same laptop, also with the dreamcolor screen.
Mmmm I see that you've got a ATi card in it, I have the Nvidia FX1800...so that's a difference and I think a big one..

---

### Post by Felix1701D on 2011-01-06
> **wilee-nilee said:**
> Your paranoia of the MS needing to have its bootloader has left you where your at. You don't need a separate boot partition.

If you just remove that boot partition and purge and reload grub and load it to the mbr correctly it will work.

Thanks for the gentle nudge... :)  I did some reading on GRUB2 and I think I have a better understanding of why the installation of GRUB2 on a partition is problematic (the physical location of core.img being hardcoded in partition-based installations).  I am not sure I fully agree philosophically with the Linux bootloader behaving like the Windows bootloader in that sense, but that is beside the point...

For anyone else who might run into a similar problem on a system where a reinstall of Ubuntu would not be as "enjoyable," I was able to fix my booting problem in a few minutes without reinstalling Ubuntu by using the Ubuntu 10.10 CD in Live mode.  I opened a console, mounted my boot partition (sda5) at /mnt/boot, and reinstalled GRUB2 using grub-install with the force option, the root directory at /mnt, and the target at /dev/sda5.  After that was done I generated a new boot sector image file to be used by NTLDR (replacing the ubnt1010.lnx file noted in my boot script results).  I rebooted, and was able to load Windows 7 and Ubuntu without problems, as I had prior to the partition resize.

Having said that, since my installation of both OS's is still young and I have not settled-in yet, I may redo my partition layout this weekend to get rid of the boot partition and reinstall Ubuntu with GRUB2 in the MBR as recommended.


> **Priyantha Bleeker said:**
> Felix1701D, did you have a successfull installation of Ubuntu already ?
Because I can't even get my graphics up and running.
And I have the same laptop, also with the dreamcolor screen.
Mmmm I see that you've got a ATi card in it, I have the Nvidia FX1800...so that's a difference and I think a big one..     

Hi Priyantha.  My installation of Ubuntu went without major problems.  It was easier than I expected after reading some of the compatibility reports.  The only issue I had was a scrambled display when booting from the installation CD just prior to the part where the Try/Install graphical window appears.  This scrambling of the display was temporary though and corrected itself in a few seconds.  

In the installed system I still experience this scrambling occasionally just prior to the log-in screen and a reboot takes care of it (I have not researched how to restart just the graphics server or equivalent; in OpenSuSE I can do that pressing Ctrl-Alt-Backspace twice).  I had the fan-always-on problem noted [in this page]("http://www.linlap.com/wiki/hp+elitebook+8540w").  I solved it by adding the following line:

```
echo disable > /sys/firmware/acpi/interrupts/gpe01
```to /etc/rc.local as noted in the Summary on that page.

Hardware-wise, I have not yet confirmed what works and what does not.  So far all of the basics appear to be working.  I have not checked camera, fingerprint scanner, etc.  Some minor annoyances I need to look into are the switch from a graphical boot splash screen to an ugly text version of it after installing the proprietary ATI drivers, a seemingly random switch in the theme from the normal dark gray "contemporary" look to a bland light gray theme, and the occasional disappearance of the power button on the task bar.  I suspect none of these have to do with the computer hardware itself though...

---

