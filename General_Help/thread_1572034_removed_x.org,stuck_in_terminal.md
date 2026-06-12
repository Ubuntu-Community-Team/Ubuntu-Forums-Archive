---
title: "removed x.org,stuck in terminal"
date: 2010-09-10
forum: General Help
---

### Post by soryu on 2010-09-10
i was trying to reconfigure xorg, i removed it now im stuck in the terminal
tried different commands.but nothing is helping. 
is there anyway i could save some data? 
 thinking reinstall.

---

### Post by WorMzy on 2010-09-10
How did you remove it?

It's worth noting that Linux will continue to work fine without xorg, so there's no need to reinstall the whole OS, just reinstall the packages you removed. The command line application for installing packages is:

```
sudo apt-get install <package name>
```

If you just removed xorg, reinstall with

```
sudo apt-get install xorg
```

Reconfiguring it depends on what graphics drivers you have installed.

If you're an nvidia user, run:
```
sudo nvidia-xconfig
```

Otherwise, you can get a generic xorg configuration by running:
```
sudo mv /etc/xorg/xorg.conf /etc/xorg/xorg.conf.old && Xorg -configure
```

---

### Post by soryu on 2010-09-10
when chosing to install, i get messages failed to fetch. maybe run apt-get update
when i run apt-get update iget failed to fetch again.
 
how do i check how im connected?
i have an ethernet and wireless card .

---

### Post by soryu on 2010-09-10
nvidia-xconfig =gtk warning cannot open display
sudo mv /etc/xorg/xorg.conf. /etc/xorg/xorg.conf.old && x= no such file or directory

---

### Post by realzippy on 2010-09-10
try (if nvidia-driver installed)

```
sudo nvidia-xconfig
```

---

### Post by Gunman1982 on 2010-09-10
> **soryu said:**
> when chosing to install, i get messages failed to fetch. maybe run apt-get update
when i run apt-get update iget failed to fetch again.
 
how do i check how im connected?
i have an ethernet and wireless card .

You probably aren't connected. Easiest solution is: Get a network cable, plug it into your router and execute 'sudo dhclient eth0' on the console/terminal.
If that doesn't work try eth1 instead of eth0.
If that doesn't work either you should give us information like: 
sudo iwconfig
sudo ifconfig

---

### Post by realzippy on 2010-09-10
If you **not** have ATI or Nvidia driver installed,you could simply delete xorg.conf  (no need for it since 9.10)...

```
sudo rm /etc/X11/xorg.conf
```

```
sudo reboot
```

---

### Post by soryu on 2010-09-10
> **Gunman1982 said:**
> You probably aren't connected. Easiest solution is: Get a network cable, plug it into your router and execute 'sudo dhclient eth0' on the console/terminal.
If that doesn't work try eth1 instead of eth0.
If that doesn't work either you should give us information like: 
sudo iwconfig
sudo ifconfig
 
 
 
not connected that was it.
  updating and installing  xorg, rebooting hope it worked.

---

### Post by soryu on 2010-09-10
thank you everyone for you're input.
i was searching sites for 1 hr.
 30min on the foums thanks.):P

---

