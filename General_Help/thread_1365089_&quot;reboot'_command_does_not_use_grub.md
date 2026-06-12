---
title: "&quot;reboot' command does not use grub"
date: 2009-12-26
forum: General Help
---

### Post by landersohn on 2009-12-26
I ran into a curious situation after upgrade to karmic: if I use "reboot" (either from the command line or the GNOME applet) the system does not show the grub boot options screen but boots straight into the kernel that comes with karmic. This is pretty annoying since I do explore and build my own kernels, so afgter a compile I have to turn my laptop off to boot the new kernel.
What is also curious is that the reboot command does NOT boot the same kernel it was called from but the kernel that ships with karmic.
Does anyone have anyh idea how to teach "reboot" to use the grub boot loader?
Thanks

---

### Post by taurus on 2009-12-26
Sounds like you have set the timeout to 0 in /etc/default/grub.

---

### Post by landersohn on 2009-12-26
Thanks for the tip. Unfortunately I don't have that file.

---

### Post by landersohn on 2009-12-26
.... to add to my previous reply: my menu.lst file as a 10 sec timeout

---

### Post by taurus on 2009-12-26
I thought Karmic uses Grub2 where there is no more /boot/grub/menu.lst.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by audiomick on 2009-12-26
Grub 2 only comes in with a fresh install. If you use the updater, it doesn't change from the old grub.

---

### Post by Madel on 2009-12-26
Try:
sudo shutdown -r now

to reboot.

---

### Post by landersohn on 2009-12-26
Madel,
that command creates the same behavior

---

### Post by Compintuit on 2009-12-26
> **landersohn said:**
> Madel,
that command creates the same behavior

you could try to wither upgrade, or reinstall grub.

---

### Post by dcstar on 2009-12-27
> **landersohn said:**
> I ran into a curious situation after upgrade to karmic: if I use "reboot" (either from the command line or the GNOME applet) the system does not show the grub boot options screen but boots straight into the kernel that comes with karmic. This is pretty annoying since I do explore and build my own kernels, so afgter a compile I have to turn my laptop off to boot the new kernel.
What is also curious is that the reboot command does NOT boot the same kernel it was called from but the kernel that ships with karmic.
Does anyone have anyh idea how to teach "reboot" to use the grub boot loader?
Thanks

Chances are it **is** using Grub but the video display is not resetting correctly on the reboot so you don't see anything until the splash screen loads.

Set Grub to use the "saved" settings for last entry selected, and try to set the VGA mode as well.

---

### Post by landersohn on 2009-12-27
David,
good idea, I'll try it out. Problem is, though, that it does not boot the kernel that is the default in menu.lst. if the screen just stayed dark, the grub timeout expires and the default OS boots, I would expect a different kernel than the one I am getting.

---

### Post by landersohn on 2009-12-27
is it possible this may be somehow GDM related? I tried to downgrade my gdm 2.8 back to 2.20 from jaunty. Didn't work well so I undid those changes are I am back to gdm 2.8

---

### Post by dcstar on 2009-12-27
> **landersohn said:**
> is it possible this may be somehow GDM related? I tried to downgrade my gdm 2.8 back to 2.20 from jaunty. Didn't work well so I undid those changes are I am back to gdm 2.8

Test it by creating a new user, logging in to it and seeing how it behaves when rebooted.

If the new user works differently, then there may be a bad configuration in the other user.

---

### Post by landersohn on 2009-12-27
David,
tried your suggestion, no luck.
One curious thing is also that the LED indicators on my laptop never go off: when I do a shutdown, I see for exmaple the wireless LED change colors to inidcate the wireless adaptor is turned off because everything goes blank then the laptop shuts off. During the reboot sequence the LEDs never change state, meaning that a lot of the hardware never gets fully re-booted.
It's almost as if I only get logged out of the GNOME session and dumped back at the loging screen.

---

### Post by falconindy on 2009-12-27
This is one of several things I had on my 's' list that even had me leave Ubuntu. You request a restart, and the OS does something similar to what I do now with dropping down to init 1 (stopping all services) and back up to 5 (graphical environment). System uptime does reset itself, so maybe its using kexec? In any event, the OS never fully gives up control.

Really annoying. Happened on 2 out of 3 of my rigs I had Ubuntu setup on.

---

### Post by landersohn on 2009-12-28
falconindy,
thanks for your post, your mention of kexec did the trick: reboot or shutdown -r now indeed uses kexec by default if kexec-tools is installed.
By changing the /etc/defaukt/kexec file I could restore my desired hard reboot behavior

---

### Post by falconindy on 2009-12-28
> **landersohn said:**
> falconindy,
thanks for your post, your mention of kexec did the trick: reboot or shutdown -r now indeed uses kexec by default if kexec-tools is installed.
By changing the /etc/defaukt/kexec file I could restore my desired hard reboot behavior
Wow. That's unexpected. Neat, though. Glad I could help.

---

