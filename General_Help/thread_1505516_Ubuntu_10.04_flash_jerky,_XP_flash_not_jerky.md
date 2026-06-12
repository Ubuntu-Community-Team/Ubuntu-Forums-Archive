---
title: "Ubuntu 10.04 flash jerky, XP flash not jerky"
date: 2010-06-09
forum: General Help
---

### Post by ph0b0s123 on 2010-06-09
Got a system which I wanted to get rid of Windows from, as all I do with it is watch flash videos. So thought I would give Linux another try and check how it had changed since I last tried it. So bunged on 32 bit 10.04 and just added standard adobe flash plugin. But I find that a lot of the flash videos I am watching from the net, are pretty jerky. It is not that the hardware is not up to it as I can boot into XP and the same videos play smoothly, even 720p ones.

So I wanted to ask the community for any advise. I have searched around and looked through the Ubuntu flash optimisation guide, but since I am using the bog standard adobe flash plugin and have not installed anything else since installing Ubuntu, I don't think anything in there applies.

I have a suspicion that it is to do with the machine having an ATI Radeon X850 card and that there are no native drivers any more for Ubuntu, but am not 100% sure.

Anyway if anyone has any advise or fixes it would be appreciated otherwise I will have to go back to XP....

My spec

AMD Athlon 64 X2 3800+
 Asus A8N-SLI Deluxe Motherboard
 2GB DDR 400 Memory
 ATI Radeon x850 XT PE GPU
 Realtek On-board sound
 60 Gb HDD

---

### Post by Louisraritan on 2010-06-09
Cant speak to the hardware aspect but I was having same problem with choppy video.  Try this link to the Ubuntu Forum topic, is what I learned and it helped me.

[http://ubuntuforums.org/showthread.php?t=1503018]("http://ubuntuforums.org/showthread.php?t=1503018")

---

### Post by philinux on 2010-06-09
> **ph0b0s123 said:**
> .

I have a suspicion that it is to do with the machine having an ATI Radeon X850 card and that there are no native drivers any more for Ubuntu, but am not 100% sure.

Anyway if anyone has any advise or fixes it would be appreciated otherwise I will have to go back to XP....

[https://help.ubuntu.com/community/RestrictedDrivers#ATI](https://help.ubuntu.com/community/RestrictedDrivers#ATI)

Not much help there I suppose. Just check the right thing is installed.
```
apt-cache policy xserver-xorg-video-ati driver
apt-cache policy xorg-driver-fglrx
```

First one should be installed, second one not.
Also try with compiz off.

---

### Post by ph0b0s123 on 2010-06-09
> **philinux said:**
> [https://help.ubuntu.com/community/RestrictedDrivers#ATI](https://help.ubuntu.com/community/RestrictedDrivers#ATI)

Not much help there I suppose. Just check the right thing is installed.
```
apt-cache policy xserver-xorg-video-ati driver
apt-cache policy xorg-driver-fglrx
```First one should be installed, second one not.
Also try with compiz off.

Used: metacity --replace command, made no difference

This is the result from running those commands. I think the results are as one would expect:

mat@mat-desktop:~$ apt-cache policy xserver-xorg-video-ati driver
xserver-xorg-video-ati:
  Installed: 1:6.13.0-1ubuntu5
  Candidate: 1:6.13.0-1ubuntu5
  Version table:
 *** 1:6.13.0-1ubuntu5 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
W: Unable to locate package driver
mat@mat-desktop:~$ apt-cache policy xorg-driver-fglrx
xorg-driver-fglrx:
  Installed: (none)
  Candidate: 2:8.723.1-0ubuntu3
  Version table:
     2:8.723.1-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Packages
mat@mat-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]

---

