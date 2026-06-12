---
title: "dock autohide: redress black artefact after autohiding"
date: 2011-09-05
forum: General Help
---

### Post by kbrand on 2011-09-05
Esteemed Ubuntu Users and Devs,

After rearranging icons on the dock (& possibly other dock specific activities), when the dock autohides, it leaves a black bar in its place which obscures any maximised apps. The only way i can get rid of this artefact is logging out and logging back in again. 

What're the fastest ways to get rid of this artefact when it occurs? Or better - prevent it from occurring.

tia, kb

---

### Post by Frogs Hair on 2011-09-05
I assumed you are using the Unity launcher , but if you are using another dock , please specify . I have not seen what describing , so information about your graphics card and driver could be useful.
```
lspci
```    

You could try the command below if the problem is icon settings related and you are using Unity .
```
unity --reset-icons
```

---

### Post by kbrand on 2011-09-06
Hey Frogs Hair, thanks a lot for your fast response.

Yes, i'm using Unity with a few adjustments made using the 'ccsm' package.

Q. Before i use it let me ask if 'unity --reset-icons' will reset the icons to the 'default' state (after installing 11.04), or the state they were in when i last logged in? The latter being the obvious preference, but i fear the former is the case when i read 'man unity'.

FWIW, i tired to reproduce the error now, but failed. On reflection, this behaviour appears after a period of 'normal' desktop use - switching btwn workspaces, making a tweak or two using ccsm, and other small things i would like to be clearer about. It occurs nearly on a daily basis. This may also reflect my constant fiddling with the fun new toy that unity is :)

Next time the problem occurs, i'll post a screen cap.

ttia, kb

Output from 'lspci':.

OptiPlex@OptiPlex-780:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
OptiPlex@OptiPlex-780:~$

---

### Post by kbrand on 2011-09-15
Attached is a screen cap showing the symptom. I guess it's only happening once every 1-2 weeks presently.

This time round, the preceding action was a perusal of the screen saver options under system settings. Although half a day of normal usage preceded this and could also have  precipitated the dreaded black artefact.

Further thoughts/suggestions appreciated, kb

EDIT:

And then the Unity dock dissappeared altogether - stubbornly remaining 'autohidden' - leaving the black artefact in its place. No amount <super> pressing or mouse pointing to the top left brought it back. Only logging in and out again.

---

### Post by aciel on 2011-09-15
I have this same problem on a new install of natty.

I saw something like it before when I was using docky, and had forgotten to turn compositing on. But in this case, compositing is definitely turned on.

---

