---
title: "projectM trying to get the splash to go away"
date: 2011-06-23
forum: General Help
---

### Post by boblizar on 2011-06-23
ive edited ~/.projectM/config.inp

```

# config.inp
# Configuration File for projectM

Texture Size = 1024			# Size of internal rendering texture
Mesh X  = 32            	# Width of PerPixel Equation mesh
Mesh Y  = 24          		# Height of PerPixel Equation mesh
FPS  = 75          		# Frames Per Second 
Fullscreen  = false		
Window Width  = 640  	       	# startup window width
Window Height = 512            	# startup window height

Smooth Transition Duration = 5  # in seconds
Preset Duration = 30 	     	# in seconds
Easter Egg Parameter = 0

Hard Cut Sensitivity = 10       # Lower to make hard cuts more frequent
Aspect Correction = true	# Custom Shape Aspect Correction

Preset Path = /usr/share/projectM/presets # preset location
Title Font = /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
Menu Font = /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMono.ttf

```

so far this configuration runs GREAT on my machine, however i still get the "project M" splash at start when i want to go directly into the voodoo.  thanks in advance for any info updates :popcorn:

update from me, im getting the bright idea to boot into my doze partition and to look at all the milkdrop settings and post accordingly...  and i know i dont like a few of the presets, like the cheesy junky faces and dancing stick figures, so ill write a command to delete those presets.

from doze
meshz
```

8x6 (FAST!!)
16x12 (fast)
24x18
32x24
40x30
48x36 (default)
64x48
80x60 (slow)
96x72 (SLOW)
128x96 (SLOW!)
160x120 (REALLY SLOW!!!)
192x144 (TURTLE SLOW!!!!!!!)

```
(i feel dirty posting to a linux forum from windows)

80x60 runs great on my machine!!!  however it makes the processor run hot, from 100f idle to 120f

another note, projectM is not multi thread aware, it punishes a single core to the max.  if this program was multi thread aware i could probably push it even further.

my machines phenom 9950 x4 4gb ram 800mhz...  geforce 9600 GT gig edition.  850 watt power supply....  does anyone know anything about virtical sync for projectM???  i get some page tearing going on for some presets.

found M produces a menu in projectm pulse audio....  i belive the search shows a geiss project m one
i think i want to remove the TGA files that say "projectM" @ boot of the program....  deleted the files, but it still shows up

sudo rm /usr/share/projectM/presets/Rovastar\ -\ A\ Million\ Miles\ from\ Earth.milk

---

