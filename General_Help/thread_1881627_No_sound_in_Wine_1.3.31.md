---
title: "No sound in Wine 1.3.31"
date: 2011-11-15
forum: General Help
---

### Post by ethenstien on 2011-11-15
Hi, I am aware that this has most likely been covered tons of times, but I am completely confused and clueless as how to solve this. I am running Ubuntu 10.04 and Wine 1.3.31, and as the title says, I have no sound. I am mainly trying to play Torchlight, but Diablo 2 and Clive Barkers Undying don't have sound either. Any help in solving this would be greatly appreciated, because I have no idea of what to do.

---

### Post by valantis1985 on 2011-11-26
i have the same problem exactly

---

### Post by andrewcd on 2012-01-19
I have the same problem.  I tried to run wine from the terminal, and here is all of the ouput I got:

```
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ wine "Diablo II.exe"
fixme:advapi:SetSecurityInfo stub
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ fixme:win:EnumDisplayDevicesW ((null),0,0x33f208,0x00000000), stub!
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1625b0, last error 0x591
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1625b0, last error 0x591
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x14adf8, last error 0x591
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winediag:AUDDRV_GetAudioEndpoint PulseAudio "default" -22 without handle_underrun. Audio may hang. Please upgrade to alsa_plugins >= 1.0.24
fixme:d3d_surface:wined3d_surface_flip Ignoring flags 0x1.
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for candrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1917d8, last error 0x591
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1917d8, last error 0x591
err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:d3d_surface:surface_remove_pbo Surface 0x144638 has heapMemory 0x3ff0020 and flags 0x130138.
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for candrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1917d8, last error 0x591
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1d35348, last error 0x591
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1d21e88, last error 0x591
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for candrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x1cd6e70, last error 0x591
andrew@andrew-laptop:~/.local/share/wineprefixes/diablo2/drive_c/Program Files/Diablo II$ err:wgl:internal_SetPixelFormat Invalid operation on root_window
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 1 for context 0x23b6708, last error 0x591

```

When I do this, the game loads, and the sound blips on, and then off.  It doesn't come back.

I don't know what all of that means.  Other [threads]("http://ubuntuforums.org/showthread.php?t=1534466") say to select "emulation" in the audio tab in winecfg.  But there is no audio tab in winecfg.  

Any help much appreciated.

---

### Post by neigun on 2012-02-10
Hi Guys 

There has been a bit of a rewrite in Wine in relation to sound.  Have a read of this article for more info:

[http://www.omgubuntu.co.uk/2011/07/latest-wine-update-breaks-pulseaudio/](http://www.omgubuntu.co.uk/2011/07/latest-wine-update-breaks-pulseaudio/)

I would try an earlier version from:

[http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)

1.3.24 for natty should be OK.

TTFN Neil

---

### Post by neigun on 2012-02-10
Hi Guys 

Its me again!  You'll probably have dependency issues with those earlier versions.

Try installing this ppa: ppa:ubuntu-wine/ppa

Its currently on 1.4rc2 and works fine on Ubuntu 11.10, Gnome 3, etc.

The graphics and sound seems to be far better than on earlier versions.  

My kids ;-) can now play Diablo II and Simcity 4!
 
TTFN

Neil

---

### Post by eniodefarias on 2012-10-05
try this:

1. open Winetricks:
 $ winetricks

2. check “Select the default wineprefix” and clik OK

3. check “Changes settings”  and clik OK

4. check “ddr=gdi”  and clik OK


[http://aoredordoburacotudoebeira.wordpress.com/2012/10/05/wine-sem-som/](http://aoredordoburacotudoebeira.wordpress.com/2012/10/05/wine-sem-som/)

---

