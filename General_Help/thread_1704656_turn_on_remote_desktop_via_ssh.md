---
title: "turn on remote desktop via ssh"
date: 2011-03-11
forum: General Help
---

### Post by gsi095 on 2011-03-11
Hi,
 
I have an AppleTV running a version of Ubuntu on a usb drive. I want to be able to use my iPhone as a wireless keyboard and mouse but the apps require that I turn on remote desktop in ubuntu. 
 
problem is, I use it for xbmc (crystalbuntu) and since the AppleTV only has 1 usb port, I cant plug a usb keyboard or mouse in as the flash drive with the OS on it is in the usb port.
 
I can ssh into the AppleTV and run terminal commands. Is there a terminal command to turn on remote desktop so I can use the iphone keyboard app?
 
Dave

---

### Post by doas777 on 2011-03-11
this is probably what you are looking for:
[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

---

### Post by gsi095 on 2011-03-11
> **doas777 said:**
> this is probably what you are looking for:
[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

The first few steps say to go and click an option which I can't do

---

### Post by nothingspecial on 2011-03-11
```
ssh -X user@host
vino-preferences
```

---

### Post by doas777 on 2011-03-11
> **gsi095 said:**
> The first few steps say to go and click an option which I can't do
read deeper. if you ssh in, and run the second gconftool command, it will enable the option.
vino-preferences is also a good option.

---

