---
title: "Change automount mountpoint"
date: 2006-03-20
forum: General Help
---

### Post by Ramses de Norre on 2006-03-20
Is it possible to change the mount point of automounted devices? So that, for an example, my mp3 would automount under ~/mp3/ ?

---

### Post by taurus on 2006-03-20
But of course.  Change it in /etc/fstab...

---

### Post by Ramses de Norre on 2006-03-20
But I haven't got a line there for automounted devices, or should I add one for them?

---

### Post by barthel on 2006-03-20
With automounted devices it gets a bit tricky. For example, I have 2 external usb hard drives, a USB floppy, a digital camera, and a flash stick. All of these are given /dev/sd? nodes when detected. The tricky part is that those /dev/sd? nodes are assigned in order of recognition. So if your mp3 player is at /dev/sda1, there is no gurantee that it will **always** be /dev/sda1. The next time you attach it, it might be /dev/sdc1. So you can't write an fstab entry based on the raw SCSI device node.

But you can do it with custom udev rules. Here's a good resource for writing those rules: [http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

**Caution:** There is a trade-off. If you create an fstab entry, the device will no longer be mounted automatically. You will have to manually mount and unmount the device.

Let me share an example of what I use. Here's my custom udev rules file ( /etc/udev/rules.d/001_trippant.rules):

```
# There are a number of modifiers that are allowed to be used in some
# of the different fields. They provide the following subsitutions:
#
# %n the "kernel number" of the device.
#    For example, 'sda3' has a "kernel number" of '3'
# %e the smallest number for that name which does not matches an existing node
# %k the kernel name for the device
# %M the kernel major number for the device
# %m the kernel minor number for the device
# %b the bus id for the device
# %c the string returned by the PROGRAM
# %s{filename} the content of a sysfs attribute
# %% the '%' char itself
#

# 060226-BaP: New local script for Ubutu 5.10....
# NOTE: Although on the USB bus, USB drives are given SCSI device nodes...

# USB floppy drive
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="MITSUMI USB FDD", SYMLINK=="ufa"

# WDC 880BB USB drive...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="Western Digital USB Hard Drive", SYSFS{serial}=="AC030714020331", SYMLINK="uda%n"

# 3.5" external USB hard drive enclosure...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="USB2.0 Storage Device", SYSFS{serial}=="DEF1FE27ED9DCDEF", SYMLINK="udb%n"

# 2.5" external USB hard drive enclosure...
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="USB2.0 Storage Device", SYSFS{serial}=="DEF1093F9404", SYMLINK="udc%n"

# W@LK KEY USB flash drive
# NOTE: The old product string is gone--had to resort to the id numbers.
#   BUT--it's WORKING for the first time since I bought it!!!
BUS=="usb", KERNEL=="sd*", SYSFS{idProduct}=="0005", SYSFS{idVendor}=="0c76", SYMLINK="flash"

# Nikon CoolPix digital camera (thank you Christine!)
BUS=="usb", KERNEL=="sd*", SYSFS{manufacturer}=="NIKON", SYSFS{serial}=="000030697413", SYMLINK="camera"


```
(A note on the filename: "001" ensures that the rule will be read first and take precedence over the default rules. "trippant" is the host name for this particular system.)

As you can see, for each device I found a set of unique identifiers and defined a specific symlink for each one. Now, it no longer matters which SCSI device node is used--udev will always create the same synlink for the device in question and we can use that to create fstatb entries.

```
# /etc/fstab: static file system information.
#
# 060225-BaP: Retweaked after reinstall of base packages
#
#<file sys> <mount point>   <type>      <options>                <dump>  <pass>
proc        /proc           proc        defaults                     0       0
/dev/hda3   /               ext3        defaults,errors=remount-ro   0       1
/dev/hda5   /opt            ext3        defaults                     0       2
/dev/hda6   /usr/local      ext3        defaults                     0       2
/dev/hda2   /winxp          ntfs        noauto,nls=utf8,umask=0222   0       2
/dev/hda7   none            swap        sw                           0       0
/dev/hdc    /media/cdrom0   udf,iso9660 users,noauto,ro              0       0

# 060226-BaP: Added mountpoints for udev-defined devices
/dev/ufa    /media/floppy   auto        users,noauto                 0       0
/dev/uda1   /media/uda1     ext3        defaults,noauto              0       0
#/dev/udb1   /media/udb1     ext3        defaults                     0       0
/dev/udc1   /media/udc1     ntfs        noauto,nls=utf8,umask=0222   0       0
/dev/udc2   /media/udc2     ext3        defaults,noauto              0       0
/dev/flash  /media/flash    auto        users,noauto                 0       0
/dev/camera /media/camera   vfat        users,noauto,ro              0       0


```

