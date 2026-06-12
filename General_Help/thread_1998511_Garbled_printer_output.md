---
title: "Garbled printer output"
date: 2012-06-06
forum: General Help
---

### Post by bkline on 2012-06-06
I've got a Brother HL5370DW laster printer attached to an Xubuntu workstation (12.04).  I've shared the printer via SMB, and sometimes when I print from another Xubuntu machine I get garbled output.  I've attached an example of the problem.  The first image is what I get printing from the workstation to which the printer is directly attached.  The second image is what I get printing across the (local) network from a second Xubuntu system.  Both are using the recommended driver for the printer model.  Anyone ever seen anything like this?  Where should I start looking for the cause of the problem?

---

### Post by plucky on 2012-06-07
> Both are using the recommended driver for the printer model.


Did you download the driver from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) or just use the "recommended" from the list of drivers?

The drivers for your printer are not packaged in ubuntu. See [Wiki](https://wiki.ubuntu.com/BrotherDriverPackaging)

Please post the terminal output from both systems for ```
dpkg -l | grep -i brother
```

Good Luck

---

### Post by bkline on 2012-06-07
> **plucky said:**
> Did you download the driver from the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) or just use the "recommended" from the list of drivers?

I used what Ubuntu had installed.  I assumed it was a driver for my specific printer, as it had the exact model number.

> **plucky said:**
> The drivers for your printer are not packaged in ubuntu. See [Wiki](https://wiki.ubuntu.com/BrotherDriverPackaging)

Looks like the 5370 isn't in the list (as you say).  I'll get the PPD from Brother and install it manually; will report results back here.

> **plucky said:**
> Please post the terminal output from both systems for ```
dpkg -l | grep -i brother
```


```
$ dpkg -l | grep -i brother
ii  printer-driver-ptouch                  1.3-3                                   printer driver Brother P-touch label printers
```

Thanks!

---

### Post by bkline on 2012-06-08
I installed the PPD from Brother's web site, but that didn't solve the problem.  So then I installed the two .deb packages from that site (forcibly, since those 32-bit packages are a mismatch with the client's 64-bit OS, which made me a little nervous).  That did the trick.  Thank you for pointing me in the right direction.

I have to say, I'm more than a little baffled by the fact the Ubuntu ships with drivers which (a) claim to be for exactly the model printer I have but (b) don't work.

---

### Post by bkline on 2012-06-08
Hmm.  That worked for all but one of the client machines on the network, which is still producing garbled output as illustrated in the first post in this thread.  Will continue investigating.

---

### Post by bkline on 2012-06-08
> **bkline said:**
> Hmm.  That worked for all but one of the client machines on the network, which is still producing garbled output as illustrated in the first post in this thread.  Will continue investigating.

I thought about two things I could do to solve the problem.  I could reboot the machine (sort of treating it like a Windows system) or I could upgrade it from 11.10 to 12.04.  I did the upgrade, and now that's printing correctly.  However, it's still a bit of a mystery, because there's one machine on the network which is still on 11.10, and it's printing correctly.  So perhaps it just needed to be rebooted?  Again, that usually more of a solution for Windows machines, but who knows?

---

### Post by bkline on 2012-06-08
What's up with the spam I'm seeing recently on the Ubuntu forums?  I've been on this forum for many years, and this is the first time they've let the spammers get through that I've noticed. :-(

---

