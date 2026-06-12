---
title: "Cannot get past splash screen after battery died except in FailSafeX"
date: 2011-06-10
forum: General Help
---

### Post by sddhhanover on 2011-06-10
I installed Ubuntu on my Asus K72F laptop about a month ago, and it has worked seamlessly for me up until now:

I ran cat **/etc/issue** in terminal, here' the result:

```
Ubuntu 10.10 \n \l


```This started after my computer's battery died while it was running.

When  I try to boot, I get the splash screen, then the screen goes blank (as it should), but  the problem is, it stays blank rather than going to the login screen immediately as  it should. When I press and hold the power button to turn off the  computer, I see the splash screen briefly again before the computer  shuts down.

IMPORTANT: When I boot into recovery mode and choose  FailSafeX, the computer then goes to the screen where it says the  graphics card could not be detected properly, and gives me a list of  options, one of which is to run Ubuntu in low-graphics mode for one  session. I usually choose that and then I get the login windows as I  should, I login and everything is working perfectly except, of course,  the 3D graphics are gone (for example, CompizConfig is almost completely  unnoticeable when I use Ubuntu in this mode).

When I run **lspci** in terminal, this is one line of the result:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
```Judging  by the other forums I have searched, I may have been running an update  when my computer died, but I'm not sure. I have already tried dpkg from  the recovery mode multiple times to no avail.

---

### Post by pqwoerituytrueiwoq on 2011-06-10
you could probably just reinstall the "xserver-xorg-video-intel" in synaptic or
try this
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates  
sudo apt-get update
sudo apt-get upgrade
```
it should install a later version of the graphics driver
then it you want to revert back to the old driver you can use the ppa-purge package

---

### Post by linuxinstalledfromhdd on 2011-06-10
Why don't you go back into recovery mode and boot into failsafe graphics mode.. and completely uninstall your graphics driver in "Additional Drivers" and reboot your system? You can reinstall it again later on. :)

Don't forget to turn off your effects in Appearance...

---

### Post by sddhhanover on 2011-06-11
pqwoerituytrueiwoq:

It turns out that I currently need to update xserver-xorg-video-intel, but when I try to update it, I get that it needs the following dependency to proceed:

```
Depends: xorg-video-abi-7.0
```and I can't find it.

Is it still okay to remove xserver-xorg-video-intel?

I also tried the terminal commands, the last one gave me this:

```
The following packages have been kept back:
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following packages will be upgraded:
  fglrx-modaliases nvidia-current nvidia-current-modaliases nvidia-settings

```Not sure why they are kept back...

linuxinstalledfromhdd:

The intel driver is not in additional drivers, it is a package found in synaptic package manager. :)

---

### Post by pqwoerituytrueiwoq on 2011-06-12
xserver-xorg-video-intel i would think is very important to your intel graphics and since it is missing a dependency there is your issue are you sure 
googled "xorg-video-abi-7.0" and found:
[http://ubuntuforums.org/showthread.php?t=1571711](http://ubuntuforums.org/showthread.php?t=1571711) (not much use)
what happens if you try ```
sudo apt-get install xorg-video-abi-7.0
``` hopefully it will tell you it is part of such and such package
you can try forcing the held back stuff to install my laptop is doing that with the kernel will probably just backup a few files and copy my desktop's install to it

---

### Post by sddhhanover on 2011-06-15
I did apt-get install and here's the result (sudo password request omitted):

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-video-abi-7.0 is a virtual package provided by:
  xserver-xorg-core 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid [Not candidate version]

E: Package 'xorg-video-abi-7.0' has no installation candidate

```I'll have to do some research on this.

Good idea!

UPDATE: I have decided to do a full reinstall of my system. I now have ubuntu 11.04 and everything is working again!

---

