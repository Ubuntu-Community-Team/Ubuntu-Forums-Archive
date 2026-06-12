---
title: "Fixing HDAPS (harddrisk protection) on Thinkpad Edge 15"
date: 2011-04-13
forum: General Help
---

### Post by Redsandro on 2011-04-13
I am trying to use my **accelerometer** as joystick just so I know it's working, but I can't figure out how.

To my surprise, Ubuntu doesn't seem to have a nice GTK joystick testing dialog. There used to be **hdaps-gl** out there for testing, but this was for very old models and is only released for *Ubuntu 8.04* afaik. So I tried installing **neverball** for that purpose. It doesn't have options for joystick selection, but apparently it works out of the box with a *Thinkpad T61*.

```
sudo aptitude install tp-smapi-dkms
sudo modprobe tp_smapi
sudo modprobe hdaps
```

dmesg:```
[  720.093604] thinkpad_ec: thinkpad_ec 0.40 loaded.
[  720.095348] tp_smapi 0.40 loading...
[  720.095786] tp_smapi successfully loaded (smapi_port=0xb2).
[  842.860767] thinkpad_ec: thinkpad_ec_read_row: failed waiting for data: (0x13:0x00)->0xfffffff0
[  842.860773] hdaps init failed at: hdaps_get_ec_mode failed
[  842.861321] input: ThinkPad HDAPS joystick emulation as /devices/virtual/input/input10
[  842.861696] input: ThinkPad HDAPS accelerometer data as /devices/virtual/input/input11
[  842.861883] hdaps: driver successfully loaded.

```

lsmod:```
Module                  Size  Used by
hdaps                  10772  0 
tp_smapi               26194  0 
thinkpad_ec             5842  2 hdaps,tp_smapi
(..)
```

I've also tried to use **jstest** with 
*/dev/input/js*[0|1]
and
*/devices/virtual/input/input10/*[many things]
But the former gives static 0 for both axes and the second gives error messages (you're probably not supposed to use it like this).

Any ideas?

---

### Post by Redsandro on 2011-04-26
*[COLOR="DarkRed"]*Well-deserved-bump*[/COLOR]*

Anyone? Lenovo is a popular brand, and above all, the Thinkpad Edge is **[Ubuntu Certified](http://www.ubuntu.com/certification/hardware/201011-6828:201101-6965)**, so I am guessing a lot of people have this laptop.

And since it is certified, one would guess stuff like this should work.

Apparently, there's also a special image of Ubuntu 10.10 available for this laptop but I cannot find it on the entire internet.

---

### Post by Tyler Kessler on 2011-05-19
I'm trying to figure out how to use my accelerometer as well. It seems nobody on here knows how to do it. :(

---

### Post by matthewbpt on 2011-05-21
I've got exactly the same problem on my Thinkpad Edge 11. The driver loads fine, but when testing with jstest I just get a static 0 on both axes, and neverball doesn't work.

---

