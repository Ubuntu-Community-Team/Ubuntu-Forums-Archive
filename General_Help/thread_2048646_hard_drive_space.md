---
title: "hard drive space"
date: 2012-08-27
forum: General Help
---

### Post by jrod102 on 2012-08-27
Hello forum my name is Jim and I really could use some help.  Please forgive me as I'm completely a noob at ubuntu.  I'm having a problem with a window poping up telling me i'm running out of hard drive space?  I don't know how to proceed to fix it or what i need to do about it.  But I do have some info for the "tech minded" guru's to look at.  Let me know what you think. 

jrod102@jrod-Satellite-M45:~$ df -h; mount
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        72G  6.4G   62G  10% /
udev            994M  4.0K  994M   1% /dev
tmpfs           402M  832K  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1003M  156K 1003M   1% /run/shm
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jrod102/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jrod102)

Any and all help is extremely appreciated!!!!!  Thank you.  If need be feel free to email me at [EMAIL="jrod102@comcast.net"]jrod102@comcast.net[/EMAIL].    ):P

---

### Post by spjackson on 2012-08-27
Does the message indicate /dev/sda1? How often does it appear? Does it go away after a reboot, then appear several hours later?

Obviously, /dev/sda1 is not full when you ran that df. Perhaps some of the methods for detecting what is going on in [this thread]("http://ubuntuforums.org/showthread.php?t=2043716") will help.

---

### Post by dcstar on 2012-08-27
> **jrod102 said:**
> Hello forum my name is Jim and I really could use some help.  Please forgive me as I'm completely a noob at ubuntu.  I'm having a problem with a window poping up telling me i'm running out of hard drive space?  I don't know how to proceed to fix it or what i need to do about it.  But I do have some info for the "tech minded" guru's to look at.  Let me know what you think. 

```
jrod102@jrod-Satellite-M45:~$ df -h; mount
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        72G  6.4G   62G  10% /
..........
```


Go into Synaptic and uninstall all but the latest two kernels.

Is the message referring to the root partition?

---

