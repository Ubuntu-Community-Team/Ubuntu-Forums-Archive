---
title: "Configuring grub"
date: 2009-11-03
forum: General Help
---

### Post by nolsen01 on 2009-11-03
I had windows xp dual booting with opensuse.

I decided I didn't like opensuse and installed ubuntu on its partition. Does anybody have any idea what I need to do in order to configure grub so that I can get access to windows xp? Thank you.

---

### Post by XDevHald on 2009-11-03
Welcome to Ubuntu Forums.

Do the following: ```
sudo gedit /boot/grub/menu.lst
```

In this file you can see below it will show your menu boot list and you can edit the menu. Secondly, download Startup Manager from the Software Center or Synaptic and in there you can edit the menu boot list with just one click. Let us know if you need any further support.

---

### Post by drs305 on 2009-11-03
Which version of Ubuntu did you install - it makes a difference because it effects which version of Grub you have. You can also tell from the main Grub menu. At the top it will say 0.97 or 1.97xxx. The 1.97xxx one is the newer version, GRUB 2.

You can use StartUp-Manager with either grub *IF* your Grub menu already knows of it's existence. You can click on the "SUM" link in my signature line for information on this GUI app.

If you have GRUB 2, first run the following to see if it will locate your Windows installation. Watch the terminal commands as it runs to see if it locates the Windows install:
```

sudo update-grub

```

---

