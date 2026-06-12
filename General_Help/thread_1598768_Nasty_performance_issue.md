---
title: "Nasty performance issue"
date: 2010-10-16
forum: General Help
---

### Post by broomfighter on 2010-10-16
When I upgraded to 10.04, I started to experience some minor performance issues. Slow downs when opening multiple programs, freezing, that sort of thing. But since I've upgraded to Maverick, it's gotten much worse. I consistently get freezes when opening programs, and more than 4 tabs in chrome brings the desktop to a halt. I've checked my ram, and it's working fine. I've tried playing with vm.swappiness, but it hasn't helped. The only thing that has made any difference is starting with the recovery mode kernel, oddly enough, but it's definitely not doing the trick. It's an old computer, Pentium 4 processor, integrated graphics, 512MBs of RAM, but it's always run well enough under Ubuntu. Does anybody have any idea what could be causing this?

---

### Post by James78 on 2010-10-17
Are you using integrated graphics? They definitely could be causing LOTS of slow down. My computer right now has onboard, P4 @ 3.4GHz. It works reasonably well, but because of the onboard, using too many graphics causes slowdown, because certain features aren't supported. Disabling some of them (KDE blur filter specifically) increased performance significantly for me.

Other than that, I don't know in your particular case.

---

### Post by soldier1st on 2010-10-17
his issue is the lack of memory. 512MB is the min to run Ubuntu and it will not run too well unless the memory is upgraded to say 2GB or maybe 1GB and the integrated graphics card is not helping as it is taking resources away from the system like the ram. if the integrated gpu were to be replaced with a dedicated graphics card that would help.

---

### Post by broomfighter on 2010-10-17
It's definitely not lack of ram. I've been using Ubuntu since 7.04, and I've never had a problem like this until 10.04. The change was dramatic. The memory requirements have not gone up, and benchmarks show only minor increases in memory usage. 

I am using integrated graphics, but I didn't have issues like this when compiz was introduced a couple years ago. Maybe a new plugin was enabled? I'll play with CCSM and see it doesn't make a difference. Then I'll report back.

EDIT

Nope, I disabled compiz and it hasn't improved

---

