---
title: "Kernel Panic on Gateway T-6330u Laptop"
date: 2010-06-01
forum: General Help
---

### Post by chessnerd on 2010-06-01
Every once and a while, my entire system will freeze and the light for "Caps Lock" on my keyboard will flash. Nothing will bring my system out of this state other than a hard-reboot.

I recently discovered that this is what happens during a "kernel panic" which, from my understanding, is a not-very-good thing.

I'm currently using Lucid, but this also happened under Karmic.

I think the issue might have something to do with the wireless card, but I'm not sure at all. 

I can't seem to find any commonalities in these panics. Sometimes I'm doing heavy multi-taksing, other times I'm only working with one application. From my understanding, however, kernel panics can only be caused at the, well, "kernel" level, not by failing applications.

So, I was wondering if anyone has any ideas as to what I could do to diagnose/fix this.

---

### Post by chessnerd on 2010-06-04
Sadly this is still a major problem for me. This system has crashed 2 times in under 30 minutes. ](*,)

However, both times it crashed when I was streaming a YouTube video, so I believe that it has something to do with the Internet.

I checked the logs, and this was the log for the minute leading up the failure:

```
Jun  4 02:19:18 jason-laptop kernel: [   86.655068] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:4d:13:eb:8d:00:22:6b:50:51:b2:08:00 SRC=208.117.248.27 DST=192.168.1.107 LEN=1500 TOS=0x00 PREC=0x20 TTL=54 ID=7298 DF PROTO=TCP SPT=80 DPT=44719 WINDOW=135 RES=0x00 ACK URGP=0 
Jun  4 02:19:38 jason-laptop kernel: [  106.665040] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:4d:13:eb:8d:00:22:6b:50:51:b2:08:00 SRC=208.117.248.27 DST=192.168.1.107 LEN=1500 TOS=0x00 PREC=0x20 TTL=54 ID=7299 DF PROTO=TCP SPT=80 DPT=44719 WINDOW=135 RES=0x00 ACK URGP=0 
Jun  4 02:19:42 jason-laptop kernel: [  110.548419] __ratelimit: 9 callbacks suppressed
Jun  4 02:19:42 jason-laptop kernel: [  110.548428] operapluginwrap[2022]: segfault at 0 ip (null) sp 00007fff3169ba48 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:42 jason-laptop kernel: [  110.594413] operapluginwrap[2038]: segfault at 0 ip (null) sp 00007fff6512aaf8 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:42 jason-laptop kernel: [  110.688997] operapluginwrap[2070]: segfault at 0 ip (null) sp 00007fffb1b79c78 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:42 jason-laptop kernel: [  110.979702] operapluginwrap[2113]: segfault at 0 ip (null) sp 00007fff883a73b8 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:43 jason-laptop kernel: [  111.100769] operapluginwrap[2145]: segfault at 0 ip (null) sp 00007fff8b2352f8 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:43 jason-laptop kernel: [  111.133328] operapluginwrap[2161]: segfault at 0 ip (null) sp 00007fffdd5009e8 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:43 jason-laptop kernel: [  111.162023] operapluginwrap[2177]: segfault at 0 ip (null) sp 00007fffbab2d3a8 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:43 jason-laptop kernel: [  111.255771] operapluginwrap[2220]: segfault at 0 ip (null) sp 00007fff8154c578 error 14 in operapluginwrapper-native[400000+2e000]
Jun  4 02:19:58 jason-laptop kernel: [  126.675134] [UFW BLOCK] IN=wlan0 OUT= MAC=00:23:4d:13:eb:8d:00:22:6b:50:51:b2:08:00 SRC=208.117.248.27 DST=192.168.1.107 LEN=1500 TOS=0x00 PREC=0x20 TTL=54 ID=7300 DF PROTO=TCP SPT=80 DPT=44719 WINDOW=135 RES=0x00 ACK URGP=0 
Jun  4 02:21:07 jason-laptop kernel: [  195.600067] CE: hpet increasing min_delta_ns to 15000 nsec
```
I believe the last entry was when I rebooted.

Going back through the logs, it looks like the common pattern is: several UFW blocks, a load of operapluginwrapper segfaults, and then a gap when I reboot the system.

