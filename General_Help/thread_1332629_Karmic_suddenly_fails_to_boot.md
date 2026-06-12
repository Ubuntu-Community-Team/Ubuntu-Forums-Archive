---
title: "Karmic suddenly fails to boot"
date: 2009-11-20
forum: General Help
---

### Post by wanfahmi on 2009-11-20
I hope somebody else will find this useful. Ubuntu 9.10 ext4 partition.

I rebooted my notebook and suddenly ubuntu stopped with some message that unable to mount root partition (or something like that, can't remember exactly). I suspect initramfs is not recognizing my ext4 partition (for whatever reason)

You need to find out which partition is your ubuntu partition. It was /dev/sda3 for me. Unfortunately you can't do this within grub.

Use your live cd and find out.
Boot up and run this command

```
sudo fdisk -l
ls -la /dev/disk/by-uuid

```

Compare the two outputs. One entry from fdisk is missing from by-uuid list (look for something like sda1 sda2...etc in the outputs)

The missing partition (lets call it /dev/sda2, I might be different on your system)

Now reboot Ubuntu. Once you get your grub menu, Hit 'E' key to edit.

Find the line that starts with linux. Somewhere on that line, you'll find root=uuid=43456543675365sf9s8df7

change that to root=/dev/sda2

at the end of that line, add rootfstype=ext4 

Then press Ctrl-X to continue to boot. You should have a running system now. 

Now, run this commands to make it permenant. Edit grub options

```
gksudo gedit /etc/default/grub

```
Change this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4"

```
Uncomment this line
```
#GRUB_DISABLE_LINUX_UUID=true

```to this
```
GRUB_DISABLE_LINUX_UUID=true

```
save this file and quit gedit

then run 
```
sudo update-grub

```
Reboot and enjoy again!

---

### Post by drs305 on 2009-11-20
Very nice guide. One note on finding the system your Ubuntu install is on. You should be able to determine this from within Grub 2. 

1. At the Grub 2 menu, press "c" to get to the command line. 
2. Type "ls" and press ENTER. That should show the devices and partitions, for example: (hd0), (hd0,1), (hd0,2), etc
3. You can then use "ls (hd0,1)/boot" or similar to see what is in that partition/folder.
4. Once you find the correct location, translate it to device format. (hd0,1) is sda1, (hd1,3) is sdb3, etc.

Your guide should prove very useful to users having this problem. Thanks.

---

