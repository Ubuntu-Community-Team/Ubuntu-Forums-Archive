---
title: "Uninstalling windows but not Wubi"
date: 2010-06-17
forum: General Help
---

### Post by theman1 on 2010-06-17
I installed Ubuntu on my windows using Wubi. Is it possible to Uninstall  windows and remain with Wubi and make Ubuntu the Operating system?

---

### Post by Spr0k3t on 2010-06-17
Best way I know of to remove Windows without removing Wubi is to set up a new partition for Ubuntu, install to that.  Then boot into Wubi and mount whereever the /home partition is located on the new install.  Copy the contents of {wubi}/home/* to {ubuntu}/home/*.  From there you can then remove the Windows partition (which will remove Wubi as well) and resize the remaining partition accordingly.

---

### Post by pastalavista on 2010-06-17
Wubi is a Windows program and won't work without it. Windows can't be "uninstalled", only erased. Best option is to back up /home in Ubuntu and whatever you want to keep from Windows, and do a clean install of Ubuntu.

---

### Post by mike555 on 2010-06-17
If you format over Windows it will format over Wubi ... because wubi is inside Windows .........  Uninstall windows is not the right term , to get rid of an operating system you format the partition containing it, often installing another operating system there......
  such as installing Ubuntu on that partition as a full install ..

---

### Post by steveneddy on 2010-06-17
Simply put the Ubuntu CD in the drive and start the PC

Ubuntu will install itself and erase Windows

Be sure that you back up /home

---

### Post by vince2678 on 2010-06-17
[LIST=1]
[*]_[SIZE=4]REMOVING WUBI[/SIZE]_
[/LIST]

How do I migrate to a real partition, and/or get rid of Windows  entirely?
  Existing Wubi/Lubi installations can be upgraded to an installation on a  dedicated partition via LVPM. The main  site for LVPM is at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) and the guide  and support forum is at [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).
  
  As an alternative, the following script can be used with Wubi 8.04. (or later by modifying the file,  though it works fine , besides installing grub)
  
  ```
 #!/bin/sh -e

# Moves a loopinstallation (e.g. Wubi) to a dedicated partition.
# Copyright (C) 2008 Agostino Russo <agostino.russo@gmail.com>
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option) any
# later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA

dev=$1
swapdev=$2
target=/tmp/wubitarget
swap=/tmp/wubiswap    
usage="
The function should be invokes as follows:
\n
\n\tsudo sh $0 target_partition [swap_partition]
\n
\nFor instance, in order to move to /dev/sda3 use:
\n
\n\tsudo sh $0 /dev/sda3
\n
\nand if you want to have swap on sda5 use:
\n
\n\tsudo sh $0 /dev/sda3 /dev/sda5
\n
"

usage(){
    echo $usage
    exit 1
}

sanity_checks(){
    echo "Sanity checks..."
    if [ -z "$dev" ] || [ ! -b "$dev" ]; then
        echo "First argument (target_partition=$dev) must be a valid partition."
        usage    
    fi
    if [ -n "$swapdev" ] && [ ! -b "$swapdev" ]; then
        echo "Swapdevice=$swapdev is not a block device."            
        usage
    fi
    if [ "$(whoami)" != root ]; then
        echo "Admin rights are required to run this program."
        exit 1
    fi
    mkdir -p $target    
    umount $target 2> /dev/null || true
    if mount -t auto "$dev" $target 2> /dev/null; then
        if [ $(ls -1 $target | wc -l) -gt 1 ] || \
        [ "$(ls -1 $target)" != "lost+found" ]; then    
            echo "Volume $dev is in use. Aborting"
            umount $target || true        
            exit 1
        fi
        umount $target
    fi
}

create_root(){
    mkfs.ext3 $dev
    mount $dev $target
    size=$(df | awk '$5=="/" || $5=="/home" || $5=="/usr" {sum += $3} END {print sum}')
    free_space=$(df $target|tail -n 1|awk '{print $4}')
    if [ $free_space -lt $size ]; then
        echo "Not enough free space ($free_space MB < $size MB), aborting."
        exit 1
    fi
}

migrate_files(){
    echo "Migrating files..."
    rsync -av --exclude=/host --exclude=/dev/* --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / $target
}

edit_fstab(){
    echo "Editing fstab..."
    sed -i 's:/.*[\.]disk .*::' $target/etc/fstab
    sed -i 's:/.*/disks/boot .*::' $target/etc/fstab
    echo "UUID=$(vol_id --uuid $dev)    /    ext3    errors=remount-ro    0    1" >> $target/etc/fstab
    if [ -b "$swapdev" ]; then
        echo "UUID=$(vol_id --uuid $swapdev)    none    swap    sw    0    0" >> $target/etc/fstab
    fi
}

target_cmd(){
    mount -o bind /proc $target/proc
    mount -o bind /dev $target/dev
    mount -o bind /sys $target/sys
    chroot $target $*
    umount $target/proc
    umount $target/dev
    umount $target/sys     
}

