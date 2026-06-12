---
title: "Karmic loses keyboard / mouse focus"
date: 2009-12-21
forum: General Help
---

### Post by jrop on 2009-12-21
I just installed Karmic / 9.10 on my desktop, and at random times, the desktop "freezes".  This happens in GNOME, as well as XFCE.  The last time it happened though, was when I logged out of an account (I was switching users).  This time, though, the cursor was blinking in the textbox, but I could not type or click any of the buttons.

This is driving me nuts, so any help would be appreciated! :(  I'm just about to revert back to 9.04.

---

### Post by louvann on 2009-12-24
I can confirm this behaviour. There are several threads on this topic. Currently, I am in the impaired state where only some of the functionality of the mouse and keyboard are available. I have the poor behaviour only on my IBM thinkpad (8.10=>9.04). My DELL units (3: 9.04 or 9.10) are fine. It appears after extended use, but not right away.

Anyone, if there is any way to restart a process to cure this, please elaborate.

---

### Post by jrop on 2009-12-24
In my case, I have narrowed it down to the suspend feature.  On all accounts, I disabled suspend (System->Preferences->Power Management), and I haven't had a freeze yet.

This seems like a sloppy workaround to me, but hey- it keeps me from having to install Jaunty!

An interesting note: when the system does freeze, I can ssh into it and bring it down gracefully with the command: "sudo shutdown -r now".  So it seems that only X11 or the desktop environment (I tried GNOME and XFCE) are affected.

---

### Post by jrop on 2009-12-24
Well, I spoke too soon.  I just got another freeze (thought they seem a lot less frequent).  This time, the screen was white and shifted left ~100px, but I could move my mouse around.

Attached are a handfull of files from the /var/log directory that I was able to get via SSH.

I find this line interesting (from Xorg.0.log):
> (II) AIGLX: Resuming AIGLX clients after VT switch

There seems to have been a discussion on this on the following forum:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/63584](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/63584)

---

### Post by jrop on 2009-12-27
BTW, here's some info on my video controller:

Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by jrop on 2009-12-28
It seems a lot of people have this problem, but nobody has any answers. :(

Booted Jaunty from live usb and so far, no freezes.

---

