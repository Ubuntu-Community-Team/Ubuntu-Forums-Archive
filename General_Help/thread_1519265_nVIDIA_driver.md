---
title: "nVIDIA driver"
date: 2010-06-27
forum: General Help
---

### Post by maghoxfr on 2010-06-27
I have the 173 nvidia driver installed from synaptic but when I get on the Hardware manager window it says that "the driver is activated but it's not being used currently" what does that mean? I'm having some troubles with video performance and I'm not even using the pc for gaming or anything "heavy-duty". I get flashes whenever I open/close/minimize a window or when I start session, nothing important but I'd like it to run smoothly.

I can't use compiz and it don't even allow me to choose the normal radio button in setting the desktop effects appearence. I didn't use it anyway but I'd like to have it running at its best.

 Does anyone know how could I "USE" this driver or enhance the performance so it's flawless?

---

### Post by WorMzy on 2010-06-27
Try this:

First, make a backup of /etc/X11/xorg.conf (in case something goes wrong)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
The file may not exist, so don't worry if you get an error saying that.

Next, run the following:
```
sudo nvidia-xconfig
```

Finally, restart X by either restarting, or switching to a tty (e.g. Ctrl+Alt+F1) and running ```
sudo /etc/init.d/gdm restart
```

Note: Save any open documents first.

---

### Post by maghoxfr on 2010-07-14
Thank you very much WorMzy, you saved me, I was going crazy. It worked, it was simple and fast, a miracle for me!

Thanks

---

