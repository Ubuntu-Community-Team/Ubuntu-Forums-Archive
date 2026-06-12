---
title: "Ubuntu no longer accepts input in X"
date: 2010-07-16
forum: General Help
---

### Post by creatorbri on 2010-07-16
I can no longer use a keyboard or mouse in Ubuntu!

Flash has worked just fine on this computer since I got it setup right. But lately it has had difficulty playing any sound.

Well today I was just working away and I loaded some video that used Flash and the whole machine locked up entirely.

After a hard reboot, I can still type in my password to get to the desktop. But once Gnome loads, I am completely unable to use either my mouse or keyboard. Everything else appears to be working correctly, but with no mouse or keyboard, there's really nothing I can do but reboot. (Another odd symptom is that my taskbar panels appear darker than usual).

I have a fairly new ASUS laptop running Windows 7 Home 64-bit and Ubuntu 9.10 Karmic x64 (dual booted, GRUB managed).

Any ideas what would be causing this or how I can fix it?

---

### Post by creatorbri on 2010-07-17
Please, does anyone have any ideas? I use my Ubuntu machine for my work and I'm going to be in a world of hurt if I can't get the thing working again :(

I should mention that I AM able to move the mouse cursor around the screen, and the OS appears to be fully operational except that it just doesn't recognize any Keyboard or Mouse actions. :(

---

### Post by SaintDanBert on 2010-07-17
First, dance with settings to re-enable keyboard restart of your X-server -- traditionally CTRL-ALT-BACKSPACE. When things stall, can you reset your X-server?

Next, try to access a console:  CTRL-ALT-F1, ... CTRL-ALT-F4 (maybe more). this will take you away from your graphics desktop to a character interface. Can you get to a console?  login?  type commands?
If you cannot get you a console, that is one sort of "system stall".
If you can get to a console and do things, then your system is running and the desktop [aka, X-windows (X11, Xorg), etc] has stalled.

If you can get to a console, they you can use commands like **htop** to see what is going on without using power-off to force a reboot.

Also, which video and display hardware is involved. In my case, I have Intel parts and there are known issues and interventions that deal with stalled X11. Your mileage may vary.

~~~ 0;-Dan

---

### Post by creatorbri on 2010-07-22
Thanks for your help! After 6 days and a bunch of fiddling (all to no effect), I booted into X again and just started randomly clicking things and pounding keyboard keys. Everything suddenly started working again. I have no idea why, but I uninstalled a couple of programs I'd installed recently. Hopefully one of those was the offender and the problem will just be gone -- won't know until I reboot again (which I'm rather afraid to do at this point)!

---

### Post by SaintDanBert on 2010-07-25
I feel like the auto mechanic who moves a flat tire to an alternate wheel and the puncture goes away.  Don't know what I did, but I'm glad it helped...

X-windows has always been a black-art -- starting with the fact that the "client" is the computer and the "server" is the display.  X11 and Xorg continue to evolve in functionality and the docs follow behind at a reasonable rate. Most of the books are X11R6 which is close enough to current to be useful.

Just a thought, while there are system-wide settings and workings, almost all of them can be set on a per-user basis. You can create a separate user and then tinker with the hidden files and folders in that user $HOME without messing with your primary login. For details, start with **man xorg** and **man xorg.conf**.

Happy reading,
~~~ 0;-Dan

---

