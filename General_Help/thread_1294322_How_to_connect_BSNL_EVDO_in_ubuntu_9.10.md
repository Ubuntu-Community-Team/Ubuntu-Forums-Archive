---
title: "How to connect BSNL EVDO in ubuntu 9.10"
date: 2009-10-18
forum: General Help
---

### Post by brijith on 2009-10-18
Hai All,
Today I installed Ubuntu 9.10 beta .... Previously I was using 9.04. In 9.04 I could connect BSNL evdo very easly... But When I try to connect it in 9.10 it won't work . It says offline ....
Please help me

---

### Post by vinaykumaruppalapati on 2009-11-01
> **brijith said:**
> Hai All,
Today I installed Ubuntu 9.10 beta .... Previously I was using 9.04. In 9.04 I could connect BSNL evdo very easly... But When I try to connect it in 9.10 it won't work . It says offline ....
Please help me

Hi guys i do have the same problem, pls check can any one help.

Hello friends out of frestation i have deleted the auto mobile broadband connection in the network connections. I tried adding new wireless connection, however after entering all the details i.e user id and password i am getting the same problem, i am unable to connect to the net.
Can any on ther help me??????????????????
Its totally frustatin i have upgraded to 9.10 a weak agow and till now i am unable to connect to the net. foutunately i have windows as well.

---

### Post by brijith on 2009-11-01
> **vinaykumaruppalapati said:**
> Hi guys i do have the same problem, pls check can any one help
But I tried it in Ubuntu 9.10 beta it is obvious to have some bugs in it.... I think this might be not there in the released version (released on 29 th last month). Did you tried it after installing the released version. 

Also when I gone through the launchpad I came to know that this bug is already reported by some one else.So I think the released version may not be having this bug.

another thing I noticed in 9.10 beta was there is only one service provider (RIM) listed Under India for mobile broadband. but in Ubuntu 9.10 released version, though I didn't installed it, When I booted it live I found that now it lists all the service providers under India.

So I hope they might have solved the issue.... 

:D

---

### Post by puneet on 2009-11-02
> **brijith said:**
> But I tried it in Ubuntu 9.10 beta it is obvious to have some bugs in it.... I think this might be not there in the released version (released on 29 th last month). Did you tried it after installing the released version. 

I installed the released karmic koala on my two laptops and the BSNL device does not work on either. Earlier with Jaunty installed, the device worked flawless with wvdial.

Here is the USB device that I got from BSNL.

Bus 002 Device 002: ID 05c6:3197 Qualcomm, Inc. CDMA Wireless Modem/Phone

> **brijith said:**
> 
another thing I noticed in 9.10 beta was there is only one service provider (RIM) listed Under India for mobile broadband. but in Ubuntu 9.10 released version, though I didn't installed it, When I booted it live I found that now it lists all the service providers under India.


BSNL does not get listed even now. Only RIM, and TATA get listed.

> **brijith said:**
> 
So I hope they might have solved the issue.... 


The reality is that it is still an issue.

---

### Post by brijith on 2009-11-02
> **puneet said:**
> 
BSNL does not get listed even now. Only RIM, and TATA get listed.
The reality is that it is still an issue.


Please see the attached image... 
It shows what I am getting when I booted 9.10 in virtual machine ...

---

### Post by digwashegde on 2009-11-05
i do have the same problem, pls check can any one help

---

### Post by vinaykumaruppalapati on 2009-11-05
Hello friends out of frestation i have deleted the auto mobile broadband connection in the network connections. I tried adding new wireless connection, however after entering all the details i.e user id and password i am getting the same problem, i am unable to connect to the net.
Can any on ther help me??????????????????
Its totally frustatin i have upgraded to 9.10 a weak agow and till now i am unable to connect to the net. foutunately i have windows as well.

---

### Post by brijith on 2009-11-06
Hai Guys,
Check thread [[COLOR="Blue"]Read me[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1314217"). In it rajesh1136 says that he could do connect to net by configuring wvdial. I think  we too can go for it until the bug get fixed ...
:p

---

### Post by eshant_engineer on 2009-11-14
For me also it is not working. WVDIAL is very old way to get connected in ubuntu. I had used it with ubuntu 8.04.

---

### Post by brijith on 2009-11-14
> **eshant_engineer said:**
> For me also it is not working. WVDIAL is very old way to get connected in ubuntu. I had used it with ubuntu 8.04.

Hai ,

Did you updated you Ubuntu recently....
There are lot of bug fixed coming these days....
Few days back some where in mailing list I came across a mail In that one guy says that ubuntu people fixed the bug in network manager and here after one can connect mobile broadband through network manager

So, What I suggest if update your Ubuntu and then give try ...

:D

---

### Post by icdileep on 2009-11-20
I'm also having the same problem with network manager applet in Ubuntu 9.10(released ver.) :(  Mine is BSNL NIC (Huawei EC325 USB modem). I tried update but the problem persist, Luckily I'm able to connect with wvdial :P  after downloading and copying wvdial files from another system.

---

### Post by shahesan on 2010-07-31
> **brijith said:**
> Hai ,

Did you updated you Ubuntu recently....
There are lot of bug fixed coming these days....
Few days back some where in mailing list I came across a mail In that one guy says that ubuntu people fixed the bug in network manager and here after one can connect mobile broadband through network manager

So, What I suggest if update your Ubuntu and then give try ...

:D

Friend,I am using Ubuntu 10.04 LTS.It detects BSNL EVDO modem (Huawei) easily.But after configuration,It doesn't Connects.. I really donno what to do.. I googled a Lot and tried out many WVDIAL methods.. But showing Modem Not responding.. Any suggestions ??:(

---

