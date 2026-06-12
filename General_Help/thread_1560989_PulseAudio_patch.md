---
title: "PulseAudio patch"
date: 2010-08-25
forum: General Help
---

### Post by andyturner87 on 2010-08-25
Hello.  I'm really new to Ubuntu and I'm struggling.  Trying to run an M-Audio Audiophile 2496, with Ubuntu 9.10 studio, not getting anywhere so far.  But, after a lot of searching I found this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63") - which seems to be worth trying.

The thing is though, I don't know what any of it means.  I'm stuck on what seems to be pretty basic but not for someone that doesn't have a clue.

Anyway, this possible solution tells me twice to create a file.  Once in one directory I guess and once in another.  So far, that's all I've worked out.  I've been to the directory it says and I can't create a document in there.  I tried making the document on the desktop and moving it over to the place but I still couldn't do it, said permission denied.

I've looked online for a while now and cant find anything that is getting me passed this hurdle.  I must be missing something obvious but I'm pretty tired now and fed up sooo....   if anyone could  please let me know where I'm going wrong I would be ever so grateful.

Andy

---

### Post by Smart Viking on 2010-08-25
```
sudo touch /etc/udev/rules.d/ice1712-pulseaudio-workaround.rules

``````
sudo gedit /etc/udev/ rules.d/ice1712-pulseaudio-workaround.rules
 
```The above command will enter text editor, and past the following command into the editor and save:
```
SUBSYSTEM!="sound", GOTO="ice1712_end"
ACTION!="change", GOTO="ice1712_end"
KERNEL!="card*", GOTO="ice1712_end" SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="via-ice1712.conf"
 LABEL="ice1712_end"
``````
sudo touch /usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf

``````
sudo gedit /usr/share/ pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf
 
```then do the same, but enter this text into the file:

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Via ICE1712 multi-channel audio chipset
;
; This chipset has up to four stereo pairs of input and four stereo pairs of
; output, named channels 1 to 8. Also available are separate S/PDIF stereo
; channels (input and output), and a separate "system-out" stereo jack that
; supports 6-channel hardware mixing.
;
; The S/PDIF stereo channels can be controlled via the mixer for hw:0, and
; additionally, the 8 main outputs can be loop-routed to a separate stereo
; input pair, available as channels 11 and 12.
;
; Many cards available from vendors do not expose all channels from this chip
; to an external port, which effectively reduces the number of channels that
; are useful to the user. However, the ALSA driver still exposes all channels
; even if they are not connected.
;
; We knowingly only define a subset of the theoretically possible
; mapping combinations as profiles here.
;
; See default.conf for an explanation on the directives used here.

[General]
auto-profiles = no

[Mapping analog-mch-in]
description = Analog Multi-Channel Main Input
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1,aux2,aux3
channel-map = aux0,aux1,front-left,front-right,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9
direction = input

[Mapping analog-mch-out]
description = Analog Multi-Channel Main Output
device-strings = hw:%f,0
#channel-map = front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
direction = output

[Mapping digital-stereo]
description = Digital Stereo Input/Output
#device-strings = hw:%f,1
device-strings = iec958:%f
channel-map = left,right
direction = any

[Mapping analog-system-out]
description = Analog Stereo System-Out
device-strings = hw:%f,2
channel-map = left,right
direction = output


[Profile output:mch]
description = Multi-Channel Output Active (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings =
priority = 90
skip-probe = yes

[Profile output:mch+input:mch]
description = Multi-Channel Input/Output (Digital Disabled)
output-mappings = analog-mch-out analog-system-out
input-mappings = analog-mch-in
priority = 100
skip-probe = yes

[Profile output:spdif]
description = Digital Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings =
priority = 80
skip-probe = yes

[Profile output:spdif+input:spdif]
description = Digital Input/Output (Multi-Channel Disabled)
output-mappings = digital-stereo analog-system-out
input-mappings = digital-stereo
priority = 90
skip-probe = yes

[Profile output:system]
description = System Output Only
output-mappings = analog-system-out
input-mappings =
priority = 60
skip-probe = yes


```Beware if errors i may have made, i made it pretty quick. :)

EDIT: By the way, you post those command into the "terminal" program, except for the parts that are text you put into the files. :)

EDIT2:
run the following command when you are done, to restart pulseaudio(as the guy stated in the bug report):
```
pulseaudio --kill && pulseaudio --start
```

---

