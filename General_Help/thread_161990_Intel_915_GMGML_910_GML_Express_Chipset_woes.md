---
title: "Intel 915 GM/GML 910 GML Express Chipset woes"
date: 2006-04-18
forum: General Help
---

### Post by jimikimble on 2006-04-18
I've installed Breezy on my laptop (Gateway M325) and dual-boot.   When I boot in XP I have 1280 X 768 resolution and in Gnome I have 1024 X 768.   When I try and change the resolution using the GUI it doesn't give me any other options.  Also tried editing the X conf file.  (not sure of the name but it was suggested in another post). No joy.   Any help is appreciated.

---

### Post by Castar on 2006-04-18
[QUOTE=jimikimble]I've installed Breezy on my laptop (Gateway M325) and dual-boot.   When I boot in XP I have 1280 X 768 resolution and in Gnome I have 1024 X 768.   When I try and change the resolution using the GUI it doesn't give me any other options.  Also tried editing the X conf file.  (not sure of the name but it was suggested in another post). No joy.   Any help is appreciated.[/QUOTE]

I have the Dell Latitude X1. There is an issue with the driver in Linux. Install package 855resolution (or 915resolution) and write at the final line of /etc/init.d/bootmisc.sh

855resolution 3c 1280 768

and this should solve your problem as it did for me. I hope it works :)

---

### Post by krismatth3 on 2006-04-18
In Breezy you need to install "855resolution" (I think it's in universe?). In dapper it's called "915resolution." Once you've installed that, edit /etc/defaults/855resolution (or /etc/defaults/915resolution) and fill out the info. Here's mine:
```

#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE
#
MODE=5c
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=768
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

Just seet "XRESO" and "YRESO" to what you want. "5c" should be ok for "MODE." Then, reboot. (Or do this from a command line: "sudo /etc/init.d/855resolution start && sudo /etc/init.d/gdm restart").

---

### Post by krismatth3 on 2006-04-18
Oh, I have the Gateway MX3560 - very similar to your laptop. On mine I had to disable the "External Amp" switch in the mixer settings to get sound. How about you? Once you get up and running, maybe you could add your laptop to [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsGateway?highlight=%28laptop%29](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsGateway?highlight=%28laptop%29) :)

---

### Post by jimikimble on 2006-04-18
Sweet.  That worked.  Now I have more real estate.  
> Oh, I have the Gateway MX3560 - very similar to your laptop. On mine I had to disable the "External Amp" switch in the mixer settings to get sound. How about you? Once you get up and running, maybe you could add your laptop to [https://wiki.ubuntu.com/HardwareSupp...%2](https://wiki.ubuntu.com/HardwareSupp...%2) 8laptop%29 

I had to disable the external amp switch also.  Still having problems with sound in some applications (games), but StreamTuner works so I'm good.  Also the front volume control doesn't control the master volume just the system speakers, and since I plug in external speakers that's somewhat annoying but bearable since I can use the volume control on the speakers.  I was waiting to  add my laptop untill I get everything "there".  Should I go ahead and add it?

---

### Post by krismatth3 on 2006-04-18
You can control which mixer the front volume control .. controls .. by right clicking the speaker (mixer) icon in the upper right hand corner and choosing "Preferences..." and selecting a different item to control.

I'd add it whenever you're ready :)

---

