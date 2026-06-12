---
title: "Black screen on boot after AMD ATI driver installation"
date: 2011-10-22
forum: General Help
---

### Post by Abi79 on 2011-10-22
Hello. After updating to Ubuntu 11.10, I have installed the latest Catalyst drivers, following the instructions provided at: [http://ubuntuforums.org/showpost.php?p=11326398&postcount=5](http://ubuntuforums.org/showpost.php?p=11326398&postcount=5) [because from the additional drivers screen, the fglrx with post release updates gave errors when I tried to activate it]

However, after rebooting, I got a black screen a few seconds after the Ubuntu loading logo appeared. I've managed to step around this so far by going into the recovery mode from Grub, then dropping into the shell and then doing a sudo reboot now, which correctly starts Unity.

Here is some more info that may shed light on the issue for those more experienced than myself:

**DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p**
```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 5400 Series
OpenGL version string:  4.1.11079 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```[B]glxinfo | grep -i "direct rendering"
[/B]direct rendering: Yes[B]

Other info:
[/B]Ubuntu 11.10 32 bit
ATI Radeon HD 5470
Trying to run at a resolution of 1366x768

Is there some way to fix it? Thanks :)

---

### Post by j.benes on 2011-11-02
I have the similar, if not the same problem. After clean install on HP 4520s (ATI HD5470) I activated the ATI proprietary drivers. They worked just fine, except, I couldn't switch off or reboot - ever. So I uninstalled the ATI drivers, help to reboot/shutdown problem and installed OSS drivers. They work just fine, but not with unity, only with gnome shell. So I decided to go back to ATI proprietary and since then black screen on boot. Couldn't get to TTY, or anything else. Solved it after many hours, a bit awkwardly. First I replaced lightDM with gdm (in recovery console). It helped - I could get to TTY, but black screen didn't disappeared. Then I uninstalled the ATI proprietary and am back to OSS drivers, and back to gnome shell. After this I gradually tried ATI proprietary 11.8, 11.9 and 11.10. Not even the last ones helped with black screen, so I am stuck with OSS driver, for now (no disrespect to the guys doing that).
Hope it helpes a bit.

---

