---
title: "bash live cd customisation script"
date: 2011-06-28
forum: General Help
---

### Post by jazzerit on 2011-06-28
Could somebody help me with my bash script please? It's to edit live cds, but I'm not sure what's happening: It's saying ~/livecdtmp/mnt/live/filesystem.squashfs does not exist, even though it most definately does.
here's the script:
```

#!/bin/bash
#this is a live cd customiser
#All changes will be done in the command line
#The live cd will be the very similar to the original, unlike things like remastersys, so multiboots will be easier to make with it.
#this takes only one argument, the file name. If the argument is not given, then it'll ask for a file name
#TO DO: add X support
#possible gui? Zenity/Kdialog?

#check for root
if [ "$(whoami)" != "root" ]; then
echo "Please run this as root. Press any key to continue."
read -n 1 uselessvar
exit
fi

#check for needed tools
if [ -z "$(which rsync)" ]; then
echo "Please install rsync to continue. Press any key to continue."
read -n 1 uselessvar
exit
fi
if [ -z "$(which unsquashfs)" ]; then
echo "Please install unsquashfs (might be called the squashfs tools) to continue. Press any key to continue."
read -n 1 uselessvar
exit
fi
if [ -z "$(which sed)" ]; then
echo "Please install sed to continue. Press any key to continue."
read -n 1 uselessvar
exit
fi
if [ -z "$(which mksquashfs)" ]; then
echo "Please install mksquashfs (the squashfs tools) to continue. Press any key to continue."
read -n 1 uselessvar
exit
fi
if [ -z "$(which mkisofs)" ]; then
echo "Please install mkisofs (the genisoimage tools) to continue. Press any key to continue."
read -n 1 uselessvar
exit
fi

#check for filename
#set checker variable to one. It is used to control the while loop.
checker=1
  while [ "$checker" = "1" ]; do
    if [ -e "$1" ]; then
      cdpath="$1"
    else
      echo -n "Please enter the full path, including the filename, of the cd you want to edit: "
      read cdpath
    fi
    if [ -f "$cdpath" ]; then
      checker="0"
    fi
  done
#that checks for an argument, if it's not there,it asks for a path, checks to see if it's a regular file, and if it is, lets it out of the loop.

#do all pre-customisation settings
mkdir ~/livecdtmp
cp "$cdpath" ~/livecdtmp
mkdir ~/livecdtmp/mnt
mount -o loop "$cdpath" ~/livecdtmp/mnt

echo -n "Please type the path to the squashfs filesystem without including ~/livecdtmp/mnt/: "
read squashfs

mkdir ~/livecdtmp/extract-cd
rsync -exclude="/$squashfs" -a ~/livecdtmp/mnt ~/livecdtmp/extract-cd
unsquashfs "~/livecdtmp/mnt/$squashfs"
mv ~/livecdtmp/squashfs-root ~/livecdtmp/edit

#add networking files
cp /etc/resolv.conf ~/livecdtmp/edit/etc/
cp /etc/hosts ~/livecdtmp/edit/etc/

#add mount points
mount --bind /dev/ ~/livecdtmp/edit/dev
chroot ~/livecd/edit mount -t proc none /proc
chroot ~/livecd/edit mount -t sysfs none /sys
chroot ~/livecd/edit mount -t devpts none /dev/pts

#enter chroot
chroot ~/livecd/edit

#do in-chroot cleanups
chroot ~/livecd/edit rm /etc/hosts
chroot ~/livecd/edit rm /etc/resolv.conf
chroot ~/livecd/edit umount /proc || umount -lf /proc
chroot ~/livecd/edit umount /sys
chroot ~/livecd/edit umount /dev/pts

#post-chroot unmounting
umount /edit/dev

#producing the cd image
mkdir ~/livecd
rm "~/livecdtmp/extract-cd/$squashfs"
mksquashfs "~/livecdtmp/edit" "~/livecdtmp/extract-cd/$squashfs"

checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the isolinux.bin file: "
read isolinuxbin
if [ -f "$isolinuxbin" ]; then
checker="0"
fi
done
checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the boot.cat file: "
read bootcat
if [ -f "$bootcat" ]; then
checker="0"
fi
done

sudo mkisofs -D -r -V "~/livecd/custom_distro.iso" -cache-inodes -J -l -b "$isolinuxbin" -c "$bootcat" -no-emul-boot -boot-load-size
4 -boot-info-table -o "~/livecd/custom_distro.iso" .
umount ~/livecdtmp/mnt
rm -R ~/livecdtmp
echo "The file should be in ~/livecd/custom_distro.iso"

```

