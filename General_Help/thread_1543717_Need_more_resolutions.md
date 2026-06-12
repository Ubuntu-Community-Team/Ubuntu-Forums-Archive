---
title: "Need more resolutions"
date: 2010-08-01
forum: General Help
---

### Post by AbraKdabra on 2010-08-01
I've installed the ATI drivers for my HD5770, but in the Catalyst Control Center I have just 5 resolutions, and not the one I need, 1280x960, is there anyway to change to that resolution not using the CCC?

Thanks.

---

### Post by prodigy_ on 2010-08-01
Press Alt+F2, type ```
xrandr -s 1280x960
``` into the dialog window that will appear and press Enter.

---

### Post by AbraKdabra on 2010-08-01
> **prodigy_ said:**
> Press Alt+F2, type ```
xrandr -s 1280x960
``` into the dialog window that will appear and press Enter.

Nothing happened.

---

### Post by prodigy_ on 2010-08-01
Then, most probably, your ATI driver isn't installed correctly.

Open terminal and run ```
fglrxinfo
``` command. What does it say?

---

Also you might want to read [this HOWTO](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).

---

### Post by AbraKdabra on 2010-08-01
fglrxinfo:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.0.10057 Compatibility Profile Context

---

### Post by prodigy_ on 2010-08-01
Hmm. Looks right. Still, if you can't change resolution, it's most probably a driver issue. Have you tried to reinstall the driver?

---

### Post by AbraKdabra on 2010-08-02
Yeah, I reinstalled it some times and the same resolutions are available, only 5.
I tried the open source but it gave me an error while installing so I came back to ATI's.
AND, there is one more thing, that is way more confusing than everything that happened in my entire life...
When I change the resolution in the CCC, something strange happens, it's like my window gets small and I see a border, but this border has some images from... WINDOWS, yeah, I see Winamp and Steam from Windows 7, I was like :| when I saw it, here's a screenshot:

[[IMG]http://img405.imageshack.us/img405/1003/pantallazo1hg.th.png[/IMG]](http://img405.imageshack.us/my.php?image=pantallazo1hg.png)

That grey thing you see, thats Winamp, and the green thing at the bottom left, thats my Steam avatar, weird.

So, I changed my resolution in the default Screen configuration, and it's OK, but I still don't see 1280x960.

---

