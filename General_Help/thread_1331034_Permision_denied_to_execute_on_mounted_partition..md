---
title: "Permision denied to execute on mounted partition."
date: 2009-11-18
forum: General Help
---

### Post by HegonBadde on 2009-11-18
Here's the Scenario,
I've got rather large partition of stuff I want to mount in ~/data
I set it up that way during a clean 9.04 install. 

However it wouldn't let me mount it without authentification
so I did a 
*chown -R myuserid:myuserid ~/data *
and added *,auto,user* to the end of the partitions /etc/fstab entry.
to make it auto mount at boot time, and rebooted.

It automouted just fine, however that made everything noexec.

I tried adding uid=1000 as well but that caused an invalid paramter error

I'm sure it's something simple I'm missing, here's the data.

[B]
myuserid@myuserid-desktop:~/data/software/eclipse$ ./eclipse [/B]
bash: ./eclipse: Permission denied
[B]
myuserid@myuserid-desktop:~/data/software/eclipse$ ls -la ./eclipse[/B]
-rwxr-xr-x 1 myuserid myuserid 68333 2009-05-19 18:04 ./eclipse

**Here's my /etc/fstab**
[I]
# .. snip header details
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=c5556277-0feb-4d67-a088-24af4f856505 /               ext3    relatime,errors=remount-ro 0       1
# /home/myuserid/data was on /dev/sdb2 during installation
**UUID=55258583-595c-4744-b562-0ce23a66c5d6 /home/myuserid/data ext3    relatime,auto,user       0       2**
# swap was on /dev/sda1 during installation
UUID=c0df13b9-9d45-457a-a9bd-704913a9542b none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=cd93740f-1b20-4b6b-9243-0e5b2e27464c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/I]


**here's the results of  no argument mount**
[I]
myuserid@myuserid-desktop:~/data/software/eclipse$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
**/dev/sdb2 on /home/myuserid/data type ext3 (rw,noexec,nosuid,nodev,relatime)**
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/myuserid/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=myuserid)
myuserid@myuserid-desktop:~/data/software/eclipse$ 
[/I]

---

### Post by HegonBadde on 2009-11-18
Fixed it.

I removed the users from /etc/fstab and now it automounts and the permissions seem to be correctly working.

---

