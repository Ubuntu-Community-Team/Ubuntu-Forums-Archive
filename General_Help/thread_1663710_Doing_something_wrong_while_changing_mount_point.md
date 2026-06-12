---
title: "Doing something wrong while changing mount point"
date: 2011-01-10
forum: General Help
---

### Post by n125 on 2011-01-10
I have an NTFS partition that I keep data on to use between Ubuntu 10.10 and Windows. In Ubuntu, it mounts in /media after I select it from the Places menu. I want to change it so that when I select the partition from the Places menu, it mounts in /home instead.

I followed several instructions that should let me do this by editing /etc/fstab. But no matter what I try, the partition disappears from the Places menu, and if I log off and back on, all of my settings (panels shortcuts, appearance, etc) are reset to default.

Here is what I have tried doing; maybe someone can please point out what is wrong?

First I unmount the partition and make sure nothing is in /media and /mnt. I also make sure to back up /etc/fstab.

I get the partition's UUID and type with blkid:

```

/dev/sda1: LABEL="Windows" UUID="6C648DAC648D7A1A" TYPE="ntfs" 
**/dev/sda2: LABEL="Data" UUID="1F3965BF02253467" TYPE="ntfs"** 
/dev/sda5: UUID="52150b71-5cdd-4461-8b5f-327e9afb6a45" TYPE="ext4" 
/dev/sda6: UUID="848aa84e-5782-42f6-a3cb-ddf405efa7f1" TYPE="swap" 
/dev/sda7: UUID="9f33e4d4-d160-4419-a4fd-80a6d5d9c169" TYPE="ext4"

```

Then, I run gksudo gedit /etc/fstab and ADD the following line:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=52150b71-5cdd-4461-8b5f-327e9afb6a45 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=9f33e4d4-d160-4419-a4fd-80a6d5d9c169 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=848aa84e-5782-42f6-a3cb-ddf405efa7f1 none            swap    sw              0       0
[b]# New Data mount point
UUID=1F3965BF02253467 /home ntfs defaults 0 0[/b]

```

And that basically results in what I described above.

I have only been using Linux for about a year, so I'm still...learning. I'm not even sure if this is the correct procedure to do what I want, nor if what I want is even possible.

---

### Post by Idefix82 on 2011-01-10
Linux relies on /home to store many personal settings. When you mount a different partition under that folder name, it cannot access the settings and reverts to defaults. You can mount it as something like /home/mydata (make sure to create that folder first), then your problems should disappear.

---

### Post by cavalier911 on 2011-01-10
Your double mounting /dev/sda7 and /dev/sda2(ntfs) on the same mount point  /home
/dev/sda7 your /home partition which contains system files/user settings must be mounted on /home
Make a mount folder of it's own like /home/your.username/data,then make a Bookmark for it in Nautilus, name it Data,it will appear in the Places column on left.

---

### Post by bodhi.zazen on 2011-01-10
That and you can not use a ntfs partition for /home

---

### Post by n125 on 2011-01-10
Thanks for the replies.

I tried this:

> **cavalier911 said:**
> Your double mounting /dev/sda7 and /dev/sda2(ntfs) on the same mount point  /home
/dev/sda7 your /home partition which contains system files/user settings must be mounted on /home
Make a mount folder of it's own like /home/your.username/data,then make a Bookmark for it in Nautilus, name it Data,it will appear in the Places column on left.

and while it appears to work, I get the following error when attempting to access the partition by selecting it from Places:

> 
**Unable to mount Data_Mount**
Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it rebuild root. Please see more information at: [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
I thought this was caused because I had the defaults option set in fstab, which implies nouser. So I set it to user and that didn't really do anything.

Is this what bodhi.zazen was referring to?

---

### Post by n125 on 2011-01-10
Sorry for the bump. Does anyone have any ideas as to how to solve the error I'm getting when attempting to change the mount point of a partition?

---

