---
title: "Grub issue when running Ubuntu on External Drive on a different system"
date: 2011-09-19
forum: General Help
---

### Post by rickygarg on 2011-09-19
Hi all, this is my first post in this forum and I hope you will forgive me if I am breaking any forum rules. 

I installed Ubuntu 11.04 on my external hard drive without issue. Grub was installed on the external drive itself such that the Grub screen only appears when I boot from my USB HDD. All this works beautifully on my laptop.

Now, when I try to boot from USB on another computer, Grub opens up with a 'grub rescue' prompt. Can anybody help me setup grub so that I can boot on any system using my external hard drive?

I found a thread on a similar topic, where no problems were reported in achieving this. Since the thread is quite old, I decided to create a new one. 

Thanks!

---

### Post by Bodsda on 2011-09-19
> **rickygarg said:**
> Hi all, this is my first post in this forum and I hope you will forgive me if I am breaking any forum rules. 

I installed Ubuntu 11.04 on my external hard drive without issue. Grub was installed on the external drive itself such that the Grub screen only appears when I boot from my USB HDD. All this works beautifully on my laptop.

Now, when I try to boot from USB on another computer, Grub opens up with a 'grub rescue' prompt. Can anybody help me setup grub so that I can boot on any system using my external hard drive?

I found a thread on a similar topic, where no problems were reported in achieving this. Since the thread is quite old, I decided to create a new one. 

Thanks!

When do you get the grub rescue prompt, before or after seeing the list of boot options from grub?

If grub is identifying your external drive by device name/number (e.g:root=hd(0,1)) instead of UUID, it wont work on another system 

It might be helpful to paste the contents of your /etc/default/grub file

Thanks,
Bodsda

---

### Post by rickygarg on 2011-09-19
I do not see the GRUB menu when I boot my external drive on another system (I see the menu and successfully boot on the system I installed in). As soon as I boot from my external HDD, I see the grub rescue prompt. 

Here are the contents of the /etc/default/grub file:
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Also, here's a  menu entry from grub.cfg

```

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e3e03a11-028d-4795-90af-0b470f0c0140 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}

```

---

### Post by drs305 on 2011-09-19
When you are running Ubuntu following a normal boot, you should be able to 'code' Grub into that device's MBR and have it look for the Grub files on the same device, making it independent.
```

sudo grub-install /dev/sdX
```
with X being the same (external) drive. (Example: sudo grub-install /dev/sdb)

Once you do that, as long as any computer you connect it to should boot Ubuntu provided BIOS boots the external drive first.

If this doesn't happen, please download/extract/run the boot info script and post the contents of RESULTS.txt  This file will show us how your boot files are configured. Click on the "BIS" link in my signature to take you to the script's page.

---

### Post by rickygarg on 2011-09-19
> **drs305 said:**
> When you are running Ubuntu following a normal boot, you should be able to 'code' Grub into that device's MBR and have it look for the Grub files on the same device, making it independent.

Grub was always installed on my external hard drive itself. So does that mean that I need to have it look for the files on the same device? If so, will simply reinstalling grub achieve this or do I also have to make any config changes?

In any case, I have installed Grub on /dev/sdb (my external drive) following your instructions but I will only be able to test this later when I have access to another computer. Thanks for the help. I will post the results.

---

### Post by drs305 on 2011-09-19
We would have to see the RESULTS.txt but if the external Grub originally pointed to an Ubuntu installation on another drive it would explain why it didn't work when you changed computers.

If you are running the OS on the external druve and then update grub it will now point to the files you are currently using (i.e. the Ubuntu installation on the external drive). In that case, you should be able to boot it from any computer that boots your external drive first.

---

