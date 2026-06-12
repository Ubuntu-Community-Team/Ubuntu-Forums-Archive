---
title: "Start filesystems automatically at boot"
date: 2010-03-04
forum: General Help
---

### Post by shockandawe on 2010-03-04
When I go to 'Places' on my panel, my windows drives are listed. I can click on one, it then asks me for password, then it puts a hard drive icon on my desktop. This is excellent.

They are listed as '200 GB Filesystem' etc.

My only problem, is how to make these icons stay after I shut down. I don't want to do this every time I boot up.


Cheers!

---

### Post by cjhabs on 2010-03-04
> **shockandawe said:**
> When I go to 'Places' on my panel, my windows drives are listed. I can click on one, it then asks me for password, then it puts a hard drive icon on my desktop. This is excellent.

They are listed as '200 GB Filesystem' etc.

My only problem, is how to make these icons stay after I shut down. I don't want to do this every time I boot up.


Cheers!

Check out:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by bowmanr@mailcity.com on 2010-03-04
NOTE :: i'm on a Windows machine at work, not with my linux machines at home. The following is from memory.

~~~

I'd suggest looking at your /etc/fstab file. Also, you need to explicity create mount points and have the partitions mounted at boot time. Here's some rough steps to follow:

1) Isolate the drive partitions you want to be mounted ...

   $ sudo fsdisk -l

2) Ceate a directory under mnt, for example "/mnt/200Gb_filesystem" ...

   $ sudo mkdir /mnt/200Gb_filesystem

3) Edit your /etc/fstab file with some like ...

   /dev/sdDN      /mnt/200Gb_filesystem     FS     defaults    1       1

where "DN" are Device letter and partition Number (for example /dev/sda5) and "FS" is the filesystem (NTFS or VFAT)

Then check it mounts correctly without reboot ...

   $ sudo mount -a

If all ok, then reboot. If not, then please post the output from "sudo mount -a" here, along your /etc/fstab file and the result of "ls /mnt/".

With good luck, and a fair following wind, on reboot, /mnt/200Gb_filesystem will be auto mounted.

I'm not sure how you make those appear in the left hand shortcut pane of Nautilus though.

Hope that helps
Robert

---

### Post by sisco311 on 2010-03-04
> **cjhabs said:**
> Check out:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

That tutorial is for network shares. I think the OP wants to mount an internal partition:

[http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig](http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig)

---

### Post by shockandawe on 2010-03-04
Thanks very much sisco311, your guide was excellent. Worked like a charm.

Cheers!

---

