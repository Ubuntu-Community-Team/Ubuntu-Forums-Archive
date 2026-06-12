---
title: "Ubuntu 12.04 Windows Snap Feature"
date: 2012-10-13
forum: General Help
---

### Post by Vesnog on 2012-10-13
Greetings,

When I first installed Ubuntu 12.04 LTS 32.bit from a Live-CD without internet connection and any updates the snapping feature worked fine for windows of all applications. However, after some updates and installations it stopped working. I can no longer drag a window to the edge of the screen and have it resized. Thinking the problem is from my lack of experience I did a clean install of Ubuntu 12.04 again with internet connection; however, the problem still persists and I am fed up with this. Do you have any suggestions for remedy? Thanks in advance.

P.S: The feature when working properly was just like that in Windows 7. I am a new user BTW so I might be skipping some important details, and I would be glad if you can remind me of them. In addition to that when I drag a tab in Google Chrome it just opens it in a new window instead of replacing it. How can I change this situation? I also tried installing Nvidia Bumbleebee before these problems occurred, yet I have formatted since then.

---

### Post by rhlegion on 2012-10-13
When you log in did you use the ubuntu 2D or 3D desktop? because if i remember right the 2D desktop doesn't have the snap feature

---

### Post by Vesnog on 2012-10-13
Since I am a complete beginner I don't know if it is possible to select 2D or 3D desktop, since I am not asked at startup. Can you please explain the 2D and 3D desktops?

---

### Post by stinkeye on 2012-10-13
What is your output of the terminal command...
```
echo $DESKTOP_SESSION
```
eg my output...
```
[COLOR="DarkGreen"]glen@Quantal:~$[/COLOR] **echo $DESKTOP_SESSION**
ubuntu
```

---

### Post by Vesnog on 2012-10-14
Thanks for the command the output is as follows:

vesnog@Vesnog:~$ echo $DESKTOP_SESSION
ubuntu-2d

I think this is the reason why Chrome fails when I try to change the position of a tab and the Window Snap feature does not work. Am I correct?

Note: I am running a Dell Laptop with model number XPS L502X which has a Nvidia GT540M video card with Optimus enabled. By the way I downloaded drivers supporting this video card from the website of Nvidia, but they have the extension ".run" which I am unfamiliar with. How can I install these drivers?

---

### Post by Vesnog on 2012-10-14
[SIZE=3]I am posting some information which might b[SIZE=3]e related with[/SIZE] the problem:[/SIZE]

@Vesnog:~$ dpkg-query -l nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  nvidia-180-mod <none>         (no description available)
un  nvidia-185-mod <none>         (no description available)
ii  nvidia-common  1:0.2.44.2     Find obsolete NVIDIA drivers
ii  nvidia-current 304.51-0ubuntu NVIDIA binary Xorg driver, kernel module and
un  nvidia-current <none>         (no description available)
ii  nvidia-current 295.49-0ubuntu NVIDIA binary Xorg driver, kernel module and
ii  nvidia-setting 304.51-0ubuntu Tool of configuring the NVIDIA graphics driv
ii  nvidia-setting 295.33-0ubuntu Tool of configuring the NVIDIA graphics driv

[SIZE=3]The part of the output of the command "sudo lspci -v" is as follows:[/SIZE]

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 050e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 3000 [size=128]
    Expansion ROM at f1000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [b4] Vendor Specific Information: Len=14 <?>
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nvidia, nouveau, nvidiafb

---

### Post by stinkeye on 2012-10-14
Your problem seems to be nvidia optimus.
Your being dropped back to the 2d session which doesn't run compiz and doesn't need the 3d drivers.
Can you turn optimus off in the BIOS?
If not there is a solution called bumblebee.
I don't have sufficient knowledge about this to give you answers.
Hopefully someone who does, will come along, or do some searches for
your card(GeForce GT 540M) and optimus, bumblebee.

Ps. Just to  check, try logging out, then at the greeter click on the cog wheel and choose **ubuntu** as the session.
Log in and run...
```
echo $DESKTOP_SESSION
```
Is it still telling you **Ubuntu-2d**?

---

### Post by ranger1021994 on 2012-10-14
Did you update nvidia drivers in recent ??

---

### Post by Vesnog on 2012-10-14
Thanks for the answer, and the command you mentioned returns Ubuntu 2-D. Thinking it is safer than messing up with BIOS, I have tried installing Bumblebee up to no avail. I failed to understand why the attempt was unsuccessful. I would be glad if someone could provide an explanation.

user@Vesnog:~$ echo $DESKTOP_SESSION
ubuntu-2d

P.S: Let me now if further information is needed.

Thanks

---

### Post by stinkeye on 2012-10-14
I can't help much more except you could try installing the latest drivers from the x-swat/x-updates ppa.
[**_[COLOR="DarkRed"]Install Latest Nvidia Drivers in Ubuntu 12.10/12.04/11.10/Linux Mint 13/12[/COLOR]_**]("http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html")

---

### Post by Vesnog on 2012-10-14
I managed to get Bumbleebee installed and my PCI graphics card work by first installing Ironhide than installing Bumblebee with the following command:

sudo apt-get install bumblebee

Excluding writing Nvidia-bumblebee sort of thing seem to have resolved the situation.

---

