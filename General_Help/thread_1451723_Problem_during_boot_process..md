---
title: "Problem during boot process."
date: 2010-04-10
forum: General Help
---

### Post by dlw on 2010-04-10
During boot up, after the white 'ubuntu' logo goes off, a sign in screen appears. It reads; 'Ubuntu 9.10 don-desktop tty1' ' don-desktop login:_'

The problem is the sign in screen is blinking on and off so fast I can not enter anything. My only option is to turn of the computer... then it happens every time I try to boot.

Any ideas on how to solve this?

dlw

---

### Post by Skidbladnir on 2010-04-10
Reinstall.  Probably off of a new disk.  It MIGHT be that GNOME or X11 is trying to start then crashing, starting, crashing, etc.  Try pressing CTRL+ALT+F1 after it starts "switching" and see if the shell stays there.  Otherwise, burn a new disk (at the slowest speed) and reinstall.

---

### Post by dlw on 2010-04-11
Thank you for responding.
I solve the problem by reinstalling 9.04 instead of 9.10.
My objective is to have multiple monitors and I now understand that 9.10 either does not support this or its very difficult.

dlw

---

### Post by lidex on 2010-04-11
> **dlw said:**
> Thank you for responding.
I solve the problem by reinstalling 9.04 instead of 9.10.
My objective is to have multiple monitors and I now understand that 9.10 either does not support this or its very difficult.

dlw

For that you may need to install using one monitor and get that going first then configure xorg.conf

---

