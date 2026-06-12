---
title: "Wireless router configuration page not showing all devices on LAN"
date: 2010-02-01
forum: General Help
---

### Post by ram2500 on 2010-02-01
Hi there,

I posted previously with concerns of my wireless router being hacked (see post [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1385445](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1385445) for more information) - Anyhow, family came over to visit and my nephew had an iPhone. She wanted to check something on the Internet, and I gave her the password to my router. She couldn't get in, so I opened my router configuration page to see what was the matter to reset it. (But that's another matter: she typed it in wrong :)). I went to see if the iPhone was connected and it wasn't listed--**and she was now on my wireless network, on the Internet**. For the past month, I have experienced slow Internet (the Qwest people came over three times to fix the problem, to no avail.) And, when my laptop and desktop are turned off, the modem still shows activity, as if someone was downloading large files. Qwest insists that my network is secure and no one is using my network (and my house was built in 1997, so the wiring is fairly new and I have had NO issues with Internet/phone and had Qwest service longer than I can remember).

To make a long story short, I am concerned that my router has been hacked. I live in a rural area, so there's no teenagers or weird-o's around that I know of that would do that (unlike city/suburban areas)--and my Linksys router is "lying" to me, as my nephew was ON MY NETWORK and the SSID, MAC address and IP number was not listed on the LAN device list--only my laptop/desktop are listed, and she was happily checking emails on my network. I have changed my WPA2 password three times just in case, no fix. I think something is wrong.

---

### Post by Tourdog on 2010-02-01
It is my contention that nobody in a rural area is likely (for what reason) to "hack" your wifi.  WEP and better your WPA2 is going to encrypt and is simply not hackable.  You know the signal strength of these modems is very small.......................  good for a hundred yards plus the house where it resides. 

You say that phone is on your wifi.....................  ieee 802.11g  at 2.4 ghertz is not a normal phone band.   Do you think maybe that phone was actually data linked to the nearest cell tower......................  the phone owner is paying for a "data plan" right?

Look at that phone (do the same for your router) and google its mfg # and see if it includes a 802.11abgn adapter ie wifi capable.   And, see if it (phone and your router) is a dual channel ie capable of simultaneously transceiving on 2 channels between 1 and 11.  If it is capable then your "other" channel is "open" and not secure.  Lottsa "ifs" here which is why I think she was actually on a "cell" not your "wifi".

hth !!!

---

### Post by ram2500 on 2010-02-01
I don't have the Qwest wireless router adapter (although my modem can have one)--I have a Linksys Wireless 802.11g router. The problem is, my niece was on the Internet connected to my Wi-Fi but her iPhone did not show up on the Device table of my router. Something is wrong here, I think. And, add to the fact that my Internet feels like dial-up at times--and my Qwest modem's Internet and Ethernet lights blink rapidly even when my machines are off. When my machines are on, they are the only devices showing up on the router, and the Internet is still slow, and the lights still blink rapidly as if I was downloading a large file, even though I am doing something "light", i.e. reading the news or checking my e-mail. Qwest has been trying hard to fix the problem--I've even recieved a new modem--but it's the same thing. Aside from that, all devices should show on the Device table of a router! My niece's iPhone did not show up...so, I figure if the router was hacked, the hacker would do something to the effect of disabling the logging of devices of the router so that he/she could cover their tracks, and even though my 12-year old niece is no hacker, I think that any other device will not show for this reason.

My niece was on my network--on the phone, it had my SSID. However, no proof of her connecting on my router.

---

### Post by ram2500 on 2010-02-02
I think I am going to give up the ability to go on the Internet/network from the kitchen table/couch...I am going to unplug the bloody thing, put it away and just use my desktop with the physical Ethernet connection and see if the problem persists. I doubt it will, since there's no Wi-Fi to hack. :p If it persists, then it's an ISP problem. My Internet is very slow, and the lights are blinking rapidly as if I was downloading a HUGE file or files. 

That will take care of the worries of being hacked. Every so often, I read of innocent grandmothers being brought in for downloading copyrighted/illegal content because their Wi-Fi wasn't secure, and the fact that the terms of service forbid intentionally or unintentionally sharing an Internet connection. I trust and know my neighbors well, the few that I have, but I have heard of wardriving and anyone can just hop in a car and go to any neighborhood and hack a network. It's ridiculous, and I think I am going to report this issue to the police if it's not an ISP problem.

It's inconvenient being tethered to the modem to check emails or catch up on the news, but it's really inconvenient to have a hacked network. This is ridiculous, and has been persisting for weeks now. 

I think I will just buy a new router and see if that remediates the problem. If it doesn't then I'll get my $80 back :). Any other ideas before I do this?

---

### Post by Tourdog on 2010-02-02
I guessing you receive "broadband" via a dsl not cable?

Your nearest neighbor is > than 100 yards?

You are wifi connected 802.11g to your router/gateway that is cat 5 hardwired connected via dsl and is encrypted wpa2?

