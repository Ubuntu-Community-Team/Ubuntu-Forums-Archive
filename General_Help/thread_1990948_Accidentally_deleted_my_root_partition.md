---
title: "Accidentally deleted my root partition"
date: 2012-05-30
forum: General Help
---

### Post by kevpatts on 2012-05-30
Okay, I'm an idiot!

I was looking to wipe a USB and I inadvertently used Gparted and wiped the root (boot) partition of my mdadm raid mirror! I'm still running the machine so I need to repair this before I shutdown.

I have used parted's rescue command and I was offered:
```
Information: A ext4 primary partition was found at 0.00B -> 984GB.  Do you want to add it to the partition table?
Yes/No/Cancel? Yes
```

I can now see the partition in Gparted again but it has a warning:
```
e2label: No such file or directory while trying to open /dev/md1p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: No such file or directory while trying to open /dev/md1p1

Unable to read the contents of this filesystem!
Because  of this some operations may be unavailable.

The cause might be a missing software package.
The following list of software packages is required for ext4 file system support: e2fsprogs v1.41+.
```

I tried running sudo fsck /dev/md1 but /dev/md1 is mounted so it would cause damage.

Where do I go from here??

---

### Post by anonymous5 on 2012-05-30
> **kevpatts said:**
> Okay, I'm an idiot!

I was looking to wipe a USB and I inadvertently used Gparted and wiped the root (boot) partition of my mdadm raid mirror! I'm still running the machine so I need to repair this before I shutdown.

I have used parted's rescue command and I was offered:
```
Information: A ext4 primary partition was found at 0.00B -> 984GB.  Do you want to add it to the partition table?
Yes/No/Cancel? Yes
```

I can now see the partition in Gparted again but it has a warning:
```
e2label: No such file or directory while trying to open /dev/md1p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: No such file or directory while trying to open /dev/md1p1

Unable to read the contents of this filesystem!
Because  of this some operations may be unavailable.

The cause might be a missing software package.
The following list of software packages is required for ext4 file system support: e2fsprogs v1.41+.
```

I tried running sudo fsck /dev/md1 but /dev/md1 is mounted so it would cause damage.

Where do I go from here??

Maybe this could help you :
[http://linuxers.org/howto/how-recover-a-lost-partition](http://linuxers.org/howto/how-recover-a-lost-partition)

---

### Post by kevpatts on 2012-05-30
That's exactly what I said I did. The problem though is that it's a raid array.

I think the error message listed is a red herring and is always listed for mdadm raid arrays in gparted.

I'm going to risk restarting and I'll let you know how it goes!

---

### Post by kevpatts on 2012-05-30
Okay, I had no issues after the reboot.

Thanks all

---

### Post by swarooppalsonupal on 2012-06-06
I  mounted the root folder to a folder inside /dev and accidentally deleted the folder now when i select ubuntu after restarting it prompts a screen with grub>

Can i recover everything if yes please share the steps.

i was using ubuntu 11.10 and had installed it through wubi installer.

Regards,
Swaroop

---

### Post by kevpatts on 2012-06-19
How did you delete the folder? Through the graphical interface or on the command line. If the latter, what command did you use?

---

