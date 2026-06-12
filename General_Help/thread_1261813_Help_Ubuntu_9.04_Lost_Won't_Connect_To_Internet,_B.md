---
title: "Help: Ubuntu 9.04 Lost Won't Connect To Internet, But Google Can Search!"
date: 2009-09-09
forum: General Help
---

### Post by AlexanderDGreat on 2009-09-09
Hi, I'm so confused!

I'm using Ubuntu 9.04. I had a fresh install, then, updated my box via Synaptic.

Now, I'm surfing the internet, working as usual, etc...

Then I rebooted, all of a sudden my Ubuntu 9.04 LOSES Internet connectivity, I can't surf, I can't download in Synaptics, everything!

What's weird about this is, sometimes I go to Google and I can search, but when I click on the website it won't display the contents!

This happened to me 3 times already, so I also installed Ubuntu 3 times, it always does this.

What's happening? Help!

---

### Post by alienclone on 2009-09-09
well im not sure what is causing your internet connection loss, but i can explain the google search issue, when you lose your connection FF sets itself to "work offline" mode which will cause it to pull up cached pages from your computer, you are probably typing in a search phrase that you have used before.

---

### Post by AlexanderDGreat on 2009-09-09
Hi alienclone thanks for your quick reply.

Were you referring to cache?

Sorry, but I don't think that's it, I can CHECK EMAIL!

I can basically access every service Google has, but not Yahoo, not my website, not my twitter, not ubuntuforums.org, nothing...

Also, I've tried switching browsers I installed Opera 10 and same result!

It's soooooo weird.

It's frustrating. Is this a virus?

On a lighter side, I hope it is, and it will be named after me! =)

---

### Post by credobyte on 2009-09-09
Show us the output of:
```
ifconfig
```

---

