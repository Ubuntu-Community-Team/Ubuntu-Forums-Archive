---
title: "xorg.conf in Karmic"
date: 2010-01-05
forum: General Help
---

### Post by james_mcl on 2010-01-05
I know that Karmic and Hardy use different versions of Xorg, and that Karmic doesn't usually have xorg.conf.

By following some instructions

(boot into recovery mode,
```
Xorg -configure
```
move the file thus created into /etc/X11 and rename it xorg.conf, IIRC)

I was able to create one a couple of months ago.

I was experimenting to see if adding the following:

```

Section “ServerFlags”
Option “AutoAddDevices” “off”
EndSection

```

would allow me to work around a problem I was having. However, I got stuck at the console, it wouldn't boot into Gnome (probably because it hadn't automatically added my laptop's screen!)

I'm wondering whether I could get round this by pasting the following lines from Hardy's xorg.conf into Karmic's new xorg.conf

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Any advice?

Thanks!

James.

---

### Post by audiomick on 2010-01-05
Hi,
I don't want to comment on the specific content, but if you have an xorg.conf that worked in an older version, you should be able to just paste it in instead of what is not working, or combine the two if you need to.

Have you tried simply removing what you added and re-booting?

As a word of advice, if you change your xorg.conf, even if the point you are starting from only half works, always make a backup copy so you can go back.

If you are only changing a line or a few lines, comment out what you change instead of changing or erasing it, and add new with a comment marking the new stuff. Lines starting with # are seem as comments.

I would look like this.


```
#I made changes here
#this is the old line
#the next line is what I added
this is the new line
```

---

### Post by doas777 on 2010-01-05
run lspci, and make note of the bus id for your video card. 
then under your device section add a line like this:
```
BusID	"PCI:1:0:0"
``` replacing "1:0:0" with the busid from lspci.

you will also need a driver line, appropriate for your vid card, and probably a good bit of other config. 
hope that helps

---

### Post by james_mcl on 2010-01-06
Thanks for the help,

Taking a look at the Karmic file (which I've now managed to retrieve) some of the relevant sections are sufficiently different to their corresponding sections in Hardy's that I don't think it's worth the risk (especially given the new version of X.org) but thanks anyway!

---

