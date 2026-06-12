---
title: "Enable re-attached mouse/keyboard via ssh?!"
date: 2010-05-19
forum: General Help
---

### Post by as2003 on 2010-05-19
I had 9.10 x64 Desktop installed on a nettop I have (that I normally run headless), and yesterday I decided to take the plunge and update to 10.04.

So, I plugged in a screen and usb mouse/keyboard and set to work.

It was 1am, and it was telling me it had 3hrs left to install all the new packages, so I unplugged the screen and usb mouse/keyboard, left the box running, and went to bed.

This evening, I plugged it all back in again to check progress. It's asking if I want to remove obsolete packages. I do, but neither the mouse nor keyboard work!

I can access the box via SSH like I normally do; is there any way I can re-enable the keyboard from there?

I'm reluctant to restart the box (via ssh) mid-way through such a complicated upgrade.

Thanks for any help!

lsusb (with mouse/keyboard wireless unplugged):
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
lsusb (with mouse/keyboard wireless attached):
```
Bus 004 Device 005: ID 045e:005f Microsoft Corp. Wireless MultiMedia Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by as2003 on 2010-05-24
In the end I just restarted. There are some possible solutions though:

[http://serverfault.com/questions/143778/enable-re-attached-mouse-keyboard-via-ssh](http://serverfault.com/questions/143778/enable-re-attached-mouse-keyboard-via-ssh)

---

### Post by jerome1232 on 2010-05-24
Not that it helps but in the future I'd use screen, that way you could've logged in via ssh and grab the session.

---

