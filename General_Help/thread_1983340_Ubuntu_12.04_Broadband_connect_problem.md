---
title: "Ubuntu 12.04 Broadband connect problem"
date: 2012-05-20
forum: General Help
---

### Post by Hawkeye25 on 2012-05-20
I have an AT&T Sierra Wireless USBConnect Momentum 313 4G modem and a brand new install of Ubuntu 12.04 on it's own HD. System is AMD 64 and works fine on Windows 7 on it's own HD. Cannot get Ubuntu to 'see', 'find', 'recognise', whatever, the Sierra modem. Any help would be greatly appreciated. I've had high hopes this version would finally free me from Windows, but to find such difficulty in what should be an almost automatic function, once again shakes my confidence in the integrity of this OS. I don't want to be a programmer - just a user. It should be simpler than this.

---

### Post by celldweller1591 on 2012-05-20
i think you should go through this link first - [https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)

---

### Post by Hawkeye25 on 2012-05-22
I live on a boat and travel around, trying not to stay in marinas. The ethernet modems I've found so far are for cable or DSL, landline broadband. I will keep looking, but really just want to find out how to alert Ubuntu 12.04 to the perfectly fine modem in the USB port.

---

### Post by Hawkeye25 on 2012-05-23
I keep watching and searching the discussion forums and have yet to see much of anything about this, except that it is difficult. The thing is, I can't see why it should be. USB is a standard system on all motherboards. Mice, keyboards, external hard drives, cameras, microphones, and on and on. Windows does it without so much as a hiccup, as does Mac. Why should it be increasingly difficult for Linux? It worked quickly and easily on my older Ubuntu. It's completely counterintuitive to accept it should be so difficult now as to be dismissed as unavailable.

---

### Post by servant74 on 2012-07-03
Bump

---

### Post by msammels on 2012-07-03
I'm not too familiar with mobile broadband dongles, but don't they need some software to connect to the internet? As far as I'm aware, this software logs them in with a username and password? Saying that... I could be wrong.

---

### Post by Hawkeye25 on 2012-07-04
The same modem does require a specific connection manager in Windows, but a typical malfunction in that system is the modem connecting on boot without the CM being initialized. It turns out the CM is essential for tracking and a degree of control, but not for connection, and it does not require a password or any of the security issues typical in the Linux CM.
 
In Ubuntu 10.04, all I ever had to do was complete the initial setup and the connection was always ready and quick to connect, plus a great deal faster and more stable than in Windows. I was sooooooo hopeful 12.04 was about to free me from Windows forever. What a disappointment. This is like a HUGE slide backwards and the promise of an effective alternative to Windows - most noteably in the highly mobile spectrum - has been somehow deliberately flushed away by the Ubuntu developers.
 
WiFi is too short a leash to be considered 'Mobile'. It is like being a train on tracks - you can NEVER step too far away from the narrow path where it is available. Cellular is infinitely more desirable for someone living on a boat, or motorhome, or traveling on a motorcycle, etc, etc. At this point, Ubuntu is removed from my system and I presently consider it unusable. It has to perform the functions I require or it is less than useless. All I'm asking is what EVERY other OS does quickly and easily - connect to the internet in what is now the fastest growing method available.
 
Ubuntu is now like having a Ferrari that MUST remain is your living room. You can sit in it and rev the engine, but never take it out for a drive.

---

### Post by haresear on 2012-07-04
I have a Pantech 3G broadband modem which is recognized by Ubuntu 12.04 same as earlier versions -- don't know why your 4G modem isn't recognized. Is your USB modem listed when you issue the 'lsusb' command in a terminal window? One thing I've noticed that is different in 12.04 is that I have to reenable 'mobile broadband' every time I reboot before my 3G modem connection is listed in the network manager.

---

### Post by Hawkeye25 on 2012-07-04
I've tried everything (two weeks worth of patient efforts, online research, forum searches, etc) and the system never 'saw' the modem. I went through the standard ADD procedure again and again, exhausting every possible combination of variables, without getting even the slightest glimmer of hope. I scoured the manufacturers websight for help with Linux connections and came up empty.
 
I began building my boat in 1986. Through thick and thin, severe illness and almost dying, hurricanes and financial devestation, I never gave up and it is almost completely finished. Through it all, I have been trying one version of Linux after another. I don't give up. I really don't, but for me to remove it from the system means something serious: I've tried everything ..... everything, and this one doesn't work.
 
