---
title: "uninstall every video driver"
date: 2009-10-13
forum: General Help
---

### Post by bd41 on 2009-10-13
What happened was i downloaded the ati driver from the ati website and installed that. then i tried to make the extra desktop effects but it told me to enable the fglrx propriety driver. i did that under hardware drivers, restarted the computer and got some weird green and purple logos and i couldn't do anything except for restart into recovery mode.

i some how uninstalled the fglrx driver but i want that one instead of the one i have right now.


So, how do i check what graphics card drivers i have currently installed, and how do i remove those drivers? so i can install the propriety driver

---

### Post by bd41 on 2009-10-13
bump

---

### Post by lidex on 2009-10-13
Look in your gnome menu "System>Administration>Hardware Drivers" to enable/disable drivers. I'm a little confused - you have fglrx installed and want to replace that with catalyst drivers? Is that correct?

---

### Post by hubiedo on 2009-10-19
here is how i just fixed mine with the same problem the best i can tell from your description. i found the answer on linux forums. i use ubuntu 8.04 and lost??? my fglrx proprietary driver as noted above. i have a asus  m3a78-emh hdmi mobo w/ onboard ati radeon hd 3200 graphics card that i found listed in my lspci command line output.

the link to linux forum is:
[http://www.linuxforums.org/forum/ubuntu-help/152125-driver-radeon-3200-ubuntu-8-04-a.html](http://www.linuxforums.org/forum/ubuntu-help/152125-driver-radeon-3200-ubuntu-8-04-a.html)

the link to the newest?? driver is:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

i just downloaded, ran sudo sh command (with the name xxx.run file) after i cd to the directory with the downloaded file. 

i hope this helps someone including yourself. my display was a mess after i deleted?? the proprietary driver file needed.

---