### Post by rickygarg on 2011-09-20
Please find my RESULTS.txt file below:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/bcd

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    13,367,295    13,365,248  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     13,367,296   312,579,759   299,212,464   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   281,744,064   281,744,002   7 NTFS / exFAT / HPFS
/dev/sdb2         281,745,406   312,580,095    30,834,690   5 Extended
/dev/sdb5         308,408,320   312,580,095     4,171,776  82 Linux swap / Solaris
/dev/sdb6         281,745,408   304,234,495    22,489,088  83 Linux
/dev/sdb7         304,236,544   308,400,127     4,163,584  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3A7C690D7C68C56B                       ntfs       Recovery
/dev/sda2        F4CA6C34CA6BF0F2                       ntfs       
/dev/sdb1        55D123D9E79ABF54                       ntfs       OneTouch4 Mini
/dev/sdb5        687ba950-5097-4904-be6f-19fd29371945   swap       
/dev/sdb6        e3e03a11-028d-4795-90af-0b470f0c0140   ext4       
/dev/sdb7        62a283a0-8db4-44e7-80fc-f7879b53e3df   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/OneTouch4 Mini    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/My Disc           iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos6)'
search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e3e03a11-028d-4795-90af-0b470f0c0140 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e3e03a11-028d-4795-90af-0b470f0c0140 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos6)'
    search --no-floppy --fs-uuid --set=root e3e03a11-028d-4795-90af-0b470f0c0140
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
#menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
#    insmod part_msdos
#    insmod ntfs
#    set root='(/dev/sda,msdos1)'
#    search --no-floppy --fs-uuid --set=root 3A7C690D7C68C56B
#    drivemap -s (hd0) ${root}
#    chainloader +1
#}
#menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
#    insmod part_msdos
#    insmod ntfs
#    set root='(/dev/sda,msdos2)'
#    search --no-floppy --fs-uuid --set=root F4CA6C34CA6BF0F2
#    chainloader +1
#}
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=62a283a0-8db4-44e7-80fc-f7879b53e3df none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.749855042 = 148.981522432  boot/grub/core.img                             1
 142.602058411 = 153.117794304  boot/grub/grub.cfg                             1
 135.350803375 = 145.331818496  boot/initrd.img-2.6.38-8-generic               2
 138.749328613 = 148.980957184  boot/vmlinuz-2.6.38-8-generic                  1
 135.350803375 = 145.331818496  initrd.img                                     2
 138.749328613 = 148.980957184  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```Please note that I removed the entries that pertain to my Windows 7 on my internal hard drive in grub.cfg but that didn't help (I didn't break anything, just commented off the win 7 entries and everything still works as before). I am guessing that my hard drive is not recognized as 'sdb6' on another pc which is causing this issue?

---

### Post by drs305 on 2011-09-20
The problems are arising from the "/dev/sdb,msdos6" designations that are contained in the header section of the grub.cfg file. Does you second computer have more than one drive in it?

Even though Grub 2 uses UUIDs, these are incorporated in the menuentries but not the sections preceeding these entries. In your case, the drive is hard coded in G2 as sdb6 in the 00_header section. If the drive isn't sdb6 in the second computer it never gets to the menuentry (which would work since it uses UUIDs).

As a test, in the second computer, at the grub rescue prompt, you should be able to boot it with the following commands. Substitute the drive number for X:
```
set root=(hd**X**,6)
set prefix=(hd**X**,6)/boot/grub
insmod normal # Load the 'normal' module
normal  # Should bring up your normal Grub menu.
```

One workaround might be to get your second computer's BIOS to report the external drive, when connected, as the second drive in priority. This should then designate your Ubuntu drive as sdb and I believe the external would then boot.

---

### Post by rickygarg on 2011-09-20
When using ls command on grub rescue, I can see that X is 1 for the external hard drive. By running the commands given below (using hd1,6 and hd1,msdos6 in different attempts), I get the error when I execute 'insmod normal'. Error: Unknown Filesystem

If I designate this drive as second drive in priority, the BIOS boots the first drive instead. 

If there is a way to remove hardcoding from grub.cfg, that may be helpful?

---

### Post by YesWeCan on 2011-09-20
I don't think the problem is grub.cfg because of the appearance of grub-rescue. The bootinfoscript looks ok to me, the "/dev/sdb,msdos6" is irrelevant as it is faulty anyway (there is a bug in update-grub: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/820500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/820500)) and it is superseded by the search directive. 

The rescue prompt occurs when the Grub boot program in the MBR area is unable to find the /boot/grub directory. I notice that the root partition starts 144GB into the external drive so it is possible that the cause is that the host PC has an old BIOS that has a 137GB limit for finding partitions. If grub.cfg were the problem then I would expect to see a grub> prompt.

The fix would be to move the location of the /boot/grub directory nearer to the start of the external drive or, possibly, to upgrade the BIOS firmware in the host PC.

@rickygarg: what motherboard have you got in the host PC?

---

### Post by drs305 on 2011-09-20
[COLOR="DarkRed"]Edit Added: I think YesWeCan has come up with the issue. If so, the section below won't work. What you can try from the grub rescue prompt is to "ls (hd1,6)/boot/grub". Does it see any of the *.mod files. If not, this would strengthen the case of a BIOS limitation.[/COLOR]

> **rickygarg said:**
> When using ls command on grub rescue, I can see that X is 1 for the external hard drive. By running the commands given below (using hd1,6 and hd1,msdos6 in different attempts), I get the error when I execute 'insmod normal'. Error: Unknown Filesystem
After running the 'root' and 'prefix' commands it looks like you are going to have to load the 'ext' module
```
insmod ext2
insmod linux

