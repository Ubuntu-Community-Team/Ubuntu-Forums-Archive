---
title: "Rebooting on Startup"
date: 2010-05-17
forum: General Help
---

### Post by Jonny87 on 2010-05-17
I have made a similar post on this topic but I thought it had came right and I was getting ready to go and mark it solved until it happened last night.

I'm running Ubuntu 10.04 64bit, dual booting with Win7 Prof 32bit. But every now and then when I start up it comes to the grub boot loader, and I hit enter to boot 10.04 (even if I leave it for the 10sec countdown), it changes screens to start booting. It sits on a black screen for a few seconds and then reboots the computer. And the cycle starts all over again.
This can occur over and over for multiple attempts to boot. But randomly it will boot fine. 

Last night while i was attempting to boot also tried booting Win7. It went straight in no trouble. I even managed to start up a game.

When it does boot fine it's usually fine for the remainder of the session. 

Also I'm running 10.04 32bit on an old laptop and have had no trouble with this.

Is this a fault in 10.04 or could it be hardware? How can I find out or fix the problem if it is Ubuntu?

I don't think it is Hardware (though won't say it's not) as I've tried different tests like memtest and CPU stress tests and still no problem came up.

---

### Post by johngreth on 2010-05-18
Since it is only a problem in ubuntu on the one computer it is probably a hardware software incompatibility thing. I don't really have a solution though. You could try running "sudo update-grub" just incase it is grub's fault, but I doubt it.

---

### Post by Darkness Des on 2010-05-18
I had this same problem on my old computer. I eventually just put that hard drive in my newer desktop as the slave, it worked just fine. But if you don't want to go to extensive measures, try turning off quite splash. This can be done by running the following commands:

```
gksudo gedit /etc/default/grub
```

Once that opens up in Gedit, change the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
The next time you boot it won't show the splash screen but a bunch of lines of code. Just ignore it. This is what I was doing on my old computer to fix it, but I just ran out of patience and moved the drive so I could have better hardware running on Ubuntu.

---

### Post by Jonny87 on 2010-05-19
> **johngreth said:**
> Since it is only a problem in ubuntu on the one computer it is probably a hardware software incompatibility thing. I don't really have a solution though. You could try running "sudo update-grub" just incase it is grub's fault, but I doubt it.


Is there a page anywhere that lists all of the compatible/un-compatible hardware?

Also like I mentioned. It doesn't always do this. Often it starts fine with no trouble. but when it doesn't start properly, it's a pain in the butt.

---

### Post by johngreth on 2010-05-20
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by Jonny87 on 2010-06-14
**[UPDATE]**
I've still been having some trouble though slightly different. It's not just limited to the start up. I can be working fine then sometimes when go to do something (often something minor) it suddenly reboots its self. However as it tries to boot it doesn't get past the BIOS stage where it try to boot to the HDD, it come up saying Boot Error or something along those lines.
It crashed last friday and I spent it all weekend trying to get it to start again kept getting boot error. Occasionally it would get to the grub but after selecting the OS it would reboot again if I choose Ubuntu, or I got a blue screen if I chose windows.
However on sunday evening I had an idea to try something different. I got an old PATA HDD with an un-updated version of 9:10, and installed into my comp. After booting to 9:10, I ran...
```
sudo update-grub
```
9:10 then picked up 10:04 and windows, I then rebooted and selected 10:04 and its been working fine since. This has got me wondering, could it be some issue with grub or something related.


I have checked and tested each of the hardware for errors and it all looks fine.


Does anyone have any ideas on whats happening or what may fix it?

---

