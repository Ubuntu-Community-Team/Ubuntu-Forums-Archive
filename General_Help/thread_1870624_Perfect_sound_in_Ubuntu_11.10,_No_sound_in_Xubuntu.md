---
title: "Perfect sound in Ubuntu 11.10, No sound in Xubuntu 11.10"
date: 2011-10-27
forum: General Help
---

### Post by razaz03 on 2011-10-27
**Perfect sound in Ubuntu 11.10, No sound in Xubuntu 11.10** 			
 			 			 		   		 		 		The most  significant input I can provide without pasting terminal commands is the  above, Sound works perfectly with my Creative X-Fi soundcard in W7 and  Ubuntu 11.10 (fresh install) but not Xubuntu 11.10 (fresh install), so I  refuse to believe an ALSA driver doesn't exist.

I can see my volume button with Creative X-FI (Alsa mixer) and Playback:  SB X-Fi Analogue Stereo (Pulse Audio Mixer) amongst others, with every  option unmuted.

[COLOR=navy][U]**[SIZE=4][B]Comprehensive Sound Problem Solutions Guide** v0.5e 

[/SIZE][/B][/U][/COLOR]
[LEFT][SIZE=2]**(1)** Go to a shell and type:      Code:
     aplay -l 
[/SIZE][/LEFT]
[COLOR=navy][FONT=Verdana][SIZE=4][COLOR=Black][SIZE=2]card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

and 

card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Amongst onboard.

[/SIZE][/COLOR][/SIZE][/FONT][/COLOR][LEFT][SIZE=2]**(2)** Type this into the shell:      Code:
     lspci -v 
[/SIZE][/LEFT]
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs Device 0023
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at ec00 [size=32]
    Memory at fea00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

[SIZE=2]**(3)** Check to see if the ALSA driver for your sound card exists. Go to [/SIZE][[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")[SIZE=2]   and search for your sound card (chipset) manufacturer in the dropdown   box. You'll be given a matrix of the sound cards made by the   manufacturer. Try to match the chipset you found in step 2 with the   driver([COLOR=seagreen]green hyperlink text[/COLOR]).[/SIZE]

I don't see ctxfi in the list but big deal; it works in Ubuntu 11.10.

[SIZE=2]**(4)** Now go back to the shell and type      Code:
     sudo modprobe snd-ctxfi 
[/SIZE]
[LIST]
[*][SIZE=2][COLOR=red]**Failure**[/COLOR] -You have two options[/SIZE]
[/LIST]

[LIST]
[*][SIZE=2]Move on to **Getting the ALSA drivers from a *fresh* kernel**.   This step is easier and is recommended to users who might have been   tinkering with their sound settings and want to revert back to the way   it was just after installing **Ubuntu **(without reinstalling Ubuntu of course :wink: )[/SIZE]
[/LIST]
[SIZE=2]Move on to **ALSA driver Compilation**, if you have not done so already. If you have, please post a new thread with your problem.[/SIZE][COLOR=navy][FONT=Verdana][SIZE=4][COLOR=Black][SIZE=2]


Many thanks,


Followed the guide to a tee and it doesn't work: My user was not in audio when I typed into terminal:

raz@raznix:~$ grep 'audio' /etc/group
audio:mad::29:razz:ulse

after following the guide, changing it to:

raz@raznix:~$ grep 'audio' /etc/group
audio:mad::29:razz:ulse:raz

It. Still. Doesn't. Work

Included is a screen shot I took in desperation, please help![/SIZE][/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by razaz03 on 2011-10-27
Buuuuuump, no solution as yet and I would really appreciate any ideas!

---