*Tangent: It's always a good idea to have a separate home partion. However, I don't have a home partition becuase I symlink /home to /usr/local/home. That way I have one less partition to deal with and a bit more flexibility in terms of allocating space.*

A final note: I deal with manual mounting by setting up gkrellm primary filesystems for the ones I'm most likely to swap in and out during a logon session. For those devices which are semi-permanently attached (this is a laptop), I have a script that will mount those symlinks if they exist.

**Warning!** This script works for me. However it is not bullet-proof and must be modified for your local setup. Use at your own risk.

```

#!/bin/bash

# /etc/init.d/trippant-init.sh - local system initialization script

# update-rc.d trippant-init.sh defaults 99 00

# 060301-BaP: v0.1
#   For now, I just need to ensure that the primary USB drive is
#   mounted if it's available. (And ensure it's unmounted as well...)

# Per Debian policy, we have to support the following arguments:
#   start, stop, restart, and force-reload (and optionally, reload)

# But first, we'll define some functions we'll be using...

. /lib/lsb/init-functions

# In the future, we'll probably create a separate config file, but for
#   now, let's just incorporate everything into this script.

#DEVLIST=${1-$(cat /etc/fstab | sed -e "s/^ *//" | grep "^\/dev" | grep -v "^#" | cut -f 1 -d " ")}
DEVLIST=/dev/uda1

##### mount_available starts

function do_fsck {
    CHECKABLE="/dev/flash /dev/ufa /dev/uda1 /dev/udc2"
    for fsck_dev in $CHECKABLE; do
        if [ "$fsck_dev" == "$1" ]; then
            /sbin/fsck -T $fsck_dev
            return $?
        fi
    done
    return 0
}

function is_mounted {
    # As of 060228, /proc/mounts will contain the /dev symlink used in the
    #   mount command, but /etc/mtab will contain the symlink's target. So
    #   checking both should help us eliminate "already mounted" errors.
    for mounted in $(cat /etc/mtab /proc/mounts /proc/swaps | cut -f 1 -d " " | grep "^\/dev" | sort -u); do
        if [ "$mounted" == "$1" ]; then
            echo 1
            return
        fi
    done
    echo 0
}

function user_mountable {
    # If the device doesn't exist, return 1
    if [ ! -r $1 ]; then
        echo 1
        return
    fi
    # If the device's fstab entry includes "user(s)", return 0
    if [ $(cat /etc/fstab | grep -v "^#" | grep $1 | grep -c "user") -gt 0 ]; then
        echo 0
        return
    fi
    # If the user is effectively "root" return 0, otherwise 1
    if [ $(id -u) -eq 0 ]; then
        echo 0
      else
        echo 1
    fi
}

# 060301-BaP: Conver mount_available's main routine into a function call
#   Also reformatted to more easily adhere to Debian policy.
function mount_available {
    for dev in $DEVLIST; do
        log_begin_msg "Mounting $dev filesystem..."
        # Return success if already mounted.
        if [ $(is_mounted $dev) -gt 0 ]; then
            log_end_msg 0
            return
        fi
        # Return failure if user doesn't have permission
        #   BUG: This check will fail if the device node isn't in /etc/fstab
        if [ $(user_mountable $dev) -gt 0 ]; then
            log_end_msg 1
            log_failure_msg "Device $dev is not mountable by $(id -u -n)."
            return
        fi
        # Perform an fsck if device is listed in the do_fsck routine
        do_fsck $dev
        rc=$?
        if [ "$rc" -gt 0 ]; then
            log_end_msg $rc
            log_failure_msg "fsck of $dev failed. Please correct manually."
            return
        fi
        # Finally, attempt to mount the device
        mount $dev
        log_end_msg $rc
        if [ "$?" -gt 0 ]; then
            log_failure_msg "Device $dev not mounted (return code $rc)."
        fi
    done
}

##### mount_available ends



case "$1" in
    start)
        # Due to possible fsck messages, we log each device separately
        #   while mounting.
        mount_available
        ;;
    stop)
        # Unmount the file systems we unmounted earlier.
        log_begin_msg "Unmounting trippant USB file systems..."
        umount $DEVLIST
        log_end_msg $?
        ;;
    restart)
        mount_available
        ;;
    force-reload|reloada)
        mount_available
        ;;
    *)
        echo "Usage: /etc/init.d/trippant-init.sh " \
            " {start|stop|restart|reload|force-reload}" >&2
        exit 1
         ;;
esac


```

