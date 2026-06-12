---
title: "Ubuntu stopped working again - Boots to a console login prompt"
date: 2010-03-06
forum: General Help
---

### Post by Endolith on 2010-03-06
Yet again, Ubuntu has stopped booting correctly.  Now it shows the Ubuntu logo and then, instead of GDM, it shows a console login prompt.  

How do I go about troubleshooting this?

I'm in Windows XP (which I like a lot better than Ubuntu, because it actually works) but all my files and work are on my Linux partition.

---

### Post by flippo on 2010-03-06
Can you attach your /var/log/Xorg.0.log?

---

### Post by Endolith on 2010-03-06
Is that the problem?  I thought it was supposed to have a nice blue screen when X failed and it would use a failsafe mode.

---

### Post by flippo on 2010-03-06
If it can't find a screen to open, then it can't even do that.

Yep, it can't load your nvidia driver and it just quits.

Reinstall your nvidia driver and you should be good to go.

---

### Post by Endolith on 2010-03-07
Why would it suddenly be unable to load the nvidia driver?  How do I reinstall it?  Download a .deb in Windows and copy it over?

---

### Post by flippo on 2010-03-07
I *think* what you want to do is:```
sudo apt-cache search nvidia-glx
```a list of nvidia drivers should pop up, choose one then```
sudo aptitude reinstall <nvidia driver of your choice>
```

---

### Post by Endolith on 2010-03-08
That doesn't work.  It seems that none of the nvidia-glx packages are installed (?????), and when I try to install one, it says it needs to remove tons of packages.  It can't install anything anyway because the Wi-Fi isn't connected until after I log into Gnome.   :mad:

---

### Post by flippo on 2010-03-08
How did you install your nvidia drivers before? Did you download them from the nvidia website, or did you click the install drivers thing on the gnome gui?

---

### Post by Endolith on 2010-03-08
> **flippo said:**
> How did you install your nvidia drivers before? Did you download them from the nvidia website, or did you click the install drivers thing on the gnome gui?

used Jockey hardware manager thing

---

### Post by patchwork on 2010-03-08
You can login from the console, and activate your wireless:

```
ifconfig wlan0 up && iwconfig wlan0 essid NETWORK_ID key WIRELESS_KEY
```(from [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/) )

then get your drivers

EDIT: assuming wlan0 is the name of your interface, you can check using ```
ifconfig
```

---

### Post by Endolith on 2010-03-09
I connected up a cable and used aptitude to install nvidia 173 drivers.  It needed to remove liggl1-mesa-swx11.  After that it worked.  Did a conflict with third-party repositories force nvidia drivers to be uninstalled or something?  i don't remember ever seeing a screen asking me if i wanted to remove them.

---

