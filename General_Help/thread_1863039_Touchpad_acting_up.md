---
title: "Touchpad acting up"
date: 2011-10-17
forum: General Help
---

### Post by jan.petras on 2011-10-17
Hei. I can't believe Ubuntu Oneric was released and the touchpad issue still isn't solved.

For crying out loud, all I want is drag and drop, and right click...

I knew there was a workaround, but then the edge scrolling would stop working.

---

### Post by jan.petras on 2011-10-19
Well, a few days passed and I still haven't been able to solve the touchpad issue. It's driving me crazy. I can't do anything without proper right click and drag&drop capabilities.

---

### Post by crjackson on 2011-10-19
I feel you pain. I'm not in love with this release so far myself.

---

### Post by MarjaE on 2011-10-19
Does anyone have a link to the psmouse patch?

I recently installed Xubuntu and by default there are no touchpad preferences. I ended up installing two extra apps just to get touchpad preferences - apparently Pointing Devices wasn't Xfce compatible so I had to turn to Synaptiks, even though it didn't used to supposed my touchpad,

---

### Post by jan.petras on 2011-10-20
Yeah I installed synaptiks too, I thought it would solve it but no way. Right now only left click works.

No right click, no drag and drop. I'm basically screwed without those.

---

### Post by Hylas de Niall on 2011-10-20
Sad to report same problem here. (11.10 - O.O.)
I think (but will check) control is there to start with, but then stops after a certain time.
Medion Akoya mini e1210 (basically MSI Wind u100)

---

### Post by Hylas de Niall on 2011-10-20
Well, i just checked mouse and touchpad settings, all checked, logged out, had touchpad control at the log-in screen immediately, logged in with pad and mouse control again.

For how long i can only guess.

Hope this helps - seems odd that it 'wakes up' at the log-in screen?

---

### Post by Carborundum on 2011-10-20
What kind of touchpads are you guys using? I have an ETPS/2 Elantech, and for me right click (two-finger tap) worked from the start. Middle button (three-finger tap) on the other hand does not work.

Drag-and-drop initially did not work, but this was easy to fix in my case. I just need to run these commands at login:
```
synclient FastTaps=1
synclient LockedDrags=1
```

---

### Post by Hylas de Niall on 2011-10-20
> **Carborundum said:**
> What kind of touchpads are you guys using? I have an ETPS/2 Elantech, and for me right click (two-finger tap) worked from the start. Middle button (three-finger tap) on the other hand does not work.

Drag-and-drop initially did not work, but this was easy to fix in my case. I just need to run these commands at login:
```
synclient FastTaps=1
synclient LockedDrags=1
```


The e1210 is synaptics touchpad.
just to add some more detail, i have suspended and resumed, and still have pad control at the moment. That's about 40 mins so far.

Additional: 50mins since the para ^above^ and i still have touchpad control.
I'm now wondering if it's lost after using update manager? (which was the last thing i did before losing it earlier this evening)
I might see if it drops in Unity 2D or Gnome shell  ...at least i'll know then if it's Unity or Ubu as a whole that's dropping it.

---

### Post by jan.petras on 2011-10-22
I also have a synaptics touchpad, from a HP Probook 4520S, and still not working.

---

### Post by Hylas de Niall on 2011-10-22
I've un-checked 'disabe touchpad while typing' in settings, no problems since.
...though i wouldn't cite that as a cure, as the symptom was rare anyway.

---

### Post by MarjaE on 2011-10-22
I used psmouse-alps-dkms. I don't know what touchpads you're using, but this fixes the Alps.

It works well in Ubuntu 11.04. It requires some additional software in Xubuntu 11.10, but that's a Xubuntu issue, and shouldn't affect other Ubuntu versions. I reinstalled Ubuntu 10.10 after trouble with Xubuntu 11.10, and the psmouse patch does not work in 10.10. I re-upgraded to 11.04 and it works again, though the upgrade has some minor glitches.

---

### Post by jan.petras on 2011-11-20
Well this is bulls*it. I've been waiting for almost 2 years now and used 3 different laptops and each had the same problem with Ubuntu.

The damn touchpad won't do right click; drag & drop.
Can someone please solve this problem? I would do anything just to have this problem fixed. I've started using the touchpad more and more and now it's driving me mad and I can't get used to it. Why should I?

I don't get it, I've tried other linux flavors BASED on Ubuntu and they didn't have this problem. Somehow they fixed it. However, Ubuntu officials still don't. They don't consider this to be a problem, I guess it's more important poor-behaving left-side panels that can't be deactivated.

