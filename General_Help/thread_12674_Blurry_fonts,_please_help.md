---
title: "Blurry fonts, please help"
date: 2005-01-26
forum: General Help
---

### Post by Sham on 2005-01-26
I installed Warty on my desktop which is attaceh to an LCD screen. Problem is, the fonts look blurry around the edges. Its so bad I'm starting to feel sick :(

Is there anything I can do about this to make the fonts nice and crisp?

---

### Post by albersag on 2005-01-26
[QUOTE=Sham]I installed Warty on my desktop which is attaceh to an LCD screen. Problem is, the fonts look blurry around the edges. Its so bad I'm starting to feel sick :(

Is there anything I can do about this to make the fonts nice and crisp?[/QUOTE]
 I have the same problem during weeks. I went to optics because i though were my eyes but no ;)

is a font config problem. At least i have mi fonts beautifull on my laptop. Presario 2516.

Before i read too much without any luck

try desactivate autohinting on font config.

sudo dpkg-reconfigure fontconfig

Then you can choose the tipography you like via desktop->preferences->tipography

I hope you would resolve your sick problems, i have had the same sensation ;)

---

### Post by nocturn on 2005-01-26
[QUOTE=Sham]I installed Warty on my desktop which is attaceh to an LCD screen. Problem is, the fonts look blurry around the edges. Its so bad I'm starting to feel sick :(

Is there anything I can do about this to make the fonts nice and crisp?[/QUOTE]

Since you are on Warty, maybe you could file a bugreport on this?

---

### Post by Sham on 2005-01-26
This is so annoying. I have to use my computer for 10 hour a day. I'll be lucky to make it to 11am at this rate.

I tried turning off the autohinting in Computer -> Desktop Prefs -> Font, but they look really crappy. KDE under Fedora Core 3 looked so much better than this.

---

### Post by nocturn on 2005-01-26
[QUOTE=Sham]This is so annoying. I have to use my computer for 10 hour a day. I'll be lucky to make it to 11am at this rate.

I tried turning off the autohinting in Computer -> Desktop Prefs -> Font, but they look really crappy. KDE under Fedora Core 3 looked so much better than this.[/QUOTE]

Are you unsing KDE?

If so, check kcontrol, font settings to see if anti-aliassing is on.

---

### Post by nocturn on 2005-01-26
I don't know if the problem will show, but can you take a screenshot of them?

---

### Post by Sham on 2005-01-26
[QUOTE=nocturn]I don't know if the problem will show, but can you take a screenshot of them?[/QUOTE]

I'm running Gnome. I've seen a few screenshots of people trying to demonstrate blurry fonts, but to be honest, it doesnt show well at all.

The only way I can decribe it is to say the edges lack definition. It looks really grim in Firefox and Xemacs doesn't look any better either. The letters don't look solid black, but kind or charcoal grey.

Does this make sense?

This is what my XF86Config-4 looks like:

```
 Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600XT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-90
	VertRefresh	60-75
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV31 [GeForce FX 5600XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection 
```

---

### Post by nocturn on 2005-01-26
[QUOTE=Sham]I'm running Gnome. I've seen a few screenshots of people trying to demonstrate blurry fonts, but to be honest, it doesnt show well at all.

The only way I can decribe it is to say the edges lack definition. It looks really grim in Firefox and Xemacs doesn't look any better either. The letters don't look solid black, but kind or charcoal grey.

Does this make sense?

This is what my XF86Config-4 looks like:
[/QUOTE]

I don't see anything wrong with the config.  
Do you have the Ubuntu livecd?  Try if it shows the same problem.

Maybe you can try something like knoppix too.
If they are fine, you can check what the difference between their config and yours is.

---

### Post by Sham on 2005-01-26
[QUOTE=nocturn]I don't see anything wrong with the config.  
Do you have the Ubuntu livecd?  Try if it shows the same problem.

Maybe you can try something like knoppix too.
If they are fine, you can check what the difference between their config and yours is.[/QUOTE]

Good point. Will try soon and post back.

---

### Post by Buffalo Soldier on 2005-01-26
I've had same problems with my fonts too, it was bad especially in FireFox. I tried the  [HOWTO: Make your fonts smooth enough to drool over](http://ubuntuforums.org/showthread.php?t=4456). It made some improvement on my desktop fonts but the fonts in Firefox still looks bad. But after some tweaking around, I finaly managed to find a setting that I like.

I've set my desktop font resolution to 96 DPI
[indent]*Computer -> Desktop Preferences -> Font -> Details*[/indent]

Then I set me FireFox font at 72 DPI and minimum font size at 14
[indent]*Edit -> Preferences -> General -> Fonts & Colors*[/indent]

Now all of my fonts are better looking than what was on my WinXP. Using only Ubuntu default fonts. No msttfonts.

(I'm on a 19" CRT monitor with 1600x1200 resolution.)

---

### Post by Sham on 2005-01-26
[QUOTE=Buffalo Soldier]I've had same problems with my fonts too, it was bad especially in FireFox. I tried the  [HOWTO: Make your fonts smooth enough to drool over](http://ubuntuforums.org/showthread.php?t=4456). It made some improvement on my desktop fonts but the fonts in Firefox still looks bad. But after some tweaking around, I finaly managed to find a setting that I like.

I've set my desktop font resolution to 96 DPI
[indent]*Computer -> Desktop Preferences -> Font -> Details*[/indent]

Then I set me FireFox font at 72 DPI and minimum font size at 14
[indent]*Edit -> Preferences -> General -> Fonts & Colors*[/indent]

Now all of my fonts are better looking than what was on my WinXP. Using only Ubuntu default fonts. No msttfonts.

(I'm on a 19" CRT monitor with 1600x1200 resolution.)[/QUOTE]

I tried that, but no joy. I have a feeling it has something to do with antialiasing which tries to smeooth the edges. I guess to some people it looks nice and smooth, but to me it looks out of focus. I'm pretty sure my eyes are ok ;)

---

### Post by Sham on 2005-01-26
Ok, I tried antialiasing, and it still didn't work. I'm off home to lie down. My head is throbbing like a mofo.

Any ideas would be more than appreciated, lifesaving is more the word.

---

### Post by mendicant on 2005-01-26
Some people have problems with anti-aliasing.  It makes letters fuzzy--the blurring.  You can try the various options under fontconfig:

dpkg-reconfigure fontconfig

Maybe try the one for CRT screens?  Also, check the subpixel rendering in /etc/fonts/local.conf--you can try setting rgba to none instead of rgb.

---

### Post by neville_lobo on 2005-03-04
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=257705&perpage=15&pagenumber=1)

Try the instructions in the above link. Page 1 has got all the main instructions and page 4 has got Ubuntu specific instructions. It worked amazingly well for me. My desktop is as crisp as my old windows desktop. I will try and compile a warty specific How-to.

Neville

---

