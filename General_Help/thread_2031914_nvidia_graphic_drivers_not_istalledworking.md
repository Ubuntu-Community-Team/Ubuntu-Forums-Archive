---
title: "nvidia graphic drivers not istalled/working"
date: 2012-07-22
forum: General Help
---

### Post by cindy1990 on 2012-07-22
i installed ubuntu 12.04 yesterday on my laptop (dell inspiron 1545) when i try to use the nvidia setting it says 

   "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

how do i do that?

also "additional drivers" never showed my graphics driver. only did my wireless card driver.

---

### Post by robtygart on 2012-07-22
Open Terminal or press ctrl+T

run this command.

```
sudo nvidia-xconfig
```

Let me know how it works. :D

---

### Post by cindy1990 on 2012-07-22
> **robtygart said:**
> Open Terminal or press ctrl+T

run this command.

```
sudo nvidia-xconfig
```Let me know how it works. :D


i got.

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


i also forgot to mention myunity was working and now it wont. says im running in 2d mode.

---

### Post by cindy1990 on 2012-07-22
> **robtygart said:**
> Open Terminal or press ctrl+T

run this command.

```
sudo nvidia-xconfig
```Let me know how it works. :D

i got.

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


i also forgot to mention myunity was working and now it wont. says im running in 2d mode.

---

### Post by robtygart on 2012-07-22
> **cindy1990 said:**
> i got.

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


i also forgot to mention myunity was working and now it wont. says im running in 2d mode.

Go to System settings> Additional Drivers, check to see if your driver shows up there and is on.

---

### Post by cindy1990 on 2012-07-22
> **robtygart said:**
> Go to System settings> Additional Drivers, check to see if your driver shows up there and is on.

nope not there...im goin to re istall and go from there

---

### Post by robtygart on 2012-07-22
> **cindy1990 said:**
> nope not there...im goin to re istall and go from there

This will install open source nvidia driver
```
sudo apt-get install nouveau-firmware
```

or
This will install current invidia drivers ( I and others have been having some trouble with this one. Don't know why! 

```
sudo apt-get install nvidia-current
```

---

### Post by cindy1990 on 2012-07-23
> **robtygart said:**
> This will install open source nvidia driver
```
sudo apt-get install nouveau-firmware
```or
This will install current invidia drivers ( I and others have been having some trouble with this one. Don't know why! 

```
sudo apt-get install nvidia-current
```

"facepalm" silly me just relized my computer has intel not  nivdia...thankfully i relized that b4 i typed it the above. im so use to  working with computers that has nividia. ( this laptop was just given  to me).......though under system-details. it says graphic  unknown.......anyway to tell what my graphic is?

---

### Post by cindy1990 on 2012-07-23
> **robtygart said:**
> This will install open source nvidia driver
```
sudo apt-get install nouveau-firmware
```or
This will install current invidia drivers ( I and others have been having some trouble with this one. Don't know why! 

```
sudo apt-get install nvidia-current
```


"facepalm" silly me just relized my computer has intel not nivdia...thankfully i relized that b4 i typed it the above. im so use to working with computers that has nividia. ( this laptop was just given to me).......though under system-details. it says graphic unknown.......anyway to tell what my graphic is?

---

### Post by robtygart on 2012-07-23
Use this
```
lspci -nnk | grep -iA2 vga
```

Please post the results.

---

### Post by cindy1990 on 2012-07-23
> **robtygart said:**
> Use this
```
lspci -nnk | grep -iA2 vga
```Please post the results.

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: i915

---

### Post by NikTh on 2012-07-24
Hi , 
you must delete , remove nvidia graphics driver .. you have not nvidia graphics as you can see. 
You have intel graphics. 
Intel has not additional drivers for Ubuntu. Intel's driver is already installed and you use it (Kernel driver in use : i915) 

So please remove nvidia drivers..and xorg.conf file.. 
```
sudo apt-get purge nvidia-current nvidia-settings 
sudo rm /etc/X11/xorg.conf
```Reboot your pc , login to Ubuntu and open a terminal.. 
give this command and post the results back here.
```
/usr/lib/nux/unity_support_test -p
```

Thanks

---

### Post by cindy1990 on 2012-07-24
> **NikTh said:**
> Hi , 
you must delete , remove nvidia graphics driver .. you have not nvidia graphics as you can see. 
You have intel graphics. 
Intel has not additional drivers for Ubuntu. Intel's driver is already installed and you use it (Kernel driver in use : i915) 

So please remove nvidia drivers..and xorg.conf file.. 
```
sudo apt-get purge nvidia-current nvidia-settings 
sudo rm /etc/X11/xorg.conf
```Reboot your pc , login to Ubuntu and open a terminal.. 
give this command and post the results back here.
```
/usr/lib/nux/unity_support_test -p
```Thanks

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by NikTh on 2012-07-24
Hi , 

ok your card seems to support unity 3D . 

Is there an other problem ? 

If not you can mark this **thread as solved** , from **thread tools** .

Thanks

---

