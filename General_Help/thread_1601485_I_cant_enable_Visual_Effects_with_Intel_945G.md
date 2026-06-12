---
title: "I cant enable Visual Effects with Intel 945G"
date: 2010-10-20
forum: General Help
---

### Post by frosklo on 2010-10-20
[FONT=&quot]I was using a NVIDIA 7200GS on Ubuntu 10.04 (compiz+emerald+cairo) but it broken for over-temperature so I use my onboard graphpic intel 945G now.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I installed the intel drivers but couldn’t enable “Visual Effects”. So I decided install Ubuntu 10.10 after that everything was Ok. I could enable “Visual Effects” and use compiz+emerald.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I added app “x-updates” ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")) and I updated my ubuntu. The kernel was updated. After that when I  reboot ubuntu the visual effects was disable.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]**I can’t enable “Visual Effects” on Ubuntu 10.10 with my onboard graphic card intel 945G.**[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]When I try to enable, the ubuntu searches “video drivers” but It doesn't find anything. Don’t understand why it searches drivers.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]How can I do to solve my problem? Thanks[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]_Some information about my problem:_[/FONT]
  [FONT=&quot] [/FONT]
  ```
a@desktop:~$ glxinfo | grep "rendering"

direct rendering: Yes
```[FONT=&quot][/FONT]
  [FONT=&quot] [/FONT]
  **[FONT=&quot] [/FONT]**
```
a@desktop:~$ ./compiz-check
   
  Gathering information about your system...
   
   Distribution:          Ubuntu 10.10
   Desktop environment:   GNOME
   Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
   Driver in use:         intel
   Rendering method:      AIGLX
   
  Checking if it's possible to run Compiz on your system...
   
   Checking for texture_from_pixmap...               [ OK ]
   Checking for non power of two support...          [ OK ]
   Checking for composite extension...               [ OK ]
   Checking for FBConfig...                          [ OK ]
   Checking for hardware/setup problems...           [ OK ]

```[FONT=&quot]  
[/FONT]
  **[FONT=&quot] [/FONT]**
```
a@desktop:~$ DISPLAY=:0 glxinfo 
   
  name of display: :0.0
  display: :0  screen: 0
  direct rendering: Yes
  server glx vendor string: SGI
  server glx version string: 1.4
  client glx vendor string: Mesa Project and SGI
  client glx version string: 1.4
  OpenGL vendor string: Tungsten Graphics, Inc
  OpenGL renderer string: Mesa DRI Intel(R) 945G GEM 20100330 DEVELOPMENT 
  OpenGL version string: 1.4 Mesa 7.9-devel

```[FONT=&quot][/FONT]  [FONT=&quot] [/FONT]
[FONT=&quot]
[/FONT]
```
a@desktop:~$ sudo lshw -C display
   
    *-display
         description: VGA compatible controller
         product: 82945G/GZ Integrated Graphics Controller
         vendor: Intel Corporation
         physical id: 2
         bus info: pci@0000:00:02.0
         version: 02
         width: 32 bits
         clock: 33MHz
         capabilities: msi pm vga_controller bus_master cap_list rom
         configuration: driver=i915 latency=0
         resources: irq:16 memory:dfe00000-dfe7ffff ioport:8800(size=8) memory:e0000000-efffffff memory:dfe80000-dfebffff

```[FONT=&quot][/FONT]

---

### Post by ivarn on 2010-10-20
Have you added the gfx card to your x-server file yet?
sudo nvidia-xconfig
If yes, try:
*sudo nvidia*-glx-config *enable*

---

### Post by frosklo on 2010-10-20
> **ivarn said:**
> Have you added the gfx card to your x-server file yet?
sudo nvidia-xconfig
If yes, try:
*sudo nvidia*-glx-config *enable*

Thanks!

I don't understand why i must use "nvidia" drivers. My video card is a intel 945G (onboard)

---

### Post by ivarn on 2010-10-20
oh sorry, I thought u said u r using a nvidia 7200G.

---

### Post by matsuzine on 2010-10-20
I realize that this response is not very helpful, but I believe there have been some long-running issues with support for the 945G.  I never was able to use visual effects with mine, and the display was a little bit flaky for me.  You might try a search of these forums for threads with people having problems with the 945G.  

Sorry I don't have a fix for you!

--
actually, not just this chipset, but several intel chips seem flaky...

---

### Post by madmax1735 on 2010-10-20
i was able to enable transparency for windows by installing the latest intel graphics driver from launchpad and removing compiz completely from the system.

i now use metacity for composition as well as window management.

this doesnt give u all the features that are present in compiz but this is the only way i have been able to get a stable system with the intel graphics drivers.

---

### Post by TBABill on 2010-10-20
You may have luck in compiz by disabling "blur". I could not enable 3D effects in another distro and it was all because blur was enabled. By disabling it I got full functionality back. Worth trying...just untick one box and see if it works.
 
Edit: would obviously require reinstallation of compiz :)

---

### Post by frosklo on 2010-10-21
> **TBABill said:**
> You may have luck in compiz by disabling "blur". I could not enable 3D effects in another distro and it was all because blur was enabled. By disabling it I got full functionality back. Worth trying...just untick one box and see if it works.
 
Edit: would obviously require reinstallation of compiz :)

Thanks :D

I think you are right. I see about "blur" and intel driver and I found 
[http://ubuntuforums.org/showpost.php?p=4390181&postcount=8](http://ubuntuforums.org/showpost.php?p=4390181&postcount=8)
[http://ubuntuforums.org/showpost.php?p=3954694&postcount=5](http://ubuntuforums.org/showpost.php?p=3954694&postcount=5)

But i had another problem. When i tried to disable blur, the compiz was having all the options disabled. And when I uninstalled compiz, after that all the options in "visual effects" are disabled. I was very ungry.

I could solve this problem so I reinstall ubuntu again.

---

