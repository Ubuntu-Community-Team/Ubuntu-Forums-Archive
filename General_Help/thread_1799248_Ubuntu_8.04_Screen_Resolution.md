---
title: "Ubuntu 8.04 Screen Resolution"
date: 2011-07-07
forum: General Help
---

### Post by Brian Mines on 2011-07-07
My operating system is Ubuntu 8.04.  I have been using this system for more than three years.  The screen resolution has always been 800 x 600.  I want to change this screen resolution to a finer resolution.
In going to System, Administration, Nvidia, the Nvidia window comes up with the message :
'You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the x server.'
In Terminal mode I have access as the root user.  My question is :
'What code do I enter to restart the x server?'

---

### Post by seawolf167 on 2011-07-07
Welcome to the forums!

Try:

```
sudo nvidia-xconfig
startx
```

If you need to stop the server first, hit [CTRL][ALT][F1] to enter tty1, then type

```
sudo service gdm stop
sudo nvidia-xconfig
sudo service gdm start
```

---

### Post by mikewhatever on 2011-07-07
You can just log out of session to restart xserver, alternatively,
```
sudo /etc/init.d/gdm restart
```

---

### Post by psusi on 2011-07-07
8.04 is depreciated and no longer supported on desktops.  You should upgrade to 10.04.  A clean install of 10.04 should "just work" with your monitors native resolution.  No settings needed.

---

