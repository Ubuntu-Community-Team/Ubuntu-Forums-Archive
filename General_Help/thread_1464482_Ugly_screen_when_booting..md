---
title: "Ugly screen when booting."
date: 2010-04-28
forum: General Help
---

### Post by proyectomx on 2010-04-28
Hi.

I've just installed ubuntu 10.04 Release Candidate in my desktop and I have a problem.

First of all, it is installed side by side with windows 7, so the grub menu appears and everything is just fine selecting windows.... but when I select ubuntu, where it's supposed to show the animated boot logo, it shows an ugly image repeated four times across the screen (I would swear is the boot logo, but rendered real bad).

My configuration is: 
  motherboard DFI with ATI 790FX chipset
  AMD Athlon 5200+ dual core processor
  4gb of OCZ Ram
  Nvidia 9600 GT video card, 512mb vRam
  Two Sata hard drives, one western digital 320GB, the other seagate 500GB

Please notice:
  the boot logo was showing HUGE before I installed nvidia restricted drivers with the icon that shows aside the date in the top panel, so I guess the problem would be somewhere near that.

How do you report bugs??? I know this is a silly question, but put yourself in the user side, you have to open an openid account, and follow I don't know how many links.... haven't found an easy way to do it, this is why I post this here.

wouldn't be nice that betas and release candidates come with an application to report bugs, collecting logs and configuration??? 

Though my priority is to make the bootlogo work.
Any help will be appreciated.

---

### Post by lordbux on 2010-04-28
> **proyectomx said:**
> Hi.

I've just installed ubuntu 10.04 Release Candidate in my desktop and I have a problem.

First of all, it is installed side by side with windows 7, so the grub menu appears and everything is just fine selecting windows.... but when I select ubuntu, where it's supposed to show the animated boot logo, it shows an ugly image repeated four times across the screen (I would swear is the boot logo, but rendered real bad).

My configuration is: 
  motherboard DFI with ATI 790FX chipset
  AMD Athlon 5200+ dual core processor
  4gb of OCZ Ram
  Nvidia 9600 GT video card, 512mb vRam
  Two Sata hard drives, one western digital 320GB, the other seagate 500GB

Please notice:
  the boot logo was showing HUGE before I installed nvidia restricted drivers with the icon that shows aside the date in the top panel, so I guess the problem would be somewhere near that.

How do you report bugs??? I know this is a silly question, but put yourself in the user side, you have to open an openid account, and follow I don't know how many links.... haven't found an easy way to do it, this is why I post this here.

wouldn't be nice that betas and release candidates come with an application to report bugs, collecting logs and configuration??? 

Though my priority is to make the bootlogo work.
Any help will be appreciated.

just try re configuring 
the xorg using the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

and about bug reports 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by proyectomx on 2010-04-28
> **lordbux said:**
> just try re configuring 
the xorg using the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

and about bug reports 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Wow! this was fast! 
I will try it when I get home.

Thank you very much lordbux

---

