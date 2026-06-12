---
title: "My unity doesn't looks like your unity. :)"
date: 2011-10-03
forum: General Help
---

### Post by adeee on 2011-10-03
I just upgrade ubuntu from 10.10 to 11.04 and after the completion of up-gradation and installation procedure. its same as it before in 10.10 see 

[ATTACH]203490[/ATTACH]

Well here is something you might notice that during installation of packages 1n 89 % completion the mysql stops the process. and i hard reboot the computer.

i mean something like this massage appear in terminal.

installing mysql-server version name

and stop working. looks like it held the procedure of installing. not the computer. :P

and after reboot i start again updating. and its complete. but its not looks like the unity show in the ubuntu.com website screanshots.
whats wrong here?:popcorn:

---

### Post by [S|G] on 2011-10-03
> **adeee said:**
> 
and after reboot i start again updating. and its complete. but its not looks like the unity show in the ubuntu.com website screanshots.
whats wrong here?:popcorn:

Unity requires that your computer meet certain video card requirements in order to run. Could you please post your hardware configuration? 

Furthermore even if you have a good video card (such as an NVidia or an ATI card) you might still need to install the correct video drivers before using Unity.

---

### Post by adeee on 2011-10-04
> **'[S|G] said:**
> Unity requires that your computer meet certain video card requirements in order to run. Could you please post your hardware configuration? 

Furthermore even if you have a good video card (such as an NVidia or an ATI card) you might still need to install the correct video drivers before using Unity.
here it is.

```

adeee@adeee:~$ [COLOR="red"]lspci[/COLOR]
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
adeee@adeee:~$ lspci | grep vga
adeee@adeee:~$[COLOR="red"] lspci | grep VGA[/COLOR]
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
adeee@adeee:~$  [COLOR="Red"]/usr/lib/nux/unity_support_test -p[/COLOR]
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
adeee@adeee:~$ 

```

What you say now.

---

### Post by [S|G] on 2011-10-04
I think Unity doesn't support your graphics card since it requires OpenGL 1.4 and your card only does 1.3. Take a look at this bug: [https://bugs.launchpad.net/unity/+bug/696999](https://bugs.launchpad.net/unity/+bug/696999). Also take a look here: [https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

