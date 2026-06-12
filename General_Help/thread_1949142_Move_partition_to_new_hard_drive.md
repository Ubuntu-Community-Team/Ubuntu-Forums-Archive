---
title: "Move partition to new hard drive"
date: 2012-03-29
forum: General Help
---

### Post by SnoopFogg on 2012-03-29
Hi, I'm trying to move Ubuntu to a new larger hard drive. I've been following this howto:

 [http://ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition](http://ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition)

Which basically says use a live CD and gparted to create the partitions of exactly the same size on the new disk (leaving space to expand afterwards).  Then use partimage to transfer the files.

After I've gone through:

mkdir newdisk (on the new partition sdb7)
mount /dev/sdb7 newdisk
cd newdisk
mkdir systemimage
chmod 777 systemimage

I get an error message from Partimage that there is either not enough disk space, or I don't have permissions.  

As the disk space is the same, and I did the chmod bit, I don't know why I'm getting the message.  Can anyone help?

Cheers

---

### Post by dcstar on 2012-03-30
> **SnoopFogg said:**
> Hi, I'm trying to move Ubuntu to a new larger hard drive. I've been following this howto:

 [http://ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition](http://ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition)
........

What a lot of overcomplicated stuff in that HOWTO.

If you want to copy a Partition with **gparted** simply "Copy" and "Paste" from one drive to the other.

Then:

[LIST=1]
[*]Change the UUID of the new Ubuntu partition (search for detailed instructions)
[*]Boot the old system (with the new drive attached)
[*]Do:
```
sudo update-grub
```
[*]Reboot and select the new entry in the Grub menu.
[*]Then in the newly booted partition:
```
sudo dpkg-reconfigure grub-pc
```
and install the bootloader onto the new drive.
[*]Shut down, unplug the old drive and the system should now boot up on the new drive and Ubuntu partition.
[/LIST]

---

### Post by SnoopFogg on 2012-04-01
Hi, I tried to start from scratch on the new hard drive (sdb) using a live disk and gparted.  I now get an error "unable to delete /dev/sdb5!  Please unmount any logical partitions having a number higher than 5"

I have tried to umount all the sdb drives but get message that the drive is not mounted.  The affected partition is an extended partition containing a swap partition so wondered if that might be being used.  If so, how do I umount it so I can start over?

Cheers

---

### Post by dcstar on 2012-04-03
> **SnoopFogg said:**
> Hi, I tried to start from scratch on the new hard drive (sdb) using a live disk and gparted.  I now get an error "unable to delete /dev/sdb5!  Please unmount any logical partitions having a number higher than 5"

I have tried to umount all the sdb drives but get message that the drive is not mounted.  The affected partition is an extended partition containing a swap partition so wondered if that might be being used.  If so, how do I umount it so I can start over?


Turn Swap off in the partition properties. Then Create a new Extended partition and just individually copy the other partitions.

---

### Post by SnoopFogg on 2012-04-12
> **dcstar said:**
> What a lot of overcomplicated stuff in that HOWTO.

If you want to copy a Partition with **gparted** simply "Copy" and "Paste" from one drive to the other.

Then:

[LIST=1]
[*]Change the UUID of the new Ubuntu partition (search for detailed instructions)
[*]Boot the old system (with the new drive attached)
[*]Do:
```
sudo update-grub
```
[*]Reboot and select the new entry in the Grub menu.
[*]Then in the newly booted partition:
```
sudo dpkg-reconfigure grub-pc
```
and install the bootloader onto the new drive.
[*]Shut down, unplug the old drive and the system should now boot up on the new drive and Ubuntu partition.
[/LIST]

Hi, at stage 4 I didn't get a new entry in the Grub menu.  So then I booted into the original hard drive and tried to edit the fstab of the new copied hard drive with the new UUID that I created.  

When I put in "gksu gedit /media/143704be-714d-4d5e-9a04-e07e372e5d88/etc/fstab &" The fstab itself was blank with no text in it, so I copied the original fstab into the file and made the changes to the new UUID.

However, when I tried to save the new fstab I get an error message "Could not find the file /media/143704be-714d-4d5&#8230;04 e07e372e5d88/etc/fstab.  It doesn't seem to want to let me update it.  

Any ideas on how I can manually update / create new fstab file?

Sorry about the break - I've been away for Easter and would now love to get this sorted.  Cheers

(And thanks for help with the other instructions about swapoff which worked perfectly)

---

### Post by SnoopFogg on 2012-04-21
Hi, I'm trying to move Ubuntu to a new hard drive.  Using gparted and a live disk I have copied the old documents partition, OS partition (and a windows partiton) to the new hard drive, creating more space on each new partition. And created a new swap partition. 

I have created a new UUID for the new swap, documents and OS but now I'm stuck.  The advice above didn't work.  If I left the old hard drive in, I didn't get an option to "select the new entry in the Grub menu".  It was the same menu I had before and so the only option was to boot into the old ubuntu os.  If I disconnect the old hard drive, it boots straight into windows without giving me a grub to select Ubuntu.

Step 5 here [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition) also gives me problems.  It suggests:

shell> gksu gedit /media/<new partition uuid>/boot/grub/grub.cfg &

And then edit all the SDA numbers to the new drive.  However, when I do shell> gksu gedit /media/< I insert new partition uuid here>/boot/grub/grub.cfg &, I get presented with a blank grub.cfg file.  

I am happy to start from scratch if someone can point me to a better set of instructions.

Many thanks

---

### Post by SnoopFogg on 2012-04-21
Not sure if it helps but here is blkid showing unique uuid's. Just need to figure out how to update grub (and if necessary fstab?) so I can boot from sdb2:

/dev/sda1: LABEL="Vista-OS" UUID="0E9575077B2C8E0C" TYPE="ntfs" 
/dev/sda2: LABEL="Ubuntu-OS" UUID="41822a74-05eb-4ad2-9a41-7bbe7cd087ec" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="793f482e-5525-45f0-b216-3056ed430344" TYPE="swap" 
/dev/sda6: LABEL="Ubuntu-Docs" UUID="3e79c520-891e-4815-b5f4-2895286308f8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: LABEL="Vista-OS" UUID="21FE5A5902CA713C" TYPE="ntfs" 
/dev/sdb2: LABEL="Ubuntu-OS" UUID="1b37d2a5-c064-4b1c-91be-a1bf33cbb588" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: LABEL="Vista-DOCS" UUID="35B7365E008600A4" TYPE="ntfs" 
/dev/sdb5: LABEL="Ubuntu-Docs" UUID="8f1ed0bb-079b-4977-8d91-b059d124f90b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="da5f24fc-a85d-4c21-be82-ab5e581dcdfb" TYPE="swap" 

Cheers

---

### Post by NTL2009 on 2012-04-21
I doubt I can help, but just want to let you know others are very interested in this also. It seems that so many of the tutorials on this are complex (to me), and/or require that the destination partition be the same size (or larger) than the source partition ( I guess gparted has this requirement also). It'd be great to be able to clone to smaller partitions, to have a back-up that could just be swapped in. I have plenty of spare space on my main drive, I don't need to maintain all that spare space on a swapable back-up, a little will do.

I'd really like to find a way to do this along the lines of what **dcstar** listed in post #2.   If this can be done, I'd look into writing detailed instructions and posting them somewhere.

One thing - could it be that your version of grub is different than what some of these instructions are working with? I've seen a lot of stuff reference grub installations, while most people are now on grub2? That's probably not it, just thinking out loud.

-NTL2009

---

### Post by oldfred on 2012-04-21
So we can see UUID, partitions and grub.cfg and fstab, run the boot info script. 

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or you can run script directly:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by SnoopFogg on 2012-04-23
Hi, I had a number of issues.

1. Using old grub (thanks to NTL2009 for highlighting).  I was aware that it needed to be grub2, but incorrectly assumed that was what I was using.  Hadn't appreciated that grub2 was not automatically upgraded.
2. Using the UUID with the command "gksu gedit /media/<UUID>/boot/grub/grub.cfg &" wouldn't work.  But using the label I had previously created did work "gksu gedit /media/Ubuntu-OS/boot/grub/grub.cfg &. (Same for trying to update new fstab)
3. After updating grub2 and the new fstab, it still came up with a grub error.  However, Boot-Repair fixed that for me completely (thanks to oldfred for that). 

It wouldn't be what I would call a textbook partition move, but I'm now up and running on the new hard drive.  Thanks everyone.

---

