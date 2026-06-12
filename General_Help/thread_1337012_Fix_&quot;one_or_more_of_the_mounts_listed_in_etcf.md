---
title: "Fix: &quot;one or more of the mounts listed in /etc/fstab cannot yet be mounted&quot;"
date: 2009-11-25
forum: General Help
---

### Post by mikerobinson on 2009-11-25
I was getting this error after upgrading to 9.10 on every boot and it was slowing boot times for me by about 30 seconds. I finally pinpointed it down to fsck. I just found a fix for it and thought I would share it with everyone. You need to edit your /etc/fstab file and change all of the 1's at the end of every line to a 0 which will disable fsck from checking the filesystem at every single boot. See [here]("http://www.linuxforums.org/forum/ubuntu-help/88818-disabling-fsck-startup.html") for more info. My boot times are now significantly faster.

---

### Post by prshah on 2009-11-25
> **mikerobinson said:**
> I finally pinpointed it down to fsck. I just found a fix for it and thought I would share it with everyone. You need to edit your /etc/fstab file and change all of the 1's at the end of every line to a 0 which will disable fsck from checking the filesystem at every single boot. 

This is really bad advice. The function of this field is to specify the order of checking of the file systems. Quoted from man```
The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

```

fsck should not run on every boot unless there is a specific problem. Besides that, a run of fsck will cause a delay of considerably more than 30 seconds.

Disabling fsck (by putting a 0 in the sixth field) will not run fsck even when the filesystem is damaged. It should not be thus.

---

### Post by shaibn on 2009-12-01
You should check out [this]("http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10") solution (worked for me).

> **kentaur said:**
> Your installs have failed.

remount your filesystem like this:

```

mount -o remount,rw / 
```then do a 

```
sudo dpkg --configure -a 
```And the installation will continue.

When you get the error, hit Enter. Type in the root password and continue solution above.

---

