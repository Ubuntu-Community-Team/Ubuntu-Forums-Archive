---
title: "Small problems with 9.10"
date: 2009-12-19
forum: General Help
---

### Post by rules on 2009-12-19
Hi all

Well was I pleasantly surprised when I installed 9.10 and out the box the wifi worked and it would seem as if syncing my WM phone is also becoming a possibility. 

I have 3 small problems though ...

1. Although the internet seems to be pretty fast(Firefox)I have intermittent problems with Evolution not connecting to the mail server (both pop3 as well as smtp). When booting back into Windows, then I have no problem again, so it's not my connection/isp.

2. I have selected the option to display the weather next to the time, but it never comes up. Any ideas?

3. This might be linked to problem 1 ... I can't seem to download any applications through Synaptic or the Software manager. Also when I search for certain things in Synaptic it does not find anything.

Any help would be much appreciated :)

Cheers.

---

### Post by TyrantWave on 2009-12-19
1) Try Thunderbird maybe?

2) Is it getting the weather info? If it can't get any info, it won't display IIRC.

3) Does it ask for your password when you boot them? It needs to be run as root to work (Which will happen when you enter your password). If you are, then... I don't know o_O

---

### Post by rules on 2009-12-19
Is it just me, or does it seem like I have network issues :confused:

---

### Post by audiomick on 2009-12-19
> **rules said:**
> Is it just me, or does it seem like I have network issues :confused:

That would be my first guess. If you are using a wireless connection, try plugging a cable in instead. Wireless is black magic, not just computers, radio mics and stuff as well...:)

If the cable works better, you know where to start looking.

---

### Post by rules on 2009-12-19
Ah goody, got it all sorted. Apparently there has been some IPv6 and DNS issues in the 9 series Ubuntu's. While disabling IPv^ in Firefox gets it to work, the rest of the goodies (weather, repositories etc.) then have DNS problems which can be solved by manually entering a DNS into your network config (just remember to do it for all network devices, wired and wireless).

Also found another small problem with Evolution where as soon as it detects you are setting up a gmail account it seems to load it's own "hidden" settings (ports) and if you don't use gmails smtp with the correct option and settings, it will just not work.

But it's all working and I'm royally chuffed that linux can work almost out the box. Wireless is working, got my HTC Touch Diamond 2 to sync, the sleep/suspend works, it actually feels faster (OS and internet). If wine plays along, I will finally get to make the jump :P

Cheers.

---

