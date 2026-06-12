---
title: "Huawei Mobile Partner HELP..."
date: 2010-03-27
forum: General Help
---

### Post by thanuja on 2010-03-27
Hi all, 
im totally new to linux..I need to connect to internet using a mobile partner device..It is Huwaei model E220. How do I run this device in ubunu??

Thanks a lot

---

### Post by redbook4574 on 2010-03-27
You don't say which version of ubuntu you are running so I will assume Karmic.

It is very simple, Just plug in the E220, go to network manager and set up your provider.

---

### Post by linux_new on 2010-03-27
Welcome to Linux.

I am using the same modem, What version of Ubuntu have you installed?  

If you are lucky and installed 9.10 then go to system--->preferences--->network connection

Go to mobile broadband tab and ---> ADD. Follow the instruction from there.

---

### Post by thanuja on 2010-03-27
thanks a lot people it helped a lot. Its 9.1. I followed ur instructions and did upto Network connections part. But how do I run it. I mean I still cant get connected to internet.

Pls help me with this..
Thanks again

---

### Post by thanuja on 2010-03-27
Its saying that a zip file is missing... How do i get it..

---

### Post by 3rdalbum on 2010-03-27
> **thanuja said:**
> Its saying that a zip file is missing... How do i get it..

You're going to have to be more specific than that - what is giving you this message? And what is the exact message?

The E220 should be supported out-of-the-box on Ubuntu since 8.10.  Once you have set up the mobile broadband stick using the Network Manager applet, you should be able to connect. You don't run the software that is on the stick, or on a CD provided with the stick; just run the Network Manager wizard and connect.

---

### Post by PorkyPie on 2010-03-27
Hi. You should see an applet at the top right corner of your screen, beside your username, that looks like two plugs plugged together. Right click it and click "Edit Connections" (I think). Go to Mobile Broadband, click add and follow the steps. Now, close that window and click on the two plugs again. You should see your connection under Mobile Broadband or similar. Click the connection, and it should connect with no problem.

You can also change a few things, like if you right click the two plugs and click "Edit Connections" and click edit on the E220 connection, you can tick the box "Connect Automatically". This will make it connect automatically each time it starts.

I wrote this based on memory (I now have Windows 7 installed :() so I am sorry if this doesn't work for you.

---

### Post by thanuja on 2010-03-27
Nw i have setup the mobile partner using Network connections. I have plugged the device into USB port. Does it automatically gets connected or, do I have to do something else?

---

### Post by 3rdalbum on 2010-03-27
> **thanuja said:**
> Nw i have setup the mobile partner using Network connections. I have plugged the device into USB port. Does it automatically gets connected or, do I have to do something else?

Left-click the Network Manager applet and select your mobile broadband account from the menu, and it will connect.

---

### Post by thanuja on 2010-03-27
Thanks..excuse me for my lack of knowledge in linux.. i just installed it... is network manager applet means the same thing as 'Network connections' where i went from System->Preferences. But this doesnt allow me to right click.!!!!

---

### Post by thanuja on 2010-03-27
got it... but it says device not ready.. bt the device is working fine in windows.. do i need to install anything else..or configure anything???

---

### Post by 3rdalbum on 2010-03-27
Unplug it and plug it back in, give it a few moments as well to become ready.

---

### Post by bigseb on 2010-03-27
I have/had similar issues. Its quite simple though. Just plug it in and after half a minute or so it should be ready. No software or anything need be installed.

Sometimes when I connect (and it tells me I'm connected) the browser tells me it cannot find whatever server... Then I just disconnect and try again, sometimes 5 or 6 times. Sucks but ultimately it gets there...

---

### Post by 3rdalbum on 2010-03-27
> **bigseb said:**
> I have/had similar issues. Its quite simple though. Just plug it in and after half a minute or so it should be ready. No software or anything need be installed.

Sometimes when I connect (and it tells me I'm connected) the browser tells me it cannot find whatever server... Then I just disconnect and try again, sometimes 5 or 6 times. Sucks but ultimately it gets there...

I sometimes forget that it does that on Karmic. I'm using Lucid, where the problem has been fixed.

---

### Post by jalirious on 2010-03-27
On karmic before the network manager took care of it there was this fix:

[http://ubuntuforums.org/showthread.php?t=1395685](http://ubuntuforums.org/showthread.php?t=1395685)

Which provides a stable connection on the occasions that the (now standard automatic) method fails. You may want to try that.

---

### Post by bumanie on 2010-03-27
I have not been able to get 3G modem working in ubuntu since version 9.04 - works in 9.04, but not 9.10 or 10.04 Beta 1 - at least I have not been able to get it to work in them. I thus reverted my laptop back to 9.04 - very easy connection. 
9.10 etc. sees it as a read only device. I believe a kernel update to do with usb has caused the problem. I am yet to find a solution that works, thus I am back on 9.04. Some people have been successful with [mode switch]("http://www.draisberghof.de/usb_modeswitch/"), but it didn't work for me. Some have used gnome-ppp and wvdial to get 3g modems working - I didn't try them and chose to revert to 9.04 instead.

---

### Post by jalirious on 2010-03-28
Try this if you didn't manage with modeswitch 

[http://sakis.tel4u.gr/blog/sakis3g/](http://sakis.tel4u.gr/blog/sakis3g/)

---

### Post by senior_moments on 2010-03-29
I am running Karmic 9.10 and have tried installing an E220. Have followed the steps above but have been unable to persuade my system to see the modem. More stupidly, I have managed to revoke all privileges from the Network Connections applet. As an old UNIX hand I really miss the simple cli ... at least SMIT on AIX told you what cli commands it was running - is there an option to tell Ubuntu to do the same?
1. How do I re-establish privileges on the Network Connections applet?
2. My system seems unable to see the modem; I have 4 USB slots, lsusb gives:
    
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3. Have followed setup advice and am sure it is set as others have claimed to have it working. Cannot see an option to make Mobile Broadband the default connection - no right click available in Network Connections.

Have listed these in priority order. Any help and assistance would be greatly appreciated.

---

### Post by jalirious on 2010-03-31
Have you tried wvdial? You wont need to modeswitch the e220. Had one running fine in karmic a few months back. wvdial is independent of network-manager. If I could help with the rest I would.

---

### Post by sabitha on 2012-01-03
maybe you want try this
[http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html](http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html)
its like windows version but run on ubuntu

---

