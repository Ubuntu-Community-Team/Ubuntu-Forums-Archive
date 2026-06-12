---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-06-15
forum: General Help
---

### Post by Hungry Man on 2012-06-15
Can't update...
```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up unity-2d-common (5.12.0-0ubuntu1.1) ...

(gconftool-2:19728): GConf-WARNING **: Failed to load source "xml:merged:/tmp/gconf-WnXk6X/gconf": Failed: Could not make directory `/tmp/gconf-WnXk6X/gconf': Permission denied
**
GConf:ERROR:gconftool.c:969:main: assertion failed: (err == NULL)
dpkg: error processing unity-2d-common (--configure):
 subprocess installed post-installation script returned error exit status 250
dpkg: dependency problems prevent configuration of unity-2d-panel:
 unity-2d-panel depends on unity-2d-common (= 5.12.0-0ubuntu1.1); however:
  Package unity-2d-common is not configured yet.
dpkg: error processing unity-2d-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d-spread:
 unity-2d-spread depends on unity-2d-common (= 5.12.0-0ubuntu1.1); however:
  Package unity-2d-common is not configured yet.
dpkg: error processing unity-2d-spread (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d-shell:
 unity-2d-shell depends on unity-2d-common (= 5.12.0-0ubuntu1.1); however:
  Package unity-2d-common is not configured yet.
dpkg: error processing unity-2d-shell (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d:
 unity-2d depends on unity-2d-panel; however:
  Package unity-2d-panel is not cNo apport report written because the error message indicates its a followup error from a previous failure.
                                                           No apport report written because the error message indicates its a followup error from a previous failure.
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             onfigured yet.
 unity-2d depends on unity-2d-spread; however:
  Package unity-2d-spread is not configured yet.
 unity-2d depends on unity-2d-shell; however:
  Package unity-2d-shell is not configured yet.
dpkg: error processing unity-2d (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d-launcher:
 unity-2d-launcher depends on unity-2d-shell; however:
  Package unity-2d-shell is not configured yet.
dpkg: error processing unity-2d-launcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-2d-places:
 unity-2d-places depends on unity-2d-shell; however:
  Package unity-2d-shell is not configured yet.
dpkg: error processing unity-2d-places (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 unity-2d-common
 unity-2d-panel
 unity-2d-spread
 unity-2d-shell
 unity-2d
 unity-2d-launcher
 unity-2d-places

```

---

### Post by Hungry Man on 2012-06-15
No one?

---

### Post by diesch on 2012-06-15
Please post the output of
```
sudo apt-get -f install
```
and 
```
ls -ld /tmp/ /tmp/gconf*
```
and
```
mount
```

---

### Post by Hungry Man on 2012-06-15
-f install gave the same error

ls gave ls: cannot access /tmp/gconf*: No such file or directory
drwxrwxrwt 14 root root 4096 Jun 15 22:53 /tmp/


mount


/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/colin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=colin)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

---

