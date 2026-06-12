---
title: "Install Ubuntu from another ubuntu..."
date: 2010-04-23
forum: General Help
---

### Post by Monotoko on 2010-04-23
I have a laptop which i dropped a while ago, therefore it doesnt work as well as it used to, it doesnt recognise the USB ports or the DVD drive sadly, i shall be taking it to be repaired soon.

But for now i am left with no way of installing any external media, and i would like to install a clean Ubuntu on a new partition, is this possible from inside my old one, if i do not have any disks?

~Daniel

---

### Post by colorlessprism on 2010-04-23
information used from Ubuntu documentation. *See original [HERE]("https://help.ubuntu.com/community/Installation/FromLinux")*

If you already have a working linux system, installing without external media is easy. You need to create a new partition, copy the CD contents over to it, boot from the new partition, and proceed as if you were installing from a CD.

**Step 1.** Use gparted to create a new primary partition and format it to ext3. You need slightly more than 700MB of free space on it. 750MB should be sufficient. Let's say the name of the partition is /dev/sda1. If your new ubuntu install is going to coexist with your old system, you might find it convenient to create space for your new system as well at this point using gparted. 

**Step 2.** Copy CD contents over to the new partition using the command 

 mkdir /tmp/install_cd
 mkdir /tmp/installer

 sudo mount disk-image.iso -o loop /tmp/install_cd
 sudo mount /dev/sda1 /tmp/installer

 sudo rsync -a /tmp/install_cd/ /tmp/installer

 sudo umount /tmp/install_cd
 sudo umount /tmp/installerReplace the name of the iso to whatever you downloaded and /dev/sda1 with whatever your new partition is. 

**Step 3.** Edit your grub (see part 2 for Grub2) configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) to boot from the new partition by adding the lines 

title           installer
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz

The first line after the title tells grub which partition contains the installer. hd0 stands for "first hard disk," and the 0 following it standards for first partition. You will need to change this if your installer partition is different from /dev/sda1. sdaN becomes (hd0, N-1), sdbN becomes (hd1,N-1) and so on. As you can see, grub starts counting from 0, which can be confusing. 
[B]
Part 2[/B]
If you are trying to use Hard Disk installation with Ubuntu 9.10 chances are initrd.gz is renamed as initrd.lz now. So rename accordingly in menu.lst. 

With Grub2, the bootloader in new installations of 9.10, the procedure is a little different. You should edit the file /etc/grub.d/40_custom and add the lines 

menuentry "installer" {
        insmod ext2
        set root=(hd0,1)
        linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
        initrd /casper/initrd.lz
}

Having done that run update-grub to rebuild the grub configuration. Note that Grub 2 counts drives from 0, but partitions from 1, so /dev/sda1 becomes (hd0,1). 
[B]
Step 4.[/B] Reboot, and choose "installer" from the grub boot menu, and continue as if you were installing from CD. 

**Note:** if you unpacked the livecd on the same disk where you want to install Ubuntu, chances are you'll run into [LP#288675]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675"), and be unable to select a partition. The workaround by Nick Spencer ("sudo umount -l -r -f /dev/sda3 or sudo umount -l -r -f /cdrom (where sda3 was the device mounted as cdrom)") is a rather terrible hack, but usable as a workaround. 
**Note2:** Instead of using 'workaround', an alternative is to modify the file /etc/mtab by erasing the line that specifies the partition where the cdrom is mounted. This way the kernel thinks thats the /cdrom is not mounted and will not show the advice when installing ubuntu. I think this procedure is less dangerous than the one in the previus note.
*[]("https://help.ubuntu.com/community/Installation/FromLinux")*

---

### Post by cariboo on 2010-04-23
Have a look [here]("https://help.ubuntu.com/community/Installation"), and see if the network install works for you.

---

