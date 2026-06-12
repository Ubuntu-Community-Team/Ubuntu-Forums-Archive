---
title: "I can't delete files"
date: 2009-09-14
forum: General Help
---

### Post by grandpa2390 on 2009-09-14
Whenever I try to delete a file, It just sits there and does nothing. no error message or anything.

---

### Post by Gen2ly on 2009-09-14
have you tried using the terminal?  Do

```
rm <filename>
```

and it it spits out an error, post it here.

---

### Post by grandpa2390 on 2009-09-14
rm: cannot remove `music': Read-only file system

---

### Post by maclorenza on 2009-09-14
Running the file again , or
Different user

---

### Post by grandpa2390 on 2009-09-14
same user as I am i didn't sudo and of course I don't want to have to sudo to do something like delete a file on a flash drive. now if it was a system file by all means but I want to be able to delete it like anything else.

---

### Post by grandpa2390 on 2009-09-14
tried to sudo it, and it gave the same error.

---

### Post by bchurchill on 2009-09-14
> **grandpa2390 said:**
> rm: cannot remove `music': Read-only file system

As the error suggests, your filesystem is read only.  You probably can't create or change any files in your music folder.  Depending on how your partitions are set up, you may have trouble in any other folder in the same partition.  Can you delete other files on your computer?  Is 'music' in your home folder?  Post the output of running

sudo cat /etc/fstab

so we can help you a bit more :)

---

### Post by grandpa2390 on 2009-09-14
I can delete them
I must add that I just added these lines to fstab, rebooted, and it didn't work.
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0 
should I delete them?

[sudo] password for simon: 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9a356a97-2011-4ad3-8d56-851038077bd7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7a285b13-bcef-4477-842e-866cb4e57297 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0 simon@simon-desktop:~/Documents$

---

### Post by sanguinoso on 2009-09-14
What shows up when you run the mount command?

This is the output relevant to my flash drive

/dev/sdc1 on /media/USB20FD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

Note the rw within the parentheses. Do you have a ro?

---

### Post by bchurchill on 2009-09-14
Your fstab looks alright, you'll want to restore the fstab file to the way it was before

Let's take a step back.  Have you tried
 
sudo rm -rf music

what error messages do you get?

***** BE CAREFUL WITH THIS COMMAND!  make sure you refer to the right folder and double check before pushing enter.  People ruin their installs by accidently deleting / or other important folders instead.  Sounds silly, but it happens....

---

### Post by grandpa2390 on 2009-09-14
I don't know what I did, I got a little impatient and figured since it was aproblem with permissions that I would have the problem no matter what. So I plugged it into my windows pc and deleted all of the files and now that I've plugged it back in, i can create files and delete them with no problems.

---

### Post by grandpa2390 on 2009-09-14
Thankyou so very much for both your time and help. I only wish I knew what the problem was in case it happens again in the future. But atleast I know I can count on you all if it does.

---

### Post by bchurchill on 2009-09-14
> **grandpa2390 said:**
> same user as I am i didn't sudo and of course I don't want to have to sudo to do something like delete a file on a flash drive. now if it was a system file by all means but I want to be able to delete it like anything else.

oh, I didn't catch that this is a flash drive.  In addition to telling us how it was mounted, you can modify your udev rules so that a certain group can have full access to usb devices so you don't need sudo. 

For example, you can create a 'usb' group using

$sudo groupadd usb

and then add yourself to the group

$sudo usermod -a -G usb myusername

create the file /etc/udev/rules.d/10-local.rules
(you'll need to use sudo to edit this file, eg
$sudo gedit /etc/edev/rules.d/10-local.rules


and put the following two lines in it:

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usb", MODE="0660"
SUBSYSTEM=="usb_device", GROUP="usb", MODE="0660"


You'll probably need to restart afterward, but this allows anyone in the USB group to read/write/edit/delete to usb desvices, and mounted filesystems bound to those devices.

---

### Post by grandpa2390 on 2009-09-14
oh ok. I'll save that thought to my thumbdrive. I have a thumbdrive dedicated to troubleshooting that I go through just in case I have to do a reinstall. Thanks again.

---

