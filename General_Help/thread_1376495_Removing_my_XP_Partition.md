---
title: "Removing my XP Partition"
date: 2010-01-09
forum: General Help
---

### Post by sandkernel on 2010-01-09
Hello all,
I'm currently dual booting XP/Ubuntu 9.1 on my T400. I have a 150G drive of which 40G is dedicated to XP. The reason I left a small XP partition was that I wasn't 100% sure my vpn client would work in Ubuntu so I had to leave the option to go back into windows. Now that that is taken care of, I want to completely turn this laptop into a 100% Ubuntu laptop without re-installing.

My plan is to fire up Gparted, delete the XP partition and create a new ext4 filesystem in its place or resize the current 100G ext4 filesystem (i.e. / ) to swallow up that extra 40G.

My question is - am I missing anything here? I would hate to have a dead laptop that requires a re-install but how does this sound? Doable? Also, I see there is no menu.lst in karmic so do I have to run update-grub2 after removing the XP partition?

---

### Post by muteXe on 2010-01-09
No idea about grub2 sorry, but if you're planning on resizing your current partition you'll need to boot up a live cd and use gparted from here, cuz you cant resize a partition that's currently mounted.

---

### Post by sandkernel on 2010-01-09
> **muteXe said:**
> No idea about grub2 sorry, but if you're planning on resizing your current partition you'll need to boot up a live cd and use gparted from here, cuz you cant resize a partition that's currently mounted.

Yes, you're right on that. If I want to do this live then I'll need to remove the XP partition and add it as a new device, /dev/sda4 I think in my case.

---

### Post by mk1w86 on 2010-01-09
See here for information about Grub2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

If you are already using grub all you have to do is remove the Windows XP boot entry (see link above) after resizing your Ubuntu partition. :D

Although it probably seems obvious I would also recommend backing up any important data on your Ubuntu partition before resizing just in case something goes wrong.

---

### Post by sandkernel on 2010-01-09
> **mk1w86 said:**
> See here for information about Grub2:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

If you are already using grub all you have to do is remove the Windows XP boot entry (see link above) after resizing your Ubuntu partition. :D

Although it probably seems obvious I would also recommend backing up any important data on your Ubuntu partition before resizing just in case something goes wrong.

Looks like removing the XP partition and running update-grub should do it then.

---

### Post by louieb on 2010-01-09
> **sandkernel said:**
> ... My plan is to fire up Gparted, ...and create a new ext4 filesystem ...

Thats what I would do. Its nice to have a separate /data partition.

---

### Post by Leppie on 2010-01-09
> **sandkernel said:**
> Looks like removing the XP partition and running update-grub should do it then.

that's correct.
bear in mind that if the location of the /boot folder is physically changed, you most probably have to boot using livecd to re-install grub2 to the mbr (it looks like both grub and grub2 don not use a link to the partition, but the physical address). this is a bit inconvenient, but it shouldn't take very long.

---

