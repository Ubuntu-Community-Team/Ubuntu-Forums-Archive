---
title: "Ubuntu boots to console and won't load anything"
date: 2009-09-28
forum: General Help
---

### Post by gobberpooper on 2009-09-28
This is very strange. I got up to eat dinner and when I got back it was a black screen at the console, asking me to login. I logged in and then I rebooted and entered GRUB and started from a different kernel. That didn't work so I used the commands
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.copy
```
and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
but it told me that it's a read-only file system. Now I'm booting from the Ubuntu disc to see if that does anything.

---

### Post by tuxxy on 2009-09-28
Try remounting the driver as read write? then run sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by gobberpooper on 2009-09-28
thanks for the reply. How do I remount as read-write?

---

### Post by undecim on 2009-09-28
sudo mount -o remount,rw [filesystem or mountpoint]

although it shouldn't be mounted as read-only unless there is a problem. Try booting without the "quiet" option (edit the line in grub) and see if you get any message about your root filesystem

---

### Post by bluTaz on 2009-09-28
hmmm...  could you of switched to a virtual terminal(tty) by mistake.

try pressing ctrl+alt+F9... should be the right one... if not... just go from ctrl+alt+F1, ctrl+alt+F2, ctrl+alt+F3, .... and so on ... see if it gets you back where you need

---

### Post by gobberpooper on 2009-09-28
it's not a virtual terminal. They're all at "shridhar-desktop login: _" and booting with the quiet option doens't do anything.  Exactly how do I do the read/write remount?
Is there a way to fix it using the LiveCD?

---

### Post by gobberpooper on 2009-09-28
Okay I've decided I'm going to create a new partition for my files and then reinstall ubuntu over the first partition and then mess around with it to get everything back to normal.

---

