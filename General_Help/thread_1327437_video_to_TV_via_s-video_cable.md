---
title: "video to TV via s-video cable"
date: 2009-11-15
forum: General Help
---

### Post by mr clark25 on 2009-11-15
i am trying to hook up my TV to my computer so i can watch shows on my TV.
i don't really know what i'm doing, so could someone help me get started? i hook up the TV and it displays when i first turn it on(the computer), and then it stops after Ubuntu starts. then it goes to my LCD display only. they are both hooked up to the same graphics card (radeon is all i can remember). 

i can go to the display manager, and it only recognizes the LCD...

could someone tell me what to do?

---

### Post by mr clark25 on 2009-11-15
just realized i should have put tis in form "desktop environments" i will put a copy of this there.

---

### Post by jocko on 2009-11-15
Are you using the open source (radeon) driver or the proprietary (fglrx) driver?

With the open source driver, try with xrandr.
First, set the TV standard:
```
xrandr --output S-video --set tv_standard [COLOR=Red]pal[/COLOR]
```Set the standard to the correct for your TV (if you don't specify this, it will use the default setting according to your graphics cards bios, which may or may not be correct for your TV. Valid options are [COLOR=Red]ntsc[/COLOR], [COLOR=Red]pal[/COLOR], [COLOR=Red]pal-m[/COLOR], [COLOR=Red]pal-60[/COLOR], [COLOR=Red]ntsc-j[/COLOR] and [COLOR=Red]scart-pal[/COLOR]).

Then activate the TV output (800x600 is the maximum resolution):
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
```After the second command your display will flicker and part of your desktop should appear on the TV.
To make an extended screen with your TV below your monitor:
```
xrandr --output S-video --[COLOR=Blue]below[/COLOR] [COLOR=Red]DVI-0[/COLOR]
```[COLOR=Red]DVI-0[/COLOR] is if your monitor is connected through DVI, otherwise use [COLOR=Red]VGA-0[/COLOR] (or check the output of "xrandr -q"). If you don't want it below, try "[COLOR=Blue]--above[/COLOR]", "[COLOR=Blue]--left-of[/COLOR]" or "[COLOR=Blue]--right-of[/COLOR]", but it may happen that right and left won't work due to limitations of your graphics cards maximum total output size.

Finally, to be able to set the xv video overlay to show fullscreen video on the TV, install xvattr:
```
sudo apt-get install xvattr
```Then to set it to the TV:
```
xvattr -a XV_CRTC -v 1
```And to set it back to the monitor:
```
xvattr -a XV_CRTC -v 0
```

---

### Post by mr clark25 on 2009-11-15
thanks, ill try tat later. i found out that my card is a radeon X1300. that might help some later on.

---

### Post by mr clark25 on 2009-11-20
thanks, but i dont know if i am using (or have) xrandr.

when i run the first command you mentioned, i get this:
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24



i have to hook up the cable after i boot, or i dont get any display when ubuntu boots. if i do hook it up, i get display on both screens(TV and monitor) untill ubuntu starts booting, and then it switches to whatever the blue port is called. (so i lose display on my white output and s-video) that is very strange as far as i know...  i ran the command again with the s-video hooked up, and got the same result.

---

### Post by mr clark25 on 2009-11-20
help?

---

### Post by mr clark25 on 2009-11-20
it seems like i get more performance out of my card when i dont use a driver. the one that comes with the catalyst control center seems to downgrade my card. i cant even hardly watch videos on youtube.

---

### Post by jocko on 2009-11-21
> **mr clark25 said:**
> thanks, but i dont know if i am using (or have) xrandr.

when i run the first command you mentioned, i get this:
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24



i have to hook up the cable after i boot, or i dont get any display when ubuntu boots. if i do hook it up, i get display on both screens(TV and monitor) untill ubuntu starts booting, and then it switches to whatever the blue port is called. (so i lose display on my white output and s-video) that is very strange as far as i know...  i ran the command again with the s-video hooked up, and got the same result.
To see the names of the outputs on your card:
```
xrandr -q
```
The blue port is probably vga and the white is probably dvi.
Ati cards just do these weird things. My card (radeon 9600) can't detect anything connected to the S-video port if the dvi port was active when the card was initialized during boot, so the only way to activate tv-out is to reboot with my monitor disconnected and plug the monitor back in before ubuntu starts booting to let ubuntu detect the monitor.
Exactly what graphics card do you have? If it's new enough to use the proprietary driver (radeon HD 2xxx or higher), you may be better off using that, as it should handle tv-out through the catalyst control center.

---

### Post by mr clark25 on 2009-11-21
thanks for the reply.

when i run that command (xrandr -q), i get this output:
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)


my card is a radeon x1300 pro. it being a pro, it has 128mb more ram. (totals 256 mb) i dont know if it can use those drivers or not.

i now have another problem. i tried to install the catalyst control center and the driver that comes with it, and it must have done away with whatever driver i had before. now i cant use any visual affects. (i had it set to custom) i dont really know what i had before, so i don't think there is any way to fix this... i might have had that proprietary driver you mentioned... i really don't know...

---

### Post by mr clark25 on 2009-11-21
and now HD on a game i play (runescape) wont work because of that...

---

### Post by jocko on 2009-11-21
> **mr clark25 said:**
> thanks for the reply.

when i run that command (xrandr -q), i get this output:
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)


my card is a radeon x1300 pro. it being a pro, it has 128mb more ram. (totals 256 mb) i dont know if it can use those drivers or not.

i now have another problem. i tried to install the catalyst control center and the driver that comes with it, and it must have done away with whatever driver i had before. now i cant use any visual affects. (i had it set to custom) i dont really know what i had before, so i don't think there is any way to fix this... i might have had that proprietary driver you mentioned... i really don't know...
Ati's proprietary driver (fglrx/catalyst) does not support your card. It only supports radeon HD 2xxx and better cards. You have to use the open source driver (named radeon), which is installed and activated by default in ubuntu.
If the xrandr output was generated when you used the correct driver (radeon), it seems like the driver does not detect that you have a s-video output, but if it was generated after you tried to install fglrx it does not mean anything...

---

### Post by realzippy on 2009-11-21
You could test again:
Using the free ati driver make your xorg.conf look like this:

**gksudo gedit /etc/X11/xorg.conf**

[I]Section "Device"
Identifier "Configured Video Device"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "PAL-B"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Depth 24
Virtual 2480 1050
EndSubSection
EndSection[/I]




Restart X (log out/in)
Then terminal:

[B]xrandr --output S-video --set load_detection 1

xrandr --output S-video --set tv_standard pal

xrandr --addmode S-video 800x600

xrandr --output S-video --right-of VGA-0 --mode 800x600 [/B]

---

### Post by AlHounos on 2009-11-22
> **jocko said:**
> 
If the xrandr output was generated when you used the correct driver (radeon), it seems like the driver does not detect that you have a s-video output.

I have the same problem.  Like the thread starter, S-video works during bios and grub, but not when ubuntu begins loading.

How can I force ubuntu to recognize the s-video output?

---

### Post by mr clark25 on 2009-11-22
my xorh.conf file doesnt look like that mine reads:
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

should i just delete what is there and replace it? or do i need to do something?


it seems like my radeon card is good at corrupting data. i dont know how but it does. must be because they (the video card and HDD) are linked to the north bridge through the same chip. that is why i am using this instead of windows. i was messing with the card outputs(just hooking up and unhooking things) then windows crashed and slowly went downhill from there. now, my "places" thing in the top left got a little messed up, but i think i will survive.

---

### Post by realzippy on 2009-11-22
yes,replace all.To open:

**gksudo gedit /etc/X11/xorg.conf**

Then restart X
and run given xrandr commands



@ AlHounos:

if you have same hardware/software as OP you can try the same xorg.conf and xrandr commands.Otherwise suggest to open new thread.

---

### Post by mr clark25 on 2009-11-22
when i run the first command, i get what i believe to be an error message:
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24



i think this is the same message as earlier... i pasted that stuff to that file after deleting the old contents and then saved. it does have some stuff written in that file before the part that i removed. the whole file now reads:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
Option "TVOutFormat" "COMPOSITE"
Option "TVStandard" "PAL-B"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
SubSection "Display"
Depth 24
Virtual 2480 1050
EndSubSection
EndSection

---

### Post by gfox on 2009-11-22
Hi All,

I'm having the same problems I'm running karmic and have a ATI X1300. I modified the xorg.conf to one suggested, restarted X and I'm getting same error when trying to run any of the xrandr commands.

---

### Post by realzippy on 2009-11-23
What is xrandrs output after changing xorg.conf file?

**xrandr -q**

---

### Post by mr clark25 on 2009-11-23
that command gives me:

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 2480 x 1050
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
VGA-0 disconnected (normal left inverted right x axis y axis)

---

### Post by realzippy on 2009-11-23
Which resolution  can second monitor (TV on supervideocable) run?

Was xrandr -q output made when both monitors connected??

---

### Post by mr clark25 on 2009-11-23
1. i think jocko told me that its max is 800x600, although i dont know if that is true.

2. sorry, i forgot to hook it back up. ill try that and then run the command. if it still says that, ill reboot.

---

### Post by mr clark25 on 2009-11-23
i still get the same result when its hooked up.

after a reboot, i dont get any video on the s-video or my lcd.

---

### Post by gfox on 2009-11-23
I get a bit different result from the xrandr -q, but its the same no matter if the tv is connected to the S-Video or not, here is my xrandr -q

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2480 x 1050
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+   50.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4

---

### Post by mr clark25 on 2009-11-24
your xrandr is different than mine because you are running a different resolution than i am.

(this is an excuse for a bump...)

---

### Post by mr clark25 on 2009-11-25
bump...

---

### Post by sdowney717 on 2009-11-25
as far as i know, at this time, svideo tv out is not supported in the r500 chipset of which x1300 is a member.
so get an nvidia card, use the nvidia driver and you can get tv out

for example, here is my nvidia xorg.conf this gives me tv out in color
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@nannyberry)  Sat Sep  5 21:13:00 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-E540"
    HorizSync       30.0 - 110.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    Option         "TVStandard" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 1600x1200 +0+0, TV: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



---

### Post by mr clark25 on 2009-11-25
ok, i might go pick one up off of ebay.

---

### Post by gfox on 2009-11-26
What I don't understand is why it used to work with Intrepid, unless it has to do with preloaded drivers on Karmic, I remember that I had to use EnvyNG to install the correct drivers for my X1300 in Intrepid, so maybe I'll have to try EnvyNG again

---

### Post by jocko on 2009-11-27
> **gfox said:**
> What I don't understand is why it used to work with Intrepid, unless it has to do with preloaded drivers on Karmic, I remember that I had to use EnvyNG to install the correct drivers for my X1300 in Intrepid, so maybe I'll have to try EnvyNG again
It worked in intrepid because your graphics card was supported by ati's proprietary driver. Now ati has dropped support for your card, so you can't install the proprietary driver. That means EnvyNG will not help (but it may very well mess things up completely).
I also think that the open source driver (radeon) does not support tv-out on the newer cards yet, so you are out of luck.

---

### Post by gfox on 2009-11-27
thanks for letting me know or I would have done it and messed up the video, I guess I'll have to wait for the drivers to support the svideo out.

---

### Post by bts_22 on 2010-01-27
any update on this?

---

### Post by elliotn on 2010-01-27
I have da same problem, why coz windows displays well

---

### Post by simormate on 2010-03-08
My problem is setting the video output to pal. I did as jocko suggested:

> **jocko said:**
> First, set the TV standard:
```
xrandr --output S-video --set tv_standard [COLOR=Red]pal[/COLOR]
```

It is not clear for me if I have to do this command while the s-video is plugged in. I did it when s-video was not plugged in.
I got an error message similar to others before me: 

```
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  28
  Current serial number in output stream:  28
```


I also tried the command xrandr -q
The result was:

```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by gfox on 2010-06-13
Ok, since I installed **Lucid**, I haven't been able to use my VGA output, I've done some research and found a post to someone with video problems with ATI I gave it a try and my VGA output now works!, I haven't tried the svideo as I lost my cable but if anyone wants to try this here is the post, AGAIN this worked to fix my **VGA** problem in **Lucid**

[http://swiss.ubuntuforums.org/showpost.php?p=9223503&postcount=30]("http://swiss.ubuntuforums.org/showpost.php?p=9223503&postcount=30")

it just tells you to install from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc6-lucid/") the following kernel for Lucid in the order they appear, once installed restart the computer and try it out.

For intel processors 
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb

For AMD processors
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb

Let me know if this works!

---

### Post by cascade9 on 2010-06-13
> **gfox said:**
> 
For intel processors 
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_i386.deb

For AMD processors
linux-headers-2.6.34-020634rc6_2.6.34-020634rc6_all.deb
linux-headers-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb
linux-image-2.6.34-020634rc6-generic_2.6.34-020634rc6_amd64.deb


Just for your info, i386 works on both AMD and Intel CPUs, same with AMD64. i386 = 32bit, AMD64 = 64bit (x86-64).

---

