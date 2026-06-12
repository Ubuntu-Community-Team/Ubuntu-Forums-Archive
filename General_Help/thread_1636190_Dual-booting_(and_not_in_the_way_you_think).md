---
title: "Dual-booting (and not in the way you think)"
date: 2010-12-02
forum: General Help
---

### Post by neoValmar on 2010-12-02
I installed 10.10 Maverick Meerkat a week or so ago, and had problems, so reinstalled, but into a new partition, leaving the original untouched. After reinstallation, GRUB wouldn't register the old partition (with the original installation). That was fine until a few days ago, and now I wish to access the old partition again. I want to enable a custom GRUB menu entry pointing to the partition with my original install of Maverick. It is located in sda6 (or msdos6) if that helps. I thin it involves editing grub.cfg, but I don't know what to do. Can someone give me a template (or something) to help me out? If so, thank you!

---

### Post by drs305 on 2010-12-02
Have you tried running "sudo update-grub". If your old installation is usable Grub 2 should find it and automatically place it in your Grub menu.

If you would run the boot info script from the following location we can give you the exact entry for a custom menu, or perhaps tell you why your current Grub2 isn't finding the old installation.

Please post the contents of the RESULTS.txt between 'code' tags, which you generate by using the # icon in the post's menubar.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Tiit_Helimut on 2010-12-03
I'm having the same problem, just did clean install of Ubuntu 10.10 on an empty partition (sda4) but kept my copy of CentOS 5.5 on sda2. Ubuntu is the only OS available on the boot menu now and I need to be able to boot CentOS!

I don't want to mess about with the grub.cfg manually but I did try ```
 sudo update-grub
