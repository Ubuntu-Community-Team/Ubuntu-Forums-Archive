---
title: "computer going crazy"
date: 2011-09-26
forum: General Help
---

### Post by daniel.cotter on 2011-09-26
My laptop is acting as if the right mouse button is stuck, popping up context menus every time I move the cursor (with or without the mouse attached), and creating folders all over the desktop.  I can't even log into it, because it is flipping out.  It started with no warning.  I would suspect a virus, but have never downloaded anything beside recommended updates.

I doubt I could paste in contents of any log files, because it moves focus to the context menu every half-second or so.  I CAN switch to text mode.  Can you tell me what to do to be able to use the GUI?

Ubuntu 11.04

Thanks!

---

### Post by haqking on 2011-09-26
> **daniel.cotter said:**
> My laptop is acting as if the right mouse button is stuck, popping up context menus every time I move the cursor (with or without the mouse attached), and creating folders all over the desktop.  I can't even log into it, because it is flipping out.  It started with no warning.  I would suspect a virus, but have never downloaded anything beside recommended updates.

I doubt I could paste in contents of any log files, because it moves focus to the context menu every half-second or so.  I CAN switch to text mode.  Can you tell me what to do to be able to use the GUI?

Ubuntu 11.04

Thanks!

have you rebooted ?

---

### Post by daniel.cotter on 2011-09-26
yes, several times, with and without the mouse attached

---

### Post by daniel.cotter on 2011-09-26
anyone?

---

### Post by TeoBigusGeekus on 2011-09-26
Could it be possible that your synaptics pointing device is faulty/stuck?
Is there an option to disable it (physically or from bios)?

---

### Post by daniel.cotter on 2011-09-26
I have never looked in the BIOS for that.  I tried in the GUI and can't.  That's a good idea...I'll try it.

---

### Post by matt_symes on 2011-09-26
Hi

Can you boot into a live CD/USB to check if it is happening then ? This may eliminate/implicate a hardware issue.

Kind regards

---

### Post by daniel.cotter on 2011-09-26
No, the synaptic device doesn't appear in the BIOS

---

### Post by TeoBigusGeekus on 2011-09-26
Try what matt suggested, and if the problem persists (-> hardware error), boot up into recovery mode and see [this]("https://help.ubuntu.com/community/SynapticsTouchpad") for disabling it (Section 3.2).
Give 
```
startx
```
to get into a graphics environment and see if that was it.

---

### Post by daniel.cotter on 2011-09-26
Okay, I booted to a Live CD.  It's still popping up menus at the cursor.  That makes it a hardware issue (touchpad)?

---

### Post by TeoBigusGeekus on 2011-09-26
I guess so. See my previous post.

---

### Post by matt_symes on 2011-09-26
Hi

> **daniel.cotter said:**
> That makes it a hardware issue (touchpad)?

Almost definitely. Follow Teo's advice and disable the touchpad using xinput. The tab key is your friend now. Ctrl + atl + t will bring up the terminal.

Can you get into the laptop to clean it or give it a visual inspection ?

Kind regards

---

### Post by daniel.cotter on 2011-09-26
Okay, I disabled it using xinput, as suggested, but on boot, it is enabled again.  I thought it was the mouse, but after unplugging it again, I get the same issue, and the touchpad works.

---

### Post by daniel.cotter on 2011-09-26
As soon as I plug a usb mouse in, the touchpad comes to life again!

---

### Post by TeoBigusGeekus on 2011-09-26
Alright, can you repeat the procedure but this time posting us your input and your terminal's responses?

---

### Post by matt_symes on 2011-09-26
Hi

> **daniel.cotter said:**
> Okay, I disabled it using xinput, as suggested, but on boot, it is enabled again.  I thought it was the mouse, but after unplugging it again, I get the same issue, and the touchpad works.

You will have to set it up as a script. Make sure the script is executable. Or you could blacklist the touchpad driver.

Kind regards

---

### Post by daniel.cotter on 2011-09-26
I blew air into the touchpad, and it appears to have stopped momentarily.  I will look into opening it to clean it better.  I appreciate you guys -- the time you put into investigating my problem, and the great, helpful ideas.

Have a great day!

---

### Post by TeoBigusGeekus on 2011-09-26
> **daniel.cotter said:**
> I blew air into the touchpad, and it appears to have stopped momentarily.  I will look into opening it to clean it better.  I appreciate you guys -- the time you put into investigating my problem, and the great, helpful ideas.

Have a great day!

Glad to hear it; have a great day yourself! :D

---

### Post by daniel.cotter on 2011-09-26
Teo:

```
xinput list
```


```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Dell Dell USB Mouse                     	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]

```

```
xinput set-prop 12 "Device Enabled" 0
```

No response in the terminal window; it just goes back to the prompt


I have discovered that when the mouse is already plugged in and I disable the touchpad in this way, it stays disabled.  If I plug the mouse in afterward, it re-enables the touchpad.

---

### Post by TeoBigusGeekus on 2011-09-26
So, create a text file in your home folder, put
```
xinput set-prop 12 "Device Enabled" 0
```
in it, name it whatever you like, disable_synaptics for example, make it executable
```
chmod +x ~/disable_synaptics
```
and add it as a startup application, so that it loads whenever you start your pc.
Give it a name and add as its command
```
bash ~/disable_synaptics
```

---

