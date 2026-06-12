---
title: "Error while doing lubuntu live cd"
date: 2012-07-09
forum: General Help
---

### Post by codingman on 2012-07-09
I'm trying lubuntu from a live cd, but when I boot into it, and choose "try lubuntu" and the animated dots show up after 15 seconds, it gives me this message 

```
*starting configure network device security [OK]
*starting configure network device [OK]
[90.292213] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[90.292249] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[90.292270] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```
:confused::confused::confused:
Thanks in advance,
Codingman

---

### Post by angryfirelord on 2012-07-09
The broadcom open-source driver needs firmware for it to work. There are three different packages available: firmware-b43-installer, firmware-b43-lpphy-installer, and firmware-b43legacy-installer. You'll have to know which card you have for it to use the right firmware.

Otherwise, you can let Jockey install the proprietary driver.

---

### Post by robert219 on 2012-11-09
This is still a problem with the latest lubuntu-12.10-desktop-i386.iso .
To be clear, it is impossible to launch a live session. With my meagre understanding this means that the solution has to come from a change to the iso image.

I'd like to change to lubuntu, but my Fujitsu Siemens laptop does not allow usb booting. The iso cd which I burned does not even get me into a live session for testing.  It hangs on the b43 problem and I have to force a brutal shutdown.

I'll try the solutions suggested. I just wanted to let people know that the problem still exists.

Regards
Robert

---

### Post by ibjsb4 on 2012-11-09
Looks like you need to bypass your wireless and install with a wired internet connection.  I have not found a bug report, maybe someone should start one.

[https://answers.launchpad.net/ubuntu/+question/105026](https://answers.launchpad.net/ubuntu/+question/105026)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ERROR%3A+Firmware+file+%22b43%2Fucode5.fw%22+not+found&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ERROR%3A+Firmware+file+%22b43%2Fucode5.fw%22+not+found&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Cheesemill on 2012-11-09
You could also try using the alternate installation CD as it uses a different installer.
 
[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-alternate-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-alternate-i386.iso)

---

### Post by robert219 on 2012-11-09
Thanks Cheesemill and gcdsfR0b
I'll try the alterate iso.
The current iso fails to boot the live session *even with a cable connection*...
but it *seems* that the solution is here:
[http://ubuntuforums.org/showthread.php?p=11883375](http://ubuntuforums.org/showthread.php?p=11883375) 

I'm not at home and will only be able to try it and/or the alternate CD this weekend. Just seems strange that the main iso continues to pose such a well-known problem...
regards
Robert

---