``` which finds CentOS but then doesn't create an option in the boot menu for it, annoyingly.

I used the script to get some information on the HDD and partitions. The original CentOS mounted my userspace from the network, which is why some of the links look a bit odd. By the way, I've removed some information (replaced with .........) in sda2 so that the name of the institution has been removed:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [01;36m .......... [0;39m 
                       [01;36m ......... [0;39m
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2             208,845    84,100,274    83,891,430  83 Linux
/dev/sda3          84,100,275   104,567,084    20,466,810  82 Linux swap / Solaris
/dev/sda4         104,568,832 1,250,263,039 1,145,694,208  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,543,920,062 1,543,920,000   7 HPFS/NTFS
/dev/sdb2       1,543,921,664 1,605,361,663    61,440,000   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0feffeaf-cc55-4617-a48d-8f0f968db50f   ext3       /boot                         
/dev/sda2        55393cd4-554d-4416-852a-ce629ce908c4   ext3       /                             
/dev/sda3                                               swap                                     
/dev/sda4        605915ed-a3af-4bd7-ae74-d8e4edba2551   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb2        0637-4421                              vfat       DOUCHE                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/DOUCHE            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/sda2
#          initrd /initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
password --md5 $1$hEPDsr61$K0cJkFN33.q30x.d76lVq1
title CentOS (2.6.18-194.11.3.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-194.11.3.el5 ro root=LABEL=/ rhgb quiet
    initrd /initrd-2.6.18-194.11.3.el5.img
title CentOS (2.6.18-164.el5)
    root (hd0,0)
    kernel /vmlinuz-2.6.18-164.el5 ro root=LABEL=/ rhgb quiet
    initrd /initrd-2.6.18-164.el5.img

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initrd-2.6.18-164.el5.img
    .0GB: initrd-2.6.18-194.11.3.el5.img
    .0GB: vmlinuz-2.6.18-164.el5
    .0GB: vmlinuz-2.6.18-194.11.3.el5

=============================== sda2/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
LABEL=/scratch          /scratch                ext3    defaults        1 2
LABEL=/boot             /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
LABEL=SWAP-sda3         swap                    swap    defaults        0 0
#<remote-update>
# This section of /etc/fstab was generated elsewhere"
# Manual changes to this section will be over-written"
# SECAMFS HOME SPACE ########################################################
secamfs:/secamfs/userspace/staff      /secamfs/userspace/staff  nfs rsize=8192,wsize=8192,rw,nosuid,nodev,hard,defaults 0 0              
secamfs:/secamfs/userspace/phd        /secamfs/userspace/phd    nfs rsize=8192,wsize=8192,rw,nosuid,nodev,hard,defaults 0 0              
secamfs:/secamfs/userspace/msc        /secamfs/userspace/msc    nfs rsize=8192,wsize=8192,rw,nosuid,nodev,hard,defaults 0 0              
secamfs:/secamfs/userspace/ug         /secamfs/userspace/ug     nfs rsize=8192,wsize=8192,rw,nosuid,nodev,hard,defaults 0 0              
# SECAMFS WEB AND CA ########################################################
secamfs:/secamfs/ca                   /secamfs/ca               nfs rsize=8192,wsize=8192,rw,nosuid,nodev,hard,defaults 0 0
secamfs:/secamfs/web/html_homes/msc   /secamfs/web/people/msc   nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard,nfsvers=3 0 0
secamfs:/secamfs/web/html_homes/staff /secamfs/web/people/staff nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard,nfsvers=3 0 0
secamfs:/secamfs/web/html_homes/ug    /secamfs/web/people/ug    nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard,nfsvers=3 0 0
secamfs:/secamfs/web/html_homes/phd   /secamfs/web/people/phd   nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard,nfsvers=3 0 0
secamfs:/secamfs/web/webpublic        /secamfs/web/webpublic    nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard,nfsvers=3 0 0
# SECAMFS READONLY SECTION ##################################################
# N.B. A BUG IN SOME NFS VERSIONS MEANS THIS MUST COME AFTER READ/WRITE ENTRYS #####
secamfs:/secamfs/usrlocal  /usr/local nfs rsize=8192,wsize=8192,ro,nosuid,nodev,hard,defaults,nfsvers=3 0 0
# N.B. A BUG IN SOME NFS VERSIONS MEANS THIS MUST COME AFTER READ/WRITE ENTRYS #####
secamfs:/secamfs/homelinks /home      nfs rsize=8192,wsize=8192,ro,nosuid,nodev,hard,defaults,nfsvers=3 0 0

# TRON HOME SPACE ###########################################################
tron:/people1 /u/tron1 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
tron:/people5 /u/tron5 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
tron:/people6 /u/tron6 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
tron:/people7 /u/tron7 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
tron:/people8 /u/tron8 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
tron:/people9 /u/tron9 nfs exec,nodev,rsize=8192,wsize=8192,nosuid,rw,bg,hard 0 0
#</remote-update>

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=605915ed-a3af-4bd7-ae74-d8e4edba2551 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=605915ed-a3af-4bd7-ae74-d8e4edba2551 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 605915ed-a3af-4bd7-ae74-d8e4edba2551
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 277.0GB: boot/grub/core.img
 286.0GB: boot/grub/grub.cfg
  71.6GB: boot/initrd.img-2.6.35-23-generic
 277.0GB: boot/vmlinuz-2.6.35-23-generic
  71.6GB: initrd.img
 277.0GB: vmlinuz
```What confuses me is that the old OS (CentOS) has it's own boot partition (sda1), which I assumed Ubuntu would modify and use but it appears to ignore the boot partition.

Any ideas why ```
sudo update-grub
``` does not update grub.cfg in Ubuntu's grub folder, even though it reports that it "finds" CentOS?


Any help would be appreciated!

Thanks.

---

### Post by drs305 on 2010-12-03
> **Tiit_Helimut said:**
> 

Any help would be appreciated!

Thanks.

I haven't used Centos, but I would suggest you try this from the Grub2 menu on boot:
At the menu, press "c" to get into the grub command line.
Then type:
```
configfile **(hd0,1)/grub/grub.conf**
```
I think it will boot when you press ENTER, but if not press CTRL-x

If it boots, we can try to build a custom menu. If it doesn't, from the command line type:
```
**ls (hd0,1)/**
```
Does it see your Centos kernel(s)?

