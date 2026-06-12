---
title: "what kernel is the best for my cpu?"
date: 2006-06-23
forum: General Help
---

### Post by vranikx on 2006-06-23
hello all, does anybody knows what is the best kernel for my opteron cpu?
k7, 386 or 686?

---

### Post by frodon on 2006-06-23
The k7 kernel is the best for your opteron if you use the 32bit ubuntu version (X86), if you use the 64bit version of ubuntu don't change your kernel.

---

### Post by bruce89 on 2006-06-23
[QUOTE=frodon]...if you use the 64bit version of ubuntu don't change your kernel.[/QUOTE]
Really, why not?  I'm fine on the -k8 one here, as opposed to the -generic kernel.
Anyway Opteron is -k8 on the AMD64 version.

---

### Post by frodon on 2006-06-23
It was just an advice, i never used the k8 kernel neither the 64bit kernel but some users like you say that it works pretty well, however i can't advice it because i never used it.
Did the k8 kernel improve your performances compared to the default 64bit kernel ?
I'm curious, thanks for the useful input bruce89 ;)

---

### Post by vranikx on 2006-06-23
[QUOTE=frodon]The k7 kernel is the best for your opteron if you use the 32bit ubuntu version (X86), if you use the 64bit version of ubuntu don't change your kernel.[/QUOTE]

hmm, ok, i change to k7 kernel, but is it possible to change my kubuntu 32bit to 64bit? i mean kernel? or not?

---

### Post by bruce89 on 2006-06-23
[QUOTE=vranikx]hmm, ok, i change to k7 kernel, but is it possible to change my kubuntu 32bit to 64bit? i mean kernel? or not?[/QUOTE]
No, you'd have to reinstall from the 64bit CD, there is no way (yet) to upgrade from an i386 (K)Ubuntu to an AMD64 (K)Ubuntu, as all the binaries are different.  A 64bit kernel in a 32bit environment wouldn't work, and there wouldn't be a huge amount of point.
[QUOTE=frodon]It was just an advice, i never used the k8 kernel neither the 64bit kernel but some users like you say that it works pretty well, however i can't advice it because i never used it.
Did the k8 kernel improve your performances compared to the default 64bit kernel ?
I'm curious, thanks for the useful input bruce89 ;)[/QUOTE]
It seems reasonable to not suggest it if you haven't had any experience of it, but I wouldn't advise against it.  I can't remember if it sped things up, I suppose it did.

---

### Post by vranikx on 2006-06-23
[QUOTE=bruce89]No, you'd have to reinstall from the 64bit CD, there is no way (yet) to upgrade from an i386 (K)Ubuntu to an AMD64 (K)Ubuntu.[/QUOTE]

:(( aaha, so when i will reinstall kubuntu i will lost all my settings :( is any chance to reinstall kubuntu without reformating drive? i want 64bit because sometimes my kubuntu is so slow and i dont know why, rendering of windows etc...i have nvidia 6800 and opteron 2700mhz and 1 gb of ram in dual channel and it so slow and dont know why:(

---

### Post by bruce89 on 2006-06-23
[QUOTE=vranikx]:(( aaha, so when i will reinstall kubuntu i will lost all my settings :( is any chance to reinstall kubuntu without reformating drive? i want 64bit because sometimes my kubuntu is so slow and i dont know why, rendering of windows etc...i have nvidia 6800 and opteron 2700mhz and 1 gb of ram in dual channel and it so slow and dont know why:([/QUOTE]
You could back up your /home directory, and then reinstall.  You then need to put your /home directory back.  Better still would be creating a seperate /home partition.  See [http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html).  This way all your settings will remain, but all your installed programs won't be, you'll have to reinstall them.

---

### Post by vranikx on 2006-06-23
[QUOTE=bruce89]You could back up your /home directory, and then reinstall.  You then need to put your /home directory back.  Better still would be creating a seperate /home partition.  See [http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html).  This way all your settings will remain, but all your installed programs won't be, you'll have to reinstall them.[/QUOTE]

aha, thanx man :D i will try it :D and last question, is it amd64 kubuntu stable? because when i had 5.10 amd64bit it was so buggy, so many hardware not working etc...

---

### Post by bruce89 on 2006-06-23
[QUOTE=vranikx]aha, thanx man :D i will try it :D and last question, is it amd64 kubuntu stable? because when i had 5.10 amd64bit it was so buggy, so many hardware not working etc...[/QUOTE]
All I can say is that it works on my hardware, 6.06 should be better than 5.10.  Try the Desktop CD (used to be called LiveCD), and see if it works (that's the CD you use to install it now anyway).
You have to forfeit a few things on AMD64, such as WINE, w32codecs, flash, java applets; so don't use it if you can't live without these.  It is possible to make these work, but it is difficult to do so (even I haven't attempted it).

---

### Post by vranikx on 2006-06-23
[QUOTE=bruce89]All I can say is that it works on my hardware, 6.06 should be better than 5.10.  Try the Desktop CD (used to be called LiveCD), and see if it works (that's the CD you use to install it now anyway).
You have to forfeit a few things on AMD64, such as WINE, w32codecs, flash, java applets; so don't use it if you can't live without these.  It is possible to make these work, but it is difficult to do so (even I haven't attempted it).[/QUOTE]

aaha, thanx man, so i will be still in 32bit kubuntu....btw still i dont understand why is rendering of windows so slow in kubuntu, in windows xp i have really performance of rendering but not in kubuntu...weird because i have strong graphic card......

---

### Post by frodon on 2006-06-23
Did you install the drivers for your graphic cards ?

If yes you could tweak a little bit your xorg.conf file.

---

### Post by vranikx on 2006-06-23
[QUOTE=frodon]Did you install the drivers for your graphic cards ?

If yes you could tweak a little bit your xorg.conf file.[/QUOTE]

yes, of course, i have latest...and in xorg i have this: 

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "NoLogo" "true"  # Disables nVidia's logo on start-up
        Option "NvAGP" "1"  # Tries internal nVidia AGP drivers first
        Option "RenderAccel" "true"  # Duh :)
 	Option "HWcursor" "Enabled"        
 	Option "SWcursor" "Disabled"	
	Option "CursorShadow" "true"  # Adds an alpha-shadow to your cursor
        Option "AllowGLXWithComposite" "true"  # Mostly used for cool effects
	Option "IgnoreDisplayDevices" "DFP,TV"
	Option      "backingstore" "true"
EndSection

in glxgears i have this fps: 

vranik@vranik-desktop:~$ glxgears
34613 frames in 5.0 seconds = 8313.560 FPS
41419 frames in 5.0 seconds = 8283.782 FPS
41389 frames in 5.0 seconds = 8277.764 FPS
41357 frames in 5.0 seconds = 8271.241 FPS
41600 frames in 5.0 seconds = 8319.875 FPS
41453 frames in 5.0 seconds = 8290.546 FPS
41406 frames in 5.0 seconds = 8281.195 FPS

opengl is also quick but rendering and refreshing of windows in 2D is so slow...:( i dont know why...

---

### Post by vranikx on 2006-06-23
hmm, it`s look like common problem: [http://www.ubuntuforums.org/showthread.php?t=172990&highlight=slow+rendering](http://www.ubuntuforums.org/showthread.php?t=172990&highlight=slow+rendering)
[http://www.nvnews.net/vbulletin/showthread.php?t=65857&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=65857&page=6)

[http://bw.uwcs.co.uk/nvidia-fonts.mpg](http://bw.uwcs.co.uk/nvidia-fonts.mpg)

---

