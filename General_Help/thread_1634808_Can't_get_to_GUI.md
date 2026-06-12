---
title: "Can't get to GUI"
date: 2010-12-01
forum: General Help
---

### Post by icor1031 on 2010-12-01
Installed OS, it told me I should install nVidia drivers. I told it to go ahead, it told me to restart - I did.

I restart into a command prompt... No GUI. Turn off PC, on again, still - same thing. Asks me to login, but no GUI.

How do I get back?

---

### Post by sikander3786 on 2010-12-01
Welcome to the forums :-)

We need some more info, which graphics card model is this? Do you remember which version of drivers was activated? Which version of Ubuntu?

Try

```
sudo service gdm stop
```

```
sudo service gdm start
```

Any errors?

Try reconfiguring your graphics. First backup your existing xorg.conf. There might not be an xorg.conf, if it is not found, proceed to the next command.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Reconfigure graphics,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot,

```
sudo shutdown -r now
```

Any improvements?

---

### Post by icor1031 on 2010-12-01
Didn't help...

I have the newest ubuntu and I have absolutely no idea what the GPU is, because it's integrated into this board: MCP61PM-HM... This board is so bad that I had to get a modded BIOS just to make the CPU fan work. Can't find details on it.

---

### Post by icor1031 on 2010-12-01
Forget it, I'm just re-installing. I finally got into the GUI by restarting this time, but it made my resolution even lower and xrandr won't give it to me either...

So, soon as I reinstall.. how should I get my custom res?

xrandr --output vga --mode 1440x900 --rate 60

right?

---

### Post by sikander3786 on 2010-12-01
Please post the output of

```
lscpi | grep VGA
```

It would tell about your graphics chip.

If you go to System > Administration > Additional Drivers, do you see some drivers available?

---

