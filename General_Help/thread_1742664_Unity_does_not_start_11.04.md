---
title: "Unity does not start 11.04"
date: 2011-04-29
forum: General Help
---

### Post by t36 on 2011-04-29
Hi,

I just recently upgraded from 10.10 to 11.04 and I wanted to try out the unity interface. However whenever I start Ubuntu, I always go to my "old" user interface. I have tried selecting Ubuntu and Ubuntu Classic and the login. Anyone knows what's going on?

Greetings,

t36

---

### Post by imigueldiaz on 2011-04-29
> **t36 said:**
> Hi,

I just recently upgraded from 10.10 to 11.04 and I wanted to try out the unity interface. However whenever I start Ubuntu, I always go to my "old" user interface. I have tried selecting Ubuntu and Ubuntu Classic and the login. Anyone knows what's going on?

Greetings,

t36

Hi,

Surely it's related to your graphic card specs. If you could post chipset (nVidia, ATI, intel..) and model, perhaps someone could guide you :)

Best

---

### Post by t36 on 2011-04-29
Well I have this onboard:

```

lspci -v | grep -i vga
02:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series] (prog-if 00 [VGA controller])
```

---

### Post by NormanFLinux on 2011-04-29
Cards over five years old will default to GNOME Classic. I think you would be better off installing Unity 2D from the repository.

---

### Post by t36 on 2011-04-29
> **NormanFLinux said:**
> Cards over five years old will default to GNOME Classic. I think you would be better off installing Unity 2D from the repository.

The HD5800 was announced in 2009, and seeing that it supports Directx10 and HD output I really doubt that it is older than 5 years. So I don't think this is the problem.

---

### Post by imigueldiaz on 2011-04-29
> **t36 said:**
> The HD5800 was announced in 2009, and seeing that it supports Directx10 and HD output I really doubt that it is older than 5 years. So I don't think this is the problem.

These seem to be the specs needed to tun unity according to developers:

[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

Hope It helps :)

PS. I have no idea about HD5800 capabilities :) 

Best

---

### Post by sikander3786 on 2011-04-29
Did you install the drivers for you ATI card? From the classic session, go to System > Administration > Additional Drivers and activate the recommended ones. If successful, on a reboot, it should automatically log you in to Unity.

Otherwise on the login screen, click your username and choose 'Ubuntu' from Sessions. Login. Successful?

---

### Post by t36 on 2011-04-29
> **sikander3786 said:**
> Did you install the drivers for you ATI card? From the classic session, go to System > Administration > Additional Drivers and activate the recommended ones. If successful, on a reboot, it should automatically log you in to Unity.

Otherwise on the login screen, click your username and choose 'Ubuntu' from Sessions. Login. Successful?

I was already using the recommended drivers like you said, and I have tried selecting Ubuntu from the login screen. I end up in the "old" interface.

---

### Post by robert shearer on 2011-04-29
> **NormanFLinux said:**
> Cards over five years old will default to GNOME Classic. I think you would be better off installing Unity 2D from the repository.

> Cards over five years old will default to GNOME Classic  where did you get that gem ??

Using 
 *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation

which is a wee bit more than 5 years old...:)

and not alone here, see....
[http://ubuntuforums.org/showpost.php?p=10733610&postcount=6](http://ubuntuforums.org/showpost.php?p=10733610&postcount=6)

but,yes, agreed that Unity-2d is much more appropriate for older graphics cards and lower spec hardware.

open Software centre and search for unity-2d

---

### Post by t36 on 2011-04-29
After running ```
/usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series 
OpenGL version string:  1.4 (2.1 (4.1.10665 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

I discovered that GL vertex buffer object seems to be the problem. So I will try to fix it from here.

---

