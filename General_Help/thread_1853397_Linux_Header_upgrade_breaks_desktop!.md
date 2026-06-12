---
title: "Linux Header upgrade breaks desktop!"
date: 2011-10-02
forum: General Help
---

### Post by qprfact on 2011-10-02
Hi there,

I ran an update this morning, and since then I can login and get the desktop background, but there are no title bars, no icons on screen and right clicking mouse does nothing, Drives are clearly there as I can Command-K to them from my Mac, but even with several reboots and trying the various options within recovery mode, I am still faced with the same situation.

I checked in /root/.synaptic/log and can see there a file called 2011-10-02.083040.log - that is the one I did this morning. 

Nano'ing the log shows it carried out some updates to Firefox (which I won't list), but also:

gnome-power-manager
libgksu2-0
linux-generic (2.6.32.33.39) to 2.6.32.34.40
linux-generic-pae (2.6.32.33.39) to 2.6.32.34.40
linux-headers-generic (2.6.32.33.39) to 2.6.32.34.40
linux-image-generic (2.6.32.33.39) to 2.6.32.34.40
linux-image-generic-pae (2.6.32.33.39) to 2.6.32.34.40
linux-image-server (2.6.32.33.39) to 2.6.32.34.40
linux-libc-dev
linux-server
python-smartpm
xulrunner

I think it's one of those "(2.6.32.33.39) to 2.6.32.34.40" instances, but am a bit stumped!

Is there a way I can either:

1. Get desktop to load properly as I am; or
2. Somehow revert to the version before the upgrade this morning?

Thanks in advance!

---

### Post by mcduck on 2011-10-02
What kind of graphics card you have, and are you using the drivers from Ubuntu's repositories or have you installed the drivers from AMD/nVidia manually?

At least the last time I used the proprietary drivers from the graphics card manufacturer, they had to be reinstalled after every kernel update...

Anyway, you can simply select an older kernel version from the Grub boot menu. It's definitely not a good solution in the long run, the kernel updates are done for a good reason, but at least that should allow you to get back to a working system if the problem really is caused by the new kernel.

---

### Post by qprfact on 2011-10-02
I think it's NVIDIA, but I'm unsure how to either check that or to install those from command line (I presume that's possible)

The GRUB menu only has entries with this kernel on it - no earlier ones are there. Even attempting to boot from the oldest option carries the same problem.

---

### Post by qprfact on 2011-10-02
Right, that was entirely wrong!

lspci shows:

VGA Compatible controller: VIA Technologies CN700/P4M800 Pro/P4M0 CE/VN800 [S3 UniChrome Pro]

which according to this article - [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) - should be supported under OpenChrome

---

### Post by qprfact on 2011-10-02
I just checked grub for kernels installed:

update-grub

response was:


Found kernel: /boot/vmlinuz-2.6.32-34-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-34-generic
Found kernel: /boot/vmlinuz-2.6.32-33-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-33-generic


So it doesn't appear I have any older kernels

---

### Post by mcduck on 2011-10-02
> **qprfact said:**
> I just checked grub for kernels installed:

update-grub

response was:


Found kernel: /boot/vmlinuz-2.6.32-34-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-34-generic
Found kernel: /boot/vmlinuz-2.6.32-33-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-33-generic


So it doesn't appear I have any older kernels

Well, clearly you *do* have two kernel versions installed, 2.6.32.33 and 2.6.32.34. ;)

(or actually four, since you also have both generic and generic-pae kernels)

---

### Post by qprfact on 2011-10-02
Well, yes, but both produce the same problem which I didn't have prior to the update. So I am still stuck, unfortunately!

Anything else I can try? A reinstall?

---

### Post by haresear on 2011-10-02
Before going that far, I would try reinstalling the video driver package mentioned in the link you provided, assuming you can log into a tty terminal (Alt-Ctl-F1).

E.g.:

sudo apt-get install --reinstall xserver-xorg-video-openchrome

---

### Post by qprfact on 2011-10-02
I gave that a try - no dice!

Anything else I can try before a reinstall?

---

### Post by Blasphemist on 2011-10-02
I wouldn't re-install. This sounds like an issue with the gnome panels. I haven't used lucid in a long time but I found this for instructions on resetting the panels in lucid. [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by qprfact on 2011-10-02
Hi Jim,

It was worth a try but that didnt work either. I think the problem is wider than the panels aspect as right clicking on the desktop achieves nothing either.

Really frustrating!

---

### Post by Blasphemist on 2011-10-02
Try checking this out and see if you can sort out a solution. [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

There should be an option on the grub screen for previous versions. See if one of those changes the issue. I didn't look at this complete document but I think it's saying that the open source driver isn't in the kernel for that card. It needs installed I think.

---