Hope this helps...

---

### Post by Ramses de Norre on 2006-03-20
But there isn't just a simple config file for the automounter that says mount under /media/ ?
That would be way easier:) 
I'll check out your solution anyway, thanks!

---

### Post by barthel on 2006-03-21
[QUOTE=Ramses de Norre]But there isn't just a simple config file for the automounter that says mount under /media/ ?
That would be way easier:) 
I'll check out your solution anyway, thanks![/QUOTE]

Yes, it would be. Unfortunately, it's not quite there yet. For example, my external disk with a single partition was being mounted under the drive label, not the partition label.

It will be nice to see what improvements for this are in Dapper. I'm waiting for a few apps to be repacked before I make the jump to Dapper testing. :-D 

Good luck!

---

### Post by HabbitSHardin on 2007-08-09
Probably no-one is still expecting an answer to this post, but I think I will provide the solution, if only for reference of other users.

You need not write an udev rule even if the device lacks a constant device identifier (i.e. is not always recognized as /dev/sdd). Just add a line for it in fstab, writing the ouput of the vol_id command instead of the device file name in the first field.

Example: i want my MP3 to be mounted as ~/mp3, so I plug it in and it gets automounted as /media/disk
```

user@comp: ~$ mount
(many mount entries)
/dev/sdd1 on /media/drive type vfat (rw, nosuid, ...)
user@comp: ~$ sudo -s
Password: (your user password)
root@comp: /home/user# umount /media/disk
2598-48B6
root@comp: /home/user# echo "UUID=$(vol_id -u /dev/sdd1)   /home/user/mp3  vfat  rw,user,noauto  0  0" >> /etc/fstab
root@comp: /home/user# exit
user@comp: ~$ tail -n 1 /etc/fstab
UUID=2598-48B6   /home/user/mp3  vfat  rw,user,noauto  0  0

```

Explanation:
[LIST=1]
[*]The mount command with no arguments shows the currently mounted volumes and their associated mountpoints. This allows us to discover the current device file name of our MP3 (/dev/sdd1).
[*]Next we enter a root shell with sudo -s. Usually, root commands are performed one by one just prepending sudo to each of them, but neither subshells $() nor redirection (>>) get root priviledges. Just make sure you exit root mode when you finish and be VERY careful when typing.
[*]We unmount the MP3 drive so that we don't have to later. It is not strictly needed, but will save a headache later.
[*]Here comes the biggie. We are inserting a line into /etc/fstab with echo "something" >> /etc/fstab. Be EXTREMELY careful with this line: if you write > instead of >> (one insted of two), you will OVERWRITE your /etc/fstab instead of appending a line to it. This is not exactly fatal, but near to it for inexperienced users. The other tricky part is the $(vol_id -u /dev/sdd1). This is a subshell which will be replaced with the output of the commands it contains - in this case, the UUID of the MP3 partition.
[*]Last, we exit root mode and check the last line of fstab (tail -n 1 /etc/fstab) so that there are no errors
[/LIST]
Done! Next time you plug the MP3 drive in, it will be automagically mounted where you told it to. Just an issue might remain: Feisty does not seem to like to umount volumes mounted from UUID=xxxxx. If you have trouble unmounting your drive (something like "mount of x is not in accordance to fstab"), replace the UUID=xxxxx field in your MP3 line with /dev/disk/by-uuid/xxxxx (where xxxxx is the same UUID in both cases).

Enjoy, all users!

---

### Post by texasjim on 2007-09-06
> **Ramses de Norre said:**
> But there isn't just a simple config file for the automounter that says mount under /media/ ?
That would be way easier:) 
I'll check out your solution anyway, thanks!

Yep, on the desktop, after you mount your device.  Right click on the icon for "disk" or whatever it is, select Properties, and go to the VOLUME tab, and expand the SETTINGS arrow, Then change the mount point to whatever you like. When remounted, it will be /media/newname.

---

