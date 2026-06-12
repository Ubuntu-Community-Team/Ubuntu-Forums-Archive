---
title: "mount ntfs partition with read/write access"
date: 2011-11-09
forum: General Help
---

### Post by alain.roger on 2011-11-09
Hi,

on my notebook i have 2 HDDs. 1 has Ubuntu 11.10 installed and the other one is a NTFS partition (old rest from Windows 7x64 time).

I would like to allow ubuntu to write and read on the NTFS partition in order to still allow my Windows OS to read those files (mainly it's for development purposes).

i tried the procedure on [http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu) however this is only for read mode....i'm even not able to create a simple folder on the NTFS partition from ubuntu.

Therefore i found on [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) something interesting however command:
```
gksudo ntfs-config
```

raised me the following message:
```

Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.7/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

```

Do you have any idea where is the problem and how to solve that ?
thx.

---

### Post by sikander3786 on 2011-11-09
ntfs-config doesn't work with Ubuntu Natty or Oneiric as I've already seen that error here. Still, it is in the official repositories....!

So, simply you can mount your NTFS partitions from a Terminal by following these steps:

1. Create the mount directory:

```
sudo mkdir /media/whatever-name
```

You can also mount it at your desktop or anywhere else you want to.

2. Find the UUID of your partition by running:

```
sudo blkid
```

You can also use /dev/sdXY paths for mounting it but using the UUID is recommended if you happen to add a new HDD or whatever causes a change in the partition paths.

2. Edit fstab and add an entry:

```
gksudo gedit /etc/fstab
```

3. At the end of the file that opens up, add an entry like this:

```
UUID=1E7C14BA7C148EA1 /media/Data ntfs-3g defaults,locale=en_US.utf8 0 0
```

Where:

UUID = The complex number we found by running 'blkid' command.
/media/Data = The mount point we created by running 'mkdir' command.

Leave everything else as it is as this is an entry from my own mounted NTFS partition working great.

Save and close this file.

4. Test your mounts by running:

```
sudo mount -a
```

If there aren't any errors and the partition is mounted successfully, you are good to go. Otherwise before rebooting, post the outputs here to let us take a look. Rebooting with a wrong/non-working fstab entry might not harm your original install but it might cause some problems during the boot process.

A bit outdated info here:

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

---

### Post by Mark Phelps on 2011-11-09
If you simply go into the launcher, click the Home button, you should get a list of filesystems. Click the one that is your Windows partition, and it will automatically be mounted read/write.

---

### Post by charlescarroll1 on 2011-11-14
I am not seeing my Windows NTFS partition at all. I tried clicking the Home button, but in the left column there is nothing that hints toward being the Windows partition. Under "Devices" there is only System Restore and under "Computer" is File System. I check the Media folder in the File System directory and saw nothing.

---

### Post by BHEJU on 2011-11-14
@ Alain.Roger

Just open up terminal and create this missing directory
/etc/hal/fdi/policy

You will be able to launch the ntfs-config.

Cheers,

---

### Post by BHEJU on 2011-11-14
Chuck
You will only see folders in /media if the folders/drives are mounted.
The file explorer will not specifically tell you that its ntfs partition. It will help if you know the title/name of the NTFS partition you have. most likely that will be the name you will see in file explorer.

You can try the ntfs-config to see if you have any ntfs partitions.

I haven't played with it but you might want to take a look at mountmanager (available in synaptic) if ntfs-config does not help.

cheers,

---

### Post by Morbius1 on 2011-11-14
Good golly miss molly. Just run the following command. If it doesn't show up it doesn't exist:
```
sudo blkid -c /dev/null
```

---

### Post by charlescarroll1 on 2011-11-14
BHEJU
I installed mountmanager and saw my partition in /dev/sda/sda2. But there is no /sda folder inside /dev when I search for it in the file explorer.

Morbius1
I ran the command and saw my partition. /dev/sda2 is an ntfs partition, but how do I access the in the file explorer?

---

### Post by Morbius1 on 2011-11-15
Although I would personally use a slightly different set of options the process outlined by sikander3786 above is your answer.

---

### Post by charlescarroll1 on 2011-11-15
I tried following sikander3786's instructions, but I received the following message when I entered the final command:

```
chuck@ubuntu:~$ sudo mount -a
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
```

---

### Post by polki@mac.com on 2011-11-16
It could be that windows didn't shut down properly last time. Try booting into Windows and shut it down, then try again.
I'm not sure it will work, but it might help. Hope it does.

---

### Post by Morbius1 on 2011-11-16
If you are still having problems with this post the output of the following command:
```
mount
```

---

### Post by charlescarroll1 on 2012-10-15
> **polki@mac.com said:**
> It could be that windows didn't shut down properly last time. Try booting into Windows and shut it down, then try again.
I'm not sure it will work, but it might help. Hope it does.

Nope, same problem. Occasionally, I'll get a message saying that Windows did not shut down properly...

---

### Post by charlescarroll1 on 2012-10-15
> **Morbius1 said:**
> If you are still having problems with this post the output of the following command:
```
mount
```

Here it is...
```
chuck@5P4C3:~$ mount
/dev/sda3 on / type ext2 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/chuck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chuck)
/dev/sdb1 on /media/06D2-B9A8 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
chuck@5P4C3:~$ 


```

---