Obviously, Opera has something to do with this error. The question is this: did Opera cause the system to fail, or did the system failure cause problems with Opera?

---

### Post by mickie.kext on 2010-06-04
Did you tested hardware for defects? Try MemTest86+ for RAM (you have that on Live CD i think), open Disk Utility from Linux to see SMART status of your hard drive, and you can use lm-sensors to measure CPU temp while CPU is under load. 

As for wireless card, you should be able to disable it via bios, and then see if it happens while you are offline.

---

### Post by chessnerd on 2010-06-04
> **mickie.kext said:**
> Did you tested hardware for defects? Try MemTest86+ for RAM (you have that on Live CD i think), open Disk Utility from Linux to see SMART status of your hard drive, and you can use lm-sensors to measure CPU temp while CPU is under load. 

As for wireless card, you should be able to disable it via bios, and then see if it happens while you are offline.

Thanks for your reply.

I don't believe any of my hardware has defects, as this also occurred months ago while running Karmic. However, I did the suggested tests - here is what I found:

memtest found no errors.

Disk Utility says my drive is healthy.

CPU temp under load does sometimes get pretty hot (59 C) so this could have something to do with it. If the wireless turns out to not be the problem, I will have to look into a way to better cool the CPU...

I believe the wireless card is likely the cause. For the next couple of days I'm going to disable the card and use this laptop while connected via Ethernet to see if this occurs again. 

If it doesn't then the problem is likely the drivers for the card. The card works perfectly under Windows Vista and 7, so I have no reason to believe the card itself faulty. 

The card is an N-wireless card (Atheros AR928x). I have tried NDISWrapper in the past with no success. From my understanding, N-wireless is still buggy in Linux. If the card is the problem, is there anything I can do, other than be stuck near using an Ethernet connection all the time?

---

### Post by mickie.kext on 2010-06-04
59 C temp is ok for just about any mobile CPU, so we ruled that out. 

So if you are testing wirelless, and you think hardware is OK then unload kernel module which provides driver for that wirelless card and see if issue goes away when you only use wired network.

