---
title: "How can I change the display from 16bit to 32bit or vice versa?"
date: 2009-12-13
forum: General Help
---

### Post by amar1089 on 2009-12-13
I am running Linux Ubuntu 9.1 and I am trying to to change the display sitting from 16bit to 32bit or vice versa. How would I do that?

---

### Post by hansdown on 2009-12-13
Hi amar1089.

Click system> preferences> display.

You should see some different resolutions to choose from.

---

### Post by 3Miro on 2009-12-13
> **amar1089 said:**
> I am running Linux Ubuntu 9.1 and I am trying to to change the display sitting from 16bit to 32bit or vice versa. How would I do that?

If you have an nVidia video card you can use Nvidia-X-Serve-Settings from system -> admin or prefs. This has a lot of options for the nVidia cards.

---

### Post by Isengrin on 2009-12-13
In /etc/X11/xorg.conf, go to **Section Screen**, and change the **DefaultDepth** parameter to whatever you like.

---

### Post by amar1089 on 2009-12-13
> **hansdown said:**
> Hi amar1089.

Click system> preferences> display.

You should see some different resolutions to choose from.

I already tried that I could not find the option to change that.

---

