---
title: "eee-control, eee applet, eee-pctray on karmic eee 1005HA bios 1102"
date: 2009-11-14
forum: General Help
---

### Post by deboopi on 2009-11-14
At last I have Ubuntu Karmic in a dual boot environment with win 7 on my 1005HA with the latest bios (1102) running. Ubuntu was hiding one of my windows partitions and after repaoring this in win 7, ubuntu could not find grub anymore .
 

But that's solved and now I'm trying to get one of the eee applets up and running but this seems to be the next problem.
[LIST]
[*]eee-control - the repackaged 9.04 version that should run on 9.10
I can install this one but then the applets starts complaining about a problem with the eee-control-daemon. Even if I try to start the daemon manually - which does not work - the problem persists
[*]eee-pctray
This one does not install completely, it complains about the dkms package
[*]eee-applet
this one installs flawlessly but doesn't do **** afterwards, enabling or disabling wireless, changing the fan speed, changing the cpu speed, it all doesn't matter, nothing changes.
[/LIST]I know some problems are caused by the recent bioses, I think all above release 7.03.
But I still wonder if there isn't any of these apps that can run on the combination karmic, 1005 bios 1102.
Can anybody help me out?

---

### Post by caish5 on 2009-11-18
bump!
I could use help here too

---

### Post by Nesquix on 2009-11-23
Yesterday i have flashed my bios with the latest bios (1102) on my eeePC 1000HE , and i have the same problems.

eee-applet, eee-control-tray or anything else don't work.

any ideas?

Maybe reflashing the bios with an old version who doesn't support Windows 7, not really cool with a dual boot (ubuntu / seven)....](*,)

---

### Post by jocheem67 on 2009-11-23
I've got an Arch install on my 1005HA-H.. at least I can tell you that gnome-power-manager should take care of your power-options. I think it's a default app on ubuntu.
There's also laptop-mode-tools and cpufreq, other power saving tools that should be able to install on Ubuntu...

Not much help, I know...

---

### Post by gmc on 2009-11-24
I can't help with the 1005 machines, but I have a 1000HE which I upgraded to the 1104 bios and broke eee-control functionality. I found a solution on the Italian eeepc forums and reposted the solution in the English eeepc forums.  Check out the following link..  [http://forum.eeeuser.com/viewtopic.php?pid=665130#p665130](http://forum.eeeuser.com/viewtopic.php?pid=665130#p665130)

---

### Post by ProfessionalOPs on 2009-11-25
I have heard that these tools are no longer required on 9.10

---

### Post by gmc on 2009-11-25
True enough, eee-control (etc..) are not strictly needed however, eee-control does add features that are not available in the base 9.10 install. Being able to enable/disable the webcam, wireless and control the fron side bus (fsb) does allow additional power saving. Currently I get between 7 and 9 hours on my 1000he by underclocking the FSB and turning off features that I'm not using.

---

### Post by BagRackRider on 2009-11-25
eee-control got toggle-touchpad in the settings but I can't seem to locate the script? Where do I find it?

---

### Post by PhonicsMonkey on 2009-12-02
to get better battery power I've been using powertop on my dell laptop. I don't know much about this stuff but I read somewhere that enableing laptop-mode-tools will help gain control of what's being used and not. Hope this helps

---

### Post by michaelzap on 2009-12-02
Aren't these the utils that were created by Fewt? If so, it doesn't look as if there will be Karmic versions. More here:
[http://www.fewt.com/2009/10/i-give-up.html](http://www.fewt.com/2009/10/i-give-up.html)

---

### Post by 121Lazz on 2009-12-16
Try this: In a Terminal, enter
```
find /sys/ | grep brightness 
```If you see
```
/sys/devices/virtual/backlight/acpi_video0/brightness
```Then edit the lines 85-86 in file **/usr/bin/eee-control-daemon**
From 
```
elif os.path.exists("/sys/class/backlight/eeepc/brightness"):
        brn_path = "/sys/class/backlight/eeepc/brightness"
```To
```
elif os.path.exists("/sys/class/backlight/acpi_video0/brightness"):
        brn_path = "/sys/class/backlight/acpi_video0/brightness"
```Hope that helps!

---

