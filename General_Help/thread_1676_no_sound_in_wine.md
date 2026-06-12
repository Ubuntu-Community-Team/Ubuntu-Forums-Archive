---
title: "no sound in wine"
date: 2004-10-22
forum: General Help
---

### Post by mailmesuf on 2004-10-22
I've installed wine from the debian list, version 20040716, and i'm not getting any sound in wine.
I Googled al over the place searching for posts about wine without sound but couldn't find anything regarding my problem because i don't have the esd/esound deamon running and sound works for my sytem, mplayer, xmms clone.
I tried both the wineoss.drv and winealsa.drv but wihtout succes.

using the latest Ubuntu, upgraded yesterday from the preview version.
Linux swirl 2.6.8.1-3-386 #1 Thu Oct 7 14:19:47 BST 2004 i686 GNU/Linux
my onboard soundcard: nVidia Corporation nForce2 AC97 Audio
 
Hope someone can help me out.

---

### Post by c_plus_plus on 2007-03-04
I am using the EXACT same sound device. I have the same problem with wine. I managed to get rid of all the errors that winecfg gave me, and my other system sound works with the default settings. The program I am trying to run is Starcraft.

Edit: output of running starcraft (even after enabling driver emulation):> 
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1814c0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x180c48)->(0x20024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x180c48)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


EDIT x2: Realized what instructions were actually saying... I changed pulldown to Emuation, and then unchecked driver emulation. mailmesuf: this will probably work for you.

EDIT x3: Ive been playing and the sound works, but at times I hear a loud white noise. Any Idea what would cause whitenoise?

---

### Post by Mark C on 2007-03-13
I'm having the exact same problem right now. It's on a 64-bit system. I'm sure i've installed all 32-bit libraries since wine doesn't complain about any missing library.

I can play the game using the fixes c_plus_plus said above though.

---

### Post by mmendez on 2007-05-25
Check this link out that deals with the same issue

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft[/COLOR]]("http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft")

> **knn said:**
> Those are just warnings, they're normal. You don't need the jack library, just use alsa as the audio output. The other two are missing features, but I don't think Starcraft needs sound capture. In fact, Starcraft should work pretty well with Wine:
[wine appdb entry]("http://appdb.winehq.org/appview.php?iVersionId=149&iTestingId=11607")

I was getting no sound at all and when I deselected OSS and selected ALSA everything was working A OK so you might want to try this

---

