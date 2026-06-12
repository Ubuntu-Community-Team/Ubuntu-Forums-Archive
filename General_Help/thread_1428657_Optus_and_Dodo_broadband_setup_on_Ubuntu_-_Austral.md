---
title: "Optus and Dodo broadband setup on Ubuntu - Australia"
date: 2010-03-13
forum: General Help
---

### Post by marshmugger on 2010-03-13
There are many posts about setting up wireless broadband on Ubuntu. Personally, I have had no major problems.

I have an Acer Aspire One A110. I was running Ubuntu Netbook Remix 9.04 Jaunty Jackalope until March 2010 and then upgraded to UNR 9.10 Karmic Koala. I've been using 3G wireless internet, here in Australia, first with Dodo and now with Optus. 

Dodo setup
Dodo uses the Optus network.
The modem I have used is a Huawei E169E HSDPA USB Stick (aka "dongle").
For a contract plan, my settings are:
    Number: *99#
    APN: dodolns1
    Authentication: CHAP
    DNS servers: 202.136.43.197, 202.136.42.229
    All other settings are default and/or blank.

Optus setup (prepaid)
The modem I now use is a Huawei E160E.
For a prepaid plan, my settings are:
    Number: *99#
    APN: preconnect
    Authentication: EAP, CHAP, MSCHAPv2 (it's working like this)
    DNS servers: 8.8.8.8, 8.8.4.4
    All other settings are default and/or blank.

I have installed UNR 9.10 (fresh install) and then setup my wireless fraudband as follows:
    Plug in dongle (some say that it needs to be plugged in when you boot).
    Open System\Network Connections.
    Select Mobile Broadband tab, Add new connection.
    Select Optus and then review and change the settings as required.
    Click the network connections launcher at the top of the screen and select Optus to connect.

The most frequent problem I have experienced is DNS servers. I can connect to the wireless network but no pages would load. The Automatic PPP IPv4 setting rarely works for me and I prefer to set the DNS servers manually:

    Dodo 202.136.43.197, 202.136.42.229
    Optus 192.65.90.202, 202.139.83.3 (maybe out of date?)
    Google 8.8.8.8, 8.8.4.4 (works for any internet service provider)

More tips:

For a better signal and more stable connection (but not necessarily faster), I use a 5 metre USB extension and hang the dongle in a window facing the Optus tower (basic extension will do, you don't need the fancy one with a repeater).

Sometimes, the modem is not recognized when plugged in (not in the Network Connections) launcher. Be patient, wait a bit, then unplug it and try again. It should be OK the second time.

Stephen.

---

### Post by Sharks15 on 2010-03-13
Hi Stephen

I've read your post and I agree with you.  I've replaced Windows XP with Ubuntu and I don't regret making that decision.  Although, I'm still new to the new system I'm happy with the overall performance of the system thusfar.

---

### Post by 3rdalbum on 2010-03-13
> **marshmugger said:**
> 

The most frequent problem I have experienced is DNS servers. I can connect to the wireless network but no pages would load.

Common problem in 9.10, fixed in 10.04. If you can't wait for 10.04 to be released, you can download the daily build and install it on your netbook.

---

