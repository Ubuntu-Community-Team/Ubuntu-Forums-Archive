---
title: "3M USB Touchscreen - (Can't calibrate &amp; Pulling my hair out...)"
date: 2011-01-31
forum: General Help
---

### Post by senovia on 2011-01-31
Hey Guys,
I have searched every forum I can find for a solution to my problem. I am lost, cold, and alone. I absolutely can not get my new 3M touch screen to work in Ubuntu. Yesterday I upgraded to the latest stable build of Ubuntu (10.04 LTS) because my only issue seemed to be calibration in my earlier version of Ubuntu, but now I am worse off. The reason I upgraded was to use the tool xinput_calibrator, which I couldn't build without upgrading to 10.04. Now that I've upgraded, I can install xinput_calibrator, but nothing I do actually calibrates my touchscreen. The mildly good news is that the driver seems to be working since when I touch the touchscreen, my pointer jumps to the bottom right of the screen.

In the previous build of Ubuntu I had, I was able to get the touchscreen to work, kinda, by dropping a file in /etc/hal/fdi/policy/touchscreen.fdi containing the following:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="input.product" contains="3M 3M Touchscreen - EX II">
<merge key="input.x11_driver" type="string">evtouch</merge>
<merge key="input.x11_options.MinX" type="string">14200</merge>
<merge key="input.x11_options.MaxX" type="string">2160</merge>
<merge key="input.x11_options.MinY" type="string">2580</merge>
<merge key="input.x11_options.MaxY" type="string">13800</merge>
</match>
</device>
</deviceinfo>

But now, in the current version of Ubuntu, I understand that fdi policies are a thing of the past and everything is controlled by udev rules now. That's fine, I don't care, if I could get a rule to do anything.

So I read and read and read. I started trying lots of different things to troubleshoot:

I tried using xinput to set some rules:
xinput set-int-prop "3M 3M USB Touchscreen - EX II" "Evdev Axis Inversion" 8 0 1

I tried adding a file 05-edev.conf to the xorg.conf.d directory with this contents(but that just freezes my computer on startup):

Section "InputClass"
Identifier "3M"
MatchProduct "3M"
MatchDevicePath "/dev/input/event*"
#Driver "usbtouchscreen"
Option "InvertY" "on"
Option "Calibration" "1874 14571 2344 13411"
EndSection

One odd thing is that when I use xinput to list out my devices, I see two touchscreens (one that says it's disabled. 10 is the proper one, 11 is disabled):

rmartin-laptop 1 [/home/rmartin]: xinput -list
&#9121; Virtual core pointer id=2 [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4 [slave pointer (2)]
&#9116; &#8627; SMK Standard MCE Receiver 1 id=9 [slave pointer (2)]
&#9116; &#8627; EVTouch TouchScreen id=10 [slave pointer (2)]
&#9116; &#8627; SynPS/2 Synaptics TouchPad id=13 [slave pointer (2)]
&#9116; &#8627; Macintosh mouse button emulation id=14 [slave pointer (2)]
&#9116; &#8627; EVTouch TouchScreen id=11 [slave pointer (2)]
&#9123; Virtual core keyboard id=3 [master keyboard (2)]
&#8627; Virtual core XTEST keyboard id=5 [slave keyboard (3)]
&#8627; Power Button id=6 [slave keyboard (3)]
&#8627; Video Bus id=7 [slave keyboard (3)]
&#8627; Power Button id=8 [slave keyboard (3)]
&#8627; AT Translated Set 2 keyboard id=12 [slave keyboard (3)]

I also don't understand the name "EVTouch TouchScreen" and how it correlates to my 3M touchscreen. When I list out all my usb devices using lshal, I see the name "3M 3M USB Touchscreen - EX II".

rmartin-laptop 1 [/home/rmartin]: lshal | grep input.product
input.product = 'Power Button' (string)
input.product = 'AT Translated Set 2 keyboard' (string)
input.product = '3M 3M USB Touchscreen - EX II' (string)
input.product = 'SynPS/2 Synaptics TouchPad' (string)

I have also created a udev rule '/etc/udev/rules.d/99_touchscreen.rules' with the following contents:

ACTION!="add|change", GOTO="xorg_touchscreen_end"
KERNEL!="event*", GOTO="xorg_touchscreen_end"
ATTRS{product}!="EVTouch TouchScreen", GOTO="xorg_touchscreen_end"
ENV{x11_options.swapxy}="1"
ENV{x11_options.calibration}="1958 27 187 1955"
LABEL="xorg_touchscreen_end"

Nothing seems to alter how my touchscreen responds in any way. Every time I press it, same thing, the recycle bin opens, cause thats what's on the lower right of my screen.

I'll be eternally grateful if anybody can help me. Thanks!

Ryan

---

### Post by senovia on 2011-02-02
Is there possibly a better place to post this question? Any help would be greatly appreciated. Thanks

---

### Post by gordintoronto on 2011-02-02
It's not easy to get help with unusual hardware. Did you get the software from this site:

[http://solutions.3m.com/wps/portal/3M/en_US/TouchSystems/TouchScreen/CustomerSupport/TouchScreenDrivers/](http://solutions.3m.com/wps/portal/3M/en_US/TouchSystems/TouchScreen/CustomerSupport/TouchScreenDrivers/)

BTW, the latest stable build of Ubuntu is 10.10.

3M might have their own forum on something called Touchnet.

---

