---
title: "Dual monitors mouse speed"
date: 2010-12-04
forum: General Help
---

### Post by sknoslo on 2010-12-04
Hi, I'm currently running Ubuntu 10.10 on my HP laptop with an external monitor attached. I've been having the same issue since 9.04 and just now figured I should ask about it.

Heres the deal: When I have dual monitors set up (extended desktop) the mouse speed in the X direction seems to double. ie. assume the mouse usually moves 1 pixel at a time, it now moves 2. It seems to be functioning as usual in the Y direction, which makes the motion really weird and hard to use. I'm using a Wacom tablet for the mouse, but the same happens with my laptops touch pad. Anyone else experience this/know how to fix it?

Thanks.

Other possibly relevant information: My extra monitor is a 22" widescreen 16:9, but I had the same problem with an old 4:3 15" monitor as well.

Laptop information: Notebook: HP Pavilion dv4-1125nr (Pavilion dv4 Series)
Processor: Intel Core 2 Duo T5800
Graphics Adapter: Intel Graphics Media Accelerator (GMA) 4500MHD
Display: 14.1 inch, 16:10, 1280x800 pixels

---

### Post by seanstoner on 2011-02-11
Bump!

I'm running Lucid Lynx, 2.6.32-29-generic #57-Ubuntu SMP Sun Jan 30 03:30:16 UTC 2011 i686 GNU/Linux.

FWIW, this behavior also happens if you stack the desktops vertically, in that it's the Y axis that speeds up and X stays the same. This is definitely unwanted behavior IMO. At least we should make it an option.

---

### Post by Favux on 2011-02-11
Hi sknoslo & seanstoner,

Welcome to Ubuntu forums!

Enter in a terminal:
```
xinput list
```
to get the "device name" of your Wacom stylus or mouse.  Then enter:
```
xinput list-props "device name"
```
See what's available.  Most likely you'll see the following settings:
```
"Device Accel Constant Deceleration" 1.000000
"Device Accel Adaptive Deceleration" 1.000000
"Device Accel Velocity Scaling" 1.000000
```
Then start modifying them, example:
```
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Constant Deceleration" 1.000000
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Adaptive Deceleration" 1.000000
xinput set-prop "Wacom BambooFun 2FG 4x5 Pen stylus" --type=float "Device Accel Velocity Scaling" 1.000000
```
using your device name in quotes.

You'll probably want to start with/concentrate on "Device Accel Constant Deceleration" with an initial increased value of say 1.250000.

The settings won't last through a reboot so you'll need to place them in a start up script.

Hope this helps.

---

