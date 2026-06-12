---
title: "Problems with CCSM, compiz effects and video driver, probably related"
date: 2010-04-16
forum: General Help
---

### Post by Rumtscho on 2010-04-16
Update: solved this by installing a driver from nvidia.com, it was a newer version than the one in the repository. 

I just got a new, very wide monitor (2560x1440) and there is no sense in maximizing applications. So I installed Compiz Config Settings Manager and enabled Grid. Nothing happened, the shortcuts don't move application windows.

Went to System -> Preferences -> Appearance, the Visual effects tab. It is at "disabled". When I try to set them to "normal" or "extra", a message box appears telling me that it's searching for video drivers, then disappears, and I get an error message "Desktop effects could not be enabled".

I opened Xorg.0.log, and had errors there:

(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "extmod" 

Going to Administration -> System -> Hardware drivers, it said that there are no available and/or installed hardware drivers. But apt-get said that it cannot install nvidia-glx-185, as it is already installed. Googling the error message suggested that I install and run something called envyng. This utility let me install the nvidia drivers again, and now I can see in the Hardware Drivers window that they are installed and active. But the error message in Xorg.0.log remains (problem 1), and I still cannot enable the Compiz effects (problem 2) or use Grid (problem 3).

Now, I don't have enough Linux experience to understand if this is a single cause-effect-chain of problems, or three independent ones, but I'd appreciate help for any of them.

I am running Ubuntu 9.10, the video card is a GeForce 7600GS.

---

