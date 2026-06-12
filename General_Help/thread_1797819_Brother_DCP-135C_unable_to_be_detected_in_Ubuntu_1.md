---
title: "Brother DCP-135C unable to be detected in Ubuntu 11.04"
date: 2011-07-05
forum: General Help
---

### Post by wcks48 on 2011-07-05
Hi Expert,
 
In  previous version of ubuntu before 11.04, I was installed the DCP-135C and able to print and scan.
After the upgrade, I found that xscan and "simple scan" apps unable to detect the scanner. With error: "no scanner detected". But printing is still workable.
Do you have any recommendation on how to check my system installation of the device and the solution to enable the scan function of this printer+scanner?
Thanks.

William

---

### Post by overdrank on 2011-07-05
Moved to General Help. :)

---

### Post by Garcicasti on 2011-09-19
Hello everybody,I have to say i have the same problem!I have ubuntu 11.04 too, and i can print, but not scan.I have tried many tutorial more or less the same, but they just not work in 11.04 version, just 9.10,10.10...
Does anyone have the solution to this problem?It'll be great!
Thanks in advance:popcorn:

---

### Post by davidvandoren on 2011-09-19
try this

```
sudo gedit /lib/udev/rules.d/40-libsane.rules
```

And paste this
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
follow instructions below
Ubuntu 9.10, 10.04, 10.10, 11.4 **1.** Open "/lib/udev/rules.d/40-libsane.rules" file.**2.**Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
  
  The lines to be added---------------------------              
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
       **3.** Restart the OS.

---

### Post by davidvandoren on 2011-09-21
You have to install the scanner driver from the website first of course.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

---

### Post by itagomo on 2011-09-28
my natty also acts like that but i'm using Lexmark X1185 all in one

printer works (even without ink)
scanner doesn't (usual error "No scanners detected")

it was working before when i was using maverick 10.10 or even lucid

but i think the whole distro version has the problem (reallly?)

NEED HELP HERE ! can't find any SOLVED related posts

---

### Post by mörgæs on 2011-09-28
Since this is a different printer, best is to open a new thread in Hardware and Laptops explaining the problem. 

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

---

### Post by itagomo on 2011-09-28
check this link:

[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475?comments=all](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/774475?comments=all)

follow procedures of username Ashley Hooper (ash-hooper)

MINE IS NOW WORKING !

got the link from this thread ..

[http://ubuntuforums.org/showthread.php?t=1745031&page=2](http://ubuntuforums.org/showthread.php?t=1745031&page=2)

---