### Post by AlexanderDGreat on 2009-09-09
art@lgv:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:b8:e7:e1  
          inet addr:192.168.2.50  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feb8:e7e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:824 (824.0 B)  TX bytes:6794 (6.7 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4996 (4.9 KB)  TX bytes:4996 (4.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:10:6e:b8:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-10-6E-B8-59-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by t0p on 2009-09-09
OP: stop reinstalling ubuntu!  It didn't help the first time, what made you think the second reinstallation would fix the problem?  Or the third?

Oh, and no, it is *not* a virus.  But if it were a virus, it wouldn't be named after you.  Catching a virus is not a noteworthy achievement, even if it's a non-existent virus.

---

### Post by AlexanderDGreat on 2009-09-09
Actually, I estimate it would be about 30 hours of Ubuntu-use before I lose this internet connectivity again, so I will format Ubuntu.

Quite the contrary, it really does get fixed after I format, that's why I did it 3 times already.

But now I've decided to get your comments, the experts, thanks a lot.

So do you have any ideas what's causing this thing?

---

### Post by AlexanderDGreat on 2009-09-09
Anyone else have the same problem?

Or am I forced to reformat my Ubuntu again?

Thanks.

---

### Post by hawthornso23 on 2009-09-10
How do you connect to the internet? Have you been putting stuff in your hosts file?

You say this happens regularly. Next time it happens DONT immediately reinstall.
Run some tests. Save the output. Work the problem. If you immediately reinstall
at the first sign of trouble you wont ever be able to figure out what the problem is.
Nor will the people here be able to help you much. Running tests like ifconfig isn't
going to tell us much if the problem isn't there when you run it because you reinstalled.

---

### Post by QIII on 2009-09-10
Rule out hardware problems methodically.  The periodicity makes me suspect hardware rather than the OS.  Components get hot and have just enough time to cool off while you are grousing and grumbling as you rummage through your desk drawers for your LiveCD.  Conversely, they may have time to heat up and work while you are installing.  Modern electronic components that fitfully work only when hot or cold are problematic.

Start at your modem.  Call your ISP (and hope they won't charge you) and ask them to remotely troubleshoot it.  You may need to unplug it and recycle.

If you have a router, check all the cable connections.  You may need to unplug it and recycle.  Take the router out of the loop and connect directly to your modem and see what happens.

Check behind your machine.  Check all the cables.  Dogs (and munchkins) like to hunt for their tennis balls under your desk (the munchkins like to investigate important stuff like the neat-o cable thingies next to the cool blinking green lights).

If your NIC came with some diagnostic software, run it.  Unplug your machine, open the case and see if the card is hot.  Get a can of compressed A.I.R. and blow out all the dust bunnies.  Check to see that the card is properly seated.  If your NIC is integrated, check your motherboard for swollen or burned components.  Give it a sniff and see if it smells smoky.

Periodicity is often hardware.

If you find nothing, edit your connection and try something like using OpenDNS as your DNS server.  If your email is through your ISP, the URL will almost certainly be resolved so your mail will work.  If you are depending on your ISP for DNS resolution, they may not be keeping up or they may have a small database.  You may be getting poor DNS resolution there.  Do you think they really give two flying farts about some backwater URLs like the Ubuntu repositories when they have more important things like porn sites to keep track of?

---

### Post by AlexanderDGreat on 2009-09-10
Hi, AN UPDATE:

1. I can't access Shared Folders in my other Ubuntu 9.04 HP Pavilion DV2000 Series Laptop, but MAC OS X laptop, 2 other Windows XP computers can access shared folders on same HP laptop, only this (no-internet-connection) Ubuntu OS can't.

2. I can search for websites, keywords, phrases in Google, but only titles of websites and icons show up, it hangs forever and won't load.

Other info:

My (no-internet-connection) Ubuntu 9.04 is dual boot with WinXP. WinXP has full internet connectivity, so I don't think it's a hardware problem.

Finally, when I install only Ubuntu on this machine, this doesn't happen, I don't lose internet connection. Right now, I'm dual boot with WinXp.


*****

@hawthornso23
Yeah, I save the output, that's why I still don't have internet connection. The reason I reformatted the 1st and 2nd time is because I didn't ask here, now, I'm asking so I still don't have internet, I'm using my laptop to access this forum. 

@QIII
Hey thanks for your long answer, I read them, and believe me I've done all those physical checks. I use LAN DSL cable for my internet.

However, you have an excellent idea about my ISP thinkering with my connection.

I would like to take this track, because it's really weird, my brother can play online games in our 2nd boot WinXp, this Ubuntu computer is dual boot with WinXP.

---

### Post by AlexanderDGreat on 2009-09-10
By the way thanks guys for suffering with me. =)

I used OpenDNS and still nothing.

Also, I can access a shared folder on a computer via, smb://192.168.2.20 and I will see folders there, but when I click, contents won't display.

It's the same with websites, I can use type IP addresses, but contents of webpages won't display.

---

### Post by AlexanderDGreat on 2009-09-10
Google searches, website is clickable...

BUT website WON'T DISPLAY!

I've tried, 20 websites!!!

I attached a picture of what I'm talking about...

Notice the YouTube title...

---

### Post by AlexanderDGreat on 2009-09-10
HEEEEEEEEEEYYYYYYYYY FOLKS!

Got my Internet Connection back.

Here's what I did.

I disconnected my LAN cable to my Ethernet Port.

I used a Wifi card instead. Now, everything works fine!

I hope my stupidity will help someone else in the future.

---

### Post by QIII on 2009-09-10
I'm glad you got it back, but it really might be helpful to the rest of the community if you could keep working on the wired issue.

If you mentioned the dual boot, I'm sorry I missed it.  I wouldn't have said anything about the hardware checks.

And if you are able to use the internet on a different machine, the ISP/DNS resolution questions aren't an issue.

There may be an issue with how Ubuntu interacts with your NIC (integrated or not) that might be of interest to others.

What make and model is that?

Your wired issues could be as simple as packet size and resetting the MTU value by editing your wired connection...

It would be helpful to all of us for future reference if you could keep plugging at this one.

---

### Post by AlexanderDGreat on 2009-09-10
Hi I'm using my motherboard ASUS P5S-MX SE LAN

lspci
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

I really don't know how to fix this. I'm sorry...

I tried searching for an updated SiS 191 ethernet driver for Ubuntu, but there aren't any precompiled ones, and compiling is not the sexiest thing I know in Ubuntu.

---

### Post by QIII on 2009-09-10
Found this

[https://bugs.launchpad.net/ubuntu/+bug/345374](https://bugs.launchpad.net/ubuntu/+bug/345374)

Try editing your connection and set the MTU to 1492

---

### Post by AlexanderDGreat on 2009-09-10
@QIII

Hey man, you got my eth0 WORKING!

I simply set my MTU to 1492 and that's it!

I don't even need the wifi now.

Yes I read your link.

Here's my uname -a

Linux lgv 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

You rock. Thanks for your time. Just tell me what to do next to give back to the community. Appreciate your help.

PS By the way, what does MTU mean?

---

### Post by QIII on 2009-09-10
Maximum Transmission Unit

You can give back to the community by leaving a brand new 2010 Harley Davidson Road King Classic (Vivid Black preferred) by my desk.  Please remember to include a self-tuning Thunder-Max EFI unit.

Or...

Go back to your original post and edit the title and place "SOLVED" in front of it.

---

### Post by AlexanderDGreat on 2009-09-10
Hahaha. =)

Thanks man, keep up your good work!

---

### Post by TSilvo on 2012-12-05
i try set MTU to 1492, but still not working.

"uname -r"

3.2.0-34-generic-pae



but i find problem on autonegotiation - off

install ethtool

"sudo apt-get install ethtool"

information

"sudo ethtool eth0"

change autonegotiation to on

"sudo ethtool -s eth0 autoneg on"

now eth0 working fine.

---

### Post by oldos2er on 2012-12-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