Here is crash course about kernel modules [http://edoceo.com/liber/linux-kernel-modules](http://edoceo.com/liber/linux-kernel-modules)

If you narow down a problem to a faulty module, you can try recompiling newer version of module of MadWiFi drivers. Atheros WiFi cards are usualy good suported, so I am pretty sure this is just a bug rather than real incompatibility.

---

### Post by robsoles on 2010-06-30
> **chessnerd said:**
> ...

I believe the wireless card is likely the cause. .... 

... 

The card is an N-wireless card (Atheros AR928x). I have tried NDISWrapper in the past with no success. From my understanding, N-wireless is still buggy in Linux. If the card is the problem, is there anything I can do, other than be stuck near using an Ethernet connection all the time?

hi chessnerd, (I quite like chess but am more nerdy about computers)

I have a little experience with Wireless (real modern wireless internal to 2 laptops and an older external in a desktop PC) and Ubuntu and found Canonical (perhaps Debian) seemed to nail all the wireless cards I could find when they released 9.10 Karmic so I'm a bit surprised you are inclined to blame it on that.


Please: Was Opera your browser 'six months ago' when an earlier episode of this stuff happened? Have you managed to get a kernel-panic with Opera totally uninstalled and using Firefox for instance?


Perhaps another relevant question (or two) might be: Is it 64 bit or 32 bit install? Is that right, it's 10.04 LTS doing this?

---

### Post by chessnerd on 2010-06-30
> **mickie.kext said:**
> If you narow down a problem to a faulty module, you can try recompiling newer version of module of MadWiFi drivers. Atheros WiFi cards are usualy good suported, so I am pretty sure this is just a bug rather than real incompatibility.
Well, I've used Ethernet on and off over the past few weeks and haven't been able to reproduce a crash there. However, I occasionally go weeks without crashes anyway (other times, it happens every few hours). I have gotten three crashes when using wireless in this time span.

I wouldn't mind recompiling a newer version of a MadWiFi driver if I could find one. Here is the MadWiFi site's section on my driver: [http://madwifi-project.org/wiki/Compatibility/Atheros#AtherosAR928XakaAR5009](http://madwifi-project.org/wiki/Compatibility/Atheros#AtherosAR928XakaAR5009)

The URL it gives is to an Atheros site, but there is no place to get drivers on that website. The actual Atheros website's driver page ([http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)) doesn't seem to have my driver available either.

> **robsoles said:**
> I have a little experience with Wireless (real modern wireless internal to 2 laptops and an older external in a desktop PC) and Ubuntu and found Canonical (perhaps Debian) seemed to nail all the wireless cards I could find when they released 9.10 Karmic so I'm a bit surprised you are inclined to blame it on that.
I agree. My wireless support is a lot better. I used to barely get a signal in my room at all, now I get a decent signal. However, I only experience crashes when using the wireless...

> **robsoles said:**
> Please: Was Opera your browser 'six months ago' when an earlier episode of this stuff happened? Have you managed to get a kernel-panic with Opera totally uninstalled and using Firefox for instance?
Opera was my browser back then, but I have gotten this crash when only using Chrome. I've always had Opera installed so I guess I've never tested that, but I don't think it can affect the system when it isn't open in this type of manner.

> **robsoles said:**
> Perhaps another relevant question (or two) might be: Is it 64 bit or 32 bit install? Is that right, it's 10.04 LTS doing this?
This current install of Lucid is 64-bit. The install of Karmic was 32-bit. I am tempted to go back to the 32-bit to see if that will help. Do you think it might?

---

### Post by robsoles on 2010-06-30
> **chessnerd said:**
> ...

This current install of Lucid is 64-bit. The install of Karmic was 32-bit. I am tempted to go back to the 32-bit to see if that will help. Do you think it might?

Mmmh, pity to use 32-bit where architecture supports 64-bit but doing so could eliminate it - pity it sounds like there isn't some definite series of steps you can take to reproduce the problem, it would be faster and you wouldn't have to hang around in 32-bit for upto 'months' to find out if it is a 64-bit issue your architecture can't handle.

I am not thoroughly convinced it is 64-bit causing you the grief but I'm equally unconvinced it's wi-fi. Is it a common thing that flash is running in one of these alternative browsers you use (I had trouble with chrome freezing X on me so I ditched it and have never tried Opera here) when the freeze up occurs?

Have you tried restarting the x-server instead of the whole computer? (try [www.google.com/search?=restart+x+in+lucid](www.google.com/search?=restart+x+in+lucid) - pretty sure a result will tell you how, can't remember crazy new keyboard sequence but was 'ctrl+alt+backspace' in a previous instance)

Hey, next time you get it to freeze up perhaps you could attach a few different logs to your ensuing post to this thread, I reckon I'd like to see  the dying moments of any logs with entries from up to 30 seconds before freeze up, especially Xorg.0.log (if they aren't too personal :))

---

### Post by chessnerd on 2010-06-30
> **robsoles said:**
> Mmmh, pity to use 32-bit where architecture supports 64-bit but doing so could eliminate it - pity it sounds like there isn't some definite series of steps you can take to reproduce the problem, it would be faster and you wouldn't have to hang around in 32-bit for upto 'months' to find out if it is a 64-bit issue your architecture can't handle.
I wouldn't mind downgrading to 32-bit again. After all, my system only has 3 GB of RAM. However, I kind of like the 64-bit. It seems snappier.

I wish I had a proven formula to cause these crashes. I've tried just opening up a bunch of YouTube tabs and seeing if it will crash and that hasn't worked the couple of times that I've tried it.

> **robsoles said:**
> I am not thoroughly convinced it is 64-bit causing you the grief but I'm equally unconvinced it's wi-fi. Is it a common thing that flash is running in one of these alternative browsers you use (I had trouble with chrome freezing X on me so I ditched it and have never tried Opera here) when the freeze up occurs?
It isn't just Flash, I've had it occur when testing HTML5 as well. However, Flash is usually running when it crashes... 

I've noticed that the crashes seem to occur whenever my wireless load is very high for any length of time. I've never had a crash after a Flash video has fully loaded, but they happen instead while I'm watching one that is still being streamed. However, I've never had it occur when doing updates or downloading something...

> **robsoles said:**
> Have you tried restarting the x-server instead of the whole computer? (try [www.google.com/search?=restart+x+in+lucid](www.google.com/search?=restart+x+in+lucid) - pretty sure a result will tell you how, can't remember crazy new keyboard sequence but was 'ctrl+alt+backspace' in a previous instance)
I have, but I can't even restart X. I can't go to another tty. I can't do anything other than hard boot it. (The new sequence is Alt-SysRq-K, I believe.)
Also, if there is any type of audio going, the system will repeat the last two seconds or so of audio. I don't know if X crashing could cause that...

> **robsoles said:**
> Hey, next time you get it to freeze up perhaps you could attach a few different logs to your ensuing post to this thread, I reckon I'd like to see  the dying moments of any logs with entries from up to 30 seconds before freeze up, especially Xorg.0.log (if they aren't too personal :))
Will do. I'm sure I'll be able to "gather some more data" in a couple of days. :)

