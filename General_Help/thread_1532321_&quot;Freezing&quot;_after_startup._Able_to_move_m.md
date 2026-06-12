---
title: "&quot;Freezing&quot; after startup. Able to move mouse, cannot type/click"
date: 2010-07-16
forum: General Help
---

### Post by usersock on 2010-07-16
I just installed "Gnome Do", added/removed various apps on the "Docky" toolbar, and now Ubuntu "freezes" up when I reboot. 

Two windows appear at startup; the "Gnome Do" search window, and a window for "**Unlock Login Keyring**". I did open a keyring/password app on the new "Docky" toolbar so this may be part of the issue. The mouse moves around and the clock is still ticking away, so it's not truly frozen, but I am unable to click or type. Because of this, I cannot enter a password in the Keyring.

I'm guessing the problem is either "Gnome Do" or the Keyring.

---

### Post by MooPi on 2010-07-16
An easy fix to get a usable desktop would be to reboot and restart in recovery console. Remove the offending application from docky . To enter recovery console hit the Esc button right after the bios post to enter grub. Rcovery console will be listed as an option. Recovery console is command line are you able to function with command line.

---

### Post by usersock on 2010-07-16
I've tried recovery a few times, but it's doing the same thing. I should probably add that I'm dual-booting with Windows 7, and to get to recovery I simply choose it from a list at start up. Could that be the wrong type of recovery?

---

### Post by MooPi on 2010-07-16
You can also use the live CD that you installed Ubuntu with.

---

### Post by usersock on 2010-07-16
I was able to get past the freezing by using the boot disc. Apparently, [I'm not the first person to have this happen]("http://ubuntuforums.org/showthread.php?t=1469775"). Guess I should go file a bug report with Gnome Do.

Thanks MooPi!

---

