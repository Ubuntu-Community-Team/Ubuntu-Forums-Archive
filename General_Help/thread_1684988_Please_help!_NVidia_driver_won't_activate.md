---
title: "Please help! NVidia driver won't activate"
date: 2011-02-10
forum: General Help
---

### Post by scottyja on 2011-02-10
I could really use some help... this is very frustrating. My son's 10.04 setup uses NVidia's ION graphics. He was having trouble, so I tried reinstalling the drivers, but can not get them back at all. I don't know where I went wrong. I was using the following [guide]("http://trycatch.iblogger.org/tips-n-tricks/how-to-install-nvidia-drivers-in-ubuntu-10-04-lucid-lynx").

Unfortunately, whenever I try load the module nvidia, I get the following:

[I]$ sudo modprobe nvidia
FATAL: Module nvidia not found.[/I]

If I go into Jockey, I see the driver I installed 'nvidia_173', but a message at the bottom stating "This driver is activated but not currently in use."

If I try running nvidia-settings, I get the following:
[I]
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/I]

Trying to run nvidia-xconfig:

[I]$ nvidia-xconfig
nvidia-xconfig: command not found[/I]

Trying to install nvidia-xconfig:

[I]$ sudo apt-get install nvidia-xconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-xconfig[/I]

I don't know what else to try! I also don't have xorg.conf file:

[I]$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory[/I]

Can anyone please help?! Right now I do have graphics, but they are blurry and the resolution is off. I really, really don't want to reinstall.

---

### Post by scottyja on 2011-02-10
I found the following file in /etc/X11:

[I]:/etc/X11$ cat xorg.conf.dist-upgrade-201007272102 

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection[/I]

I still don't have an ability to run nvidia-xconfig though. Any thoughts?

---

### Post by papibe on 2011-02-10
What's the output of this:
```
$ dpkg -l | grep -i nvidia
```
Regards.

---

### Post by scottyja on 2011-02-10
I made some progress, but still unsure what's wrong.  I did the following command:

sudo update-alternatives --config gl_conf

 Selection    Path                                Priority   Status
------------------------------------------------------------
* 0            /usr/lib/nvidia-current/ld.so.conf   9700      auto mode
  1            /usr/lib/mesa/ld.so.conf             500       manual mode
  2            /usr/lib/nvidia-current/ld.so.conf   9700      manual mode

And changed from mesa/ld.so.conf to nvidia. I was then able to run nvidia-settings and nvidia-xconfig.

However, when trying to run 'sudo modprobe nvidia' I still get 'Module nvidia not found'. Additionally, Jockey still reports the nvidia driver as not being used.

---

### Post by scottyja on 2011-02-10
> **papibe said:**
> What's the output of this:
```
$ dpkg -l | grep -i nvidia
```Regards.

Here you go:

$ dpkg -l | grep -i nvidia
rc  nvidia-173                            173.14.22-0ubuntu11                             NVIDIA binary Xorg driver, kernel module and
ii  nvidia-current                        195.36.24-0ubuntu1~10.04                        NVIDIA binary Xorg driver, kernel module and
rc  nvidia-kernel-common                  20080825+1ubuntu2                               NVIDIA binary kernel module common files
ii  nvidia-settings                       195.36.08-0ubuntu2                              Tool of configuring the NVIDIA graphics driv

---

### Post by lidex on 2011-02-10
What happens when you run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```
and then go into 'hardware drivers'(jockey) and select nvidia-current and reboot?
Next post this info:
```
cat /var/log/Xorg.0.log | grep -i "EE"
```

---

### Post by scottyja on 2011-02-10
> **lidex said:**
> What happens when you run these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```and then go into 'hardware drivers'(jockey) and select nvidia-current and reboot?
Next post this info:
```
cat /var/log/Xorg.0.log | grep -i "EE"
```

I was able to get the upgrade/install/nvidia-xconfig to work now. Thank you. When going into jockey, I still see it saying it's activated but not used, which doesn't seem correct:

[I]$ sudo jockey-text -l
kmod:nvidia_current - nvidia_current (Proprietary, Enabled, Not in use)[/I]

It used to say something to about recommended version, enabled and in-use. 

As for the other output:

[I]$ cat /var/log/Xorg.0.log | grep -i "EE"
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(**) |-->Screen "Screen0" (0)
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension XFree86-DRI
(II) Feb 09 23:45:33 NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) Feb 09 23:45:33 NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

[/I]I've also uninstalled and reinstalled jockey, but that didn't seem to do any good.

---

### Post by scottyja on 2011-02-10
If it helps, I've attached a screen shot of exactly what I'm seeing in jockey.

[IMG]http://i55.tinypic.com/2it6lpk.png[/IMG]

---

### Post by scottyja on 2011-02-10
OK, thank you all for the help, I think I have it solved, and was entirely too simple.

What I ran:

```
sudo apt-get purge nvidia*
``````
sudo apt-get purge jokey*
```<reboot> 

```
sudo apt-get install jockey-gtk
```

I'm not sure if the reboot was necessary after uninstalling. However, after doing this, jockey downloaded the necessary nvidia drivers. I think what I had done manually was interfering. I was then able to view the latest/recommended driver and install through jockey. After a reboot, everything looks good:
[I]
$ sudo jockey-text -l
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Enabled, In use)[/I]

---

