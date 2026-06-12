---
title: "How I solved my Karmic resolution problem"
date: 2009-12-03
forum: General Help
---

### Post by hobo14 on 2009-12-03
I have an Acer 24" monitor plugged into my laptop, Karmic only offered me the choices of 1152x864 and 1920x1080, but I wanted 1440x900 like I used to have.
I have Intel 945GM/GMS (or similar) integrated graphics.
Here's my fix:

[SIZE="3"]_**1) Get the settings you'll need later:**_[/SIZE]

$ **cvt 1440 900**

That command gives output similar to this: 
[I]# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/I]
[COLOR="Green"]Note: any text below this in green is copy-pasted from the output of the previous line[/COLOR]

$ **xrandr**

Gives output similar to this:
[I]Screen 0: minimum 320 x 200, current 1152 x 864, maximum 4096 x 4096
**VGA1** connected 1152x864+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0 +
   1152x864       75.0     
**LVDS1** connected (normal left inverted right x axis y axis)
   1024x768       85.0     75.0     70.1     60.0     
   640x350        85.1  [/I]
[COLOR="Purple"]You can see I have two screens: _VGA1_ (my monitor) and _LVDS1_ (my laptop). Yours may be named something else, substitute names below accordingly - highlighted in purple[/COLOR]



[SIZE="3"]_**2) Testing - making sure the target resolution will work.**_ [/SIZE]

$ **xrandr --newmode [COLOR="Green"]"1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/COLOR]** [SIZE="1"]<-- green stuff copied from step 1 output[/SIZE]

$ **xrandr --addmode [COLOR="Purple"]VGA1[/COLOR] [COLOR="Green"]1440x900_60.00[/COLOR]**

$ **xrandr --output [COLOR="Purple"]VGA1[/COLOR] --mode [COLOR="Green"]1440x800_60.00[/COLOR] [COLOR="Gray"]--output LVDS1 --off[/COLOR]**

[COLOR="Gray"]Note: the grey stuff in the last line is only needed if you have a screen plugged into a laptop and want to turn the laptop screen off. Otherwise, leave it out.[/COLOR]

At this point, your resolution will have changed (if you can't see anything hit RightAlt+PrintScreen+K to go back to login.
Note that this resolution change isn't permanent.
One way to make it permanent is to add the three xrandr lines from step 2 into the file ~/.xprofile (create it if it doesn't exist).
That's not a good way to do it though, so go to step 3+4 for a better but more difficult way to make the change permanent....

**_[SIZE="3"]3) Create /etc/X11/xorg.conf   if it doesn't exist[/SIZE]_**

[COLOR="Red"]Note: this step only necessary if you don't have the file /etc/X11/xorg.conf[/COLOR]
If you already have it go directly to step 4.

Write down these next three lines _BEFORE_ you execute the first one!!:

$ **sudo /etc/init.d/gdm stop**  

The previous line will close down X; you will now be in a black screen with only a command line.  You did write down the next two lines first, didn't you? :D
Login here with your usual name and password.

$ **sudo Xorg -configure**

$ **sudo /etc/init.d/gdm start**

The previous line starts X again. Login.

The file ~/xorg.conf.new has been created. Move it to /etc/X11/xorg.conf:

$ **sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**


**_[SIZE="3"]4) Apply changes to /etc/X11/xorg.conf[/SIZE]_**

$ **sudo gedit /etc/X11/xorg.conf**

I used _[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")_ for this step.

I am not an expert on xorg.conf (not even close), so I'm just showing you my xorg.conf, with all additions by me marked in [COLOR="Red"]red[/COLOR] (I didn't remove anything from the file) and then an explanation of each addition below the file.
Note I'm only showing the _Monitor_, _Device_, and _Screen_ sections of xorg.conf, as they are the only relevant ones:

```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	[COLOR="Red"]Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/COLOR]
	[COLOR="Red"]Option       "PreferredMode" "1440x900_60.00"[/COLOR]
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
	[COLOR="Red"]Option  "Monitor0"[/COLOR]
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	[COLOR="Red"]DefaultDepth    24[/COLOR]	
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection	
	SubSection "Display"
		Viewport   0 0
		Depth     24
		[COLOR="Red"]Modes   "1440x900" "1024x768" "640x480"[/COLOR]
	EndSubSection
EndSection

```

An explanation of the five lines I added:

1. [COLOR="Red"]Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync[/COLOR]
This is copied and pasted from [COLOR="Green"]the output of cvt[/COLOR] in step 1.

2. [COLOR="Red"]Option "PreferredMode" "1440x900_60.00"[/COLOR]
Just using the mode name from the line above this.

3. [COLOR="Red"]Option  "Monitor0"[/COLOR]
Used the Identifier from the Monitor section: "Monitor0"

4. [COLOR="Red"]DefaultDepth    24[/COLOR]
Pretty obvious; just choosing which subsection below is default. Choose 24.

5. [COLOR="Red"]Modes   "1440x900" "1024x768" "640x480"[/COLOR]
1440x900 is my target resolution, obviously.  The other two are just standard ones that I put in this line for no particular reason.

Once you've made your changes to xorg.conf, save it, log out, log back in, then go to

**System > Preferences > Display**

and you should be able to choose 1440x900 (your resolution) as normal.  Success!


**_[SIZE="3"]5) Conclusion.[/SIZE]_**

That worked for me, I don't know if it will work for anyone else.  I honestly know nothing about xorg.conf, so please don't ask me for help with it, I can't help you :p

Obviously, you need to substitute your own desired resolution for my 1440 and 900.

I think (although I don't know) that if you're one of the people limited to 800x600 by Karmic, you have a different problem, and this won't work for you.

This didn't solve all my Karmic display woes: Without X, my monitor just smears the display across the screen, in an unreadable mess.  I have to rely on my laptop display when this happens. Note that I had this problem before this resolution fix, it's not a result of anything in this post.
This happens to me on boot (when my laptop shows a white Ubuntu symbol on a black background, but my monitor shows a flickering thin white smear on black), and if I go to tty (eg hit ctrl-alt-F1) my laptop displays it fine, but my monitor just shows a little white garbage on black.

If anyone knows how to fix this problem, please let me know.

---

### Post by jbrown96 on 2009-12-03
Glad you got it working, but this is not the proper forum. Please post threads like these in Other Community Discussions-->Tutorials & Tips.

---