And, nothing identifying that phone (now carrying your password/ network name etc) came up when you [http://login...........your](http://login...........your) linksys router.....  

Do I have it right?

---

### Post by ram2500 on 2010-02-02
My nearest neighbor lives 1/4 miles away. They are a nice elderly couple in their eighties. 

My Internet is DSL, and my router is connected w/ Cat 5 cable, and is secured with WPA2-PSK with AES encryption. 

No other device except HPLAPTOP (my notebook) is on the list. When my niece was over at the house over the weekend, only HPLAPTOP showed, not the iPhone. However, she was on my network, which leads me to believe that someone hacked the router to only show my devices (names: HPLAPTOP and mischdsktp respectively) and nothing else so that if the hacker connects, nothing else will show up. My work laptop does list on my router, only because I bring it home frequently. So, my hypothesis is that the hacker is trying to trick me into believing that I have no other device connected other than my own.

My house sits probably 200-300 feet from the road, and from the road, my house is not visible because of the trees. The router is only an 802.11g model, which doesn't have too much span of wireless signal. This is very odd, is all I can say.

---

### Post by Tourdog on 2010-02-02
If in the remote remote manner that someone is on your wifi...................  you might download a simple little program called "vnstat"  I got it from Ubuntu software.  It can give hourly readings of your usage in kilobytes/ megabytes/ etc.  It will report hourly and/or daily Q's.  You would at least have something to argue with Qwest.  Ubuntu comes with the capability to report (realtime) graphic but thats like reading voltage...........  you need wattage ie megabytes of (your) usage and vnstat will do that.   

If you know someone who could bring over their laptop to your place and just check to see the Linksys shows them on line plus your laptop too.

One great problem we all face..................  is the loony phone companies and cable too are advertising streaming video/ audio and all are HUGE bandwidth hogs.  We all suffer slowdowns and wait..... wait .... for web pages to come up.   We are also in a rural area and get our broadband via radio link from atop a silo 2 section miles away.  There are 30 of us on that AP.   Darn it!   I know when someone is downloading a high def HD movie with 5.1 sound!     Don't give up!

---

### Post by ram2500 on 2010-02-02
Thank you for the advice and the help, I will definitely try it. I am getting sleepy-eyed, so I am just going to unplug the modem and the router tonight lest my machines are turned on remotely and wipe their disks by themselves. :D

I think I am going to buy the router to see if that remediates the problem--if not, then I'll return it and have Qwest come out again. My Linksys is two years old--out of warranty--so if the firmware was hacked, it's not their responsibility. 

Good night and take care.

---

### Post by efflandt on 2010-02-02
Script kiddies, worms, or others looking for vulnerabilities port scan constantly, so it is not unusual to see internet activity even when you have no computers on.  And any Windows box and other devices like network printers (or samba in Linux) regularly do netbios broadcasts to find other devices.

I run a test webserver on my DSL (using no-ip.com dynamic DNS).   And web worms jammed my logs so much that I configured a default virtual host with a 1 page dead end, logged separately, if the Host header was not a recognized virtual host.

Have you looked through your router logs?  To conserve battery power, it is possible that the iPhone only connects while necessary, and then disconnects.

My 2Wire DSL wireless/modem/router lists all wired or wireless devices that have connected since it was last reset (with unconnected devices grayed out).  But not sure if your Linksys router does that (might only show actively connected devices).

---

### Post by bakegoodz on 2010-02-02
Maybe your nephew's iphone never joined and it was using a cell connection when he was on the web. The activity light can be going for other reasons. I don't know if you have ruled out spyware if you have one or more Windows computers, there some really tricky ones that can allude detection for weeks, until your security software provider catches up and updates for it.

---

### Post by ram2500 on 2010-02-02
It did show that she was using my wireless network--my router's SSID appeared and was used by her iPhone. No spyware/virus on the Windows 7 partition...this is a router or modem problem. I brought my laptop to work--the Internet runs fine both in Windows and Ubuntu--but it's terribly slow at home. I don't watch television, so needless to say, I didn't bother getting this morning's news until I arrived at work.

I am going to try using a new router--before I get home this evening, I am going to pick a new one up. First thing when it's out of the box--secure it, of course;). And if the same thing happens, why then I'll just have Qwest over again. 

I'll report my findings this evening.

---

### Post by ram2500 on 2010-02-02
I bought the new router (Belkin Wireless N), enabled WPA2-PSK with AES encryption and MAC address filtering. The Internet is much faster now, and the laptop that I brought home from work (not my work laptop but just an extra one laying around) did show up on the client list on the new router. Interestingly, the laptop connected but did not show up on my old router. The modem lights are not flickering--only if I am on the computer. Either the old router fried itself or someone hacked it--even after changing the password, resetting it, unplugging it, the Internet was very slow, the modem was blinking even when my machines were off (not once in a while, but consistently for 10-30 minutes or more), and so I replaced it. The new router and my Internet runs like a top, so I'll just put the old one in the junk bin. Thanks for all your help!

---

