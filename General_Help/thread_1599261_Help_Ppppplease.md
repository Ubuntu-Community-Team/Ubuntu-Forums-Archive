---
title: "Help Ppppplease"
date: 2010-10-17
forum: General Help
---

### Post by PatK100 on 2010-10-17
Soory but I dont know a lot about Ubuntu expect I have two computers one running Karmic and one running Luicd, all I use them for is file server since they are so bloody stable.
 
Now I need to broaden my horizons, I need to install some web control to stop my fast growing step son from looking at porn and control his internet usage so he can not browse when he should be asleep or doing homework.
 
I have been given a web control virtual server appliance called smoothwall which I believe will fit the needs admirably.
 
My problem is I now need to know how to install either VMware Server or workstaion on either Karmic or Lucid.
 
Whilst I am very familiar with both products under Windows or an ESX environment I know nothing of installing under Ubuntu.
 
I have downloaed the   VMware-server-2.0.1-156745.i386.tar file.
 
Could some kind person give me step by step instructions for a Ubuntu dummy on how to install either VMWare Server from the above file or indeed if its easier can someone please help me how to install VMWare Player on Ubuntu.
 
Thanking you in anticipation of your help.
 
 
 
Pat

---

### Post by efflandt on 2010-10-17
Instead of VM, do you have any old computer that you think is obsolete?  I recently installed IPCop with squid proxy on an old K6-2/400 w/128 MB RAM and it works fine only using 30 watts headless (no monitor or keyboard once installed).  I did that as backup for our office in case there is some issue with the factory network or proxy that we are supposed to use through VPN (after we were without internet access for a full day).

I have not set any restrictions on it, but it logs URL's of all sites accessed through squid.  It does have settings for blocking sites, or optional subscription for a list of sites to automatically block.  I looked at Smoothwall, but they want you to join to get their Administrator Guide.  So I just used IPCop, which does what I need to do on very old hardware.

---

### Post by migs73 on 2010-10-17
Try looking here;

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by bakegoodz on 2010-10-17
Unlike the other I'll try to answer the specific question you asked.
Look at this guide
[http://www.howtoforge.net/vmware-server-2.0.2-x-on-ubuntu-server-10.04-with-vmware-remote-console-plug-in](http://www.howtoforge.net/vmware-server-2.0.2-x-on-ubuntu-server-10.04-with-vmware-remote-console-plug-in)

The first step is for setting a static IP, so if you don't need that you can start on Step 2, though you will need gcc installed. If it were me I would just install basic compile package (includes gcc) and make sure you have kernel headers with this command: apt-get install build-essential linux-headers-generic

---

### Post by matt_symes on 2010-10-17
Hi 

[http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04)

Hopefully this will help. Step by step instructions.

Kind regards

---

### Post by PatK100 on 2010-10-17
thanks guys Iwill give this a go tomorrow

---

