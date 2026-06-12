---
title: "Gamepads not fireing any kind of events"
date: 2009-09-16
forum: General Help
---

### Post by CyanPrime on 2009-09-16
I've been trying to get my gamepads to work with Ubuntu (and Xubuntu). I've tried it on the current alpha for Ubuntu, and Xubuntu 9.04, and I get nothing. The lights on the gamepads come on so I did some digging in my system to see if it really registered or not, and I found the /dev/input/ folder. Now when I plug in my Logitech Precision and Dual Action I get jo0 in said folder, and in the subfolder /by-id/ I get some files with the gamepad name on them, so I am quite sure the system knows the controllers are in.but when I run xev none of my  controls will fire an event of any kind.

Please help.

---

### Post by CyanPrime on 2009-09-16
bump

---

### Post by CyanPrime on 2009-09-16
bump

---

### Post by CyanPrime on 2009-09-16
=\

---

### Post by tomBorgia on 2009-09-16
Hi,

xev will show things the X-server is receiving... not necessarily everything else!

You could try using cat on the dev/<your device> file... open terminal and (as root / sudo)

```
cat /dev/<whatever file that appears when you connect your gamepad>
```

Press some buttons and you'll probably get some response... That'll show it's "working" to some extent.

As to getting it working in a game / program you'll probably need to tell the program which input to look at... as to whether it'll interpret the commands properly will be down to wheather the prog supports that type of gamepad.

Hope this helps!

Tom.

---

### Post by CyanPrime on 2009-09-16
This worked. Thank you very much!

---

### Post by tomBorgia on 2009-09-17
Your welcome :D

---

