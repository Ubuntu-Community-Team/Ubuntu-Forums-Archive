---
title: "Where is 'Local Disk' defined"
date: 2011-10-31
forum: General Help
---

### Post by dave0109 on 2011-10-31
I'm trying to find out where the definition is for the 'Local Disk' mount point, i.e. the one that my Windows install is sat on.  I want to either remove it, or change the settings to read-only, because I want to setup VirtualBox to run with that installation.

I tried putting an entry into /etc/fstab, but it didn't like the ntfs type.

I've been running a search on all files but that's been running for over 24 hours now and whilst there have been some hits, none of them hold the details that I want.

I've done numerous searches on here and the search engines, but can't find an answer.

I've hidden the icon from the desktop, through the settings, but I also have the 'Places' applet in the top panel and it's possible to mount it there.  I don't want to accidently do so, once I've got the VM setup.

Anyone?

---

### Post by Toz on 2011-10-31
This might help: [http://ubuntuforums.org/showpost.php?p=10230444&postcount=54]("http://ubuntuforums.org/showpost.php?p=10230444&postcount=54").

---

### Post by dave0109 on 2011-10-31
Thanks, I've added the rules file and just waiting for a task to finish before I reboot.

Would still like to know where the thing is defined though, so I could set it to mount read-only... but that's more a curiousity thing now.  Hiding the option will suffice.

---

### Post by Toz on 2011-10-31
udev handles these things now. Its a pretty heady topic - one that I'm still trying to wrap my head around. Anyways, here are some links that might be of interest:

- [http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-u]("http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-u")
- [https://wiki.archlinux.org/index.php/Udev]("https://wiki.archlinux.org/index.php/Udev")
- [http://manpages.ubuntu.com/manpages/oneiric/man7/udev.7.html]("http://manpages.ubuntu.com/manpages/oneiric/man7/udev.7.html")
- [http://wiki.debian.org/udev]("http://wiki.debian.org/udev")
- [http://www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

---

### Post by dcstar on 2011-11-01
> **dave0109 said:**
> I'm trying to find out where the definition is for the 'Local Disk' mount point, i.e. the one that my Windows install is sat on.  I want to either remove it, or change the settings to read-only, because I want to setup VirtualBox to run with that installation.
........

Just put it in /etc/fstab with the "noauto" option - like any other internal partition that you don't want accidentally mounted.

Use the **pysdm** tool if you don't know how to do it manually.

---

### Post by dave0109 on 2011-11-01
> **dcstar said:**
> Just put it in /etc/fstab with the "noauto" option - like any other internal partition that you don't want accidentally mounted.

That's what I did in the end.  Then trying to mount the partition results in an error because normal users can't mount NTFS partitions with FUSE (or something), which is fine because it stops me doing something that I don't want.  If I run the mount command as root, then I get the partition OK, and I've set it to read-only.

Of course, this results in 2 entries called 'Local Disk' within Gigolo, but I can live with that.

Thanks Toz for the links, something to browse at lunchtime. :)

---

### Post by Toz on 2011-11-01
If you use the udev rule from post #2 it will prevent the display (presentation) of the hidden partition in the desktop environment. But you can still mount that partition whenever you want. It might get rid of the double entry in gigolo.

---

### Post by dave0109 on 2011-11-02
Unfortunately not.  The option is hidden from the places menu, but still appears in Gigolo.  I can live with it, but I feel like I've lost. :)

---

### Post by Toz on 2011-11-02
I don't have my hidden drive showing up in gigolo. Aren't those just bookmarks anyways, that can be deleted if not required (in gigolo)?

---

### Post by dave0109 on 2011-11-03
I believe the ones created by udev are not bookmarks, and cannot be deleted.

---

