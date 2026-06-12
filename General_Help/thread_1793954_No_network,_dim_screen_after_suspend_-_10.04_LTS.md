---
title: "No network, dim screen after suspend - 10.04 LTS"
date: 2011-06-30
forum: General Help
---

### Post by Bucky Ball on 2011-06-30
Hi all,

As the title says, I have no network and the screen is dimmed when I come out of suspend; e.g. I close the lid and open. Computer suspends okay when I close the lid, though.

On opening, the screen is dimmed and the brightness control doesn't work. Logging out and in doesn't help. Restart is the only way to return to normal.

Toshiba Satellite Pro L510 running 10.04 LTS. 

Cheers ...

---

### Post by Bucky Ball on 2011-07-11
Update: I have 10.04, 10.10, 11.04 installed on this machine and after suspend, screen almost unusably dim, but strange part is ... 

* When I log out of 10.04, login screen still dim. Login, changes nothing. Desktop still dim.
* When I restart the machine still dim at the grub menu, but when I boot in to 10.04, 10.10 or 11.04 it restores brightness to normal (just before login screen).
* Adjusting brightness makes no difference.

Odd ... seems to be a known bug and haven't really found a known fix as yet ...

I found a page that suggested putting some code in /etc/rc.local, which I did, but didn't fix for me, although has for some ...

```
brt=`cat /sys/devices/virtual/backlight/acpi_video0/brightness`
abrt=`cat /sys/devices/virtual/backlight/acpi_video0/actual_brightness`
if [ "$brt" != "$abrt" ]; then
echo $abrt > /sys/devices/virtual/backlight/acpi_video0/brightness
fi                      
```... from post #4 here ...

[http://ubuntuforums.org/showthread.php?t=1479372](http://ubuntuforums.org/showthread.php?t=1479372)

I am using Xubuntu 10.04 with no third-party ATI drivers.

---

