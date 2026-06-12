---
title: "Live USB vfat write permissions"
date: 2010-09-12
forum: General Help
---

### Post by joe57005 on 2010-09-12
I created a Live usb system using grub2 to boot a ubuntu 9.10 iso as a loop device, once booted, ubuntu mounts the drive as /isodevice, i can write in that folder, but only as root. i've tried everything i can think of, searched so many forums, all to no avail. i've even tried editing /etc/fstab but no luck. (i'm not even sure if fstab edits will persist, either) i'd really like if i can just use the mount command, (so i can put it in a startup script) is there any way i can change the ownership? or sort out the groups? i've read the mount manpage and tried mounting it with different uid and gid, but still nothing! everything i've tried results in being only writeable by root.

---

### Post by oldfred on 2010-09-13
All windows partitions get their ownership from the default mount. All mine whether regular install or the loop mount show root as the owner, but I have no issues with the regular install read & write. Something about the loopmount mounting it as isodevice. I was able to write using sudo nautilus as it does not then ask for password and gives root access to the device.

---

### Post by joe57005 on 2010-09-13
I've tried that, and it works, but it's an inelegant and inconvenient solution. what i really want is to have it writable for non-root. i've been trying the mount command with the -o remount option, but with no success. 

if all else fails, i'll see about loging in as root. i don't really care about the security risks as it's only for computer repair and data recovery, so most everything i do requires root anyway.

---