People have concluded the problem lies in the USB connection and how Ubuntu manages them. Honestly, I don't know enough about THAT level of OS code construction to begin to understand why the physical method of plugging the device in should be a problem. I've been told to use an Ethernet connected modem or a LAN service. I've investigated both possibilities and found that another computer next to the one I'm working on is more accessory than I'm willing to build for an internet connection. And I simply can't find an Ethernet connected Cellular internet modem for under $500, so that option vaporized.
 
Thank you for your help. One day something will happen to change this situation and I'm hoping it will be in Ubuntu 13.04.

---

### Post by msammels on 2012-07-04
> **Hawkeye25 said:**
> Thank you for your help. One day something will happen to change this situation and I'm hoping it will be in Ubuntu 13.04.

Or, you know, Ubuntu 12.10 :P If you feel it is a bug, or something that needs to be addressed, why don't you submit it in Launchpad? :)

---

### Post by haresear on 2012-07-04
I've found that the network manager in LinuxMint 13 works like the earlier versions of Ubuntu - mobile broadband stays enabled, and the connect time is noticeably faster. Mint 13 uses the same kernel version as Ubuntu 12.04, and has many of the same Gnome3 apps (but not Unity).

---

### Post by Hawkeye25 on 2012-07-04
I don't think it is a bug. I think it is something bigger, perhaps a policy. There may be a problem with the sheer number of devices out there right now and a huge spread in the way these units are harnessed. If you try to handle them all and 2/3 are discontinued in 2 years, you've wasted a great deal of energy for no reason. Since this pathway to connection is growing so rapidly, it is possible some crucial elements will be standardized soon and a much smaller handle will be developed. I am patient, and I want to be here when Linux gets over the hump.

---

### Post by jasonditz on 2012-07-11
I'm having the same problem here on two different 12.04 systems. 

I had an older Sprint USB 3G modem that worked out of the box no questions asked forever in Ubuntu (last time I genuinely had to do anything with it was the Dell version of 8.04). My work switched to a AT&T business plan and gave me a USBConnect 4G. Works fine on a Mac (don't have any Windows systems) but its just not "there" in the Network Manager.

lsusb shows it as

Bus 001 Device 006: ID 0f3d:68aa Airprime, Incorporated 

Its a Sierra card and Sierra insists it works with Ubuntu 9.04 (though isn't officially supported) so long as you have the sierra drivers installed. It goes into excruciating detail on how to do that but Sierra drivers are installed by default on newer kernels. 

modinfo sierra and modinfo sierra_net both show v.2.0 installed properly but they're not seeing the thing.

---

### Post by Hawkeye25 on 2012-07-11
Thanks, Jason. It's good to be able to start narrowing it down to specifics. I like the 4G AT&T service a lot on my boat, and since I'm about to start a serious 2 or 3 year cruise (maybe much longer if I go South into the Caribbean) I just don't have the desire to wrestle with trying to shoehorn sideways a reluctant driver into an uninterested OS. I will keep watching the Ubuntu development and see if the issue is corrected in the future. As I have said before, simple Internet access is too easy and fundamental a facet of ANY OS to excuse its absence in something the developers rave about. It is a gun that won't shoot, a sled that can't slide, a wheel that doesn't roll. I don't care how pretty it is, how inexpensive it is, or how fast it is, if it doesn't do the simplest of jobs, it is a dismal failure.
 
I hope they fix it. Then I'll decide if I like the new GUI.

---

### Post by jasonditz on 2012-07-12
OK got it.

Turns out that while linux kernels ship with a Sierra driver, its a stupid sucky one (at least from our perspective). Here's the one we want (for Kernel 3.0 or higher) 

[http://www.sierrawireless.com/resources/support/drivers/linux/v3.2_1740_kernel-3.0.directIP.tar](http://www.sierrawireless.com/resources/support/drivers/linux/v3.2_1740_kernel-3.0.directIP.tar)

Unplug your USBConnect Momentum, tar, make, sudo make install, plug it back in, boom it shows up.

---

### Post by Hawkeye25 on 2012-07-12
Okay, great. This sounds promising. I will once again install a partition, format it and load Ubuntu 12.04. I've downloaded the v3.2_1740_kernal-3.0 driver and will carefully removed the offending one and try this. You've got my hopes up again. If I can FINALLY step away from Windows forever I will do the dance of joy and wear forever 'Unubtu Rules' T shirts.
 
Thanks again.

---

