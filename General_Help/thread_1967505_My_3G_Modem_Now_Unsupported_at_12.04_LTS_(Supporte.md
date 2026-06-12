---
title: "My 3G Modem Now Unsupported at 12.04 LTS (Supported at 11.10)"
date: 2012-04-28
forum: General Help
---

### Post by ProNux on 2012-04-28
What happened to Precise Pangolin?  It does not support my 3G  modem anymore, where, in 11.10 & below, it works out-of-the-box.  Was it done hastily?

---

### Post by codemaniac on 2012-04-28
What does **lsusb **says when you plug your modem in ?

---

### Post by ProNux on 2012-04-28
> **codemaniac said:**
> What does **lsusb **says when you plug your modem in ?
```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b213 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0718:063d Imation Corp. 
Bus 005 Device 002: ID 1690:0754 Askey Computer Corp. [hex] 
Bus 004 Device 002: ID 1c9e:6061 OMEGA TECHNOLOGY WL-72B 3.5G MODEM
ubuntu@ubuntu:~$
``` 
Thats the output of lsusb.  I know it is there, but I cannot find it in the network when I needed to connect to the internet.

---

### Post by codemaniac on 2012-04-28
> **ProNux said:**
> ```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b213 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0718:063d Imation Corp. 
Bus 005 Device 002: ID 1690:0754 Askey Computer Corp. [hex] 
Bus 004 Device 002: ID 1c9e:6061 OMEGA TECHNOLOGY WL-72B 3.5G MODEM
ubuntu@ubuntu:~$
``` 
Thats the output of lsusb.  I know it is there, but I cannot find it in the network when I needed to connect to the internet.

Your modem is perfectly  detected in the system .Now can you add a new Mobile broadband connection ?

---

### Post by ProNux on 2012-04-28
> **codemaniac said:**
> Your modem is perfectly  detected in the system .Now can you add a new Mobile broadband connection ?
I can add a Mobile Broadband connection, BUT the system cannot see the 3G modem plugged in the USB.  Actually I have no problem using this 3G modem on the previous Ubuntu versions.  That is what puzzling me...

---

### Post by codemaniac on 2012-04-28
> **ProNux said:**
> I can add a Mobile Broadband connection, BUT the system cannot see the 3G modem plugged in the USB.  Actually I have no problem using this 3G modem on the previous Ubuntu versions.  That is what puzzling me...

But lsusb output shows it is perfectly detected by 12.04 .I dont know what exactly you are trying to convey by .
> I can add a Mobile Broadband connection, BUT the system cannot see the 3G modem plugged in the USB.

---

### Post by prana on 2012-04-29
3G modems have always been hit or miss under Ubuntu especially the newer ones because they use proprietary hardware.

I know in your case something that worked in 11.10 doesn't work anymore in 12.04 so the best option is to report a bug against network-manager

ubuntu-bug network-manager

I gave up on USB based 3G modems and am now using a Mifi device because a Mifi is OS agnostic.

---

### Post by codemaniac on 2012-04-29
If everything fails , try sakis-3g .It came as rescue when i was struggling to connect a lesser known 3g modem(micromax) in my 11.10 desktop .
Download the script and provide the necessary details .
[http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading)

---

### Post by ProNux on 2012-04-29
> **codemaniac said:**
> But lsusb output shows it is perfectly detected by 12.04 .I dont know what exactly you are trying to convey by .
I mean, I can create a Mobile Broadband connection (even without a modem on hand).  You can plug the modem later and use the connection.

---

### Post by izboboy on 2012-04-29
:lolflag:v

i got most similar problem when i trying to connect to the internet but fails by using my 3g modem usb hub . when  trying to install the softwre , it cant !!!! please help me!!

---

### Post by Elfy on 2012-04-29
> **izboboy said:**
> :lolflag:v

i got most similar problem when i trying to connect to the internet but fails by using my 3g modem usb hub . when  trying to install the softwre , it cant !!!! please help me!!

Please do not hijack other people's threads with your issues - especially when you have your own thread. Your issue might be similar - not necessarily the same.

---

### Post by ProNux on 2012-05-01
What is surprising is that even my old Nokia phone is working out-of-the-box when used as a 3G modem.

---

### Post by codemaniac on 2012-05-01
It is tough to predict how a device will behave from one distro version to another .However it wont hurt the system if you give sakis-3g a try .
Have you been able to download and run the script ?

---

### Post by kdane4 on 2012-05-01
hi pronux,

may i know your brand of 3g usb modem? I have an old huawei e553 (smart) tested on kubuntu 12.04 and it worked fine. (havent downloaded ubuntu 12.04 yet)

Its really odd if you can use your phone but not the 3g modem.

---

### Post by ProNux on 2012-05-02
> **codemaniac said:**
> It is tough to predict how a device will behave from one distro version to another .However it wont hurt the system if you give sakis-3g a try .
Have you been able to download and run the script ?

Thanks for the suggestion.  I plan to try the sakis-3g, anytime within the week when I have the right time.  I just found out that numerous Ubuntu users have a similar problem come Precise.  I am monitoring also the thread below, which my modem behaves similarly.

[http://ubuntuforums.org/showthread.php?t=1969322](http://ubuntuforums.org/showthread.php?t=1969322)

---

### Post by ProNux on 2012-05-02
> **kdane4 said:**
> hi pronux,

may i know your brand of 3g usb modem? I have an old huawei e553 (smart) tested on kubuntu 12.04 and it worked fine. (havent downloaded ubuntu 12.04 yet)

Its really odd if you can use your phone but not the 3g modem.

I also have an old modem, model WM66 made by Longcheer as detected in Windows.  Ubuntu detects it as Omega Technologies 3.5G modem.  Good for you it worked in Kubuntu, most probably it will work in Ubuntu 12.04.

I read through similar threads and they seem to point out the kernel as the culprit.  I believe the Ubuntu team can release an update soon as there are numerous users having this problem.

---

### Post by ProNux on 2012-05-04
Problem considered "solved".  Solution is found on this link.

[http://ubuntuforums.org/showthread.php?t=1969322]("http://ubuntuforums.org/showthread.php?t=1969322")

Credits go to alexfish & thread-starter malakar.subhendu.

---

