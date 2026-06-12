---
title: "Help getting CAC reader working on 64-bit Natty"
date: 2011-06-08
forum: General Help
---

### Post by ken_23434 on 2011-06-08
I have tried to follow the guide to set up my ActivCard USB Reader 2.0

When I run the scan command, it does recognize my card.


```
Scanning present readers...
0: SCM SCR 331 [CCID Interface] (60600DC8) 00 00

Wed Jun  8 19:29:57 2011
 Reader 0: SCM SCR 331 [CCID Interface] (60600DC8) 00 00
  Card state: Card inserted, 
  ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 B0 F3 10 00 07 90 00 80

ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 B0 F3 10 00 07 90 00 80
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU
    250000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 312500 bits/s
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 00 31 C0 64 B0 F3 10 00 07 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: B0 F3 10 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 07 (Operational state (activated))
      SW: 9000 (Normal processing.)
+ TCK = 80 (correct checksum)

Possibly identified card (using /home/ken/.smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 B0 F3 10 00 07 90 00 80
	DoD CAC, Oberthur ID One 128 v5.5 Dual
```

When I try to go to a website that would require me to use the CAC, Firefox hangs up and eventually crashes and I get an error message saying a crash report will be sent and ...

While Firefox is "hanging up" on me, the green light on the CAC reader is flashing the whole time.  At work, the light only flashes while the computer is accessing the card and then the light goes steady.

I am using the coolkey package from the repository.  I have not tried the cackey program that is mentioned in a few of the threads (since that site requires PKI, and I cannot do that now).  What I read about that package, though, stated that it would help with the 144k cards.  It looks like my is a 128k card based on the info I posted above.

I did get this card issued w/in the past month, so it is a fairly new card, although I have no idea of this "version" is a new type.

Any help or suggestions would be greatly appreciated.

Ken

---

### Post by Cheesehead on 2011-06-08
Your output looks like your card is being recognized just fine. So it seems more likely a Firefox issue than a coolkey issue.

I have used coolkey since 9.10 with no problems.

Did you configure Firefox by downloading and installing all the DoD certificates, then restarting Firefox?

---

### Post by dillzz66 on 2011-06-08
Creepy Kenny?

---

### Post by ken_23434 on 2011-06-09
I installed all the DOD certs from the link provided in the Community Documentation.

I have restarted a number of times.

I downloaded the ISO mentioned at the end of the how-to doc and rebooted w/ it.  It worked fine that way.  I was able to go to the softwareforge.mil link in the documentation and I got a copy of the CACKEY package from there.  It is only for a 32-bit install, though.

So, I know the card reader and my card work.

I tried to link the CAC Module in Firefox to the .so file from the CACKEY package, but I am unable to get Firefox to load a module now.

Anytime I try to create the CAC Module in Firefox and link it to either the coolkey or the cackey ###.so file, it says "Failed to load Module".

That happened once early on while trying to get this to work.  I was able to reboot and then create the module.  That is not working for me know.

Maybe I should just use that ISO image and run that OS via a VM when I need to access a work site.

---

### Post by ken_23434 on 2011-06-13
OK, a few changes and a little progress.

I noticed that if I waited long enough, Firefox would eventually recognize my ID.  By long enough, I mean Firefox "locks up", I leave to go do something else and come back an hour later and under the CAC Module device in Firefox it would show my name and some information from my ID.

I can click the "Log In" button and it will ask for my PIN and ask something about my cert.

From there, I might or might not be able to access a CAC website.  It is still VERY slow to have it show any pages.

However, when I use the LPS_Common OS, it works flawlessly.  Meaning, browsing to websites is quick, no delays, no greying out of the screen w/ Firefox.

Any suggestions would be appreciated.

---

### Post by ken_23434 on 2011-06-13
Here is an error I have started to get in Firefox

```
A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.

Script: chrome://pippki/content/device_manager.js:271
```

---

