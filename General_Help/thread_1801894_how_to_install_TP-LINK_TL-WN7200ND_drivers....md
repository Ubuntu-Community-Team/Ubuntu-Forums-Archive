---
title: "how to install TP-LINK TL-WN7200ND drivers..."
date: 2011-07-11
forum: General Help
---

### Post by BOMBMASTAH on 2011-07-11
Hello, I don't know how to install TP-LINK TL-WN7200ND drivers for Ubuntu 11.04. I have a clean install of Ubuntu 11.4. I download drivers from here [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) but I don't know how to install them. Can some one help Me to do this? It must be like for dummies because I don't have enough knowledge about Ubuntu.Thank you.:-k

---

### Post by mastablasta on 2011-07-11
Do you even need drivers? if so check the additional driver menu first.
 
If they are not there and you donwloaded the drivers there are usually instructions in the driver's file. unpack the file and follow the instructions to install it. you might need to copy & paste a few commands into terminal.

---

### Post by BOMBMASTAH on 2011-07-11
Actually I found that Ubuntu 11.04 don't recognize absolute no one usb hardware.:frown::( . I don't know why. It is a fresh copy.:confused:

---

### Post by gandaran on 2011-07-11
> **BOMBMASTAH said:**
> Hello, I don't know how to install TP-LINK TL-WN7200ND drivers for Ubuntu 11.04. I have a clean install of Ubuntu 11.4. I download drivers from here [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) but I don't know how to install them. Can some one help Me to do this? It must be like for dummies because I don't have enough knowledge about Ubuntu.Thank you.:-k
did you check in additional drivers?
ralink chipsets usually are supported in ubuntu, sometimes you just have to blacklist some ralink modules to get yours working, no need to install drivers, to find out your usb adapter chipset type in terminal
```
lsusb
```
post the output

---

### Post by BOMBMASTAH on 2011-07-16
Ok! I reinstall Ubuntu, these time during the installation TL-WN7200ND was connected to the usb port. After Installation Ubuntu recognize TL-WN7200ND. The problem is that TL-WN7200ND can't connect to the WPA2-PSK secure wifi network, like mine home network.
I read in forums and people say this is normal and i have need to install the original drivers from ralink.
So far so good!
I found these theme in the forum: [http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)
and the problem is because I am a noob and I can do just to step 10 from the tutorial and the next step 11,12,13... I don't know how to make them.:confused: I just need more like "for dummies" tutorial.](*,)

---

### Post by jennifermaiya on 2011-08-26
hello I do not speak much English, so I hope you understand me.
I also I have the same problem, since versions anterirores to 11.04, the problem is with the drivers as you say, and not even following the guide and managed to make it work.
What I did was install the 11.10 version that comes with the Linux 3.0 kernel, and all resolved.
The 3.0 kernel could also be installed on ubuntu 11.04 (but not e able to manually) but it can be done to upgrade.

The 3.0 kernel already has the ralink drivers we need drivers and many more, plus other improvements.

I hope this helps.

---