```
> 
If I designate this drive as second drive in priority, the BIOS boots the first drive instead. 
The reason it's doing this may be because it considers the first (Ubuntu) drive as unbootable, although I would have thought it should use the Ubuntu MBR and proceed to a grub rescue prompt (at worst).

> 
If there is a way to remove hardcoding from grub.cfg, that may be helpful?

I haven't dealt with this issue before, so I'm still learning. I'm a bit disappointed G2 is still bound by the "sdX" device designations. I'm going to study up, do some testing (including using the 'search' command), and try to come up with something.

---

### Post by rickygarg on 2011-09-20
> **YesWeCan said:**
> 

@rickygarg: what motherboard have you got in the host PC?

Intel G41 Chipset motherboard (System: Lenovo ThinkCentre 0864E4Q)

---

### Post by drs305 on 2011-09-20
YesWeCan,

For some reason your post didn't show up prior to my last post.

You have hit on something with the 137GB limit, in that the other computer may not be able to recognize it. That would explain it and I'd place a bet this is the cause. And by "seek", I assume you refer to the "search" line.

I was looking at the wrong tree in the forest. Thanks.

---

### Post by YesWeCan on 2011-09-20
> **drs305 said:**
> YesWeCan,

You may have hit on something with the 137GB limit, in that the other computer may not be able to recognize it. That would explain it. And by "seek", I assume you refer to the "search" line.

I was looking at the wrong tree in the forest. Thanks.
It's a dark forest. :)
Yes, I meant "search" sorry. It turns out that the preceding "set root='(/dev/sdb,msdos6)'" does nothing at all because Grub's interpreter doesn't understand it. There is a mistake in the program that generates grub.cfg. It is supposed to be of the form '(hdX,Y)'. In any case, the "search" directive finds the root by UUID. The latter would also fail, of course, if the new host was already using the same UUID but this is extremely unlikely.

---

### Post by YesWeCan on 2011-09-20
@drs305 Have you got a process already documented for relocating /boot to the front of a drive?

---

### Post by drs305 on 2011-09-20
> **YesWeCan said:**
> @drs305 Have you got a process already documented for relocating /boot to the front of a drive?

I can give you a definitive answer - no.... but sort of. I wrote a guide for expanding / by taking away space from Windows. At at the bottom of the first post there is a link to a good piece by *srs5694* that explains the same process (only better).

In the current case, it looks like space is going to have to be taken by Windows. The thread covers how to do that. It doesn't cover a separate /boot.

If I had to do it, the way I'd prefer is:
Windows 120GB
Ubuntu 10-15GB
Data the rest

If Windows on this drive needs as much space as possible:
Windows: 130GB
/boot: 1GB
/ : the rest, or split with a data partition.


How to shrink the Windows partition:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

I think I've detailed how to create a separate /boot somewhere. I'll try to find it.

---

### Post by drs305 on 2011-09-20
Here are the notes I took when I created a separate /boot on my own machine back in Natty for testing purposes.

[noparse]Running Ubuntu  (new /boot partition is on sda8) after a new boot partition has been created with Gparted or another application.[/noparse]

The first command allows you to run as root. *sudo* isn't required until after the 'exit' command. These commands label the new boot partition ("boot"), copy the current /boot files to the new partition, then install grub and update it. Finally, it adds a new entry for the separate /boot partition to fstab.

```