edit_grub(){
    echo "Editing grub..."    
    sed -i "s:# groot=.*::" $target/boot/grub/grub.cfg
    sed -i "s:kopt=.* ro:kopt=root=UUID=$(vol_id --uuid $dev) ro:" $target/boot/grub/grub.cfg   
    target_cmd update-grub
    disk=${dev%%[0-9]*}
    partn=${dev#$disk}
    disk=${disk##*/}
    gdisk=$(grep -w $disk /boot/grub/device.map|cut -d ')' -f 1)
    gdisk=${gdisk#\(}
    gpartn=$(expr $partn - 1)
    [ -z "$gdisk" ] && gdisk=hd0
    [ -z "$gpartn" ] && gpartn=0    
    target_cmd grub-install ($gdisk)
    target_cmd grub-install ($gdisk,$gpartn)
    echo "
    root ($gdisk,$gpartn)
    setup ($gdisk)
    setup (hd0)
    quit" | grub --batch --device-map=/boot/grub/device.map
}

remove_lupin_support(){
    echo "Removing lupin_support..."    
    target_cmd apt-get -y remove lupin-support
}

create_swap(){
    echo "Creating swap..."
    if [ -b "$swapdev" ]; then
        mkdir -p $swap        
        if mount -t auto "$swapdev" $swap 2> /dev/null; then
            echo "Volume $swapdev is in use. Skipping swap"
            umount $swap || true
        else
            mkswap $swapdev         
        fi
    fi
}

sanity_checks
create_root
create_swap
migrate_files
edit_fstab
remove_lupin_support
#edit_grub
umount $dev
echo "\nOperation completed successfully, if all is good feel free to remove the installation from windows."
 
```  and save it as 'wubi-move-to-partition' in your home directory as  "/home/whateveryournameis/wubi-move-to-partition"
  
 Open a terminal and run:
  ```

 cd /home/yourname
   sudo sh ./wubi-move-to-partition /dev/sda9 /dev/sda10
 
```  Replace /dev/sda9 with the partition where you would like to migrate the  Wubi installation to, and /dev/sda10  with the appropriate swap partition (you can omit the second argument  completely, in which case no swap will be setup). The two partitions  must already exist and be empty (you can use any partitioning tool such  as gparted to create them in advance). Note that the script **might**  **not** install  grub as main bootloader. Also note that if you have multiple  hard-disks, the disk  order might have to be adjusted manually.

 [SIZE=2][SIZE=1]2[/SIZE]._ GRUB INSTALLATION_[/SIZE] [COLOR=DarkOrange] (if keeping windows or any system on /dev/sd*1)[/COLOR]

 Grub should not install automatically. However, if you are sure that my modification to the script for grub is safe  uncomment the line 3 lines above the last. If unsure, leave it and  complete the installation without modifying the script.
 Firstly, do:
 
 ```
sudo update-grub
``` This should detect the newly copied ubuntu system and add it to wubi's  boot list. reboot and enter the new system (make sure you know the right  one, they are completely the same). 
 
 To install grub, open up a terminal and run:
 
 ```
grub-install /dev/sda
``` or  ```
grub-install (hd0)
```To install to a partition use:

```
grub-install /dev/sda**9**
```or:

```
grub-install (hd0,**9**)
``` Another example is when you have a separate boot partition which is mounted at ‘/boot’. Since GRUB is a boot loader, it doesn't know anything about mountpoints at all. Thus, you need to run grub-install like this: 
   
  ```
grub-install --root-directory=/boot /dev/sda
```*This is only **if** you intend to keep windows(or other system on /dev/sda1). If not, look below.
 * Note: (hd0,**9**) is an example. Use your own boot or root  partition number.
 Also note that these exaples for installing to a partition are for **_chainloading_** from another grub (like windows). Grub 1 has partitions starting from "0" instead of "1" .  So instead of _(hd0,9) in grub2_, grub1 uses _(hd0,_8 ) **for  partition 9.**This applies for all devices in grub1
 
 Another example is when you have a separate boot partition which is mounted at ‘/boot’. GRUB doesn't know anything about mountpoints at all. You need to run grub-install like this: 
  ```
grub-install --root-directory=/boot /dev/sda
```You should also add your /boot partition in the /etc/fstab manually since
the script is not modified to do this. (only if you have one)
*After this you should be able to boot into ubuntu.

[SIZE=4][SIZE=1]3[/SIZE].[/SIZE][U][SIZE=4]Replacing Windows
[/SIZE][/U]
[LIST]
[*]You should have a ubuntu cd or flash ready (or any other live installer)
[*]To make a boot flash, use [Unetbootin]("http://unetbootin.sourceforge.net/") or go to System > Administration > Startup Disk Creator
[*]Use a local image for SDC or local or remote one for Unetbootin
[/LIST]
 
[LIST]
[*]You should use your windows cd to delete the windows partition or use the ubuntu cd (or flash) to remove windows and resize the ubuntu partition (if you do not intend to keep windows) .
[/LIST]

[LIST]
[*]run(or replace [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) with another mirror):
[/LIST]
```
echo "deb http://ftp.sun.ac.za/ftp/ubuntu/ lucid main restricted universe multiverse" >> /etc/apt/sources.list
```
[LIST]
[*]Run :
[/LIST]
```
apt-get update
``` then
```
apt-get install gparted
``` 
[LIST]
[*]Run gparted from **System > Administration** menu not "Disk Utility"
[*]Delete the ntfs filesystem (partition 1 probably)
[*]Resize the ext3 filesystem to fill the space
[*]Apply seetings. Do not exit.
[*]Mount the filesystem (ext3 via **Places** menu)
[*]edit /etc/fstab and make "/ (root) " partition 1 (/dev/sd*1) and swap  partition 2 (/dev/sd*2)
[*]Save the file
[*]plug in your flash drive and when icon appears , do "ls /dev/sd*" include the asterisk
[*]find the drive with one partition (eg /dev/sdb1)
[/LIST]
```
root@centauri:/home/vincent# ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sda4  /dev/sda6  /dev/sda8  /dev/**sdb** **<**=====[COLOR=DarkOrange] our flash drive[/COLOR]
/dev/sda1  /dev/sda3  /dev/sda5  /dev/sda7  /dev/sda9 _***/dev/sdb1***_ <====[COLOR=DarkOrange] our first partition on flash[/COLOR]
root@centauri:/home/vincent# 
```
[LIST]
[*]Back up EVERYTHING on the flash
[/LIST]

[LIST]
[*]run (as root):
[/LIST]
```
umount /dev/**sdb1** ; mkfs.ext2 -m 0 /dev/**sdb1**

```
[LIST]
[*]Note the letter (probably from a-c) [replace sdb1 with your own flash . _Be careful not to mistake it with another drive or usb device_!]
[*]click on the icon on the desktop or "places" menu and copy the /boot folder into the Flash disk
[*]type "mount" on the terminal (or right click on the desktop icon of the flash)
[*]find /dev/**sdb1** on **/media/universally-unique-id** type ext3 (rw) [or go to the Permissions menu and find "the permissions of **universally-unique-id **could ..."
[*]copy the text after "on" (of course, replace **universally-unique-id** with the actual location outputted)
[*]this will tell us where in /media it is mounted or anywhere else on the system
[*]Run:
[/LIST]
```
grub-install --root-directory=**/media/universally-unique-id** /dev/**sdb**

```
[LIST]
[*]open the flash folder and go into boot > grub and open the grub.cfg file
[*]add the following
[/LIST]
 ```
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
insmod ext2
set root='(hd1,1)'
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
set root='(hd1,1)'
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi

insmod ext2
set root='(hd1,1)'
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    linux    /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
# For installing GRUB into the hard disk
menuentry 'Install GRUB into the hard disk'
    root    (hd1,1)
    setup   (hd1)
}
```
[LIST]
[*]Save the file. IF it fails open gedit as root by typing:
[/LIST]
```
sudo gedit **/media/universally-unique-id**/boot/grub/grub.cfg

```
[LIST]
[*]Save and reboot.
[*]Set the flash as the default boot device in the BIOS (do it yourself , press F2, F12 , or DEL , normally these should work)
[*]Reboot and when at menu prompt , selsect the opeion ' Install to hard disk'
[*]Reset the harddrive as default boot device
[*]Enjoy Ubuntu.
[*]PS: Keep the flash as is. You can copy any files there. You might need it for emergency purposes (mistakenly deleting your MBR or a failed upgrade) but do not delete the partition unless you are sure of it.
[/LIST]

[COLOR=RoyalBlue]Or you could use StartupDiskCreator or Unetbootin and back-up all your files and do a clean install.......[/COLOR]

---

### Post by pastalavista on 2010-06-17
> **vince2678 said:**
> [LIST=1]
[*]_[SIZE=4]REMOVING WUBI[/SIZE]_
[/LIST]

How do I migrate to a real partition, and/or get rid of Windows  entirely?<snip>...

Wow, this is what Linux is all about...

---

### Post by pablokiryu on 2010-07-06
Will thie Wubi-to-Real-partition Work for Lucid?

---

### Post by vince2678 on 2010-07-20
yes it works with lucid. Thats what I used to turn my 10.04 wubi installation to a partition installation

---

### Post by bcbc on 2010-07-20
> **vince2678 said:**
> yes it works with lucid. Thats what I used to turn my 10.04 wubi installation to a partition installation

I also have an updated script (taken from the move-wubi-to-partition) that works too... it's fully automated to run; all you have to do is tell it which partition to migrate to. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

