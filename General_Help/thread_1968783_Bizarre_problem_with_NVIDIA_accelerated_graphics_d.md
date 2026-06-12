---
title: "Bizarre problem with NVIDIA accelerated graphics driver."
date: 2012-04-29
forum: General Help
---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2012-04-29
**Hi all,**

I have just successfully installed _Ubuntu 12.04_, with everything working great. 

Installing the *'NVIDIA accelerated graphics driver'* under Additional Drivers lead to a bizarre problem. After re-booting, the screen is flooded with too many tiny screens.

**Snapshot:**   [http://i.imgur.com/IsiYI.jpg](http://i.imgur.com/IsiYI.jpg)

Can someone please tell me what I need to do to overcome this problem? Uninstalling the driver is the only workaround for this problem?

Thanks!

---

### Post by SeijiSensei on 2012-04-29
1)  Which NVIDIA chipset is it?  People with adapters running 6xxx and older chips are reporting problems with the proprietary driver in 12.04.

2)  At boot, select the "recovery mode" kernel and choose "root shell" when given that option.  Run the command "nvidia xconfig" then reboot.  Does that help?

---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2012-04-29
> **SeijiSensei said:**
> 1)  Which NVIDIA chipset is it?  People with adapters running 6xxx and older chips are reporting problems with the proprietary driver in 12.04.

2)  At boot, select the "recovery mode" kernel and choose "root shell" when given that option.  Run the command "nvidia xconfig" then reboot.  Does that help?

First of all, Thanks for replying.

1) NVIDIA GeForce G 103M

2) No, It doesn't work. It shows "nvidia:command not found".

Please help me.
Thanks a lot in advance

---

### Post by pqwoerituytrueiwoq on 2012-04-29
he made a typo the command is "nvidia-xconfig"

---

### Post by SeijiSensei on 2012-04-29
Oops!  Sorry!

---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2012-04-30
> **pqwoerituytrueiwoq said:**
> he made a typo the command is "nvidia-xconfig"

Thanks for the reply.

Now, it shows:

```
root@Ubuntu-OS:~#nvidia-xconfig

Using X Configuration file:"/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf . Device section "Default Device" must have a driver line.

ERROR: Unable to write to directory "/etc/X11".
root@Ubuntu-OS:~#

```Thanks in advance
Take Care

---

### Post by effenberg0x0 on 2012-04-30
> **&#3670 said:**
> Thanks for the reply.

Now, it shows:

```
root@Ubuntu-OS:~#nvidia-xconfig

Using X Configuration file:"/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf . Device section "Default Device" must have a driver line.

ERROR: Unable to write to directory "/etc/X11".
root@Ubuntu-OS:~#

```Thanks in advance
Take Care


You could try:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig

```And reboot the PC (save your work first)
```
sudo reboot now
```
Back to the desktop, adjust other settings using nvidia-settings
If you need to revert, just run:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
And reboot the PC (save your work first)
```
sudo reboot now
```

Considering all the problems with the latest NVidia driver (295.40), you could also try Nvidia 295.20 (which is working and stable). If you look at the bug report ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)) you'll find some instructions on how to install a previous version of NVidia drivers.

Regards,
Effenberg

---

### Post by &#3670;&#1763;&#1756;Storm &#3670;&#1763;&#1756;Shadow on 2012-04-30
> **effenberg0x0 said:**
> You could try:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nvidia-xconfig

```And reboot the PC (save your work first)
```
sudo reboot now
```Back to the desktop, adjust other settings using nvidia-settings
If you need to revert, just run:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```And reboot the PC (save your work first)
```
sudo reboot now
```Considering all the problems with the latest NVidia driver (295.40), you could also try Nvidia 295.20 (which is working and stable). If you look at the bug report ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)) you'll find some instructions on how to install a previous version of NVidia drivers.

Regards,
Effenberg

Thanks for your reply.
The problem still remain without any change. After going through the X Server Configuration Window, I tried to change the resolution and the configuration of the screen. But, I can't as the other options are greyed out. The resolution field gives much smaller resolutions like 680x180 etc. The Option "Disable" is greyed out in the Configuration field which gives "Separate X Screen" as the only option available to select.

Is there any other ways?

---

