---
title: "Virtualbox USB grey on Maverick, where is /proc/bus/usb?"
date: 2010-10-15
forum: General Help
---

### Post by alfito on 2010-10-15
Hi all,

for making usb work on VBox guests I usually need to add the mount ponint for usb on fstab as is explained in several threads. But now on Maverick looks like /proc/bus/usb does not exist.
Any way to solve the greyed usb devices?

Thanks.

---

### Post by ferossan on 2010-10-15
I'm in the same boat. Anyone?

---

### Post by thuntley on 2010-10-15
Are you guys using the open-source version of VirtualBox?  If so, my understanding is that USB is disabled in the open-source version.  DL the closed-source version to get USB support.

---

### Post by ferossan on 2010-10-15
Got it to work (non-free VirtualBox).
Just follow post #2 here:
[http://ubuntuforums.org/showpost.php?p=9756001&postcount=2](http://ubuntuforums.org/showpost.php?p=9756001&postcount=2)
Don't forget to restart Ubuntu (maybe logout is enough)

---

### Post by Roger Norton on 2010-11-21
I am having a similar problem.  I have the PUEL version of virtualbox 3.2.10, with ubuntu 10.10 as host and windows xp sp3 as guest.  I have added my username to the vboxusers usergroup.  Two of my three usb devices (a pendrive and a printer) are not available in the guest, while a third works badly (speakers).  4 devices are listed as active usb devices in virtualbox, but are greyed out, including my webcam, which is not a usb device.  Also, access to CD-ROMs is uncertain, and windows xp hangs on restart.

I have tried the suggestions given in [http://forums.virtualbox.org/viewtopic.php?f=7&t=31146](http://forums.virtualbox.org/viewtopic.php?f=7&t=31146), but these have not worked.

Any suggestions?

---

### Post by sofoxy on 2010-11-21
> **ferossan said:**
> Got it to work (non-free VirtualBox).
Just follow post #2 here:
[http://ubuntuforums.org/showpost.php?p=9756001&postcount=2](http://ubuntuforums.org/showpost.php?p=9756001&postcount=2)
Don't forget to restart Ubuntu (maybe logout is enough)

The devices are still grayed out. How can you enable it. I'm using 10.10. Thanks in advance.

---

### Post by sofoxy on 2010-11-21
Got it working now. Just needed to be lp group to be able to use it on the guest.

---

### Post by ppmotskula on 2010-12-07
> **sofoxy said:**
> Got it working now. Just needed to be lp group to be able to use it on the guest.

Actually, you only need to be in the vboxusers group. However, logout alone is not enough, you'll have to reboot after having added yourself to this group before you can use USB on VirtualBox.

---

