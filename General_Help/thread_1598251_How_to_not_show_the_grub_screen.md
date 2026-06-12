---
title: "How to not show the grub screen"
date: 2010-10-16
forum: General Help
---

### Post by cam3roon on 2010-10-16
Hi. When I start my system, eventhou I have installed only Ubuntu on my machine, it's still showing me the grub menu. I looked for solutions in Internet, but I'm a noob and they only make me more confused.

How can I make the computer not to show this menu?

---

### Post by spikoley on 2010-10-16
It depends on which version of Ubuntu you are using.  Ubuntu recently upgraded to Grub 2.  More than likely this is the version you have.

Open the Grub 2 configuration file.  (gksudo is sudo for GUI apps)
```
gksudo gedit /etc/default/grub
```

Look for this line and change it to 0.  Then save the file.
```
GRUB_TIMEOUT=10
```

Update Grub 2
```
sudo update-grub
```

Reboot and the Grub menu should not show up.

If you are using an older version of Ubuntu you will need to edit /boot/grub/menu.lst.

---

### Post by CharlesA on 2010-10-16
What spikoley posted should work.

Here's some more info about grub2: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by cam3roon on 2010-10-16
Thanks spikoley, it worked

---

