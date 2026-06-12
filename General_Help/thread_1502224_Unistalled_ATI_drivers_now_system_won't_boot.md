---
title: "Unistalled ATI drivers now system won't boot"
date: 2010-06-05
forum: General Help
---

### Post by Jakiejake on 2010-06-05
Hi,
I uninstalled the proprietary ATI drivers today (or what ever they are called :P) because I was going to install the open source ones (to run a certain program) so I went to system -> preferences -> hardware drivers and hit remove
Then I rebooted and my monitor went to power saver
So I pulled out my Graphics card and put it back in
STILL Nothing
I get my POST screen, it's just when I boot the OS
I am running Ubuntu 10.04 Lucid Lynx 64 Bit
PLEASE HELP!!!
P.S. Going to bed now check for replies in the morning!

---

### Post by Jakiejake on 2010-06-05
Please help!!!

---

### Post by Jakiejake on 2010-06-05
Anyone
Please
I need to use my system

---

### Post by CarpKing on 2010-06-05
On Grub select "recovery mode."  This will book you into a text console.  

Potentially usefull commands (watch the caps!):

```
cat /var/log/Xorg.0.log | grep EE
```
Displays the lines of the xorg (display) log which contain "EE," indicating an error.  
Replace the "EE" with anything else to select for that instead; try "WW" for warnings and "fglrx"/"FGLRX" to see if it's still looking for the proprietary driver.  

```
cat /etc/X11/xorg.conf
```
Displays a config file for the display.  This may not exist.  

```
sudo apt-get install --reinstall xserver-xorg-video-ati
```
Reinstalls the open-source ATI drivers.  Installing the proprietary driver has sometimes overwritten some files used by the open-source ones, so if that is the case it helps to reinstall them.  

I hope something here works for you, or at least gives you more information to tell us.

---

### Post by Jakiejake on 2010-06-05
> **CarpKing said:**
> On Grub select "recovery mode."  This will book you into a text console.  

Potentially usefull commands (watch the caps!):

```
cat /var/log/Xorg.0.log | grep EE
```
Displays the lines of the xorg (display) log which contain "EE," indicating an error.  
Replace the "EE" with anything else to select for that instead; try "WW" for warnings and "fglrx"/"FGLRX" to see if it's still looking for the proprietary driver.  

```
cat /etc/X11/xorg.conf
```
Displays a config file for the display.  This may not exist.  

```
sudo apt-get install --reinstall xserver-xorg-video-ati
```
Reinstalls the open-source ATI drivers.  Installing the proprietary driver has sometimes overwritten some files used by the open-source ones, so if that is the case it helps to reinstall them.  

I hope something here works for you, or at least gives you more information to tell us.

I don't boot to GRUB
I have auto boot

---

### Post by Jakiejake on 2010-06-05
Anyway I fixed it
I just booted up with my VGA cable in as well
It works now

---

