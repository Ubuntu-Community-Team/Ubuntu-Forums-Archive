---
title: "can't boot, grub file needs Windows"
date: 2011-11-04
forum: General Help
---

### Post by ubscott on 2011-11-04
Hi,

I installed Ubuntu 64 bit server on a new Windows 7 machine.  During the installation, Ubuntu asked me if I wanted to install the grub on the first partition.  After wavering, I chose to do it.

Now when I boot up the PC Ubuntu begins to load.  It then asks me for my user name and password.  Upon supplying both, it takes me to a command prompt.  I never see the Ubuntu desktop.

I've been trying to figure out how to change the grub file so that it includes Windows.  However, I don't have the menu.lst file that other people are talking about.  (I guess this means I have grub2.)

I have found this page:
[http://forums.parsix.org/viewtopic.php?t=879](http://forums.parsix.org/viewtopic.php?t=879)

I tried these commands:
apt-get install os-prober
os-prober
update-grub2

Reboot.  Same thing.  Linux boots and then I'm prompted for my username and password.  I never see the grub options and I never get to the GUI.

Does anyone have any ideas about how I can see a grub file, add Windows to the list and also boot up to the Ubuntu server GUI?  thanks.

---

### Post by wojox on 2011-11-04
Try:

```
sudo update-grub
```

There is no GUI for the server edition.

---

### Post by oldfred on 2011-11-05
If Windows is in the first partition and you installed grub to that partition, you are booting grub thru the Windows partition with the Windows boot loader and have overwritten all the Windows boot code in the Windows NTFS partition.

Post this to confirm.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

If so, you need to reinstall grub2's boot loader to the MBR, then use testdisk to restore the PBR- partition boot sector. NTFS partition keep a backup of the boot sector that testdisk can recover if it is still good.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
Also check for /boot/grub in addition to /Boot

---

### Post by prodigy_ on 2011-11-05
> **wojox said:**
> There is no GUI for the server edition.

GUI can still be added with ```
sudo apt-get install ubuntu-desktop
``` command. But it's true that in most cases if you need a desktop you should simply install a desktop edition.

---

### Post by ubscott on 2011-11-05
Thanks for the help wojox, oldfred and prodigy.  

Wojox, unfortunately your tip didn't do anything helpful.  Prodigy, thanks big time for the help!  After a couple of hours my desktop has been installed and I can boot to it.  Oldfred, I plan to implement your suggestions the next chance I get.  I'll provide the requested information at that time.

Thanks again, and I'll return soon.

---

### Post by ubscott on 2011-11-05
Hi OldFred,

Thanks again for the help.  Here's my RESULTS.txt.

I will look at the rest of what you wrote probably within 24 hours.  

Thanks.



```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /grub.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

ubuntu-root': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-swap_1': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096       503,807       499,712 Data partition (Windows/Linux)
/dev/sda3         503,808 3,907,028,991 3,906,525,184 Logical Volume Manager (LVM) partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 8c7c21cb-0d00-462d-8f9f-46b50cb57000   swap       
/dev/mapper/ubuntu-root 2f43bccf-91e6-4749-90e5-72d0364e04dc   ext4       
/dev/sda2        b189ef0b-3d90-4459-a175-14422f2a2dd1   ext2       
/dev/sda3        pXR0l5-h6XB-fBJe-EvPc-43Wp-RAtQ-cAB7cL LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1
cryptswap1_unformatted
ubuntu-root
ubuntu-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu-root /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /boot                    ext2       (rw)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod lvm
insmod ext2
set root='(ubuntu-root)'
search --no-floppy --fs-uuid --set 2f43bccf-91e6-4749-90e5-72d0364e04dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/ubuntu-root ro   quiet
    initrd    /initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/ubuntu-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.035759926 = 0.038396928    grub/core.img                                  2
   0.033776283 = 0.036267008    grub/grub.cfg                                  1
   0.037789345 = 0.040576000    initrd.img-2.6.32-24-server                   71
   0.007741928 = 0.008312832    vmlinuz-2.6.32-24-server                      17

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on ubuntu-root'


Unknown BootLoader on ubuntu-swap_1'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ubuntu-root': No such file or directory
hexdump: /dev/mapper/ubuntu-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ubuntu-swap_1': No such file or directory
hexdump: /dev/mapper/ubuntu-swap_1': No such file or directory



```

---

### Post by oldfred on 2011-11-06
Ignore the rest of my previous post. You have gpt partitioning because you have a 2TB drive. There was a bug with grub not being able to boot from very large partitions. Not sure but I normally suggest a 20GB / (root) partition and then partition the rest of the drive as /home and/or /data.

I would use gparted to shrink your / to 25 to 50GB and see it it then works. You may have to reinstall grub, but I doubt it. If it then works, you may want to repartition or reinstall with a smaller / partition.

I think since you have LVM you need this also, I know the script works better with it.

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
```
sudo apt-get install lvm2
```

---

### Post by ubscott on 2011-11-14
Hi oldfred,

Sorry for the delay in responding.  Something came up...

I still haven't accomplished the task of having a grub that enables me to choose between Linux server and the Windows 7 installation that came with the PC.

I used gparted and resized the boot partition.  The minimum had to be 95 GB.  I made it 120 GB.  

I had to unmount the boot partition before the options to resize were enabled.  Since doing this I have not found a way to mount it as it was before.

Also, I ran:
sudo apt-get install lvm2
sudo update-grub

Unfortunately, when I boot the PC I go directly to Ubuntu.  I still want to be able to choose Windows 7; but the option isn't present.

Also, when I am in Ubuntu and choose "Restart", the PC doesn't restart.  I have to turn it off and turn it on again.

I sure hope the Linux community figures out what to do about today's 2TB drives; since that's this minute's standard with new PCs.

All help is appreciated.  Thanks again for your help so far.

---

### Post by ubscott on 2011-11-14
BTW, here's my new results.txt:


```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    2048 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /grub.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

ubuntu-root': __________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

ubuntu-swap_1': ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096       503,807       499,712 Data partition (Windows/Linux)
/dev/sda3         503,808 3,907,028,991 3,906,525,184 Logical Volume Manager (LVM) partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 8c7c21cb-0d00-462d-8f9f-46b50cb57000   swap       
/dev/mapper/ubuntu-root 2f43bccf-91e6-4749-90e5-72d0364e04dc   ext4       
/dev/sda2        b189ef0b-3d90-4459-a175-14422f2a2dd1   ext2       
/dev/sda3        pXR0l5-h6XB-fBJe-EvPc-43Wp-RAtQ-cAB7cL LVM2_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1
cryptswap1_unformatted
ubuntu-root
ubuntu-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/ubuntu-root /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /boot                    ext2       (rw)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod lvm
insmod ext2
set root='(ubuntu-root)'
search --no-floppy --fs-uuid --set 2f43bccf-91e6-4749-90e5-72d0364e04dc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/ubuntu-root ro   quiet
    initrd    /initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /vmlinuz-2.6.32-24-server root=/dev/mapper/ubuntu-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set b189ef0b-3d90-4459-a175-14422f2a2dd1
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.035759926 = 0.038396928    grub/core.img                                  2
   0.033776283 = 0.036267008    grub/grub.cfg                                  1
   0.037789345 = 0.040576000    initrd.img-2.6.32-24-server                   71
   0.007741928 = 0.008312832    vmlinuz-2.6.32-24-server                      17

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on ubuntu-root'


Unknown BootLoader on ubuntu-swap_1'



========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ubuntu-root': No such file or directory
hexdump: /dev/mapper/ubuntu-root': No such file or directory
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/ubuntu-swap_1': No such file or directory
hexdump: /dev/mapper/ubuntu-swap_1': No such file or directory



```

---

### Post by oldfred on 2011-11-14
There is no Windows in the boot script. Is it on another drive?

Windows will not boot from a gpt drive unless you boot with UEFI which many new systems have. If booting from gpt with UEFI the very first partition must be an efi FAT32 partition. Windows may add another boot partition at the front of the drive after the efi partition. The bios_grub partition is not used but Ubuntu and it also installs its efi boot loader in the efi partition. But there are some bugs and Ubuntu usually overwrites the Windows efi partition.

---

### Post by ubscott on 2011-11-15
Oldfred, thanks again for the response.  I don't understand what you're saying.  I think you're suggesting that I create a new efi FAT 32 partition that is the "first" one.  I will do some research on what an efi FAT 32 partition is.  I need to figure out how this is done.

I must say I'm disappointed in Ubuntu 10.04 server so far.  I have successfully put Ubuntu stand-alone on two PCs, and the grub files for both enable me to choose between windows and Linux.  Unfortunately, 10.04 server is a different ballgame.

The installation program for Ubuntu 10.04 on my CD was really lame, and looked like it came from the early 1980s.  The installation program could have helped me avoid this problem.

Thanks again for the help so far.

---

### Post by oldfred on 2011-11-15
If you have UEFI, you need the very newest version as the old versions do not work with UEFI. 

I did start using gpt several versions ago, but with a BIOS system that then has to have a bios_grub partition of 1MB to install grub2 correctly.

The server install is the text based installer that does not have the graphical bells & whistles, but just installs the system. Servers often have no graphical system at all anyway, although new users often install one.

---

### Post by ubscott on 2011-11-20
Hi,

I appreciate OldFred's replies.  However, I can't make sense of what he is saying.  I've been reading (when time permits) about UEFI versus BIOS, and dual-booting and I do not know what I should try next.

My goal is to have the grub file enable me to choose between Windows 7 and Ubuntu server.  Currently when I boot I only go to Ubuntu.  Also, I don't know if this is a related problem, but when I attempt to restart through Ubuntu the PC shuts down and doesn't restart.

I started up GParted and it conveys this information about my drives:
partition: unallocated   
file system: unallocated   
size: 1.0 MiB

partition: /dev/sda1     
file system: unknown
size: 1.0 MiB 
flags: bios grub

partition: /dev/sda2     
file system: ext2 
mount point: boot   
size: 123.51 

partition: unallocated   
file system: unallocated   
size: 120.49 MiB

partition: /dev/sda3     
file system: lvm2          
flags: lvm2


Oldfred, you have been very helpful so far.  Do you have any suggestions about what I can do?  (Remember I'm a novice.)  Does anyone else?  

thanks in advance.

---

### Post by oldfred on 2011-11-20
I do not know about lvm as that is an advance partition scheme that gives a lot of flexibility as logical partitions then can overlap the physical.

If those are the only partitions you have you do not have Windows. Windows will only boot gpt if you are in UEFI mode, not BIOS and then the very first partition sda1 would be the efi partition with both grub & Windows boot loaders. (As I said before.)

If you installed Ubuntu to a bare drive or told it to use the entire drive, it would make the drive gpt as it is over 1TB. That seems to be the default now. If you told it to use the entire drive then it overwrote any and everything on the drive before.

---

### Post by ubscott on 2011-11-21
I am really angry at the Ubuntu server installation program for not making it more clear what my choices were.  Having had pleasant experiences installing Ubuntu client, I never believed that I would only be a wrong choice away from having Ubuntu server completely overwrite my Windows installation.  

I tried to use the Windows emergency disk and it doesn't recognize the factory-installed backup.  I now would like to reinstall Windows 7.

I would like to install Windows 7 and KEEP my Linux installation.  When I put the Windows setup CD in the drive, it asks me which drive to install it in:

Disc 0 Partition 1  1.0MB Free: 0MB  Primary
Disc 0 Partition 2  123MB Free: 123MB  Primary
Disc 0 Unallocated  120MB Free: 120MB
Disc 0 Partition 3  1862GB Free: 0.0 MB Primary

The 120MB that is unallocated looks pretty tempting.  However, before I reinstall anything I have a few questions:

a. Why does it say that Partition 3 has 0.0 MB free?  (There should be nothing on it.  It seems scary that it shows 0.0 MB free.)

b. If Partition 3 is LVM, does that mean Windows and Linux can (or cannot) write to it?

c. Based on my previous post, is my Linux installation on /sda2?  (Is that what "mount point" and "boot" signify?)

d. If the Linux installation is on sda2, does that correspond with what Windows calls Partition 2 which is 123MB in size?

By the way, when my PC starts up it says "hit <del> to start EFI BIOS".

Finally, I appreciate your help, Oldfred.  I regret that I have had some difficulty understanding what you have said.  However, it isn't your fault; you've been very helpful.

thanks in advance.

---

### Post by oldfred on 2011-11-21
Doing a server install, dual booting, and choosing drive partition formats on large drives is more advanced. You will need to review & understand many options. It may be best for you to go back to the old BIOS/MBR boot and install Windows. Anything else is more advanced. See below.

Windows only installs to NTFS primary partitions with the boot flag with MBR/BIOS configuration. It looks like it sees the gpt drive and is trying to install in UEFI mode.  Windows will install to gpt disks if you are booting with UEFI, but the efi partition has to be first and a Windows boot partition has to be second.

But you have installed Ubuntu to a gpt partitioning scheme with BIOS boot.

You cannot boot Ubuntu in BIOS mode and Windows in UEFI mode. Many seem to have issues getting grub to install correctly in UEFI mode, but it is my understanding that it is best to install Ubuntu first, then Windows if using UEFI. This is just opposite of the standard recommendation of BIOS mode where you should install Windows first.

But in all cases starting from scratch, you have to know if you want to use UEFI or BIOS to boot, then gpt or MBR for partitioning and then plan all the necessary partitions. 

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
above was this:
[http://grub.enbug.org/TestingOnUEFI](http://grub.enbug.org/TestingOnUEFI)

---

### Post by ubscott on 2011-11-23
Thanks for the additional information, Oldfred.  As Txgiving is tomorrow I need some time before I have read what you recommend.  However, I want you to know I appreciate your patient replies.

best,

---

### Post by ubscott on 2011-11-28
Hi Oldfred,

I've looked over the documentation you provided.  Do you see anything wrong with the strategy of:

1. resizing the first partition to 40 GB.
2. setting the boot flag for it.
3. making sure it is of type NTFS.
4. Installing Windows in this partition, letting Windows create the System and MSR drive partitions (which I assume are created within the larger partition).

My goal would be to have windows in the first partition with the boot flag set there; and keep intact the second partition with my installation of Linux server.
 
Would the grub file be able to see both Windows and Linux if I did it this way?

thanks,

---

### Post by oldfred on 2011-11-28
If you just had MBR(msdos) that would work. But I think you still have gpt. Windows will not work with gpt unless you have UEFI booting not BIOS. That depends on your motherboard and very new Intel i3, i5 & i7 based BIOS usually have UEFI & BIOS as a legacy way to boot. Older system only have BIOS.

But you may be able to convert from gpt to msdos depending on your current partitions:

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

### Post by ubscott on 2011-11-29
Hi Oldfred,
 
I appreciate again your patient replies.
 
If UEFI and GPT are the new standards, it doesn't seem logical for me to convert back to msdos.
 
How does this sound for a solution?  I can reformat my disk completely.  Then install Windows 7.  Afterwards, I can try installing Ubuntu server again.  When the installation program reaches the point where it is asking me the crucial question of whether to write to the partition that it already knows (which will be Windows), I can make sure I answer the question correctly (by saying NO!!!!).  Alternatively, I can ask this forum what choice(s) to make when these cryptic Ubuntu questions pop up.
 
I'm thinking that if Windows is installed on the first partition, and Ubuntu creates a second one, that the grub file will recognize both and I'll be able to dual-boot.  Afterwards, I can resize the Windows and Linux partitions as needs arise.
 
Does this seem sensible?
 
thanks,

---

### Post by oldfred on 2011-11-29
That should work. But then it may be best to just use MBR(msdos). 

Windows will actually install to two primary partitions as it creates a 100MB boot/repair partition (hidden) and the main install. If you create a NTFS partition with the boot flag, it will install to one partition. Or it has to have unallocated space on the drive and an available primary partition.

Then you can install Ubuntu & swap. I would also suggest another (d: in windows) NTFS partition for shared data as it is best not to directly write into the Windows system partition. It can be primary or logical.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Lots of good info on dual boot installs:
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by ubscott on 2011-12-10
Hi OldFred, I have resumed the task of dual-booting Windows 7 and Ubuntu server.

I have reinstalled Windows 7.  The install program didn't give me any options but to delete all existing partitions and create a new one for it.

I have downloaded Ubuntu 11.10 server 64 bit.  I am running through the install program.  Here's the first question that I am wondering what is a good answer to:

```

If you choose guided partitioning for the entire disk you will be next asked which disk.

Partitioning method:
Guided - use entire disk.
Guided - use largest continuous free space
Guided - use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM.

```

My preference would be the last one.  I would like to have the encryption.  However, am I risking erasing the Windows install?

thanks,

---

### Post by oldfred on 2011-12-10
Anything that says use entire disk is just that, it will erase disk and use all of it.

Encryption adds a level of complexity. If a portable, it may be a good idea. Not sure if you need to encrypt the entire drive, but just /home or even just a data partition? I have not used encryption. Backup is even more important as recovery tools will not work on encryption.

You should use Windows partitioning tools to shrink Windows but not to create any new partitions as it may convert to dynamic which does not work with Ubuntu (or even some Windows repair tools.).

I always prefer to partition in advance with gparted, so I know the sizes of the partitions, but now you can do it as part of the install. The installer does not have the NTFS driver so you cannot create a shared  NTFS partition as part of the install. Leave space or partition in advance.

---

### Post by larrypg on 2011-12-10
Hello, 

Although oldfred is the expert here is what I would do.

For starters I am not sure that you actually need a server version.  You mentioned that things looked like back in the 1980's which tells me that you are not comfortable with the command line.  

I have a 2 TB drive so have some experience with that size.  

First I would download and burn a regular version of K,X,L,Ubuntu.  I would then install Win 7 and let it take over the whole disk.  I would use regular MBR(msdos).  

I would then defrag the disk a few times just to make sure that everything is grouped together.  I would then use Win7's disk utility to shrink the drive to lets say 1.5 Tb.  I would then make the other 500 g as an extended partition.  

The next thing I would do is boot the cd or usb of ubuntu and shoose install.  At some point you will be asked if you want to install along side or the whole disk or depending on the version something else.  Choose the manual install which is what something else is.

You have plenty of space so I would make a 50g logical partition and make it /.  I would then make a logical swap partition the size of your ram and would make the rest a logical partition /home.  The / and /home partitions should be ext4.

When asked where grub should be installed I would suggest to the MBR of sda.  Not withstanding potential video driver problems (not related) you should be good to go.

---

### Post by oldfred on 2011-12-11
Some good advice from larrypg. 

If you do want server version you can and if a new user should install a gui until comfortable with command line. Or you can install desktop and add the server software. Ubuntu is all the same with different default packages installed, depending on version you install. You can easily add or subtract packages after you have installed.

---

### Post by ubscott on 2011-12-13
Thanks, Larry and Oldfred.  I appreciate the help so far.  Unfortunately, i'm now in a dreadful state.

I downloaded the 64-bit, 11.10 desktop version of Ubuntu and made a CD.  I was unable to get the PC to boot to it.  I went into what I believe is UEFI and made the CD drive the only drive that can boot.  I restarted and kept on seeing an error that kept asking me to insert a valid boot device.  (It wouldn't read the CD.)

Then, I changed to the beginner view of the boot software (UEFI or Bios).  I saw a graphical display of my CPU and other neat images.  At the bottom was a graphical way of changing the boot order.  I kept CD as the first, made what I think was my hard drive second and a smart reader third. Saved and restarted.

Now the PC won't even boot.  When I turn it on I don't see anything show up on the monitor.  I've checked the cabling many times.  

My experiences with Linux are always like a roller coaster.  You are either on the verge of complete despair trying to solve a vexing problem or it is working, and you know sheer bliss.  There is no flat-land in the Penguin's world.

I sure hope I can get this thing to boot.  Again, sincere thanks for the help.

---

### Post by asvestomix on 2011-12-13
I don't have a motherboard that has UEFI so i dont know how things are there but since it is more advanced and makes things complicated assuming that your goal is just a normal dual boot with Windows 7 and Ubuntu desktop, Then i see no point using it and i would recommended to you to switch back to normal BIOS like the most people do in that case.

---

### Post by ubscott on 2011-12-14
Hi asvestomix, when you say "switch back to normal BIOS" what do you mean?  How do I switch between UEFI and BIOS?
 
At the moment when I turn on the PC I don't see anything at all, not even a "press <del> to enter [BIOS/UEFI]."
 
I think I'm going to have to send it out to get repaired.  That sucks.  
 
thanks,

---

### Post by asvestomix on 2011-12-14
Try clear the cmos, there should be a reset button on your motherboard.. if not then unplug the power and remove the battery for 2 minutes the place it back and your settings should be reseted

---

### Post by oldfred on 2011-12-14
I do not know a lot about UEFI, but have been saving links as I want a new system next spring/summer that will be UEFI.

Are you sure the CD was burned correctly, that would account for many errors. Do you have any known working bootable CD or another system to test that CD boots. I stopped using CDs and only use USB flash drives now as I can reuse them.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

---

### Post by ubscott on 2012-02-05
Hello, sorry for the delay.  I sent the PC back to the manufacturer and they replaced the motherboard.  Then I dealt with a few personal issues.  

However, last night I successfully installed Ubuntu 11.10 desktop on it and I am very happy!  I like the simplicity of installing the desktop version versus the server version.  Also, unlike Windows Server, it appears that desktop version of Ubuntu will take care of my needs for now.

Thanks to oldfred, asvestomix, larrypg, wojox, prodigy and everyone else for all the help.  (I'm particularly grateful to oldfred.)

Ubuntu rocks.  Thanks again!

---

### Post by oldfred on 2012-02-05
Glad it is working. 

Did you end up going back to BIOS/MBR partitioning to dual boot or did Windows install in UEFI mode?

---

### Post by ubscott on 2012-02-05
Windows installed in UEFI.  So far UEFI is very strange, because it does not appear to be willing to boot from a CD.  When I go into the control console, it lists boot devices.  It sees the CD drive, but refers to it as a "legacy boot device."  

I ended up putting Ubuntu on a flashdrive and it booted just fine from it.

So far I like 11.10.  I know a lot of Linux pros around here think it is kid stuff, but I kind of like the immediate satisfaction those icons give you.

---

