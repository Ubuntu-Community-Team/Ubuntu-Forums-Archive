---
title: "Ubuntu connects to the internet in virtual box but does not on livecd"
date: 2011-10-05
forum: General Help
---

### Post by Snowboi on 2011-10-05
Hello everyone
today i need a little bit of help

Here are my specifications

Thinkpad t520 (standard)
running windows 7 enterprise
planning on installing ubuntu 10.04.3 (full not wubi)
i5 vpro (could have to do with this 'secure' processor)

Whenever i boot off the liveCD it does not connect to internet wired or wireless, it only connects when it is running off a virtual machine

This is a university laptop i have been given i called the IT department (derp-artment) and they told me i can install an alternative OS but they did not know how to help me...

Thanks.
(i do have the drivers for the virtual machine installed, maybe windows has some kind of hardware or software block)

---

### Post by 3Miro on 2011-10-05
[http://slacy.com/blog/2011/08/thinkpad-t520-wireless-drivers-for-ubuntu-11-04/](http://slacy.com/blog/2011/08/thinkpad-t520-wireless-drivers-for-ubuntu-11-04/)

It may be the case that the wired and wireless don't have proper drivers for 10.04, which came out quite some time ago. Try 11.04, you should be able to get at least wired connection on it.

Unfortunately, if there are no drivers for the network, then there are no drivers for the network.

---

### Post by Snowboi on 2011-10-05
> **3Miro said:**
> [http://slacy.com/blog/2011/08/thinkpad-t520-wireless-drivers-for-ubuntu-11-04/](http://slacy.com/blog/2011/08/thinkpad-t520-wireless-drivers-for-ubuntu-11-04/)

It may be the case that the wired and wireless don't have proper drivers for 10.04, which came out quite some time ago. Try 11.04, you should be able to get at least wired connection on it.

Unfortunately, if there are no drivers for the network, then there are no drivers for the network.

There should be drivers

[http://www.ubuntu.com/certification/hardware/201102-7229](http://www.ubuntu.com/certification/hardware/201102-7229)

(Its 10.04.3 which is preety new tho :S)

any other options i don't like 11.04 or 10.10

---

### Post by 3Miro on 2011-10-05
> **Snowboi said:**
> There should be drivers

[http://www.ubuntu.com/certification/hardware/201102-7229](http://www.ubuntu.com/certification/hardware/201102-7229)

(Its 10.04.3 which is preety new tho :S)

any other options i don't like 11.04 or 10.10

Check on the right side of the page, only 11.04 is certified, 10.10 works only if it is pre-installed and with notes.

This laptop has a Sandy Bridge processor and those came out after 10.04 was released, a year and a half is a long time in the computer world. If the network cards did not exist before 10.04 was released, then 10.04 will not have the proper drivers.

When it comes to the different versions of Ubuntu, truth of the matter is that 10.04, 10.10 and 11.04 are not that different (use 11.04 in Classic mode).

---

### Post by Snowboi on 2011-10-05
> **3Miro said:**
> Check on the right side of the page, only 11.04 is certified, 10.10 works only if it is pre-installed and with notes.

This laptop has a Sandy Bridge processor and those came out after 10.04 was released, a year and a half is a long time in the computer world. If the network cards did not exist before 10.04 was released, then 10.04 will not have the proper drivers.

When it comes to the different versions of Ubuntu, truth of the matter is that 10.04, 10.10 and 11.04 are not that different (use 11.04 in Classic mode).

alright ill download and post the results in case anyone else has these issues :)

ill try 11.04 classic mode.
(or wait for 11.10

---

