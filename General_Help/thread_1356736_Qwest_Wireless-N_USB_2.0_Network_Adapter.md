---
title: "Qwest Wireless-N USB 2.0 Network Adapter"
date: 2009-12-16
forum: General Help
---

### Post by vinneeee on 2009-12-16
Do you guys know if this will work with ubuntu?

---

### Post by vinneeee on 2009-12-16
anyone?

---

### Post by njtuneguy on 2010-01-18
I have a similar (perhaps the same) adapter "Qwest 11n Wireless USB Adapter". The Model # on the adapter is "802AIN".

I've been searching for hours to see if there was perhaps an available driver download that could be inserted into Windows Wireless Drivers... to no avail.

The info I did discover is...

The driver is loaded automatically in Windows from the adapter itself. The actual manufaturer model is "Actiontec 802AIN Wireless N USB Network Adapter". The manufacturer part # is "HUU15090-01".
[http://www.actiontec.com/support/product_details.php?pid=196&typ=all](http://www.actiontec.com/support/product_details.php?pid=196&typ=all)

The windows driver details:
Provider: Atheros Communications, Inc.
Driver Version: 3.0.0.131
Driver Date: 9/23/2008
Firmware Revision: 01.09
Driver Name/Location: C:\WINDOWS\system32\drivers\WLANUHN
Driver File Description: Atheros Extensible Wireless LAN device driver
Driver File Internal Name: ARUSB_XP.SYS

I have no idea if any of that information will lead to a solution, BUT.....

Any help would be fantastic!! If not... I suppose it's my punishment for purchasing something I just KNEW wouldn't work outside of windows... Shame on me.

MAY THE GODS SMILE UPON US WITH AN ANSWER!!!! :)

---

### Post by bkratz on 2010-01-18
plug the device in and go to the terminal

Applications>>Accessories>>terminal

and type in 

lsusb
(that is LSUSB in lowercase) copy/paste the output back to this thread.

---

### Post by njtuneguy on 2010-01-18
Last night I performed the 'lsusb' as per instructions on this web page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

With this output for the device:

Bus 001 Device 002: ID 1668:1200 Actiontec Electronics, Inc. [hex]

But couldn't find a working driver (for chipset 1668:1200) on the ndiswrapper list. This was the closest matching chipset:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Actiontec_802UI3](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Actiontec_802UI3)

I know the adapter is backwards compatible from draft n to wireless b/g, maybe this driver will work at least for those standards?

Thanks for replying so quickly!! :))

---

### Post by supernovia on 2010-01-31
> **njtuneguy said:**
> 
I know the adapter is backwards compatible from draft n to wireless b/g, maybe this driver will work at least for those standards?


Were you able to get it working? I'm trying to install the same thing here.  I can see it in lsusb but not in iwconfig or ifconfig, and I'm really not sure where to go from there.

---

### Post by supernovia on 2010-02-01
hmm, mine when I do lsusb displays

0ace:20ff ZyDas -- and I understand that the most current driver for this one is built into the kernel.

We've both got the 802AIN though.

---

### Post by mizifih on 2012-04-24
I have the actiontec one, also 802AIN, cant make it work with ubuntu, any of you got it working?

---

### Post by sisco311 on 2012-04-24
> **mizifih said:**
> I have the actiontec one, also 802AIN, cant make it work with ubuntu, any of you got it working?

Please don't bump old threads. Start a new one with your question.

Thread Closed.

[[img]http://ompldr.org/tYzBtcQ[/img]](http://ompldr.org/vYzBtcQ)

:)

---

