---
title: "nvidia-settings wont write to xorg.conf"
date: 2009-12-02
forum: General Help
---

### Post by play_ on 2009-12-02
Hi.

I use nvidia-settings to set up my displays(dual screen, etc). When i'm done, i cilck apply and they look fine. But when i click "Save to X Configuration File", i get a message that says "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

And when I check xorg.conf, this is what it has:

> Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


The drivers seem to be installed right. I'm using compiz and all their glorious 3D effects and animations.

How can i make it save to xorg.conf? I have also tried sudo nvidia-settings

using ubuntu 9.10 x86

---

### Post by |Porsche on 2009-12-02
A) Ensure you are can write to that file.
B) Save the file somewhere else, then move it to /etc/X11/xorg.conf with a user that can write to /etc/X11.

---

### Post by wojox on 2009-12-02
Open the terminal:

```
sudo nvidia-xconfig
```

Then:

```
gksudo nvidia-settings
```

Then try setting everything.

---

### Post by play_ on 2009-12-02
> **wojox said:**
> Open the terminal:

```
sudo nvidia-xconfig
```

Then:

```
gksudo nvidia-settings
```

Then try setting everything.


sudo nvidia-xconfig:
> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


But, it did seem to work. It did write to the file.


thanks the two of you for the replies :)

---

### Post by wojox on 2009-12-02
Good to here.

---

### Post by takingbackbenny on 2009-12-08
I had the exact same problem and this worked perfectly, thanks wojox. I wasn't aware that I needed root privileges to save the config file, was doing my head in as to why I couldn't save my resolution etc but this fixed it!

---

