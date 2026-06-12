---
title: "NVIDIA hardware driver (185) breaks X."
date: 2009-11-16
forum: General Help
---

### Post by Senesence on 2009-11-16
I'm using Karmic, and I tried using jockey to enable hardware acceleration, but after doing the mandatory restart, X fails to start.

Instead of gnome, I get dropped to a cli login prompt which just keeps flickering.

After being forced to unplug my machine (because the flickering login doesn't allow you to actually log in) I started recovery mode, and was able to reach a terminal that doesn't flicker, and that allows me to actually log in and type some commands.

I did "startx" and got back some god-awful error message about "Failing to load nvidia kernel module".

Then I did "sudo jockey-text -l" and noticed that the nvidia-185 driver is Enabled, but not in use. I have no idea why.

So, to reset things to a state in which they previously worked, I did "sudo jockey-text -d xorg:nvidia-185", and than after that X would start.

Anyone have any idea as to why this is happening?

---

### Post by Senesence on 2009-11-16
*bump

---

### Post by jcxaver on 2009-11-17
> **Senesence said:**
> *bump

I have the same problem with 173,185 versions, I tried EnvyNG for installation, but the problem persists..

---

### Post by jimbob on 2009-11-17
A lot of people are having this (or related) problems with certain hardware.  I don't know why yet but see my post here.

[http://ubuntuforums.org/showthread.php?t=1327447](http://ubuntuforums.org/showthread.php?t=1327447)

---

### Post by jcxaver on 2009-11-17
Hello, thank you very much for reply.
I have installed NVIDIA-Linix-x86-190.42-pkg1.run,

but the result is the same. Blinking black screen of death :o(.

Notice: with x server not running sudo modprobe nvidia
Error inserting nvidia (/lib/modules/2.6.31-14-generic/kernel/drivers/video.ko) Operation not permited

With xserver runing sudo modprobe nvidia
-no notice.

---

### Post by fluffman86 on 2009-11-17
go to the recovery mode, and do
sudo nvidia-xconfig && sudo apt-get install nvidia-settings

Reboot, and you should be able to get into a really crappy looking ubuntu gui.

press alt+f2, and type "gksu nvidia-settings" to configure your monitors.

---

### Post by jcxaver on 2009-11-17
> **fluffman86 said:**
> go to the recovery mode, and do
sudo nvidia-xconfig && sudo apt-get install nvidia-settings

Reboot, and you should be able to get into a really crappy looking ubuntu gui.

press alt+f2, and type "gksu nvidia-settings" to configure your monitors.


hello, thank you, after:

sudo nvidia-settings

I get: the control display is undefined, please run nvidia-settings --help

and thats all, still I have a black blinking screen.

---

### Post by realzippy on 2009-11-17
Edit:no sense after your edit:

---

### Post by jcxaver on 2009-11-17
> **fluffman86 said:**
> go to the recovery mode, and do
sudo nvidia-xconfig && sudo apt-get install nvidia-settings

Reboot, and you should be able to get into a really crappy looking ubuntu gui.

press alt+f2, and type "gksu nvidia-settings" to configure your monitors.


sorry, but the result is: **black blinking screen** :(

---

### Post by realzippy on 2009-11-17
@jcxaver

Did you install nvidia manually because of jockey backend crash while installing through
administration/restricted drivers tool?

---

### Post by jcxaver on 2009-11-17
> **realzippy said:**
> @jcxaver

Did you install nvidia manually because of jockey backend crash while installing through
administration/restricted drivers tool?

no, jockey crashes not, but the nvidia 173, 185 and now 190 drivers. 
I tried it because I cannot switch to hdmi port.

---

### Post by realzippy on 2009-11-17
was asking because of restricted drivers tool working on 2.6.31-15-generic
(nvidia 185 driver) ...

---

### Post by jimbob on 2009-11-17
What is jockey backend crash ??

---

### Post by realzippy on 2009-11-17
> **jimbob said:**
> What is jockey backend crash ??

E.G.

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/365912](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/365912)

happened to me when installing nvidia before updating kernel.

---

