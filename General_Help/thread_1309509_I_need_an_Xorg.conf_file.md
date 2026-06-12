---
title: "I need an Xorg.conf file"
date: 2009-11-01
forum: General Help
---

### Post by NCLI on 2009-11-01
But Karmic no longer has one. Is there a command I can use to generate one? I need it to install a driver for my touchscreen.

---

### Post by pastalavista on 2009-11-01
In terminal, try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by NCLI on 2009-11-01
Nope, already tried that one.

---

### Post by kaibob on 2009-11-01
If you are using nvidia, you can try nvidia-xconfig

[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)

> The system X configuration file is found and read into memory. If no configuration file can be found, nvidia-xconfig generates one from scratch using default settings; in this case, nvidia-xconfig will automatically determine the name of the X configuration file to create: /etc/X11/xorg.conf if the X server in use is X.org or /etc/X11/XF86Config if the X server in use is XFree86. 

---

### Post by girto on 2009-11-01
what is the output of lshal?
```
lshal
```

---

### Post by NCLI on 2009-11-01
> **kaibob said:**
> If you are using nvidia, you can try nvidia-xconfig

[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)
Unfortunately not, that's how I did it on my desktop. This is a netbook with an embedded intel GPU.
> **girto said:**
> what is the output of lshal?
```
lshal
```
Is there something specific you need from that output? It's quite long.

---

### Post by girto on 2009-11-01
HAL is what dynamically recognizes touchscreens and other input devices in Karmic. It is scheduled to be changed to udev in the future as HAL is being deprecated.

HAL must recognize your touchscreen via an fdi file so that it launches the proper driver, such as evtouch, and assign the required parameters.

lshal will show the encountered devices and how they have been recognized/treated.

If your touchscreen is usb, include as well the output of:
```
lsusb
```

Of course, you can still do that via an xorg.conf file, but that will be inflexible due to the new xorg.

---

### Post by NCLI on 2009-11-01
Ah, well, I already know which touchscreen it is.

[QUOTE=lsusb]Bus 005 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
[/QUOTE]

The evtouch driver makes the computer crash when I've used the touchscreen for a while, and thus I arrive at needing an xorg.conf in order to install the official eGalax driver.

---

### Post by ranch hand on 2009-11-01
If you have something that actually needs the xorg.conf file it will be generated.  If that is not the case, having it may hose your booting in.

---

### Post by liquidbee on 2009-11-01
What exactly are you looking for ? For a way to create an empty xorg.conf file so the driver could automatically fill it with all kinds of weird stuff or there was a part which you needed to edit manually ?

```
sudo touch /etc/X11/xorg.conf
```

Reload ( restart PC ) X.org and the file will be automatically picked up by X.org - add whatever you need and you should be fine.

---

### Post by WorLord on 2009-11-01
Exit X (that means stop gdm and drop down to a terminal), then type

sudo X -configure

This will create an xorg.conf.new in /root.  Copy it to /etc/X11 with the following command:

cp /root/xorg.conf.new /etc/X11/xorg.conf 

for the xserver to recognize it next boot.  Modify it to your heart's content.

---

### Post by girto on 2009-11-01
I guess HAL can be used with any driver.

In any case, try:
```
sudo X -configure
```

This should create an xorg.conf.new in /root

---

