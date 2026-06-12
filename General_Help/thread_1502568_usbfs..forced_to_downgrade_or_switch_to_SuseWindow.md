---
title: "usbfs..forced to downgrade or switch to Suse/Windows"
date: 2010-06-05
forum: General Help
---

### Post by ehsaan_sh on 2010-06-05
Hi,

We need to run a software which comes with a USB Dongle in HASP USBFS format. 

Apparently, usbfs is not supported in 10.4 so i am forced to downgrade or go to other distros or give up the linux dream and go to M$Win.

Any suggestion?

so the priorities are:
1- find a way to mount usbfs
2- downgrade to 9.10 safely

thanks

---

### Post by bruno9779 on 2010-06-05
It seems like it is being worked on:

[http://osdir.com/ml/kernel-team/2010-03/msg00414.html](http://osdir.com/ml/kernel-team/2010-03/msg00414.html)

---

### Post by bruno9779 on 2010-06-05
I have read some bugreports, on which, people managed by downgrading the kernel version only (it seems to be specific to 2.6.32)

---

### Post by ehsaan_sh on 2010-06-05
can you tell me how to do that?

thanks

---

### Post by davidmohammed on 2010-06-05
the bug report says its resolved upstream - have you checked if a [later kernel]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") fixes your issue?

You might want to download the latest 2.6.34 kernel to see if it is resolved.

---

### Post by ehsaan_sh on 2010-06-05
2.6.34 only made the system super slow (prob not compatible with nvidia)

Linux photonprec 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux

FSTAB:
--------------------------------------------
#none /proc/bus/usb usbfs defaults 0 0
usbfs /proc/bus/usb usbfs auto 0 0
#none /sys/kernel/debug/usb usbfs defaults 0 0
#none /proc/bus/usb usbfs devgid=127,devmode=664 0 0

---

### Post by davidmohammed on 2010-06-06
That in a weird way is probably good news!

Boot using the standard lucid kernel using grub.

I presume you are using a proprietary nvidia driver?  If so deactivate it in administrator - hardware drivers.  Reboot into the new kernel.

Does the PC now run at the correct speed and does usbfs work OK?

---

### Post by ehsaan_sh on 2010-06-07
hi thanks.

I did disable the nividia driver and it got faster.

But still it does not recognize usbfs as a valid mountable thing.

should i change anything in my fstab?

FSTAB:
--------------------------------------------
#none /proc/bus/usb usbfs defaults 0 0
usbfs /proc/bus/usb usbfs auto 0 0
#none /sys/kernel/debug/usb usbfs defaults 0 0
#none /proc/bus/usb usbfs devgid=127,devmode=664 0 0

---

### Post by ehsaan_sh on 2010-06-22
hola!

---