I do see your kernels are named differently that Ubuntu names them. Is there a module that might need to be loaded? I would expect Ubuntu could recognize the kernels, but perhaps it doesn't recognize them because of the kernel extension. It would report having found Centos probably because it found the menu.lst and grub.conf files.

Let's see what happens. In the meantime hopefully someone with Centos experience will chime in.

---

### Post by Tiit_Helimut on 2010-12-05
Thanks for the response.

I went into the command line at the boot screen and typed configfile (hd0,1)/grub/grub.conf and it prints out the following:

```

Error: unknown command 'hiddenmenu'.
Error: unknown command 'title'.
Error: no such partition.
Error: unknown command 'kernel'
Error: you need to load the kernel first.
Error: unknown command 'title'
Error: no such partition
Error: unknown command 'kernel'
Error: you need to load the kernel first.

```So I typed "ls (hd0,1)" and it gave me:

```

Partition hd0,1 : Filesystem type ext2 - Label "/boot" - Last modification time 2010-12-03 18:32:35 Friday, UUID xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

```I have hidden the UUID number as I assume I don't need to display it.

Any idea where to go next, as I'm pretty new to linux and have never dealt with grub before?

Thanks!

---

### Post by drs305 on 2010-12-05
> **Tiit_Helimut said:**
> 
Any idea where to go next, as I'm pretty new to linux and have never dealt with grub before?

Well, that makes two of us as I haven't dealt with Centos before!

[COLOR="DarkRed"]Edit: See post #8 for the menuentry we finally got to work.'[/COLOR]

Try booting Centos from the Grub prompt. At the Grub menu, press "c" to get to the command line. Then enter these commands:
```

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux /vmlinuz-2.6.18-194.11.3.el5 root=(hd0,2) ro
initrd /initrd-2.6.18-164.11.3.el5.img 
boot

```

What I am not sure about is the location of your kernel. In Ubuntu, a link called "vmlinuz" is placed in root, and it references (for example), /boot/vmlinuz-2.6.32-22.

In your system, it appears that the actual kernel resides in / rather than /boot. That's the assumption I made above in any case. If it doesn't boot as I've entered it, try changing both the linux and initrd to add the /boot folder:  **/boot**/vmlinuz-2.6.18-164.el5 ...  **/boot**/initrd...

As far as the drive addresses (hdX,Y), my tests show that with a separate /boot partition the "root=" and "prefix=" should point to the /boot partition, while the root= in the linux line points to the OS.

Let us know if it works.

---

### Post by Tiit_Helimut on 2010-12-06
Thanks again for the reply.

I have followed your instructions but unfortunately to no avail. The first two lines do not seem to cause any problem but when I try to load the kernel (lines 3 and 4) it tells me that files cannot be found, with or without the extra /boot directory!

As far as I can tell, the kernels are located in the boot partition in the /boot folder itself. I can't find any kernels within the file system sda2 (where CentOS is installed) unless I'm looking for the wrong thing.

---

### Post by Tiit_Helimut on 2010-12-10
Thanks to drs305, the problem has been resolved!

All it took in the end was adding an entry to grub's "40_custom" file, located at:
```
/etc/grub.d/40_custom
```Since my custom file was empty, I was able to replace all the contents with:

```
#!/bin/sh
echo "Adding 40_custom." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "CentOS 5.5" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set  0feffeaf-cc55-4617-a48d-8f0f968db50f
    linux /vmlinuz-2.6.18-194.11.3.el5 ro root=UUID=55393cd4-554d-4416-852a-ce629ce908c4 rhgb quiet  
    initrd /initrd-2.6.18-194.11.3.el5.img
}                      
```Otherwise if my 40_custom file wasn't empty, I would have just needed to copy the part from 'menuentry "CentOS 5.5"' onwards.

Then checking that the file is ok (executable):

```
sudo chmod +x /etc/grub.d/40_custom
```Then update grub using:
```
sudo update-grub
```which finds the 40_custom entry and adds it to the bottom of grub.cfg.

Once I rebooted, the CentOS 5.5 entry was in the boot menu and I could successfully boot from it!


So again, thanks to drs305 and the time and effort he put into helping me!

---

