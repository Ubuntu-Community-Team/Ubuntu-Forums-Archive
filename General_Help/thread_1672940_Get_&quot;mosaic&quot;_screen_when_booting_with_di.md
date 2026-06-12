---
title: "Get &quot;mosaic&quot; screen when booting with disc"
date: 2011-01-21
forum: General Help
---

### Post by Nukam on 2011-01-21
I am currently running Win7 and want to dual boot  Ubuntu 10.10 on my computer I am currently running AMD Phenom II X4 940  Processor at 3.0 Ghz, 6gigs of ram, and have a Nvidia GT240.
 My issue is that when I boot from the disc I get up to the Ubuntu  loading screen and then it shows my background all scrambled and nothing  happens, I cant do anything, no windows pop up at all. Is this and  issue with my computer or with the disc, or maybe im missing something  necessary. Any help would be greatly appreciated, thank you.
 
Booting through the disc, which brings me here:
[http://i55.photobucket.com/albums/g139/Yoyomega/0114111510.jpg](http://i55.photobucket.com/albums/g139/Yoyomega/0114111510.jpg)
 After that screen:
[http://i55.photobucket.com/albums/g139/Yoyomega/0114111510a.jpg](http://i55.photobucket.com/albums/g139/Yoyomega/0114111510a.jpg)

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums :)

This is most likely a graphics issue.

Try booting the LiveCD with the nomodeset option.

After the first screen, choose language, try Ubuntu and then press F6 to show options.

Pick nomodeset and then Enter to boot.

---

### Post by Nukam on 2011-01-21
It worked, but after installing the nvidia drivers my reso will only go to 1024x768 even though my max screen reso should be 1440x900

---

### Post by Rubi1200 on 2011-01-21
Have a look if you can change the settings:

```
gksudo nvidia-settings
```

or 

```
sudo nvidia-xconfig
```

---

### Post by Nukam on 2011-01-21
The first command worked but my reso can only go to 1360x768 which should not be my max.

This is what I got after I input the second command

jonathan@jonathan-A780GM-A:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jonathan@jonathan-A780GM-A:~$

---

