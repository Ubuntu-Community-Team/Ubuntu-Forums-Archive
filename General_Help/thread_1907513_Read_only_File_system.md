---
title: "Read only File system"
date: 2012-01-11
forum: General Help
---

### Post by jbills on 2012-01-11
My whole file system has become read only in the past 30 minutes or so. This is a recreation of a post I accidentally put in the Apple users forum. I have tried mounting. I have tried sudo mounting with a few options. The whole system cant access any files. What is wrong?

Btw, this is what I gen when I mount:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/josiah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josiah)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.
```

---

### Post by SeijiSensei on 2012-01-11
duplicate deleted

---

### Post by SeijiSensei on 2012-01-11
Linux won't mount as writable an ext filesystem that contains errors.  You'll need to boot from a CD or USB stick and run the command "fsck /dev/sda1", or force a disk check on boot as follows:

```

sudo mount -n -o remount,rw /
sudo touch /forcefsck
sudo reboot

```

The first command forces the OS to mount the file system as writable so you can create the /forcefsck file with the touch command.  

Another option is to use the -F parameter to the shutdown command like this:

```
sudo shutdown -rF now
```

---

### Post by Mariane on 2012-01-11
Be careful, your hard disk may be failing. 

I had a similar problem. I got a new internal hard disk and installed Kubuntu on it. Then I plugged in my old hard disk with some SATA-to-usb connector and mounted it as an external hard disk. 

If you solve your problem following SeijiSensei's advice still make sure you are fully backuped as soon as possible.

---

### Post by SeijiSensei on 2012-01-12
You can corrupt a filesystem in various ways even on disks that are not in danger of failing.  One common cause is a power failure while the machine is writing a file to disk.  This problem can be solved with a good UPS and monitoring software.  I use [APC]("http://www.newegg.com/Store/Brand.aspx?Brand=1317") power supplies with the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon for monitoring.

---

### Post by Lars Noodén on 2012-01-12
> **SeijiSensei said:**
> Another option is to use the -F parameter to the shutdown command like this:

```
sudo shutdown -rF now
```

**-F** is missing from shutdown these days.  /forcefsck still works, but quite a few functions have been pulled from shutdown, not just **-F**.  It's there in the source code (part of the "upstart" package), so it won't produce an error, but is NULLed out and does nothing.

---

