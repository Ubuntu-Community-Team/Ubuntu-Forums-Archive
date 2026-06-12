---
title: "Convertive a WUBI installation to 'full'..."
date: 2009-12-13
forum: General Help
---

### Post by Gizenshya on 2009-12-13
I have a wubi installation that I would like to convert into a full install on its own hard drive.  I have all the programs and whatnot like I want them.

Is it possible to do this?  If so, how?

---

### Post by garvinrick4 on 2009-12-13
There is a save markings in Synaptic. I have never used it, I have saved markings
to a back-up drive but never tried to reinstall from them. 

Save your Home folder.

Firefox save your bookmarks in Bookmarks/Orginize bookmarks/back-up.

You have to uninstall Wubi from the C: drive. Sometimes if you uninstall from Add and Remove Programs in Windows you leave Wubi in dos4grub and have to edit it out.
So uninstall from Ubuntu in C: drive in the folder. 

Put in your live CD and boot from CD drive and go from there. Software will do most all
of work. Just pay attention.  But you cannot transfer Wubi install to a partition without some fancy Grub work a image back-up program, ect, ect, ect. if at all possible.

---

### Post by Gizenshya on 2009-12-13
Well, there are two problems with doing that first suggestion...

1.  I will only have access to 56k internet for a while.  Downloading the programs again isn't an option :(

2.  (don't know if this adds anything or not) I have C: xp/ubuntu 8.10, and D: Vista/9.04. The 9.04 is what I want.  The 8.10 is a base install with nothing else.  For some reason, when I boot to C and choose Ubuntu, I get 9.04 from my D drive, which is cool.  Vista killed itself and took its grub with it, and this is the only way I can boot to 9.04, even though I don't know how it works...

But I want to make it into a full install before xp kills it.  I want it to be on a new drive, not the C or D drives mentioned above.

I've thought about just mounting root.disk (or whatever it's cvalled) and copying everything to an empty linux-formatted drive or greater size (that also has swap).  But woud this cause problems?  What would I do about grub?