sudo -i                                # Run commands as root
tune2fs -L boot /dev/sda8              # Label boot partition
mkdir /mnt/newboot                     # Create temporary partition
mount /dev/sda8 /mnt/newboot           # Mount new boot partition on /mnt/newboot
cp -pr /boot/* /mnt/newboot            # Copy current /boot contents to new boot partition
umount /dev/sda8                       # Unmount new boot
mount /dev/sda8 /boot                  # Mount new boot over existing /boot
grub-install /dev/sda                  # Update grub 
update-grub                            # Update grub
umount /dev/sda8                       # Unmount new boot from /boot
a=`blkid -s UUID -o value /dev/sda8`   # Get UUID
echo "UUID=$a /boot ext4 defaults,exec 0 1" | tee -a /etc/fstab	# Create fstab entry for separate /boot
cat /etc/fstab                         # Display fstab
exit                                   # Exit root

```

This process leaves the original /boot files intact. They will be hidden when the /boot partition is mounted on top of them.

---

### Post by YesWeCan on 2011-09-20
I'm thinking of how to simplify it for rickygarg.
One thing is that I would not use GParted to move the start of the Windows partition because it will break the boot sector code which uses absolute sector addressing. Instead, I'd suggest booting Windows and using its Disk Manager to move it. I assume Windows will move it without breaking it.

Current situation:
```
sdb1   Windows   144GB
sdb2   extended partition (container)
sdb5   swap 2GB
sdb6   Ubuntu 12GB
sdb7   swap 2GB
```

Suggested arrangement:
```
sdb3   boot      1GB
sdb1   Windows   143GB
sdb2   extended partition (container)
sdb5   swap 2GB
sdb6   Ubuntu 12GB
sdb7   swap 2GB
```

---

### Post by drs305 on 2011-09-20
I absolutely agree about using a Windows partitioning tool for altering any windows partition. I mention it in the resizing guide but probably should have emphasized it here as well.

---

### Post by YesWeCan on 2011-09-20
> **drs305 said:**
> I absolutely agree about using a Windows partitioning tool for altering any windows partition. I mention it in the resizing guide but probably should have emphasized it here as well.
Worth mentioning again, I think. It's tempting to use GParted for everything but it may end in tears sometimes. I've not tried to move the start of a Windows partition before so I'll try it out in Windows 7 in VirtualBox and post my process here in a little while. :)

---

### Post by YesWeCan on 2011-09-20
Unfortunately, no. Windows will shrink itself ok but won't move its start. A little too much to expect in hindsight.

Alternative arrangement:
```

sdb1   Windows   130GB  [COLOR="Red"](shrink it)[/COLOR]
sdb3   boot  1GB    [COLOR="red"](make sure it is immediately after sda1 so it is well before the 137GB limit)[/COLOR]
sdb2   extended partition (container)
sdb5   swap 2GB
sdb6   Ubuntu 12GB
sdb7   swap 2GB
```

---

### Post by drs305 on 2011-09-20
> **YesWeCan said:**
> Unfortunately, no. Windows will shrink itself ok but won't move its start. A little too much to expect in hindsight.

Another minor victory for Linux. :guitar:

---

### Post by YesWeCan on 2011-09-20
To be fair (I suppose we ought to be) linux won't allow moving itself unless unmounted. I haven't tried moving the external drive partition using Windows on another drive - a little too tedious to set up.

@rickygarg  Probably best for you to say want you want to do now and whether you need that sdb1 partition or not, before we go too much further.

---

### Post by rickygarg on 2011-09-21
> **drs305 said:**
> [COLOR="DarkRed"]Edit Added: I think YesWeCan has come up with the issue. If so, the section below won't work. What you can try from the grub rescue prompt is to "ls (hd1,6)/boot/grub". Does it see any of the *.mod files. If not, this would strengthen the case of a BIOS limitation.[/COLOR]


After running the 'root' and 'prefix' commands it looks like you are going to have to load the 'ext' module
```
insmod ext2
insmod linux

```  



Okay, I'll try this first before going through what is mentioned below. I have been trying to find out if Intel G41 Chipset motherboard has such a limit but haven't struck anything yet. It is worth a note that my laptop (vaio vgn-sz-460n) is a 2007 model and the other computers I have tried running this on were purchased less than 2 months ago.

> **YesWeCan said:**
> Unfortunately, no. Windows will shrink itself ok but won't move its start. A little too much to expect in hindsight.

Alternative arrangement:
```

sdb1   Windows   130GB  [COLOR="Red"](shrink it)[/COLOR]
sdb3   boot  1GB    [COLOR="red"](make sure it is immediately after sda1 so it is well before the 137GB limit)[/COLOR]
sdb2   extended partition (container)
sdb5   swap 2GB
sdb6   Ubuntu 12GB
sdb7   swap 2GB
```



> **YesWeCan said:**
> To be fair (I suppose we ought to be) linux won't allow moving itself unless unmounted. I haven't tried moving the external drive partition using Windows on another drive - a little too tedious to set up.

@rickygarg  Probably best for you to say want you want to do now and whether you need that sdb1 partition or not, before we go too much further.

Let me point out that the sdb1 partition doesn't have windows installed on it. It is, however, a ntfs partition which is good for accessing files both on windows and linux. I am happy to shrink this to 130 GB but am unsure how to move the linux partitions safely. I will post an update when I have the chance to follow drs305's instructions on ls (hd1,6)/boot/grub. If we can confirm that this is really a BIOS issue, then only I will proceed with rearranging the partition.

On a separate note, I may be missing the crux of this discussion, but that fact that my BIOS is able to find GRUB on my external hard drive (and therefore throw the grub rescue prompt) means that 137 GB limitation is not the issue? If anything, it should be about GRUB's ability to find the partition in the external hdd?

---

### Post by YesWeCan on 2011-09-21
> **rickygarg said:**
> Let me point out that the sdb1 partition doesn't have windows installed on it. It is, however, a ntfs partition which is good for accessing files both on windows and linux. I am happy to shrink this to 130 GB but am unsure how to move the linux partitions safely. I will post an update when I have the chance to follow drs305's instructions on ls (hd1,6)/boot/grub. If we can confirm that this is really a BIOS issue, then only I will proceed with rearranging the partition.
This makes it much simpler. As the partition is not actually bootable you can use GParted in Ubuntu to shrink it by 1GB or so and move it to the right. Then insert a ext4 partition of 1GB or so just before it (as per post #18). Once you've done this, then copy the /boot files to it and mount it in fstab. I'll provide instructions if you decide to do this.

> On a separate note, I may be missing the crux of this discussion, but that fact that my BIOS is able to find GRUB on my external hard drive (and therefore throw the grub rescue prompt) means that 137 GB limitation is not the issue? If anything, it should be about GRUB's ability to find the partition in the external hdd?

Grub comes in 3 main parts:
1. Grub MBR boot code (about 440 bytes in sector 0 of the disk)
2. Grub kernel (about 25kB in sectors 1 to about 50, in an "unused" gap just before the first partition)
3. Grub config file and modules (in /boot/grub, usually in the Ubuntu root partition)

Part 1 uses the BIOS to load part 2 and part 2 uses the BIOS to load part 3. If the BIOS won't load above 137GB and the part 3 files are located above 137GB then part 2 will fail and you'll see a rescue prompt. You would also see a rescue prompt if the partition it was looking for didn't exist of it the part 3 files were missing. Frustratingly, grub doesn't report why it failed. The other failure mode is simply a grub> prompt and this happens when the part3 files are found ok but the grub.cfg file is unusable for some reason.

In your case we know that parts 1, 2 and 3 work fine when you plug the external drive into your laptop. When you plug it in to the desktop part 2 cannot find part 3. The only possible cause that I can think of is that the desktop BIOS has the 137GB restriction. We can see from the bootinfoscript output that the part 3 files are above 148GB. So this is the most likely culprit at the moment.

---

### Post by YesWeCan on 2011-09-21
GParted guide: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

