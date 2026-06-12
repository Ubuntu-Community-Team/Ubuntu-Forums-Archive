---
title: "Wacom Bamboo on ubuntu 10.04"
date: 2011-08-28
forum: General Help
---

### Post by thenightfly77 on 2011-08-28
Alright, so i've tried everything to get my tablet working. Around Christmas I got a tablet, and I found a site that had easy instructions to install it on ubuntu. So it was working for like 4 months until I reinstalled ubuntu. 

A while ago i tried reinstalling it. I've used a lot of commands in terminals etc and I think that they've messed it up. Like...I think they've partially installed my tablet...but it won't work.

Now when i try to use my tablet, if i move the pen over the tablet, the cursor just shows up on the side of my screen and only moves vertically.

Help?

---

### Post by Favux on 2011-08-28
Hi thenightfly77,

Welcome to Ubuntu forums!

Ouch.  Do you remember if what you installed around Christmas had dkms (dynamic kernel module support)?  Or can you link to the tutorial?

Let's find out what model tablet you have.  In a terminal enter:
```
lsusb
```
and post the Wacom line from the output.  Also the output of:
```
xinput list
```

---

### Post by thenightfly77 on 2011-08-28
> **Favux said:**
> Hi thenightfly77,

Welcome to Ubuntu forums!

Ouch.  Do you remember if what you installed around Christmas had dkms (dynamic kernel module support)?  Or can you link to the tutorial?

Let's find out what model tablet you have.  In a terminal enter:
```
lsusb
```
and post the Wacom line from the output.  Also the output of:
```
xinput list
```

No, I wasn't smart enough to save the tutorial I've found. I've searched numerous times and haven't found it. I don't really remember anything about it.

Bus 005 Device 002: ID 056a:00d4 Wacom Co., Ltd

And is this what you mean?

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen eraser             	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen stylus             	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger pad             	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger touch           	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Gateway USB 2.0 Webcam                  	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

---

### Post by Favux on 2011-08-28
OK, you have the Bamboo Pen.  So you have a stylus and the two stylus side buttons (rocker switch).

The *xinput list* indicates the tablet is matched in the 50-wacom.conf and placed on the Wacom X driver (xf86-input-wacom).  Let's check on that.  The wacom.conf should be in /usr/share/X11/xorg.conf.d.  What are the contents?  And let's find out what version of the driver you have:
```
xsetwacom -V
```
For the dkms check if you have something labeled wacom in /lib/modules/`uname -r`/updates/dkms.  If so post what's there.  The:
```
`uname -r`
```
outputs the current kernel number you are using.  So you can run it in a terminal to get that part of the path.

---

