---
title: "Automounting Read Only"
date: 2011-05-06
forum: General Help
---

### Post by LinuxCindy on 2011-05-06
Question for you all. I am trying to get my system so that when I insert USB drives they don't auto mount, and when I click on them in the filemanger they only mount read only. 

I am halfway there, as when I have used "gconftool-2 --set /apps/nautilus/preferences/media_automount --type bool false" to prevent the automounting. So thats working great.

However it looks like for the mounting of drives in read only mode it used to be (around 2008 or so) that this command would work "gconftool-2 --type list --list-type=string --set /system/storage/default_options/vfat/mount_options "[ro]"" However, it appears that at some point that was removed and no longer works.

Any idea on how I can get this to work? I just want to be able to click on the non-mounted USB device and when nautilus mounts it have it get mounted "ro" not "rw". Ideas?

Thanks so much!
Cindy

---

### Post by LinuxCindy on 2011-05-06
Just to reply to myself here, this is another source that is telling me that the gconftool-2 should do it for me: [http://www.linuxfromscratch.org/blfs/view/svn/general/hal.html](http://www.linuxfromscratch.org/blfs/view/svn/general/hal.html)

No such luck however. Any ideas?

Thanks

---

### Post by LinuxCindy on 2011-05-08
Looks like this needs to be done by Udev rules? Anyone know where I can find examples on editing udev rules for this purpose?

---

### Post by matt_symes on 2011-05-08
Hi

It's not directly related to your post (as it does not handle permissions) , but here's a basic primer on udev rules.

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

If you find a solution to your problem then please post it.

Kind regards

---

### Post by matt_symes on 2011-05-18
/

---

