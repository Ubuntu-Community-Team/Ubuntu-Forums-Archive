---
title: "Spinning down hard drive"
date: 2006-06-06
forum: General Help
---

### Post by matt_man22 on 2006-06-06
I'm trying to spin down my hard drive through the command line.  Whenever I do:

```
sudo hdparm -y /dev/hda
```

The drives spins down for a second and then spins back up.  From looking around it looks like it is the /var folder being on the drive.  Is there anyway to prevent disk access and power it down?

Thanks.

---

### Post by matt_man22 on 2006-06-06
I found that NOFLUSHD may do the job, but if I want to install it, I have to remove a lot of packages.  Anyone try this?

Or any other ideas?

---

### Post by Ivan Matveich on 2006-06-06
Play with your /proc/sys/vm/* configuration. For instance,

```

echo 86400 > /proc/sys/vm/laptop_mode
echo 86400 > /proc/sys/vm/dirty_writeback_centisecs
echo 86400 > /proc/sys/vm/dirty_expire_centisecs

```

---

### Post by matt_man22 on 2006-06-06
Is there a guide to doing this?  Not much came up on the forums.

Is this simply services that need to be shut down or does it have to do with the ext3 file system?

Thanks.

---

### Post by Ivan Matveich on 2006-06-07
All this is quite unusual, low-level and not well documented. I'm sure a google search for "laptop mode linux" will give you plenty to read. Basically, you have to tell the kernel to defer any writes to the disk for N minutes, unless absolutely necessary.

By the way, desktop hard disks: (a) spinup slowly; and (b) are not designed to withstand frequent spinups. Are you doing this because your disk is too loud? I could suggest other solutions if I knew what your application requires.

---

### Post by matt_man22 on 2006-06-08
I have looked around google and this forum and have tried a couple of things.  I used noatime for all mounts, and also enabled laptop-mode with AC power.  Neither of these let me spin down the drive.

It actually is a laptop I am using it for.  However, it is when the AC is plugged in.  I have the laptop in my room, close to where I sleep, but would like to keep the laptop on all night.  Just trying to quiet it down a bit, since I know the hard drive will not be used all night.  The laptop is a Thinkpad T42.

I appreciate your help.

---

### Post by Ivan Matveich on 2006-06-08
I suppose you can't suspend the laptop? Anyway, try this:

```

echo 86400 > /proc/sys/vm/laptop_mode
echo 0 > /proc/sys/vm/dirty_writeback_centisecs
echo 1 > /proc/sys/vm/block_dump
hdparm -y /dev/hda

```

When your disk spins up, run dmesg and you will see a line like:

```

[298735.484539] bash(11983): READ block 48497752 on hda1

```

which will tell you what process caused the unwanted read.

---

