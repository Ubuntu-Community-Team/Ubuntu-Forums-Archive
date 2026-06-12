---
title: "Can't get Two finger scrolling working"
date: 2012-07-21
forum: General Help
---

### Post by asadullah on 2012-07-21
I just reinstalled ubuntu 10.04 on my gateway nv57. I can't get two finger scrolling to even show in mouse options. It works in 11.04 11.10 and maybe 10.10. I've tried a couple different things but nothing.

---

### Post by MG&amp;TL on 2012-07-21
Is there a reason for you to be using 10.04? It looks like support was only added for your touchpad in 10.10 and above.

---

### Post by asadullah on 2012-07-21
> **MG&TL said:**
> Is there a reason for you to be using 10.04? It looks like support was only added for your touchpad in 10.10 and above.


Compiling android source code. I know you can do it in other versions (done it). It's just that's the recommended version. Also it's LTS and 12.04 doesn't completely work for me in more than one area.

---

### Post by MG&amp;TL on 2012-07-21
> **asadullah said:**
> Compiling android source code. I know you can do it in other versions (done it). It's just that's the recommended version. Also it's LTS and 12.04 doesn't completely work for me in more than one area.

Okay, what's your touchpad? I'll see if I can find out wwhich touchpad features were added in between 10.04 and 11.04.

---

### Post by asadullah on 2012-07-21
> **MG&TL said:**
> Okay, what's your touchpad? I'll see if I can find out wwhich touchpad features were added in between 10.04 and 11.04.


I can't remember off hand what the terminal code is to find that. I'm in windows right now can't I find out from here

synaptics touchpad v7.5

---

### Post by MG&amp;TL on 2012-07-21
You're right, it seems synaptic touchpads only got "true multitouch support" in 10.10.

Would this page be of any use to you: [https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick]("https://help.ubuntu.com/community/SynapticsTouchpad/PreMaverick")

---

### Post by asadullah on 2012-07-21
Gonna find out :-)

---

### Post by asadullah on 2012-07-21
Well I ran xinput list in terminal and got this output ```
xinput list &#9121; Virtual core pointer                    	id=2	[master pointer  (3)] &#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] &#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=13	[slave  pointer  (2)] &#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)] &#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]     &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]     &#8627; Power Button                            	id=6	[slave  keyboard (3)]     &#8627; Power Button                            	id=7	[slave  keyboard (3)]     &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]     &#8627; 1.3M HD WebCam                          	id=9	[slave  keyboard (3)]     &#8627; Logitech USB Keyboard                   	id=10	[slave  keyboard (3)]     &#8627; Logitech USB Keyboard                   	id=11	[slave  keyboard (3)]     &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)] 
```  So I know that it recognizes it but sudo trackpad returns no trackpad command  One thing that is strange is I don't have an xorg-conf in etc/x11

---

### Post by MG&amp;TL on 2012-07-21
> **asadullah said:**
> Well I ran xinput list in terminal and got this output ```
xinput list &#9121; Virtual core pointer                    	id=2	[master pointer  (3)] &#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)] &#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=13	[slave  pointer  (2)] &#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)] &#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]     &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]     &#8627; Power Button                            	id=6	[slave  keyboard (3)]     &#8627; Power Button                            	id=7	[slave  keyboard (3)]     &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]     &#8627; 1.3M HD WebCam                          	id=9	[slave  keyboard (3)]     &#8627; Logitech USB Keyboard                   	id=10	[slave  keyboard (3)]     &#8627; Logitech USB Keyboard                   	id=11	[slave  keyboard (3)]     &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)] 
```  So I know that it recognizes it but sudo trackpad returns no trackpad command  One thing that is strange is I don't have an xorg-conf in etc/x11

Not a hardware expert, but xorg.conf seems to have caught 'dot dee disease' - you may need to look in /etc/X11/xorg.conf.d/ rather than /etc/X11/xorg.conf.

---

### Post by asadullah on 2012-07-21
> **MG&TL said:**
> Not a hardware expert, but xorg.conf seems to have caught 'dot dee disease' - you may need to look in /etc/X11/xorg.conf.d/ rather than /etc/X11/xorg.conf.

 Well I looked in there nothing then I tried making the file but no go. I've been at this for hours today and hours other days so I'm gonna take the sign and move on. I appreciate your help

---

### Post by MG&amp;TL on 2012-07-21
> **asadullah said:**
> Well I looked in there nothing then I tried making the file but no go. I've been at this for hours today and hours other days so I'm gonna take the sign and move on. I appreciate your help

Okay. Hopefully 12.04 works for you one day, when point releases come out.

---