---

### Post by chessnerd on 2010-06-30
[Uh, apparently I did a quadruple post of the last post. Not sure how that happened, but I'm going to try to replace those posts with new information I've found out about my problem.]

I did a bit more research into my problem. Evidently, lspci has been misidentifying my card. According to the Device Manager in Windows Vista, the card is actually an Atheros AR5B91, not an AR928x. This is evidently a common issue, as I read several other posts on other forums about it...

---

### Post by chessnerd on 2010-06-30
I have been scouring the interwebs for drivers for the AR5B91 in Linux. As of yet, I can't find any at all. Only Windows versions seem to be available. I have found plenty of older forum posts about non-recognition/poor performance in past versions of Ubuntu, but I can't find any posts where someone was able to resolve their issues with this card.

I am wondering, there are apparently two types of drivers for Atheros cards in Linux: ath9k and ath5k. Since my card starts with a 5, does that mean that I should try to find an ath5k driver? I think I'm using the ath9k right now, but I'll need to check later (I'm under Vista at the moment).

---

### Post by chessnerd on 2010-06-30
In Windows, the name of the card in the Device Manager (under both Vista and 7) is - Atheros AR5B91 Wireless Network Adapter
In Ubuntu, the name of the card under lspci is - Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

The Hardware IDs are:
PCI\VEN_168C&DEV_002A&SUBSYS_E006105B&REV_01
PCI\VEN_168C&DEV_002A&SUBSYS_E006105B
PCI\VEN_168C&DEV_002A&CC_028000
PCI\VEN_168C&DEV_002A&CC_0280

---

### Post by robsoles on 2010-06-30
> **chessnerd said:**
> [When I get more info I'll post it here. I accidentally did a quadruple post of a previous post and so I'm filling in the remaining ones with new info... Likely, I'll post about my attempts to find ath5k drivers or a crash log if my system crashes later tonight.]

Hey, whilst in windows just (please) grab the name that Win gives it in device manager and then grab the Uuid (I think, or maybe hardware) ID from inside the property sheets of it and that may help later when I knock off work.

Handier still if you find it in the 'lspci' under Linux and tell me what that calls it too - I can't be too sure of anything about your wifi device without at least one or some of these details!

---

### Post by chessnerd on 2010-08-17
Well, I haven't had a crash since the update to 2.6.32-24 so I think that may have fixed it. It also could have been an update to the network manager, the network drivers, Opera, or any number of applications/components. Who knows why it isn't crashing anymore, I'm just glad that it isn't.

More importantly, however, is this: Not one hour ago, I experienced a nearly identical crash under Windows Vista. Everything locked up and the speakers looped the last couple of seconds of audio. Only a hard boot could fix it. :(

Good news: This may not have been the fault of Ubuntu!
Bad news: I fear this may be a hardware problem. Possibly overheating.

In light of this new evidence, I'm marking this as solved. If the issue persists, I'll start a new thread. Thank you for your help!

:mad: [RANT] Ugh! Never buy anything from Acer or any of its subsidiaries. This computer is a Gateway, who built amazing computers until they were acquired. Now, their stuff is junk too. Whenever that happens, the old company's loyal customers lose big time. A more recent case - Oracle acquiring Sun. Bye-bye OpenSolaris. Up next: the end of OpenOffice and Java. [/RANT] :mad:

---

