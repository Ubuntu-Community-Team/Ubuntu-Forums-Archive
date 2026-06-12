---
title: "Installing Nvidia driver 256.35"
date: 2010-07-17
forum: General Help
---

### Post by neoargon on 2010-07-17
I downloaded the proprietary Nvidia driver 256.35 from Nvidia website . When installing ,it shows some errors and don't install . It first shows that "the distribution provided install script failed. Continue anyway?  " . Then after trying to build kernel source, It shows that the building failed and that the installation failed . Please help

Before trying to install , I installed the needed packages by ```
sudo apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev 
```Then I entered into the console by hitting ctrl+alt+F1 . Then ran ```
sudo service kdm stop 
```Then ran the installer

Please help

---

### Post by neoargon on 2010-07-17
> **Jonson nike said:**
> Your new driver will write over an older version of a driver.  Sometimes  the update might be a partial tweak (such as a security upgrade) and  erasing the whole driver might cause problems.
Actually I uninstalled the old driver via "hardware drivers"(jockey-kde) . Iam using now the opensource nouveau driver .Do I need to uninstall nouveau driver? I don't know how

---

### Post by darco on 2010-07-17
I added the ppa and it handled everything for me....

[http://ubuntuforums.org/showpost.php?p=9417716&postcount=1306](http://ubuntuforums.org/showpost.php?p=9417716&postcount=1306)

---

### Post by stinkeye on 2010-07-17
I used this guide to intall the nvidia 256.35 drivers from a ppa.
[**_[COLOR="DarkRed"]How To Install nVidia 256.35 Display Drivers In Ubuntu (From A PPA Repository)[/COLOR]_**]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")

---

### Post by neoargon on 2010-07-17
Thanks ,but there is no way to install from the downloaded binary?

---

### Post by stinkeye on 2010-07-17
> **neoargon said:**
> Thanks ,but there is no way to install from the downloaded binary?
That's over my head.Why is it not possible to install this way?

---

### Post by Shazaam on 2010-07-17
I run Karmic (gnome) but this sloppy work-around may still apply-

Reboot, choose the "recovery mode" grub entry then choose to drop to a prompt. Stop the display manager. cd to the driver location and run the install script....
```
sudo sh NVIDIA-Linux-x86-256.35.run
```
It may complain about runlevels but I haven't had a problem continuing anyway. When done enter...
```
reboot
```

---

### Post by neoargon on 2010-07-17
> **Shazaam said:**
> I run Karmic (gnome) but this sloppy work-around may still apply-

Reboot, choose the "recovery mode" grub entry then choose to drop to a prompt. Stop the display manager. cd to the driver location and run the install script....
```
sudo sh NVIDIA-Linux-x86-256.35.run
```It may complain about runlevels but I haven't had a problem continuing anyway. When done enter...
```
reboot
```
 I too did that in karmic. The problem is is lucid. It was because of making the nouveau driver the default

---

### Post by freeman76 on 2010-07-18
Here you'll find out how to install latest drivers from nvidia:
[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by 3Miro on 2010-07-18
> **neoargon said:**
> I too did that in karmic. The problem is is lucid. It was because of making the nouveau driver the default

I have installed NVIDIA drivers from their web-page on older distros. You have to look for the specific error that you get. Otherwise everything that you are doing is correct, you are running into an issue somehow specific for your system/setup. What exactly is the error? 

On another note, have you edited /etc/X11/xorg.conf? I used to do that myself manually. Also, newer X-servers might actually be ignoring this file so something else might have to be edited.

---

### Post by thenellt on 2010-07-25
Hey, if you get it working I would love to know how. I've been trying for three days to get the 256.35 drivers working and I've had no luck with any of the many tutorials around this site. But from what I've heard, it's definitely because of the nouveau driver. For some people even blacklisting it doesn't seen to stop it from loading.

---

