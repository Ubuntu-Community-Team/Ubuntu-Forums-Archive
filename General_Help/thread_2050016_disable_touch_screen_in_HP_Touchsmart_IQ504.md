---
title: "disable touch screen in HP Touchsmart IQ504"
date: 2012-08-29
forum: General Help
---

### Post by parminides on 2012-08-29
I've been running Ubuntu on my HP Touchsmart IQ504 (a desktop) for two or three years, and I've been through two or three versions of Ubuntu in that time (I'm now on 64-bit Unity 12.04).

Initially the touch screen feature didn't work in Ubuntu, but eventually it did. Since then my cat has never been more than a tail-swipe away from messing me up. (Sometimes in the morning I wake up to discover that he has apparently read some of my gmail during the night.)

I now run xscreensaver to stop my nosy cat, but insects that occasionally get in the house seem drawn to the screen like a moth to a flame. They've caused problems even as I sit at the terminal!

I'd like to turn off the touch screen feature before the cat or a gnat deletes some important files. I have never used the feature anyway. Does anyone know how to turn it off.

---

### Post by bastones on 2012-12-02
This may work:

*Terminal commands:*
```
xinput --list
xinput set-prop 'Advanced Silicon S.A CoolTouch(TM) System' 'Device Enabled' 0
xinput set-prop 'Advanced Silicon S.A CoolTouch(TM) System' 'Device Enabled' 1
```

The second disables the touchscreen and third enables it. Change your touchscreen device name in the command(s) if applicable.

---

### Post by parminides on 2012-12-02
I tried your suggestion:

```

 ~] $ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; NextWindow Touchscreen                  	id=11	[slave  pointer  (2)]
&#9116;   &#8627; NextWindow Touchscreen                  	id=12	[slave  pointer  (2)]
&#9116;   &#8627; HP HP Wireless Keyboard Kit             	id=14	[slave  pointer  (2)]
&#9116;   &#8627; MCE IR Keyboard/Mouse (mceusb)          	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Media Center Ed. eHome Infrared Remote Transceiver (1934:0602)	id=9	[slave  keyboard (3)]
    &#8627; NextWindow Touchscreen                  	id=10	[slave  keyboard (3)]
    &#8627; HP HP Wireless Keyboard Kit             	id=13	[slave  keyboard (3)]
    &#8627; CNF7042                                 	id=15	[slave  keyboard (3)]
[~] $ xinput set-prop 'NextWindow Touchscreen' 'Device Enabled' 0
Warning: There are multiple devices matching 'NextWindow Touchscreen'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device NextWindow Touchscreen

```

So,

```

xinput set-prop 12 'Device Enabled' 0

```

That worked. I'm not sure what ID=11 is, but disabling it had no apparent effect on the touchscreen properties.

Thanks for your help. Now my nosy cat can't read my email at night.

---

