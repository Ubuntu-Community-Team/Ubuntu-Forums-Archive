---
title: "Will I eventually be able to use Ubuntu?"
date: 2010-12-30
forum: General Help
---

### Post by Mindswap1 on 2010-12-30
Hi guys! I'm really sad that I have to move back to windows 7. The only reason being is because my usb wouldn't be detected, and I really needed it for school work. Also I could never tell if a hardware would be compatible with it so yeh... Anyhow I was wondering would Ubuntu 11.04 or even 11.10 solve these problems. I really want to move back to linux. Just wondering if that would be any time soon.

---

### Post by TeoBigusGeekus on 2010-12-30
> **Mindswap1 said:**
> The only reason being is because my usb wouldn't be detected

Are you talking about a flash drive? An external hard disk? Usb ports in general?
Have launched a thread about this?

---

### Post by Mindswap1 on 2010-12-30
Yeah I was talking about flash drive, no one seemed to know what to do. I did start a thread [here ]("http://ubuntuforums.org/showthread.php?t=1656103"), but like I said no one seemed to know what to do.

---

### Post by anystupidname1 on 2010-12-30
EDIT: OK, looked at your other thread. The problem seems to be this:
```
usb 2-5: device not accepting address 6, error -62

```I would tentatively advise you to try using the irqpoll kernel boot option as explained here:
[http://ubuntuforums.org/showthread.php?t=799842](http://ubuntuforums.org/showthread.php?t=799842)

Recent news I've read indicates that Linux is actually BETTER than MS in respect to hardware support lately. Specifically which hardware component did/do you have an issue with?

OLD RESPONSE:

"lspci -vv" output would be appropriate in your answer. You could use a liveCD or WUBI to obtian this information for us without affecting your current Winders install.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

What file system(s) does it use and how many partitions does it have? Again, the output from "lsusb" might be useful here and/or from dmesg after you've just plugged in and unplugged the usb device. Also fdisk -l would help.

---

### Post by TeoBigusGeekus on 2010-12-30
Alright, lets see what we can do.
Give us the results of the 
```
lsusb
```
command, before and after you plug your flash drive in.

---

### Post by Mindswap1 on 2010-12-30
I got the following when I ran lsusb without the usb flash drive plugged in. 

```
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:1f04 Hewlett-Packard 
Bus 001 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```And this is what I got afterwards. 

```
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:1f04 Hewlett-Packard 
Bus 001 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Also I followed your instructions [anystupidname1]("http://ubuntuforums.org/member.php?u=874288") however the forum tells me to put the following into the terminal.

```
gksu gedit /boot/grub/menu.lst
```  After I did that I got a blank page. So I couldn't find the lines it was telling me to. Is this because I am running from a live cd.

---

### Post by TeoBigusGeekus on 2010-12-30
Hmm, nothing at all...
It's very strange... It should show something. Have you tried with something else in that specific usb port (printer, webcam, another flash drive, mouse, keyboard, anything at all)?

---

### Post by Mindswap1 on 2010-12-30
My sisters USB works perfectly on it so does my phone, and my psp.

---

### Post by TeoBigusGeekus on 2010-12-30
Ok, put your printer in that specific port and then plug in your flash drive in the printer's former port. Does lsusb list it now?

---

### Post by anystupidname1 on 2010-12-30
Sorry, yes partly, but those instructions are for grub"1" instead of grub2 which is in use now. This shows how you'd do it if it was installed on HDD: [http://ubuntuforums.org/showthread.php?t=1366354](http://ubuntuforums.org/showthread.php?t=1366354)

You should be able to pass the boot option at boot time from the liveCD too though.
[ ]("http://ubuntuforums.org/showthread.php?t=1366354")

---

### Post by Mindswap1 on 2010-12-30
HEY OMG IT WORKS! The USB Shows. How can I ever thank you! Both the printer, and the usb show! Thank YOU!!!!!!!!!!!!!!!!!1 You are my HERO!!! <3333333333333333 :) 

Is there a way I could make it detect from the other usb port? The one that initially didn't work. Heres what I got btw when I typed in lsusb 

```
]Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 03f0:1f04 Hewlett-Packard 
Bus 001 Device 008: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 007: ID 154b:0048 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The PNY is the usb.

---

### Post by TeoBigusGeekus on 2010-12-30
Try switching them again and post back.

---

### Post by anystupidname1 on 2010-12-30
Funky USB 1.1 hub? Interesting... I'd still try the kernel option to see if it prevents that from happening again.

---

### Post by t4thfavor on 2010-12-30
It probably has alot to do with the PNY stick being slightly cheap (as far as sticks go) and therefore being slightly mis-shapen. if all 5 pins don't connect just right, it wont show up.

I bet if you have a usb hub, you could get it to work through the affected port.

---

### Post by Mindswap1 on 2010-12-30
Didn't work :/ honestly I guess it's not that big a deal as long as it works in the other one. I really wish I could give u a hug right now lol. You saved my day! and Saved me from Windows <33333. Your truly awesome.

---

### Post by TeoBigusGeekus on 2010-12-30
Glad you stayed with us...

---

