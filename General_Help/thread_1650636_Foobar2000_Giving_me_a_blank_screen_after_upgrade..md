---
title: "Foobar2000 Giving me a blank screen after upgrade."
date: 2010-12-22
forum: General Help
---

### Post by osc1882 on 2010-12-22
Ubuntu 10.10 32 Bit
Wine 1.3.9

Alright so this happens to me after every time wine updates from the wine PPA. Foobar2000 works fine till Wine updates, after it updates it pops up a full sized window and instead of it looking like it should it.... looks like whatever was on the screen when the window opens. It's non functional. I tried using the portable version of wine this time and the same thing happens after a update. This is... sad for me because I use it for transcoding. 

Bellow is what was spat at me when I ran it thru a terminal.  


> grammatrain@tprb:~$ wine /home/grammatrain/Desktop/foobar2000/foobar2000.exe -opengl
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:win:RegisterShellHookWindow (0x10066): stub
grammatrain@tprb:~$ wine /home/grammatrain/Desktop/foobar2000/foobar2000.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:win:RegisterShellHookWindow (0x10066): stub


---

### Post by osc1882 on 2010-12-22
I found these instructions else where but I don't understand how to do this.


1. Run with -opengl

2. Run in a "virtual desktop" In the graphics settings in WINE

---

### Post by osc1882 on 2010-12-23
Can anyone help?

---

### Post by osc1882 on 2010-12-27
Anyone?

---

