---
title: "modeline help!!!"
date: 2009-11-06
forum: General Help
---

### Post by dylan_newb on 2009-11-06
[I]how do i find the current modeline im using in 9.04. Not just the resolution and HZ. i need all of it. have been up all night trying
[/I]

---

### Post by dylan_newb on 2009-11-06
help its very important

---

### Post by Giblet5 on 2009-11-06
Bring up a terminal window. Enter ```
less /var/log/Xorg.0.log
```

Hit the '/' key and enter "mode" (sans quotes), then hit Enter.

Details of how Xorg determined available modes should be displayed right there.

Hit 'q' to exit less.

You can also look at /etc/X11/xorg.conf. Did you specify any modes in there?

---

### Post by dylan_newb on 2009-11-06
```
(II) intel(0): Output VGA connected
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output VGA using initial mode 1152x864
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"

```
and
```
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
```
were the only things with mode in that file

---

### Post by Giblet5 on 2009-11-06
Do you have the horizontal sync frequency and vertical refresh range for your specific monitor model?

It's pretty easy to put that in xorg.conf. Then Xorg will know what modes your monitor will support.

The log shows that Xorg is guessing.

The best process for establishing a rock-solid Xorg configuration is to search for your specific monitor model's Horizontal Sync Frequency Range and its Vertical Refresh Frequency Range.

I have a Dell 3007wp-hc monitor.

Horizontal range is 49.31Khz - 98.71Khz and vertical is fixed at 60.0.

Flip to the text console via CtrlAltF1.

Log in.

Run ```
sudo /etc/init.d/gdm stop
sudo X -configure
sudo chown $LOGNAME:$LOGNAME xorg.conf.new
sudo /etc/init.d/gdm start ; exit
```

Log in and edit ~/xorg.conf.new and scroll down to

Section "Monitor"

After the Identifier is defined, add ```
        HorizSync     NN.nn - NN.nn
        VertRefresh   NN.nn - NN.nn
```

Where NN.nn are values supplied by the vendor for your EXACT monitor model.

Save the file as ~/xorg.conf.

From a terminal window, enter:
```
sudo cp xorg.conf /etc/X11/xorg.conf
sudo chown root:root /etc/X11/xorg.conf
sudo chmod 644 /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

Things should already look MUCH better...

---

### Post by dylan_newb on 2009-11-06
i dont know its a polaroid 720p 32" lcd tv
you see i have 3 hdd's and i used one for 9.10 and left 9.04 on my other. just in case 9.10 didnt work out for me. so i booted up 9.10 and max resolution was 800 x 600. im trying to find the right modeline for 1024x768 at least. CVT and GTF didnt give me the right output and makes my tv go out of range. and i know it suports it because im on 1024x768 right now(with 9.04). but cant get it on 9.10:mad:

---

### Post by Giblet5 on 2009-11-06
> **dylan_newb said:**
> i dont know its a polaroid 720p 32" lcd tv
you see i have 3 hdd's and i used one for 9.10 and left 9.04 on my other. just in case 9.10 didnt work out for me. so i booted up 9.10 and max resolution was 800 x 600. im trying to find the right modeline for 1024x768 at least. CVT and GTF didnt give me the right output and makes my tv go out of range. and i know it suports it because im on 1024x768 right now(with 9.04). but cant get it on 9.10:mad:

What is the EXACT model number? (on the back or bottom)

---

### Post by dylan_newb on 2009-11-06
1 min got to take it off the wall

---

### Post by dylan_newb on 2009-11-06
guess its 26" model flm-2601 form polaroid

---

### Post by Giblet5 on 2009-11-06
What kind of cable are you using to connect the monitor?


Found these specs, but not from the vendor.

HorizSync 30-55
VertRefresh 50-65

---

### Post by dylan_newb on 2009-11-06
vga

---

### Post by Giblet5 on 2009-11-06
Follow the procedure for creating a custom xorg.conf and try

```
HorizSync 30-55
VertRefresh 50-65
```

In theory, that will provide 1280 x 768 as the default resolution.

The only way to tell is to try it.

If your display is unusable with those frequencies, flip to the text console via CtrlAltF1 and run

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
sudo /etc/init.d/gdm restart
```

---

### Post by dylan_newb on 2009-11-06
thanks will try when i get up so sleepy now cant do anything :D

---

### Post by dylan_newb on 2009-11-08
you are effing GREAT!!!! man thanks so much couldn't find that at all till you helped me thanks a lot now i dont have to downgrade

---

