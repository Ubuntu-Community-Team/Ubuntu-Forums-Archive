---
title: "Mounting NTFS drives - arrrrgh"
date: 2009-07-11
forum: General Help
---

### Post by Al Grant on 2009-07-11
Hi Guys,

I am sure this may have been answered already but my searches failed to find the answer.

I want to plug in and view two NTFS drives via USB adapters.

The drives show up in the GUI, and I can right click on them and then mount, but when I go to open them I get Unable to Mount Location / Cant mount file, and the other one does nothing.

Only the drive that does "nothing" shows up in fdisk -l. (sdc)

dmesg shows sdb exists, but mounting problem as listed above and its not listed in fdisk -l.

They both show up ok in windows.

I sont need to permenantly mount them, just temporarily would be fine.

Thanks

-Al

---

### Post by randcoop on 2009-07-11
I would guess that the problem is with permissions.  There are many ways to solve the problem, but if you just want a quick fix, try running your file manager as root (in the terminal, just enter ```
gksudo nautilus
```  If the problem is permissions, then that should work.  If you want user access to the files, then, as I say, there are lots of solutions, but they would take more effort.

---

### Post by Al Grant on 2009-07-11
> **randcoop said:**
> I would guess that the problem is with permissions.  There are many ways to solve the problem, but if you just want a quick fix, try running your file manager as root (in the terminal, just enter ```
gksudo nautilus
```  If the problem is permissions, then that should work.  If you want user access to the files, then, as I say, there are lots of solutions, but they would take more effort.

Interestingly when I run nautilus as gksudo I then click on "Computer" to see these two USB drives. I get Nautlius cannot handle computer locations.

The drives are not listed down the sidebar either....

If I start Nautilus from the menu in the GUI at the same I can see the icons for the drives, but they are light grey and I still cant open them.

HTH

-Al

---

### Post by randcoop on 2009-07-13
It certainly seems like a permissions issue.  Nautilus and Ubuntu should be mounting these drives effortlessly.  But since they aren't, you might want to try a program called Mount Manager.  Take a look at this page for how to install it and how it works: [MountManager]("http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html")
or just use Synaptic and install mountmanager.

---

### Post by BbUiDgZ on 2009-07-13
boot into windows and unmount the usb drive properly using the remove hardware icon next to your system clock.

then try and mount in ubuntu

---

### Post by Fatman_UK on 2009-07-13
I think Windows sets a "locked, do not mount" flag in the NTFS partition header. Sometimes NTFS doesn't get unmounted properly and the flag isn't removed, so Ubuntu sees the flag and thinks "better not mount this".

Sometimes I need to mount manually and specify the "force" option. I don't recall the exact syntax (it's been a while), but it's something like:

$ sudo mount -t ntfs -o force /dev/sdb1 /win

It hasn't caused anything to break on my systems (yet). Make sure nothing else has it mounted first, though, otherwise you WILL corrupt the filesystem.

Hope this helps.

---

### Post by az on 2009-07-13
> **Fatman_UK said:**
> I think Windows sets a "locked, do not mount" flag in the NTFS partition header. Sometimes NTFS doesn't get unmounted properly and the flag isn't removed, so Ubuntu sees the flag and thinks "better not mount this".

Sometimes I need to mount manually and specify the "force" option. I don't recall the exact syntax (it's been a while), but it's something like:

$ sudo mount -t ntfs -o force /dev/sdb1 /win

It hasn't caused anything to break on my systems (yet). Make sure nothing else has it mounted first, though, otherwise you WILL corrupt the filesystem.

Hope this helps.


Try

sudo ntfsfix /dev/sdb1

first.

---

