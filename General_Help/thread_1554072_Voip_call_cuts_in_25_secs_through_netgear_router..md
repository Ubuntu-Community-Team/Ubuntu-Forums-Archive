---
title: "Voip call cuts in 25 secs through netgear router."
date: 2010-08-16
forum: General Help
---

### Post by subramanyamn on 2010-08-16
Hi,

I have a Compaq Presario V2000 running Ubuntu 10.04. I use voip to call international mobile numbers. I'm currently using a Netgear router (at a friend's place) and now, my calls cut in 25 seconds. The call time keeps running, but neither can hear each other after 25 seconds. I've tried using service providers like Actionvoip and Jumblo (as they are cheaper than Skype) and clients like Ekiga and Twinkle. Same thing happens! It happens on both Wi-Fi and ethernet. There is enough credit :P
I tried using my friends Dell Latitude running Windows 7 with my Jumblo account. Surprisingly, it worked perfect!
Previously I used a D-Link router and it worked flawlessly with my system.

I fail to understand if it is some settings issue or a bug with Netgear's firmware. If anyone else has come across this issue and has been successful in getting around it, I request your help! Any assistance is greatly appreciated!

PS: Skype and Pidgin audio calls work perfect.

---

### Post by Ceyx on 2010-08-17
I would look at your service providers charges....when the calls are cut off does their "meter" keep running ?  If so, then both Twinkle and your service provider believe they are connected - perhaps a clue.

I am having the same issues, sort of, where my system just hangs in the middle of a call...sometimes not for days.  I think it has something to do with my USB handset and the BIOS on my old computer. Removing USB 2.0 helped immensely,

I found the output in kern.log and dmesg.log right after a crash to be helpful.....

If Skype and Pidgin work flawlessly on your system, I would bet it is not the router....

Forgive my meandering.....hope this tweaks some ideas for you...):D

---

