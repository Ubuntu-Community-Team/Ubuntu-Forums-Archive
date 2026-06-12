---
title: "where are mp3 players mounted?"
date: 2010-05-28
forum: General Help
---

### Post by mountainmanmark on 2010-05-28
i know this is probably a really novice question.. but i can't seem to find where the mount direcotry for my mp3 player is.. its showing up in rhythm box, but when i look in media its not there, and when i click on places its not showing up either..

---

### Post by lmarmisa on 2010-05-28
Maybe they are mounted in **/media** directory.

---

### Post by mountainmanmark on 2010-05-28
> **lmarmisa said:**
> Maybe they are mounted in **/media** directory.

its not showing up..

---

### Post by lmarmisa on 2010-05-28
Try these commands:

> 
mount
ls -l /media


---

### Post by amite on 2010-05-28
can u access it?
if it is not in /media just look in /mnt

---

### Post by Spr0k3t on 2010-05-28
Generally speaking, yes they are found in the /media directory.  If they don't show up mounted there, check to see how the Sansa is set up for media transfers... it will either be MCP or MTS (if I remember correctly).  Whichever the setting is on the Sansa, change it over and remount the device after a full power cycle.  That should fix it.

---

### Post by mountainmanmark on 2010-05-28
> **lmarmisa said:**
> Try these commands:

i typed the command and i got 

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/candace/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=candace)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sda1 on /media/Storage type ext4 (rw,nosuid,nodev,uhelper=udisks)

also i looked in the /mnt directory and its not showing up either...

---

### Post by mountainmanmark on 2010-05-28
> **Spr0k3t said:**
> Generally speaking, yes they are found in the /media directory.  If they don't show up mounted there, check to see how the Sansa is set up for media transfers... it will either be MCP or MTS (if I remember correctly).  Whichever the setting is on the Sansa, change it over and remount the device after a full power cycle.  That should fix it.


k i'll try that and report back.

---

### Post by mountainmanmark on 2010-05-28
> **mountainmanmark said:**
> k i'll try that and report back.

Thanks! its letting me browse the files now.

---

### Post by mountainmanmark on 2010-05-28
> **mountainmanmark said:**
> Thanks! its letting me browse the files now.

ok.. one mroe question.. it lets me browse the folders.. but i can't see any of the files.. does anyone know how to make them not hidden?

---

### Post by lmarmisa on 2010-05-28
Are you sure you have mounted your mp3 device?.

Try Places -> Mp3DeviceLabelOrSize

---

### Post by mountainmanmark on 2010-05-28
> **lmarmisa said:**
> Are you sure you have mounted your mp3 device?.

Try Places -> Mp3DeviceLabelOrSize

when i plug in my mp3 player after changing the usb type it auto mounts and is displayed under places...  just it won't let me browse any of the files... all of the folders are showing up thoguh.

---

### Post by Spr0k3t on 2010-05-28
With nautilus open to the directory you want, do a CTRL-H to show hidden.  Another option is to right click and "Show hidden directories".

Also, don't forget to put together the ".is_audio_player" file as outlined in the [Rhythmbox FAQ](http://live.gnome.org/Rhythmbox/FAQ).  Creating the .is_audio_player file will also allow you to specify the location of music files if they differ from the default /media/music directory.

Anyway, don't forget to use the thread tools to mark the issue as solved when you get a chance.

---

