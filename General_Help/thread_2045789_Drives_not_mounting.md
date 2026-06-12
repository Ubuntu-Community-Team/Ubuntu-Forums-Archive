---
title: "Drives not mounting"
date: 2012-08-21
forum: General Help
---

### Post by Dunchillin on 2012-08-21
Hello.  I've done some forum searches on the subject and tried one or two things but have solved nothing, so apologies for putting this problem up again.

My wife's external hdd stopped mounting suddenly a few weeks ago and in trying to force it to open I seem to have caused damage to my desktop computer's inner workings.

Now when I turn on my computer, as it tries to boot up I get a message saying there is a problem with mounting a drive and I can wait or press 's' to skip.  If I wait nothing happens so I 's'kip and it boots up ok.  The problem then is when I try to plug in ANY usb device I get the following error message:

> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1

This includes a brand new external HDD that arrived in the post this morning.

I'm afraid I can't remember what I did trying to mount my wife's HDD, I foolishly just copied-and-pasted a lot of different code into terminal following various advices given throughout the forums and help pages.

Am freaking out a little, as we do, at not being able to mount anything while wotrk piles up.  Any help gratefully appreciated to the highest degree! Thank you.

---

### Post by spjackson on 2012-08-22
It looks like you have added a line in /etc/fstab, probably containing:
/dev/sdc1 /media/sdc1

Either remove that line or comment it out. (Put a # at the start of the line.) If you are not sure, then post /etc/fstab for further guidance.

---

### Post by Dunchillin on 2012-08-22
Thanks for your help.

> **spjackson said:**
> If you are not sure, then post /etc/fstab for further guidance.

> john@john-System-Product-Name:~$ /etc/fstab
bash: /etc/fstab: Permission denied

That doesn't look good :(

---

### Post by Wim Sturkenboom on 2012-08-22
You can't run it, you need to edit it.

Not sure which editor your familiar with but try

```

sudo nano /etc/fstab

```

Remove the offending line (if it's there) and save. I don't use nano often, but the shortcuts for 'save' and 'exit' are at the bottom of the text window.

---

### Post by Dunchillin on 2012-08-22
This is what I got (below).  Can't see any line as mentioned above? Not actually familiar with any editors I'm afraid, pretty green when it comes to all this, have been learning on the hop for a few years now but still lacking probably basic knowledge about how I should/could use Ubuntu.  Thanks for taking the time to help!

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid           0  0
# / was on /dev/sda1 during installation
UUID=eae32593-901a-43a5-8fa6-a46c5362ee51  /               ext4  errors=remount-ro,user_xattr  0  1
# swap was on /dev/sda5 during installation
UUID=1552f597-53df-4e67-b304-408ff377d7c8  none            swap  sw                            0  0
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8      0  0
/dev/sdc1                                  /media/sdc1     vfat  defaults                      0  0
/dev/sdb1                                  /media/sdb1     vfat  defaults                      0  0


---

### Post by spjackson on 2012-08-22
It is this line
> **Dunchillin said:**
> 
```

/dev/sdc1   /media/sdc1     vfat  defaults    0  0

```that causes
> 
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1
As a decent rule of thumb, /etc/fstab would include everything that you want mounted automatically when the system starts. Plug-in devices are mounted automatically when they are plugged in, unless there's an entry in /etc/fstab that overrides the default behaviour. You would create an entry in /etc/fstab if you want to do something different than the default mounting.

What problem were you trying to solve by adding the last 2 lines to /etc/fstab? I think
```

/dev/sdc1  /media/sdc1     vfat  defaults,user   0  0

```would correct it, because the "user" option allows ordinary users to mount the device. However, I would be inclined to remove both lines
```

/dev/sdc1    /media/sdc1     vfat  defaults     0  0
/dev/sdb1    /media/sdb1     vfat  defaults     0  0                      

```unless you have a good reason for having them.

---

