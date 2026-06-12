---
title: "Grub problems"
date: 2009-10-08
forum: General Help
---

### Post by Phalangees on 2009-10-08
Hello,

I have upgraded to 9.10 a while ago and today I started installing some updates. When I came back, my screen was dark and I was unable to "wake it up." The activity light was not flashing so I shut down the computer. I could only turn it off by holding the button. I turned it back on and my grub bootloader was in place and everything looked great until I booted. I logged in and a message flashed about gnome not being installed correctly or something. All I saw was my wallpaper and my cursor. Nothing else. I had to hard shutdown again. Grub somehow no longer works. It just shows this:

grub>

I did a little searching and I was able to get Ubuntu to boot with the following commands:

root (hd0,1)
kernel /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot

But when it boots, the backlight turns on and off and nothing ever shows up for the login.

I would appreciate any help on this. Thank you!

---

### Post by mikewhatever on 2009-10-08
Such issues are expected with beta software. Karmic is rapidly moving towards the final release wit tons of updates comping in every day. Unless you enjoy testing, I'd recommend going back to Jaunty and waiting till a few weeks after the final release.

---

### Post by Phalangees on 2009-10-09
I was able to fix everything. For some reason my menu.lst got corrupted so by just using the configfile (hd0,1)/boot/grub/menu.lst.bak, and then editing individual lines to get into a working kernel, I was able to fix the problem. Once booted into ubuntu, I ran dpkg and was able to get everything up and running again. Then I just replaced the old menu.lst with a new one I created.

---

