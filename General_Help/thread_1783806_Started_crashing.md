---
title: "Started crashing"
date: 2011-06-16
forum: General Help
---

### Post by kompotas on 2011-06-16
Hey guys, 
I am using ubuntu for almost 2 years now. And I was satisfied, that it didn't crash for me, not like windows used to. But yesterday it did, and I thought well $#!t happens. Well today it happened already twice in one hour.
I am using ubuntu 11.04 with classic environment (not the new unity). Well I grabbed a pen and written some of it down (I hope I didn't messed up) 

940.068010 [Hardware Error]: CPU 0:Machine Check Exception : 4 Bank4: b200000000070f0f
[940.068010] [Hardware Error] TSC 16c6fd244db
[940.068010] [Hardware Error] Processor 2:20fc2 TIME 1308225961 Socket 0 APIC 0 
[940.068010] [Hardware Error] No Human readable MCE decoding support  inthis CPU type.
[940.068010] [Hardware Error] Run the message through 'mcelog-ascii" to decode.

*****I scipped some lines******

[940.068010] [Hardware Error] panic occured, switching back to text console
[945.451650] Clocksource tsc unstable (delta=4686970833 ns).

I'm not sure, is this my pc falling apart ? should I hurry up and back up my documents as fast as I can ? 
I would appreciate any help or advice. Thanks in advance.
Arnas.

---

### Post by Neo2 on 2011-07-12
You're not the only one. Exact same messages on my computer too. I uninstalled Ubuntu 11.04 and re-installed Kubuntu 11.04 to see if it was the OS but no, same problem again after random times. Mostly during video playback but not exclusively (it crashed once during installation for example). Hoping my computer isn't dead.. the vast majority of people seem to say it's hardware related (once you get beyond the flash issue). Please anyone, ideas?

---

### Post by FormatSeize on 2011-07-12
> **kompotas said:**
> 
I'm not sure, is this my pc falling apart ? should I hurry up and back up my documents as fast as I can ? 

You should already have everything backed up. Anyway, it doesn't seem that your computer is falling apart, but rather your OS is falling apart. 11.04 isn't stable, and Gnome-Classic is less stable than 2.32 (from 10.04 and 10.10). Generally, 11.04 is a series of unfortunate events that all lead to crashes.
 
Not to say that it's unusable, as I have read the testaments of some that say that their install is stable, but they are probably all rocket scientists. Or something. In general, Ubuntu 11.04 isn't ready to just work on any machine. Depending on your hardware, set up, and a host of other unimaginable things, things will spontaneously start breaking and your computer will start crashing. Or it may run fine. You just happen to have the right combination of hardware and setup such that 11.04 crashes on you all the time. 
 
I'd recommend reverting back to the LTS until this new version is robust enough to work more reliably.

---

