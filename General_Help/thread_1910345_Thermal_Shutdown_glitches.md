---
title: "Thermal Shutdown glitches"
date: 2012-01-17
forum: General Help
---

### Post by chipbuster on 2012-01-17
Hey all. I installed Xubuntu recently (about a month back) and started running into a bizzarre issue. It seems that my computer will, on its own accord, make stuff up about the CPU temperature and shut itself down. The line from my syslog is > Jan 16 20:48:34 chipbuster-N3400 kernel: [11671.495635] Critical temperature reached (127 C), shutting down.
Here's the kicker: this is almost certainly just my thermal chip acting up, because on some of these, I checked the sensors command right before the computer shut down, and the temps were in the 30s. When I turned it back on, the CPU was in the 30s as well. The temperature change to go from 30 to 127 to 30 again inside of 30 seconds should blow the CPU apart, yet my computer is intact, so it's probably a naughty thermal sensor.

I'm wondering if anyone knows a way to trigger a shutdown only if the temperature reading has been above the critical point for over 10 seconds, or to disable it. I've looked through a couple things online, but some of them are really old (as old as 8.10) and the files mentioned no longer exist in 11.10 (my version).

Any help would be nice--it's really annoying to lose work because the computer is pulling random numbers out of nowhere!

---

### Post by pretty_whistle on 2012-01-17
The only one I know of runs on windows and is called speedfan.

---

### Post by chipbuster on 2012-01-18
Well, uh, I think I might have fixed it. Unloaded the thermal module from the kernel and reinserted it with crt=0. I'm just going to have to sit on this "fix" for a while to figure out if it actually worked.  Does anyone know how to make this permanent so that I don't have to do it every time I boot?

---

### Post by chipbuster on 2012-01-18
Pfft, it died on me again. Any ideas?

---

### Post by mifritscher on 2012-11-04
I managed to fix it: [http://ubuntuforums.org/showthread.php?p=12336593#post12336593](http://ubuntuforums.org/showthread.php?p=12336593#post12336593)

---

### Post by MutantJohn on 2012-11-04
This thread is ironic because my CPU doesn't shutdown when it should.

I got Battlefield: Bad Company 2 to run through Steam through Wine and the max safe temperature for my CPU is supposed to be 62 C, per AMD's website, and when I looked after quitting the game I saw that it had spiked up to 70 C.

This, of course, led to an immediate email to AMD asking them why something so root and basic wasn't working. They assured me that their chips were supposed to indeed respond to critical temperatures by cutting the power and that I was overclocking, actually.

I thought that was rather interesting seeing as I have no clue how to even overclock. I use the cpufreq info and the hardware limits are exactly where they should be, no overclocking. So either MSI wasn't lying about that Auto OC feature or I got so drunk I learned how to enable OC'ing and promptly forgot.

---

### Post by Yellow Pasque on 2012-11-04
MutantJohn: look in the BIOS and see if you can tweak the thermal shutdown settings.

---

