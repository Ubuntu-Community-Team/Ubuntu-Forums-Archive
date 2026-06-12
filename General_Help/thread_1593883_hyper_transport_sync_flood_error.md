---
title: "hyper transport sync flood error"
date: 2010-10-11
forum: General Help
---

### Post by 6mil928 on 2010-10-11
Trying to install 10.10 netbook edition on my MSI U230 netbook from a USB drive. Keep getting the error "hyper transport sync flood error occurred on last boot" Press F1 to Resume. F1 causes just a reboot and the same thing happens.  Anyone seen this error?  It happens with both the netbook and desktop version.

---

### Post by Ozdemon on 2010-10-11
> **6mil928 said:**
> Trying to install 10.10 netbook edition on my MSI U230 netbook from a USB drive. Keep getting the error "hyper transport sync flood error occurred on last boot" Press F1 to Resume. F1 causes just a reboot and the same thing happens.  Anyone seen this error?  It happens with both the netbook and desktop version.

Yep, I just tried on U230 and I get the same error.  :(

---

### Post by 6mil928 on 2010-10-11
Interesting

---

### Post by 6mil928 on 2010-10-11
Gonna try the 64 bit a friend of mine says it maybe the AMD dual core.

---

### Post by 6mil928 on 2010-10-11
Well x64 works but the wireless doesn't:-(

---

### Post by Ozdemon on 2010-10-18
I thought the problem was related to the install method.  So I just did an online upgrade.  Now my U230 is bricked.  Cannot do anything, as I just keep getting the hyper transport sync flood error, press F1 to resume, which just repeats the process on reboot.

Any idea how to solve this?  I am really surprised at this regression.

[Edit] I am now able to boot by downgrading the kernel to 2.6.32.25, so the error must be related to the later kernel.  :(

---

### Post by 6mil928 on 2010-10-19
Yea kinda ridiculous!

---

### Post by johnnyredshirt on 2010-10-21
I have a U230 as well. The exact same thing happened to me. It rebooted instead of shutting down and was bricked when I tried to upgrade to the new kernel. I downgraded to 10.04.1 and its running fine. Huge Pain in the... Guess it don't pay to run "exotic" hardware heh.

---

### Post by 6mil928 on 2010-10-21
If this is exotic then Ubuntu is hosed.

---

### Post by johnnyredshirt on 2010-10-22
Hey, I just installed 10.10 64bit desktop (I was using the gnome desktop in netbook anyway) and it is running fine with working wireless. Had to edit the blacklist.conf (added lines on launchpad). Probably should have tried 64bit first but... Anyhow it's working for now. ;}

---

### Post by 6mil928 on 2010-10-22
I got 64 to work as well.  The x86 and the netbook edition did not though.  Wireless did not work out of the box on 64 though.

---

### Post by Dolfhin01 on 2010-12-15
I am getting the same problem with an Phenomen II Cpu, any other AMD users that face this problem?

---

### Post by Lumsdoni on 2011-06-17
HI, 

I'm new to Linux / Ubuntu , but with some Mac experience.

Got fed up with Windows on my Netbook and decided to go Ubuntu. I have a MSI Wind U230 - the UK version with a single core 1.6ghz AMD MV-40. 2GB Ram.

I got the Hyper Transport Sync Flood Error (HYSFE) after a successful install of 11.04. System working fine, but whenever I rebooted or restarted, I got the HYSFE, press F1 to continue, then it would boot as usual.

This was with both 32 and 64 bit versions.

I then tried 10.10 32bit, 64bit and Netbook  - same error with 32b and 64b versions and Netbook didn't even install.

Finally 10.04 works, and no errors. Had to reinstall Wireless driver but apart from that all good.

**Is it a Hardware spec issue that I cannot run later than 10.04?**

Windows 7 ran perfectly (well, apart from the fact it was Windows!)

---

### Post by Ozdemon on 2011-06-17
It isn't a hardware issue.  I changed distro to PCLinuxOS.  I also have a U230.  No problems with this distro on a U230.  :grin:

---

### Post by Lumsdoni on 2011-06-21
Thanks for the response. 

Before i take the plunge, how would you say PcLinusOS 32bit compares to Ubunto 10.04 64bit?

Also, would you recommend KDE or Gnome?

Thanks for your time.

---

### Post by Ozdemon on 2011-06-21
> **Lumsdoni said:**
> Thanks for the response. 

Before i take the plunge, how would you say PcLinusOS 32bit compares to Ubunto 10.04 64bit?

Also, would you recommend KDE or Gnome?

Thanks for your time.

I am very happy with PCLOS.  I have been using it for many months.  It also uses the Synaptic package manager, so you will find it a very familiar distro.

I use Gnome because I am used to it.  PCLOS was originally KDE only, so KDE is very well supported.  It also has an excellent forum.

---

### Post by Lumsdoni on 2011-07-01
Quick update, after reformatting HD and installing various OS, weirdly the HTSFE went away, and amnow running 11.04 without any issues on the u230 single core.

It is possible, just don't know what I did if anything.

---