---

### Post by jazzerit on 2011-06-28
Guys, a warning: since it won't get into a chroot, it deletes your /proc filesystem. Can someone correct this?

---

### Post by jazzerit on 2011-06-29
ok, fixed it all up until one point: The image creation. This is where I'm at:
```

#!/bin/bash
#this is a live cd customiser
#All changes will be done in the command line
#The live cd will be the very similar to the original, unlike things like remastersys, so multiboots will be easier to make with it.
#this takes only one argument, the file name. If the argument is not given, then it'll ask for a file name
#TO DO: add X support
#possible gui? Zenity/Kdialog?

#check for root
if [ "$(whoami)" != "root" ]; then
echo "Please run this as root. Press any key to continue."
read -n 1
exit
fi

#check for needed tools
if [ -z "$(which rsync)" ]; then
echo "Please install rsync to continue. Press any key to continue."
read -n 1
exit
fi
if [ -z "$(which unsquashfs)" ]; then
echo "Please install unsquashfs (might be called the squashfs tools) to continue. Press any key to continue."
read -n 1
exit
fi
if [ -z "$(which sed)" ]; then
echo "Please install sed to continue. Press any key to continue."
read -n 1
exit
fi
if [ -z "$(which mksquashfs)" ]; then
echo "Please install mksquashfs (the squashfs tools) to continue. Press any key to continue."
read -n 1
exit
fi
if [ -z "$(which mkisofs)" ]; then
echo "Please install mkisofs (the genisoimage tools) to continue. Press any key to continue."
read -n 1
exit
fi

#check for filename
#set checker variable to one. It is used to control the while loop.
checker=1
  while [ "$checker" = "1" ]; do
    if [ -e "$1" ]; then
      cdpath="$1"
    else
      echo -n "Please enter the full path, including the filename, of the cd you want to edit: "
      read cdpath
    fi
    if [ -f "$cdpath" ]; then
      checker="0"
    fi
  done
#that checks for an argument, if it's not there,it asks for a path, checks to see if it's a regular file, and if it is, lets it out of the loop.

#do all pre-customisation settings
echo -n "making working folder... " 
mkdir $HOME/livecdtmp
echo "Done"
echo -n "copying image... "
cp "$cdpath" $HOME/livecdtmp
echo "Done"
echo -n "making live disk mountpoint... "
mkdir $HOME/livecdtmp/mnt
echo "Done"
echo -n "mounting live image... "
mount -o loop "$cdpath" $HOME/livecdtmp/mnt
echo "Done"
filesystem=$(find $HOME/livecdtmp/mnt -name *.squashfs | head -n 1)
filesystem_basename=${filesystem#~/livecdtmp/mnt}
echo -n "making image extraction folder... "
mkdir $HOME/livecdtmp/extract-cd
echo "Done"
echo -n "Copying files to extraction folder... "
rsync  -a $HOME/livecdtmp/mnt/ $HOME/livecdtmp/extract-cd/
rm "$HOME/livecdtmp/extract-cd$filesystem_basename"
echo "Done"
echo -n "Unsquashing live filesystem... "
unsquashfs -d "$HOME/livecdtmp/squashfs-root" "$filesystem"
echo "Done"
echo -n "moving filesystem to edit folder... "
mv "$HOME/livecdtmp/squashfs-root" "$HOME/livecdtmp/edit"
echo "Done"

#add networking files
echo -n "configuring the chroot networking... "
cp /etc/resolv.conf $HOME/livecdtmp/edit/etc/
cp /etc/hosts $HOME/livecdtmp/edit/etc/
echo "Done"

#add mount points
echo -n "Adding devices, proc, sysfs and devpts to chroot... "
mount --bind /dev/ $HOME/livecdtmp/edit/dev
chroot $HOME/livecdtmp/edit mount -t proc none /proc
chroot $HOME/livecdtmp/edit mount -t sysfs none /sys
chroot $HOME/livecdtmp/edit mount -t devpts none /dev/pts
echo "Done"
echo -n "Press any key to enter the chroot... "
read -n 1

#enter chroot
chroot $HOME/livecdtmp/edit

#do in-chroot cleanups
echo -n "Cleaning up... "
chroot $HOME/livecdtmp/edit rm /etc/hosts
chroot $HOME/livecdtmp/edit rm /etc/resolv.conf
chroot $HOME/livecdtmp/edit umount /proc || umount -lf /proc
chroot $HOME/livecdtmp/edit umount /sys
chroot $HOME/livecdtmp/edit umount /dev/pts
echo "Done"

#post-chroot unmounting
echo -n "unmounting devices from chroot... "
umount $HOME/livecdtmp/edit/dev
echo "Done"

#producing the cd image
echo -n "creating squashfs filesystem... "
mkdir $HOME/livecd
rm "$HOME/livecdtmp/extract-cd$filesystem_basename"
mksquashfs "$HOME/livecdtmp/edit" "$HOME/livecdtmp/extract-cd$filesystem_basename"
echo "Done"

checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the isolinux.bin (found in ~/livecdtmp/extract-cd): "
read isolinuxbin
if [ -f "$isolinuxbin" ]; then
checker="0"

fi
done
checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the boot.cat file (found in ~/livecdtmp/extract-cd): "
read bootcat
if [ -f "$bootcat" ]; then
checker="0"
fi
done

echo -n "making live image... "
mkisofs -D -r -V "custom_distro.iso" -cache-inodes -J -l -b "$isolinuxbin" -c "$bootcat" -no-emul-boot -boot-load-size 4 -boot-info-table -o "$HOME/livecd/custom_distro.iso" .
echo "Done"
echo -n "Cleaning up host system... "
umount $HOME/livecdtmp/mnt
rm -R $HOME/livecdtmp
echo "Done"
echo "The file should be in $HOME/livecd/custom_distro.iso"
echo "Press any key to continue... "
read -n 1

```

and this is what we're interested in:
```

checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the isolinux.bin (found in ~/livecdtmp/extract-cd): "
read isolinuxbin
if [ -f "$isolinuxbin" ]; then
checker="0"
fi
done
checker="1"
while [ "$checker" = "1" ]; do
echo -n "Please type the FULL path to the boot.cat file (found in ~/livecdtmp/extract-cd): "
read bootcat
if [ -f "$bootcat" ]; then
checker="0"
fi
done
echo -n "making live image... "
mkisofs -D -r -V "custom_distro.iso" -cache-inodes -J -l -b "$isolinuxbin" -c "$bootcat" -no-emul-boot -boot-load-size 4 -boot-info-table -o "$HOME/livecd/custom_distro.iso" .

```

My problem is the paths given to mkisofs. They are absolute, and that won't work because they need to be reletive. Could somebody help me work out what the relative path should be, if the source folder is /home/user/livecdtmp/extract-cd, the path to the boot.cat is /home/user/livecdtmp/extract-cd/isolinux/boot.cat (for instance) and the path to the isolinux.bin is, for example, /home/user/livecdtmp/extract-cd/isolinux/isolinux.bin? It shouldn't be too hard, I just can't get it to work- I'm not exactly sure where to put it.

---

