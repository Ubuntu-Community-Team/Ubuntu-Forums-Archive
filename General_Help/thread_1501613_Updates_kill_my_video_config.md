---
title: "Updates kill my video config"
date: 2010-06-04
forum: General Help
---

### Post by Calaway21 on 2010-06-04
Hello Fellow Ubuntu Users,

I develop Websites on my Ubuntu workstation running 10.04 Lucid. I have dual 20" widescreen monitors running with the extended desktop. My video card is a Nvidia Geforce 9300 and I use Nvidia X Server driver. 

The problem I am having is that whenever I update my OS through Update manager I get a message on startup saying that my computer is running in low-graphics mode and I have a few options to fix it. When I finally get login my dual monitor configuration is all messed up and the nvidia config panel says that I am no longer using the nvidia driver.

Is anyone else having this problem? It doesn't help that I've updated my os yesterday and today and I have had to reconfigure my graphics driver settings both yesterday and today. How can I fix this? 

Thank you in advance for your replies, they do not go unappreciated.

Calaway21

---

### Post by Woody1987 on 2010-06-04
sounds as though dkms may not be rebuilding the driver for kernel updates. Try installing it. Also make sure that the nvidia driver is set in xorg.conf by running sudo nvidia-xconfig

---

### Post by 3rdalbum on 2010-06-04
> **Woody1987 said:**
> sounds as though dkms may not be rebuilding the driver for kernel updates. Try installing it. Also make sure that the nvidia driver is set in xorg.conf by running sudo nvidia-xconfig

This   happens   when   you   install   the   Nvidia   driver   manually.   In   future   you   should   either   use   an   Nvidia   driver   PPA   that  will  keep  the   driver   in   sync   with  the  kernel,   or   use   the  reccommended   version   in  the  Hardware   Drivers   program.

---

### Post by Calaway21 on 2010-06-07
I didn't install the nvidia drivers manually. I installed them by going to System -> Administration -> Hardware Drivers and then selected the recommended one. The drivers downloaded and then installed. I then used the nvidia-settings panel to configure twinview.

As it turns out however, whenever I restart my machine now it gives me the message stating that my machine is running in low-graphics mode. To fix this I have to delete the xorg.conf file and replace it with my backup. Then it will start up just fine most of the time. Sometimes she gets a little moody with me I have to just start over from the beginning and totally reconfigure twinview. 

Does anybody know what causes this?

Calaway21

---

### Post by dino99 on 2010-06-07
remove your xorg.conf:

sudo rm -f /etc/X11/xorg.conf

open synaptic and add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade

you need to have nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings  installed

reboot and check that nvidia-current is activated, then run nvidia-settings

---

### Post by Calaway21 on 2010-06-07
[SIZE=5]**Success!!!**[/SIZE]

Thank you dino99 for your help. I have rebooted my machine three times now and have not received the low-graphics message even once. I really appreciate your help.

Calaway21

---

### Post by Calaway21 on 2010-06-11
The successful configuration was short lived. I now get the following message whenever I shutdown and then start my computer versus just a reboot:

"Failed to initialized the Nvidia kernel module. Please see the system's kernel log for additional error messages and consult the Nvidia readme for details."

Everything that I can find about nvidia in the system log for the last time I shut down my machine is here:

...
Jun 11 10:17:15 LucidTwo kernel: [    6.306732] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
Jun 11 10:17:15 LucidTwo kernel: [    6.306964] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:08/LNXVIDEO:00/input/input3
Jun 11 10:17:15 LucidTwo kernel: [    6.307017] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
Jun 11 10:17:15 LucidTwo kernel: [    6.350074] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
...
Jun 11 10:17:15 LucidTwo kernel: [    6.350081] nForce2_smbus 0000:00:03.2: Error probing SMB2.
...
Jun 11 10:17:15 LucidTwo kernel: [    7.672303] nvidia: module license 'NVIDIA' taints kernel.
...
Jun 11 10:17:15 LucidTwo kernel: [    8.229893] nvidia 0000:00:03.5: PCI INT B -> Link[APMU] -> GSI 21 (level, low) -> IRQ 21
...
Jun 11 10:17:15 LucidTwo kernel: [    8.230180] nvidia 0000:03:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
Jun 11 10:17:15 LucidTwo kernel: [    8.230184] nvidia 0000:03:00.0: setting latency timer to 64
...

I recognize a few key words in there but, mostly I can't make heads or tails of the kernel log. Is there a more human-readable file that I can look at.

I also tried uninstalling the nvidia drivers so that I could reinstall them. However, when I run

```
sudo apt-get remove nvidia-*
```

It tells me that the package is not found even though Settings -> Administration -> Hardware Drivers shows two different drivers available; version 173 and version current. I have tried both and received the same results both times.

When I start my computer I have to select "reset video settings to default configuration" and then restart X. I then start up a terminal and run 

```
sudo nvidia-xconfig
```

to which my machine replies that there is no xconfig file found and that it will create a new one at /etc/X11/xorg.conf. I then run 

```
sudo service gdm restart
```

to restart the x server. Once I'm back to my desktop I open a terminal and run

```
sudo nvidia-settings
```

and receive the nvidia display settings as a response. I set up twinview and save to the xconfig file at /etc/X11/xorg.conf . Everything works smooth until I shutdown and boot my machine the next day.

Its a small sacrifice and inconvenience considering the time it takes for my win7 machine to start and become usable. This isn't enough of an inconvenience to make me switch back though I would like some help with it.

Thank you in advance for your responses,
Calaway21

---

