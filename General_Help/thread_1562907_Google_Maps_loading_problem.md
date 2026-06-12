---
title: "Google Maps loading problem"
date: 2010-08-28
forum: General Help
---

### Post by rossolimo on 2010-08-28
Hi everyone,

My first post here, so please bear with me :). I've been using Ubuntu for some time now. I recently upgraded to 10.04 and since then I've been having problems with certain sites. Slashdot, Google and others (even Firefox default home page in Ubuntu) take a long time to load, if at all (sometimes I have to refresh for them to display correctly). Google Maps in particular won't work. Sometimes (but only sometimes) it will start loading and hang there showing a message to the effect that the connection is slow and suggesting alternative methods to load the page. When I click on the link it doesn't load the help page. Gmail works only occasionally and with difficulty. To put it simply, browsing is no joy, or is simply impossible.

I've tried accessing these pages in several browsers (Firefox, Chrome, Midori, even Epiphany) all with the same result. I don't have any problems with other computers in my network using the same OS (live CD on a Sony VAIO and Netbook Remix on an Asus Eee PC 701). I've had a look around in the forums and tried to see whether changing the DNS to Google's -4.4.4.4 and 8.8.8.8- would help. I've also had a look at Flash and Java fixes, but all to no avail. I've even tried different live distros to see whether the problem is unique to my fresh install of Ubuntu 10.04 (I've never had any problems of this kind with previous versions, and 9.10 was working fine). Here are the results: Ubuntu, Kubuntu (both Konqueror and Firefox), Xubuntu 10.04 and Linux Mint 9 show the same problem (not surprisingly, since Mint 9 is based on Ubuntu 10.04). OpenSuse 11.3 (both Gnome and KDE versions) and Fedora 13 work fine.

Here are the details of my laptop (Amilo Pa1510) taken with the Hardinfo program:

-Computer- 
Processor: 2x AMD Turion(tm) 64 X2 Mobile Technology TL-50 
Memory: 1930MB 
Operating System: Ubuntu 10.04.1 LTS 

-Version- 
Kernel: Linux 2.6.32-24-generic (i686) 
Compiled: #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 
C Library: GNU C Library version 2.11.1 (stable) 
Default C Compiler: GNU C Compiler version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
Distribution: Ubuntu 10.04.1 LTS 
Desktop Environment: GNOME 2.30.2 

This is very frustrating :( because I was very happy with the rest of the system. Ubuntu 10.04 is the best version I've used :D, but not being able to browse the Web is a no-no. Any help or suggestions would be much appreciated.

(On a perhaps related note, when I tried to restore my mail folder and settings from my previous install -9.10- my Gmail account wouldn't work, Evolution saying that it could not reach Gmail's servers. Does anyone know whether there is a specific problem with Google? :confused: Some of their software sources seem to be having problems too: it took me a couple of tries to download and install Chrome from within Ubuntu Tweak, and when doing a System Update some sources are still failing...)

---

### Post by Vaphell on 2010-08-28
do you have any plugins installed?
go to about:config and try disabling IP6 (network.dns.disableIPv6 = true)

---

### Post by gradinaruvasile on 2010-08-28
Are you by chance connected through wireless?

---

### Post by rossolimo on 2010-08-28
Thank you for your prompt reply, Vaphell. (My! That was quick!)

I had installed the FLASH-AID 1.0.11 extension as per the instructions on another thread in the forums regarding Flash problems (I've now disabled it when trying your suggestion). As for my plugins, here is the list:
-Adobe Reader 9.3
-DivX Web Player
-iTunes Application Detector
-Java Plug-in 1.60_20
-QuickTime Plug-in 7.6.6
-Shockwave Flash 10.1 r82
-Windows Media Player Plug-in 10

I think all of them are the default ones, except the Adobe Reader one and maybe the Java (which I think I installed myself, again following the instruction on another thread regarding Java problems). I didn't provide a list before because as I had tried different browsers I thought it could not be something to do with the plug-ins. Having said that, I followed your instructions and after I disabled IP6 Google Maps now loads and allows me to zoom in. But there is still a problem in that most pages feel sluggish (Gmail is still loading after 5 minutes, although it too shows the list of messages now; another Google help page is not loading at all).

Thanks to you too, gradinaruvasile, and yes, I'm using wireless but as I've said my other computers don't have any problem connecting, nor does this machine when using other live distros.

Any other suggestions, please? (Gmail has now finished loading up, after 10 minutes, and the other Google help page is *slowly* getting there...)

[It was taking so long in my Amilo after I clicked on "Submit Reply" that I've had time to turn on my Asus Eee PC, navigate to the forums, copied my reply, and added these couple of lines. It's *that*...*slow*... Please help :( ]

---

### Post by gradinaruvasile on 2010-08-28
It is not about the connecting. It is about its speed. I have sean Atheros wireless working at 10 KBytes/s.
Open [www.speedtest.net](www.speedtest.net) in a browser and do a test, compared it to the other computers.

---

### Post by rossolimo on 2010-08-28
Thanks for the suggestion, gradinaruvasile. I see what you mean, but the same wireless card works fine with other (live) distros. Wouldn't OpenSuse and Fedora show the same problem too, given that both also use Gnome? Or are the drivers they use for a particular card different?

Here are the results of the speed test:
-Amilo Pa1510: Download speed 3.71Mbps Ping 38ms
-Asus Eee PC 701: Download speed 3.60Mbps Ping 38ms Upload speed 0.85Mbps

The download speed is slower in the Asus but curiously enough the upload speed test doesn't seem to work on the Amilo: it just "freezes" while "Preparing Upload"... Does that mean anything to you? Could it be an indication of the source of the problem?

Thanks in advance.

---

### Post by lovinglinux on 2010-08-28
> **rossolimo said:**
> Thank you for your prompt reply, Vaphell. (My! That was quick!)

I had installed the FLASH-AID 1.0.11 extension as per the instructions on another thread in the forums regarding Flash problems (I've now disabled it when trying your suggestion). 

There is no need to disable FLASH-AID since it doesn't interact with web pages or your network in any way. It is just a tool for installing and removing flash properly.

> **Vaphell said:**
> do you have any plugins installed?
go to about:config and try disabling IP6 (network.dns.disableIPv6 = true)

Most likely you have a system ipv6 problem. See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html"). Perform the method to disable it in Grub, since you have already disabled it on Firefox. Additionally, check if the MTU value in router configuration is properly set as 1492. If it is set to 1500 it could cause such issues.

---

### Post by rossolimo on 2010-08-28
Thanks, lovinglinux (nice name by the way ).

I checked MTU and indeed it had a value of 1500, so I changed it to 1492. I've also followed the instructions to disable ipv6 but I'm still having problems. Web pages still take a very long time to load, if they load at all. Could it be something to do with the drivers? I'm using an Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) with the ath5k drivers.

Any ideas, please? :confused:

[For what it's worth, I again had to switch to my other computer because after clicking on "Submit reply" the Amilo was taking for ever... and checking the configuration on the Asus I now find that the MTU is 1500, it is also using the ath5k kernel module, and has ipv6 enabled both in the system and Firefox...]

---

### Post by lovinglinux on 2010-08-28
Have you reboot after applying those changes?

---

### Post by rossolimo on 2010-08-28
I had, indeed. And the problem continued. I have now rebooted a second time and (surprisingly!?) things do seem to have improved... a little. Pages now load reasonably well but continue loading for a long time, so I'm not sure whether the problem is gone for good or not. What I'm certain of is that this is not the normal behaviour I would expect from a browser. And it's certainly not the same experience as with my other computer. Right now after trying to load Google Maps yet again in Chrome I got an "[COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]Error 324 (net::ERR_EMPTY_RESPONSE): Unknown error"

[/FONT][/FONT][/COLOR]I'm going to click on the "Submit reply" button now and hope for the best.

---

### Post by lovinglinux on 2010-08-28
> **rossolimo said:**
> [/FONT][/FONT][/COLOR]I'm going to click on the "Submit reply" button now and hope for the best.

I guess it worked :)

Anyway, have you upgraded to Ubuntu 10.04 or is it a clean install?

---

### Post by rossolimo on 2010-08-28
Your help is much appreciated, lovinglinux.

First I upgraded and then, when I started noticing problems, I did a clean install (...well, since I double-boot with W7 -I know, a shame- I guess I should be calling a "dirty" install, but anyway...). Things have improved but still browsing is sluggish at best, and erratic to boot. I'm going to keep looking for a fix because having to hit F5 all the time to refresh a page that normally would have already loaded is no good.

I was thinking... Is there a way I could copy the settings/drivers, or something else, of a live distro that doesn't have this problem (e.g. Fedora 13) and "apply" them to my Ubuntu install? Does that make any sense? How would I go about this? I'm really not sure where to star or what to look for...

[Yet again I'm forced to add the signature "Sent from my Asus Eee PC" since the "Submit reply" no longer works in my Amilo... erratic indeed]

---

### Post by lovinglinux on 2010-08-28
> **rossolimo said:**
> Your help is much appreciated, lovinglinux.

First I upgraded and then, when I started noticing problems, I did a clean install (...well, since I double-boot with W7 -I know, a shame- I guess I should be calling a "dirty" install, but anyway...). Things have improved but still browsing is sluggish at best, and erratic to boot. I'm going to keep looking for a fix because having to hit F5 all the time to refresh a page that normally would have already loaded is no good.

I was thinking... Is there a way I could copy the settings/drivers, or something else, of a live distro that doesn't have this problem (e.g. Fedora 13) and "apply" them to my Ubuntu install? Does that make any sense? How would I go about this? I'm really not sure where to star or what to look for...

[Yet again I'm forced to add the signature "Sent from my Asus Eee PC" since the "Submit reply" no longer works in my Amilo... erratic indeed]

Before taking drastic measures, create a new Ubuntu user, log into that account and check if the problem persists. If not, then you can log into your user account again, backup all hidden folders and files (the ones with a dot before them) under /home/you, delete them and reboot. Your settings will be recreated with default values and you will have a clean user account, accept that your personal files and folders (the ones without dots in front) will be kept.

---

### Post by rossolimo on 2010-08-29
I've tried creating a new user account, lovinglinux, but the problem persists: the longer I'm logged in the worse the problem becomes (pages taking ages to load); when I restart the problem seems to improve slightly but it's still there nevertheless.

[I've also noticed now that when I use the Update Manager, after clicking the "Check" button, it still says "The package information was updated 8 days ago"... could this be related or is it a different problem? Please help anyone! ]

---

### Post by gradinaruvasile on 2010-08-29
A quick suggestion: if you can, connect your laptop via cable (disable the wireless first) and see if the problems persist.

---

### Post by rossolimo on 2010-08-30
The plot thickens... at least for me. I followed gradinaruvasile's advice and connected to the router with an ethernet cable, and it works! Now, what could possibly cause the connection problem with the wireless? I thought that it would either work just fine or not at all. So what I though at first might be a problem with DNS servers, or flash, or Java is in reality... what sort of problem? And how do I sort it out, please?

I'm very grateful for all your help but also very confused... :confused:

[I just wanted to add that now Evolution also syncs my Gmail account and Empathy connects to my MSN account... something I hadn't been able to do, if I remember correctly, since upgrading to Karmic... Update Manager, however, is still saying that it last updated 9 days ago, despite the fact that I just run it -and yes, most of the software sources worked fined when connected through ethernet cable. Why, oh, why? Any ideas anyone, please?]

---

### Post by barlaso on 2011-11-17
For me it helped to put the correct ip mapping for maps.gstatic.com in the /etc/hosts file:
74.125.39.120 maps.gstatic.com

---