---

### Post by hannah187 on 2012-03-05
Indeed it driving me mad as well, any solution as yet.. I use HP ProBook4520s..

root@bt:~# uname -a
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64 GNU/Linux

this is version I am running now..

---

### Post by volanin on 2012-03-09
Ok, let's go step by step!
Please, what is the output of:

```
$ xinput list
```

---

### Post by jan.petras on 2012-03-09
So I did this:
[http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164)

And it worked but not really. I mean, I can now right click and also drag and drop and resize, but it stopped working in other direction: No more scrolling (not edge nor double finger) and the sensitivity is really, really, really, really low - and not affected by the settings (set it to highest possible, no change).

So I fixed it by breaking it :)

```
jan@ubuntu:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam [2 MP Fixed]                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]
jan@ubuntu:~$ 
```

---

### Post by volanin on 2012-03-09
You fixed it by breaking it? That's awesome news!
Does it revert to normal when you boot?
Let me explain!

You see, Xorg detects your touchpad device as "PS/2 Synaptics TouchPad"
So now, please post the output of:

```
$ xinput list-props "PS/2 Synaptics TouchPad"
```

This lists the properties of your device, as described in the end of:

```
$ man synaptics
```

If you can post both the output of your device before "fixing it",
and after "fixing it", we could mix the relevant properties values
and make your touchpad behave exactly as you would like!

---

### Post by jan.petras on 2012-03-09
```
jan@ubuntu:~$ xinput list-props "PS/2 Synaptics TouchPad"
Device 'PS/2 Synaptics TouchPad':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (253):	0
	Device Accel Constant Deceleration (254):	1.000000
	Device Accel Adaptive Deceleration (255):	1.000000
	Device Accel Velocity Scaling (256):	10.000000
	Device Product ID (249):	2, 1
	Device Node (250):	"/dev/input/event6"
	Evdev Axis Inversion (257):	0, 0
	Evdev Axes Swap (259):	0
	Axis Labels (260):	"Rel X" (142), "Rel Y" (143)
	Button Labels (261):	"Button Left" (135), "Button Middle" (136), "Button Right" (137), "Button Wheel Up" (138), "Button Wheel Down" (139)
	Evdev Middle Button Emulation (262):	0
	Evdev Middle Button Timeout (263):	50
	Evdev Third Button Emulation (264):	0
	Evdev Third Button Emulation Timeout (265):	1000
	Evdev Third Button Emulation Button (266):	3
	Evdev Third Button Emulation Threshold (267):	20
	Evdev Wheel Emulation (268):	0
	Evdev Wheel Emulation Axes (269):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (270):	10
	Evdev Wheel Emulation Timeout (271):	200
	Evdev Wheel Emulation Button (272):	4
	Evdev Drag Lock Buttons (273):	0
jan@ubuntu:~$
``` 

