---
title: "Force Add 1440x900 Resolution to NVidia Driver"
date: 2010-06-30
forum: General Help
---

### Post by divyanshu on 2010-06-30
i'll begin by saying am completely utterly new to Linux. Always loved the idea of it but was apprehensive forever.

and then there were some exotic problems.

my monitor's dvi jack is damaged so my nvidia geforce 210 does not recognise the supported resolutions correctly.

result: while it actually can support upto 1440x900, the highest available resolution is 1360x768.

while on windows, i used the nvidia utility to add the custom resolution and everything was nice.

on ubuntu 10.04, i haven't found a way to do that yet. yes, i searched forums, tried a couple of things with the xorg.conf file and lxrandr, etc. but to no avail.

i did manage to get the resolution listed in ubuntu's own display manager, and it shows 1440x900, but it doesn't apply when i hit 'apply'. 

the nvidia settings manager does not show the resolution.

so. what do i do? need help!

---

### Post by cariboo on 2010-06-30
Try creating a new /etc/X11/xorg.conf file by running:

```
sudo nvidia-xconfig
```

in a terminal, reboot, and check nvidia-settings to see if the resolution you want shows up, if it does, run nvidia-settings as root, to save the settings:

```
sudo nvidia-settings
```

---

### Post by divyanshu on 2010-07-01
> **cariboo907 said:**
> if the resolution you want shows up

it doesn't :(

---

