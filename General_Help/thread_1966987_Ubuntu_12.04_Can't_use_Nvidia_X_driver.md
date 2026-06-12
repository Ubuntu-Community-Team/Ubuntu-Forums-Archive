---
title: "Ubuntu 12.04 Can't use Nvidia X driver"
date: 2012-04-27
forum: General Help
---

### Post by alenn on 2012-04-27
Hi all, I just installed Ubuntu 12.04 and installed all nvidia drivers, but my drivers are not activated, when I open Nvidia settings manager I get the following message: 

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Can you help me with this

---

### Post by papibe on 2012-04-27
Hi alenn.

You seems to be very close.

First, backup your actual configuration file:
```
sudo cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.old
```
If that gives you an error saying that /etc/X11/xorg.conf does not exist. Just ignore it.

Then recreate your configuration so that it takes advantage of the the Nvidia driver:
```
sudo nvidia-xconfig
```
Then restart your machine.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by alenn on 2012-04-27
now I'm stuck with 640X480 resolution :S

---

### Post by papibe on 2012-04-27
Are there other resolutions available on 'Nvidia X Server Settings'?

If not, could you paste the content of this file:
```
/var/log/Xorg.0.log
```
here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link so we can take a look?

Regards.

---

### Post by alenn on 2012-04-27
[http://paste.ubuntu.com/950863/](http://paste.ubuntu.com/950863/)

no there is no other resolutions. How to get it back, previously I had 1024 X 968

---

### Post by papibe on 2012-04-27
Thanks.

```
[    28.490] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    28.490] (II) VESA(0): VESA VBE OEM Product: NV34 Board - p162-11n
```

I'm not sure if your card (or integrated graphics) are sopported by the proprietary Nvidia drivers.

Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display
```
Regards.

BTW, you may revert to the previous state by replacing you configuration file with the old one:
```
sudo cp -f  /etc/X11/xorg.conf.old  /etc/X11/xorg.conf
```
Then restart.
(Good thing we backup the file before, isn't it?)

---

### Post by alenn on 2012-04-27
I reverted to old resolution by doing this:

sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg xserver-xorg-video-all
sudo reboot

---

### Post by alenn on 2012-04-27
00:0e.0 VGA compatible controller [0300]: NVIDIA Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]




 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 65x/M650/740 PCI/AGP VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:d7800000-d781ffff ioport:d800(size=128)
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: NVIDIA Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: memory:d4000000-d4ffffff memory:e0000000-e7ffffff memory:dffe0000-dfffffff

---

### Post by papibe on 2012-04-27
> **alenn said:**
> NVIDIA Corporation NV34 [GeForce FX 5500
Your card is not supported by the 'nvidia-current' driver.

You would have to use an older version. One that its name stars with '173.14....'

Is that version offered on the application 'Additional Drivers'?

Regards.

---

### Post by alenn on 2012-04-27
> **papibe said:**
> Your card is not supported by the 'nvidia-current' driver.

You would have to use an older version. One that its name stars with '173.14....'

Is that version offered on the application 'Additional Drivers'?

Regards.

no, only the newest driver is offered, but in 11.10 with 173... driver, everything was fine. is there a way for reverting to older driver?

---

### Post by alenn on 2012-04-27
> **rockinfreeworld said:**
> Why don't you install the proprietary driver from the web site directly like in this guide:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

That worked for me.

already have that driver

---

### Post by papibe on 2012-04-27
> **rockinfreeworld said:**
> Why don't you install the proprietary driver from the web site directly...

I would let that option as a last case scenario.

Try this first:
```
sudo apt-get purge nvidia-current
sudo apt-get update
sudo apt-get install nvidia-173

sudo nvidia-xconfig
```
and then restart.

Regards.

---

### Post by alenn on 2012-04-27
> **papibe said:**
> I would let that option as a last case scenario.

Try this first:
```
sudo apt-get purge nvidia-current
sudo apt-get update
sudo apt-get install nvidia-173

sudo nvidia-xconfig
```
and then restart.

Regards.

 sudo apt-get install nvidia-173
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-173 : Depends: xorg-video-abi-10 but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by papibe on 2012-04-27
> **alenn said:**
> The following packages have unmet dependencies:
nvidia-173 : Depends: xorg-video-abi-10 but it is not installable
E: Unable to correct problems, you have held broken packages.

I'm afraid that's bad news. It looks like it hasn't been properly ported yet.

I would report the bug to launchpad.net, or ask about it at askubuntu.com

Regards.

---

### Post by alenn on 2012-04-28
I've searched askubuntu, and found this. Since I have no expirience with GRUB can you tell me if this is safe:

edit /etc/default/grub
find the option GRUB_CMDLINE_LINUX and add nopat, so for me this looked like

GRUB_CMDLINE_LINUX="nopat"

run sudo update-grub

---

### Post by Onesimus on 2012-04-28
> **alenn said:**
> I've searched askubuntu, and found this. Since I have no expirience with GRUB can you tell me if this is safe:

edit /etc/default/grub
find the option GRUB_CMDLINE_LINUX and add nopat, so for me this looked like

GRUB_CMDLINE_LINUX="nopat"

run sudo update-grub

Do you have a direct web link to where you found that on askubuntu ?

---

### Post by alenn on 2012-04-28
> **Onesimus said:**
> Do you have a direct web link to where you found that on askubuntu ?

[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal/37925#37925](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal/37925#37925)

---

### Post by alenn on 2012-04-28
> **alenn said:**
> I've searched askubuntu, and found this. Since I have no expirience with GRUB can you tell me if this is safe:

edit /etc/default/grub
find the option GRUB_CMDLINE_LINUX and add nopat, so for me this looked like

GRUB_CMDLINE_LINUX="nopat"

run sudo update-grub

tried this, but it's the same

---

### Post by alenn on 2012-04-28
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/990539](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/990539)

I made a bug report, anyone else with this problem should do the same so the developers will fix it more quickly

---

### Post by alenn on 2012-04-29
I have ATI Radeon graphic card (don't know which model). It have similar performance like mine Nvidia GeForce FX 5500. Do you think it would be the same problem with this card too?

---

### Post by alenn on 2012-06-19
hi all. I switched to 11.10 so I'm not on a track with this problem. Can anyone tell me is this fixed, can I safely switch to 12.04 ?

---

### Post by azmand01 on 2013-03-01
Not fixed yet.

Just upgraded and same issue happened. I have a Quadro 2000.

---

### Post by AdrianS1989 on 2013-04-01
Hi guys, I have installed yesterday Ubuntu 12.04 LTS, and it seemed that tha graphic card wasn't working right, so I came here and did all those sudo commands, now I'm stuck with a 640X480 resolution, and my touchpad doesn't work anymore.
BTW: I have GT520MX 1GB video card.
Can anyone help me in this matter? :D

---

### Post by Chrisfs on 2013-04-11
When you did "sudo nvidia-xconfig"  It should have backed up your old xorg.conf file to /etc/X11/xorg.conf.backup, , rename it back to xorg.conf (remembering to rename the current one to something else first, so you can bring it back if needed), and then reboot and see if that helps anything, 

> **AdrianS1989 said:**
> Hi guys, I have installed yesterday Ubuntu 12.04 LTS, and it seemed that tha graphic card wasn't working right, so I came here and did all those sudo commands, now I'm stuck with a 640X480 resolution, and my touchpad doesn't work anymore.
BTW: I have GT520MX 1GB video card.
Can anyone help me in this matter? :D

---

### Post by kondalex on 2013-04-12
I have the same story: driver activated but not currently in use.
ak@ak-srv:~$ lspci | grep NVIDIA
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520] (rev a1)
01:00.1 Audio device: NVIDIA Corporation HDMI Audio stub (rev a1)
Ubuntu 12.04 (precise)
kernel: 3.2.0-41-generic
xorg server: 1.11.3 (27 February 2013  02:07:42AM)

I can't do sudo nvidia-xconfig since there is no such command. I ran sudo nvidia-settings, but it says I have to run nvidia-xconfig... 

Could anyone help us?

I did installation from additional drivers (system settings) tab, from command line (sudo apt-get install nvidia-current) - nothing helps. :(

---