:(

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
[http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/](http://flip.netzbeben.de/2008/08/move-wubi-installation-ubuntu-on-windows-to-a-native-ubuntu-system/)  This should work for you. You can skip the part about installing gparted because it's in the default install. Downloading the script (the wget part) shouldn't take long even on a 56k modem. Also might want to look into installing grub because I don't see that mentioned there. Just Google it and you should be golden.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
I just looked into it a little more and when I wget the script it gets named "WubiGuide?action=AttachFile&do=get&target=wubi-move-to-partition" which will obviously not work so you'll have to rename the script to well... whatever you feel like typing in the ```
sudo sh wubi-move-to-partition /dev/sdx1 /dev/sdx2
``` part of the howto. It's also not set as executable so you'll want to ```
chmod +x wubi-move-to-partition
```
If that's what you want to rename it to. I also looked at the script in gedit and it does what it says. If you want to check for yourself just as I did right click it and open with gedit. Hope this helps.

---

### Post by Gizenshya on 2009-12-13
**I solved this download issue.  I'm leaving this for a reference for others who might goggle upon it.  All I did to fix it was put quotes around the web link, as vista cuts it up and confuses itself. Edit again: I just noticed that the quotes were originally on the page in the first place, and apparently my copy paste skills are lacking.**

well, I haven't gotten that far yet...

 forgot to mention another problem, I must use a win box to get to the internet, not that box (long story).

This is what I got...

```
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\me>wget -c https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=g
et&target=wubi-move-to-partition
--2009-12-13 20:01:09--  https://wiki.ubuntu.com/WubiGuide?action=AttachFile
Resolving wiki.ubuntu.com... 91.189.90.19
Connecting to wiki.ubuntu.com|91.189.90.19|:443... connected.
ERROR: cannot verify wiki.ubuntu.com's certificate, issued by `/C=US/ST=Arizona/
L=Scottsdale/O=GoDaddy.com, Inc./OU=http://certificates.godaddy.com/repository/C
N=Go Daddy Secure Certification Authority/serialNumber=07969287':
  Unable to locally verify the issuer's authority.
To connect to wiki.ubuntu.com insecurely, use `--no-check-certificate'.
Unable to establish SSL connection.
'do' is not recognized as an internal or external command,
operable program or batch file.
'target' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\me>wget -c --no-check-certificate https://wiki.ubuntu.com/WubiGuide
?action=AttachFile&do=get&target=wubi-move-to-partition
--2009-12-13 20:01:42--  https://wiki.ubuntu.com/WubiGuide?action=AttachFile
Resolving wiki.ubuntu.com... 91.189.90.19
Connecting to wiki.ubuntu.com|91.189.90.19|:443... connected.
WARNING: cannot verify wiki.ubuntu.com's certificate, issued by `/C=US/ST=Arizon
a/L=Scottsdale/O=GoDaddy.com, Inc./OU=http://certificates.godaddy.com/repository
/CN=Go Daddy Secure Certification Authority/serialNumber=07969287':
  Unable to locally verify the issuer's authority.
HTTP request sent, awaiting response... 403 Forbidden
2009-12-13 20:01:45 ERROR 403: Forbidden.

'do' is not recognized as an internal or external command,
operable program or batch file.
'target' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\me>
```

what do I do?

edit: I pasted the link in ie and it displayed in-text.

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
    rsync -av --exclude=/host --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / $target
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
    sed -i "s:# groot=.*::" $target/boot/grub/menu.lst
    sed -i "s:kopt=.* ro:kopt=root=UUID=$(vol_id --uuid $dev) ro:" $target/boot/grub/menu.lst
    cp /usr/lib/grub/*/*stage* $target/boot/grub/    
    target_cmd update-grub
    disk=${dev%%[0-9]*}
    partn=${dev#$disk}
    disk=${disk##*/}
    gdisk=$(grep -w $disk /boot/grub/device.map|cut -d ')' -f 1)
    gdisk=${gdisk#\(}
    gpartn=$(expr $partn - 1)
    [ -z "$gdisk" ] && gdisk=hd0
    [ -z "$gpartn" ] && gpartn=0    
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
edit_grub
umount $dev
echo "\nOperation completed successfully, if all is good feel free to remove the installation from windows."




```

Now... would it be safe to just copyu and paste that into an empty text document and then rename it to whatever?

---

### Post by dasunst3r on 2009-12-13
For you, here's what I'd do.  Make sure you understand all the listed procedures before following through.  Ask for clarification wherever you need it.
**1. Back up your home folder:** Your home folder contains not only your documents and stuff, but also your preferences.
a. Insert a USB memory drive.  When the window for it opens, hit Ctrl+L to see where it's mounted.  I'm going to use /media/MightyDrive as an example.
b. Open up the terminal and type in ```
cp -R ~/ /media/MightyDrive
```  cp = copy, -R = recursive (meaning you're going into the folders and backing them up too, /media/MightyDrive = destination.

**2. Back up your /var/cache/apt**: This contains all the packages you downloaded so far.  When you come to install your stuff, the system will look there first before downloading packages from the Internet.
a. Type ```
sudo apt-get autoclean
```  This will delete packages that are old or packages not installed on the system.
b. Type ```
cp -R /var/cache/apt /media/MightyDrive
```  Again, this will copy over your files from /var/cache/apt to your flash drive.

After you finish the full installation:
1. Add any repositories you added initially.
2. Insert the USB drive you used to back up your stuff.
3. **Copy back /var/cache/apt:**
a. Open up a terminal
b. Type in ```
sudo cp -R /media/MightyDrive/apt /var/cache
```
4. Copy back your home folder.
a. Open up a file explorer window for your USB drive, and open the folder with your user name on it.
b. Open up a file explorer window for your home directory.
c. Drag and drop the files from your USB drive to your hard disk.
d. Click on the file explorer window of your USB drive, and press Ctrl+H to show hidden files on the USB drive.
e. Restore your preferences.  .mozilla contains your preferences for Firefox, .purple contains your preferences for Pidgin, etc.

There is your gentle introduction to the terminal.  If you need any clarification, let me know.

---

### Post by Gizenshya on 2009-12-13
I do remember adding repositories and keys... I'll have to figure out which ones and how to add them back.  can I do it without an internet connection? **edit:** Or would that only matter when updating?

and, it should work as long as I install the same base ubuntu version, right?  In other words, it probably wouldn't work if I tried installing 9.10, then adding that stuff (since the wubi I'm trying to back up isn't 9.04)...?

another thing... with sin's suggestion, it says move... it actually copies, right?  I don't want to delete the initial grub installation, just copy it.

---

### Post by Gizenshya on 2009-12-13
my var/cache is only ~50 mb.  var/cache/apt is only 5.  Is there another place synaptic package manager (or apt-get) searches before online (ie, a place where program installation files may still be).  Or does this basically mean if I want to go that route, I would have to re-download everything (and do a package checklist backup). :(

---

### Post by dasunst3r on 2009-12-13
Adding repositories and keys will only matter when you are installing new programs and/or doing updates.  Also, you are correct that my procedures for backing up your packages will only work if you are going to install the same version (i.e. 9.04 to 9.04).

---

### Post by Gizenshya on 2009-12-15
Well, first I tried that LV?? program from the first link... but after I tried and failed at it I saw that I had to make the ext3 and swap partitions myself first :o

For some reason I don't have gparted on mine, so I'm downloading it now.

Then I'm going to try that LV?? program again, and if I can't get it to work, then that alternate way in the first link.

I'll hold off on the second suggestion because I would like to not have to re-download things and set up repositories and the like again.

---

