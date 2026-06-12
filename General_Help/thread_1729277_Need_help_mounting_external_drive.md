---
title: "Need help mounting external drive"
date: 2011-04-14
forum: General Help
---

### Post by The Cog on 2011-04-14
I have an external drive that I would like to mount with special options when I plug it in. Specifically, I want it to mount with the btrfs compress option.

If I just plug it in, it mounts into /media/Elephant (I labelled the partition Elephant when I formatted it), but it mounts without the compress option. So I guess I need an entry in /etc/fstab for it. But when I make such an entry, it doesn't mount when I plug the drive in any more. I get an error message saying I don't have rights to mount it. 

This error happens even if I give the **user** or **users** option which allows me to mount the drive manually immediately after I get the message that says I don't have the rights. Here is an example fstab line:
```
UUID=ce99ce5e-9b5d-4f11-ab49-f0c357742e97  /media/Elephant btrfs user,compress 0 0
```

So how can I arrange that the drive mounts automatically as usual, but with the compress option as well?

---

### Post by The Cog on 2011-04-15
I also noticed that having a partition in fstab that isn't there on boot causes the system to give me an error message and not finish booting, so I also have to add a noauto option. This is getting tricky.

---

### Post by sisco311 on 2011-04-15
You could write an udev rule. Check out the Arch wiki for some examples:
[https://wiki.archlinux.org/index.php/Udev](https://wiki.archlinux.org/index.php/Udev)

---

### Post by The Cog on 2011-04-16
Thanks for the suggestion sisco311, but I'm getting nowhere trying to write a udev rule (in /etc/udev/rules.d/test.rules). I found that the command
```
mount -o remount,compress /media/Elephant
```
remounts with an added compression option. So I tried adding this rule to udev
```
ACTION=="add", ENV{ID_FS_TYPE}=="btrfs", RUN+="/bin/mount -o remount,compress /dev/%k"
``` but it didn't seem to make any difference. So I thought I'd just try to create a file to show that the rule was even triggering, like this:
```
ACTION=="add", RUN+="/bin/mount > /tmp/aaa"
```
but /tmp/aaa is not getting created, so there is something fundamentally wrong here. Maybe udev just doesn't work on Ubuntu.

---

### Post by sisco311 on 2011-04-19
Sorry for the delay.

I'm not sure why the fstab entry does not work for you. Could you post the error message you get? 

This udev rule should work in Ubuntu too:
```
KERNEL!="sd[a-z][0-9]", GOTO="auto_mount_btrfs_end"

# Import FS infos
IMPORT{program}="/sbin/blkid -o udev -p %N"

# Exit if not a btrfs partition
ENV{ID_FS_TYPE}!="btrfs", GOTO="auto_mount_btrfs_end"

# Get a label if present, otherwise specify one
ENV{ID_FS_LABEL}!="", ENV{dir_name}="%E{ID_FS_LABEL}"
ENV{ID_FS_LABEL}=="", ENV{dir_name}="usbhd-%k"

# Mount options
ACTION=="add", ENV{mount_options}="relatime,compress"

# Mount the device
ACTION=="add", RUN+="/bin/mkdir -p /media/%E{dir_name}", RUN+="/bin/mount -o $env{mount_options} /dev/%k /media/%E{dir_name}"

# Clean up after removal
ACTION=="remove", ENV{dir_name}!="", RUN+="/bin/umount -l /media/%E{dir_name}", RUN+="/bin/rmdir /media/%E{dir_name}"

#Exit
LABEL="auto_mount_btrfs_end"

```

---