And now I deleted the /modprobe.d/psmouse.modprobe file (which made my laptop think I'm using a PS/2 mouse) and rebooting. I'm going to post the input to that in a minute after reboot.

---

### Post by jan.petras on 2012-03-09
Well now, after deleting the "fix" (the psmouse.modeprobe file) I get

```
jan@ubuntu:~$ xinput list-props "PS/2 Synaptics TouchPad"
unable to find device PS/2 Synaptics TouchPad
jan@ubuntu:~$ 

```

And the problem is back. It wasn't really fixed in the first place, it was just switching one set of problems (no drag and drop, no right click) for another (no scroll, horrible sensitivity)

---

### Post by jan.petras on 2012-03-09
Also, redid the steps:

```
jan@ubuntu:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Webcam [2 MP Fixed]                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=12	[slave  keyboard (3)]
jan@ubuntu:~$ sudo xinput list-props "SynPS/2 Synaptics TouchPad"
[sudo] password for jan: 
Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled (132):	1
	Coordinate Transformation Matrix (134):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (254):	1
	Device Accel Constant Deceleration (255):	2.500000
	Device Accel Adaptive Deceleration (256):	1.000000
	Device Accel Velocity Scaling (257):	12.500000
	Synaptics Edges (258):	1766, 5392, 1627, 4329
	Synaptics Finger (259):	25, 30, 256
	Synaptics Tap Time (260):	180
	Synaptics Tap Move (261):	231
	Synaptics Tap Durations (262):	180, 180, 100
	Synaptics ClickPad (263):	0
	Synaptics Tap FastTap (264):	0
	Synaptics Middle Button Timeout (265):	75
	Synaptics Two-Finger Pressure (266):	282
	Synaptics Two-Finger Width (267):	7
	Synaptics Scrolling Distance (268):	105, 105
	Synaptics Edge Scrolling (269):	1, 1, 0
	Synaptics Two-Finger Scrolling (270):	0, 0
	Synaptics Move Speed (271):	1.000000, 1.750000, 0.038059, 40.000000
	Synaptics Edge Motion Pressure (272):	30, 160
	Synaptics Edge Motion Speed (273):	1, 420
	Synaptics Edge Motion Always (274):	0
	Synaptics Off (275):	1
	Synaptics Locked Drags (276):	0
	Synaptics Locked Drags Timeout (277):	5000
	Synaptics Tap Action (278):	2, 3, 0, 0, 1, 3, 0
	Synaptics Click Action (279):	1, 3, 0
	Synaptics Circular Scrolling (280):	0
	Synaptics Circular Scrolling Distance (281):	0.100000
	Synaptics Circular Scrolling Trigger (282):	0
	Synaptics Circular Pad (283):	0
	Synaptics Palm Detection (284):	0
	Synaptics Palm Dimensions (285):	10, 200
	Synaptics Coasting Speed (286):	20.000000, 50.000000
	Synaptics Pressure Motion (287):		... of unknown type CARDINAL

	Synaptics Pressure Motion Factor (288):	1.000000, 1.000000
	Synaptics Resolution Detect (289):	1
	Synaptics Grab Event Device (290):	1
	Synaptics Gestures (291):	1
	Synaptics Capabilities (292):	1, 0, 0, 1, 1, 1, 1
	Synaptics Pad Resolution (293):	65, 50
	Synaptics Area (294):	0, 0, 0, 0
	Synaptics Soft Button Areas (295):	0, 0, 0, 0, 0, 0, 0, 0
	Synaptics Noise Cancellation (296):	8, 8
	Device Product ID (249):	2, 7
	Device Node (250):	"/dev/input/event7"
jan@ubuntu:~$ 

```

---

### Post by volanin on 2012-03-09
That's much better!
These lots of SYNAPTICS properties are the ones we are looking for,
not the previous strange EVDEV properties! Let's start working:

Hmmm...
It seems the synaptics driver is off.
That's weird. Let's first enable synaptics:

```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Off" 8 0
```

Does this change anything?

---

### Post by jan.petras on 2012-03-09
Nope. Nothing. I rebooted just to be sure, still nothing.

---

### Post by volanin on 2012-03-09
Well, you should not reboot.
These settings are only temporary, and a reboot resets them!

Ok, let's try this.
Enable synaptics clickpad devices:

```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics ClickPad" 8 1
```

If nothing happens, try to enable synaptics driver again:

```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Off" 8 0
```

---

### Post by jan.petras on 2012-03-09
Nope, still nothing.

---

### Post by volanin on 2012-03-09
Sorry for the delay, it's almost midnight here and I am getting ready to sleep.
Well, your synaptics parameters are very good. They already support right
click and drag 'n' drop. Things should have worked just by enabling it.
But they didn't.

So I am assuming there is no synaptics support for your device yet.
I tried searching for asus 4520s, but I only found about the HP4520s.
Tomorrow, I will research a little more, and keep you posted.

See you.
:)

---

### Post by Sonsum on 2012-03-10
> **volanin said:**
> Sorry for the delay, it's almost midnight here and I am getting ready to sleep.
Well, your synaptics parameters are very good. They already support right
click and drag 'n' drop. Things should have worked just by enabling it.
But they didn't.

So I am assuming there is no synaptics support for your device yet.
I tried searching for asus 4520s, but I only found about the HP4520s.
Tomorrow, I will research a little more, and keep you posted.

See you.
:)

When I tried to help the OP in another thread, I also did a search for the Asus laptop. I believe he has the make mixed up because on the first page of this thread, it is mentioned as a HP Probook 4520s, which I believe is the model we're actually looking at.

---

### Post by stalkingwolf on 2012-03-11
Maybe it isnt an asus.  I just ran across two articles on google ,
one titled Asus aspire 4520 and the next is acer aspire 4520.

Hp also uses the designation of 4520. or as stated by the OP 4520s.

Maybe an HP with an Asus board? It looks like what board it has depends on where in the world it was purchased.

---

