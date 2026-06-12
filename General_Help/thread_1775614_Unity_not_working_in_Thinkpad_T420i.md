---
title: "Unity not working in Thinkpad T420i"
date: 2011-06-05
forum: General Help
---

### Post by donniezazen on 2011-06-05
Hi,

I got a new Thinkpad T420i with i7 Intel processor with Nvidia NVS 4200 graphic card. I installed Natty amd64 (i guess only available 64 bit Ubuntu version). It does not load Unity interface but default gnome. On my old computer i skipped Unity check by appending UNITY_FORCE_START=1 to /etc/environment. I do not want to use dirty hack and would rather file bug if required. I have Nvidia accelerated graphic driver installed but don't think it is using Nvidia graphic card. It is using inbuilt Intel graphic card as nvidia-setting give me an error to run nvidia-xconfig. When i ran nvidia xconfig it gave me following error.

> VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Thanks for your help.

---

### Post by wildmanne39 on 2011-06-05
> **soham_1207 said:**
> Hi,

I got a new Thinkpad T420i with i7 Intel processor with Nvidia NVS 4200 graphic card. I installed Natty amd64 (i guess only available 64 bit Ubuntu version). It does not load Unity interface but default gnome. On my old computer i skipped Unity check by appending UNITY_FORCE_START=1 to /etc/environment. I do not want to use dirty hack and would rather file bug if required. I have Nvidia accelerated graphic driver installed but don't think it is using Nvidia graphic card. It is using inbuilt Intel graphic card as nvidia-setting give me an error to run nvidia-xconfig. When i ran nvidia xconfig it gave me following error.



Thanks for your help.Hi, if you disable your intel graphics card you should be able to get the nividia card to work with the driver in additional drivers, also the latest driver is buggy with natty, you should use the older one and it will say that it is not in use after it is activated but that is just a bug it really is in use if you can get the unity desktop that is proof.

---

### Post by donniezazen on 2011-06-05
> **wildmanne39 said:**
> Hi, if you disable your intel graphics card you should be able to get the nividia card to work with the driver in additional drivers, also the latest driver is buggy with natty, you should use the older one and it will say that it is not in use after it is activated but that is just a bug it really is in use if you can get the unity desktop that is proof.


I don't know how to disable a driver in Ubuntu, I just disabled it from bios. I have lost ability to change brightness. It worked out of box using the latest drivers. Is brightness a bug in latest driver?

---

### Post by wildmanne39 on 2011-06-05
> **soham_1207 said:**
> I don't know how to disable a driver in Ubuntu, I just disabled it from bios. I have lost ability to change brightness. It worked out of box using the latest drivers. Is brightness a bug in latest driver?
Hi, it creates a white window sometimes, did you try the latest driver?

---

### Post by donniezazen on 2011-06-05
> **wildmanne39 said:**
> Hi, it creates a white window sometimes, did you try the latest driver?

No, i didn't see any white window. I used nvidia-current in additional drivers. I was obviously using nvidia drivers but showed as not running. Brightness is not working and i messed up with nvidia-settings and couldn't restore defaults.

Another major problem is i can't boot Ubuntu. It stops at **Checking Battery state**. I am reading about it as of now and it seems like a bug in amd64 architecture.

Update 1:-I manually downloaded 270.42.19 drivers from nvidia website which seem to have solved checking battery state problem but i still can't control brightness and text is blurry.

Update 2:-Why isn't integrated Intel graphic card not supported by Unity? This is pretty high end latest laptop.

---

### Post by wildmanne39 on 2011-06-05
> **soham_1207 said:**
> No, i didn't see any white window. I used nvidia-current in additional drivers. I was obviously using nvidia drivers but showed as not running. Brightness is not working and i messed up with nvidia-settings and couldn't restore defaults.

Another major problem is i can't boot Ubuntu. It stops at **Checking Battery state**. I am reading about it as of now and it seems like a bug in amd64 architecture.

Update 1:-I manually downloaded 270.42.19 drivers from nvidia website which seem to have solved checking battery state problem but i still can't control brightness and text is blurry.

Update 2:-Why isn't integrated Intel graphic card not supported by Unity? This is pretty high end latest laptop.
Hi, the 270 driver is buggy, that iis why I told you in my previous post not to install the latest and to use the additional drivers to install from. When new tech comes out like your intell graphic card the vendor does not supply a linux deriver for it so the developers of ubuntu and other linux distro's have to backward engineer drivers for each new piece of hardware and that takes a very long time.

---

### Post by donniezazen on 2011-06-05
> **wildmanne39 said:**
> Hi, the 270 driver is buggy, that iis why I told you in my previous post not to install the latest and to use the additional drivers to install from. When new tech comes out like your intell graphic card the vendor does not supply a linux deriver for it so the developers of ubuntu and other linux distro's have to backward engineer drivers for each new piece of hardware and that takes a very long time.

Only latest Nvidia Drivers were available in Additional Drivers. I tried nvidia-173 from synapatic but it gave me "Checking Battery State" bug. I have just re-installed whole system and text is no longer blurry. The only problem i have right now is that i can't change brightness using hotkeys or power management, i have to use nvidia settings which is not handy.

---

### Post by donniezazen on 2011-06-06
[http://www.andresclari.com/blog/enable-nvidia-brightness-control-in-ubuntu-10-04/](http://www.andresclari.com/blog/enable-nvidia-brightness-control-in-ubuntu-10-04/)

This blog has correct method of solving brightness problem. Thanks for your help.

> Make sure you have a saved copy of xorg.conf (the default configuration is without configuration file):
The easy way to save a xorg.conf file is System->Administration->Nvidia X Server Settings there go to “X Server Display Configuration” and choose “Save to X Configuration File” and accept the default location.

The actual fix:

Open a terminal window and type:


sudo gedit /etc/X11/xorg.conf

On the “DEVICE” section append the following line:


Option "RegistryDwords" "EnableBrightnessControl=1"

Log back in and your done.

---

### Post by donniezazen on 2011-06-08
Any experience how battery life would be if i completely go discrete graphic card. And will XP in virtualbox run games smoothly as dedicated XP/win7 platform would.

---

