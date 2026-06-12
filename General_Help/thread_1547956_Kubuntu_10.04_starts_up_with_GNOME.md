---
title: "Kubuntu 10.04 starts up with GNOME???"
date: 2010-08-07
forum: General Help
---

### Post by xXxBlender3DxXx on 2010-08-07
I have just started up Kubuntu, and it shows the Ubuntu desktop instead of Plasma. Before this, the only change I did was remove my Broadcom WiFi card because Kubuntu sometimes couldn't boot because of some error mentioning the bcm driver and phy5.

I removed the card, and no errors on boot. Now, I can't get on the internet because Kubuntu can't connect to anything. I see all of the networks, but I guess GNOME is interfering with Network Manager...

Any ideas?

---

### Post by bergfly on 2010-08-10
Are you selecting KDE at the login screen? If you are auto logging in, log out and select KDE from the dropdown from the icon that appears to the bottom left of the normal KDM login screen. If you are seeing the Gnome login screen rather than KDE, you have GDM running rather than KDM. The X session environment selector is somewhere along the bottom.

Hope that makes some sense.

---

### Post by xXxBlender3DxXx on 2010-08-10
It shows the KDE login, but starts Gnome. I'm quite confused.

---

### Post by bergfly on 2010-08-10
To confirm, you are pulling down the list of options off the little icon that looks like a list and checking the checkbox next to KDE and then logging in..?

What other options are showing on this list?

---

### Post by jcolyn on 2010-08-10
I was not aware that Kubuntu installed the Gnome desktop.

Kubuntu=KDE??

Ubuntu=Gnome??

---

### Post by xXxBlender3DxXx on 2010-08-10
Oops, after re-reading my original post, I left out something (and did a TERRIBLE job at explaining): I installed avant-window-navigator, which in turn dragged 200mb of GNOME stuff with it onto my HDD.

After I rebooted, I was dropped to the shell login. I then proceeded to kill kdm, gdm, and looked at the xorg log. Xorg said it can't detect displays or something, so I removed my NVIDIA driver (from NVIDIA.com) and reinstalled it. Still no luck...

It's good now (no compositing, but at least I have a desktop environment), but I'm still trying to sort it out. But yes, it does login directly into GNOME (some really ugly theme, too), and clicking on the KDE option at the login prompt yields the same results as I described before...

---

### Post by bergfly on 2010-08-11
Ok I'm a bit clearer on this, thanks for the update. MY guess is all the reconfiguring has lost some core KDE files. I recommend reinstalling the KDE environment. If you want to make sure you have everything then use the package manager (you probably have synaptic now..) to install kde-full

or use the terminal to do this

```
sudo apt-get install kde-full
```

This is not going to give you all the kubuntu branded stuff, but should cover everything you could need to run KDE. 

It should ask you if you want to change to kdm as the default display manager, which I would do. Once it is all installed, I would then do a reboot and see where you are.

---

