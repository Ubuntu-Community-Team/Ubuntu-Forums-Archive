---
title: "Counter-Strike 1.6 Steam"
date: 2006-02-25
forum: General Help
---

### Post by lektrik on 2006-02-25
I've recently installed ubuntu, and I've got Counter-Strike running with wine.
There looks to be many errors in terminal upon loading steam, and entering a server:

matthew@ubuntu:~$ wine ~/.wine/drive_c/ProgramFiles/Steam/Steam.exe Segmentation fault
matthew@ubuntu:~$ err: ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err: ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme: ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme: process: SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme: d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is none xistent at the moment!
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe082d0)->((nil),00000008 )
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe082d0)->((nil),00000013)
fixme: xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: process: SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
err: ole: CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err: ole: CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme: ole: CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
err: wave: DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err: wave: DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err: dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: process: SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16err: dscapture: widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  4
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme: xrandr: X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme: xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
matthew@ubuntu:~$ fixme: process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless

Once in a game, it often locks up and I have to kill counter-strike.

Any suggestions on getting this to work properly with wine?

---

### Post by soulglo83 on 2006-02-25
does alt-ctrl-f1 then alt-ctrl-f7 unlock the game for a few seconds? then respond back with whether or not it unfreezes steam/cs, then how important cs is to u, say in comparison with the stability of ur system and bootsplash for instance, and how linuxcapable are u?

---

### Post by Trab on 2006-02-25
this should be posted in the gaming forum mate...
also try looking around there... alot of helpful info, i installed CS the other day with wine, jsut fine (actually i used cedega, but there is a howto to use wine in the forummm...)

---

### Post by Ocxic on 2006-02-25
use cedega it's work' pretty good with CS

---

