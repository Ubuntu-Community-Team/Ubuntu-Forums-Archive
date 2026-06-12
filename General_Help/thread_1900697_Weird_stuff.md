---
title: "Weird stuff"
date: 2011-12-26
forum: General Help
---

### Post by d.vanheeckeren on 2011-12-26
I can't seem to find anything related to this, so I'm asking here...I have a WEIRD problem:

When I'm running something in a terminal, especially batches, after about 20 seconds, processing in that terminal stops......until I move the mouse, at which point it continues.  I'm not exactly new to linux, I'm familiar with navigating and many terminal commands and have an actual understanding of what they do.  I am not, however, very familiar with hardware issues or drivers and such.  Any ideas?

Using Ubuntu 11.10 32-bit

---

### Post by West201 on 2011-12-26
Report the bug using launchpad. 

Ubuntu 11.10 is still semi-buggy.

---

### Post by QIII on 2011-12-26
Do other things that can take minutes to run work properly without pausing?

What sorts of "batches" are you running?  Is this something of your own design?  Your own scripts?

---

### Post by d.vanheeckeren on 2011-12-27
jesse:  It's not appropriate to report a bug unless you verify it to have no discernible reason...and this thread is the beginning of that investigation.

QIII:  The sort of batches I'm running are just simple prefab scripts to compress and decompress files in quantity.  However, I've also determined that the whole system seems to sit in some sort of standby if there is no mouse action.  Move the mouse pointer, and everything resumes.  I've got 11.10 running on many computers, and this is the only one that does it.  Come to think of it, it's the only one running 32-bit.  It's an AMD Athlon XP 2100+ running on an Epox 8K5A2+ with plain sis300 graphics, via rhine II integrated nic, 512MB RAM, 80GB Maxtor HDD.  Serial ports, parallel port, floppy controller all disabled along with integrated sound and midi.  Oh, and a CDRW, AOpen I think...but I don't even know if it works cuz I've never used a CD on it.  *LOL*  Using rt3070 wireless adapter for connectivity.
Just on a hunch, I've logged in both with the regular Unity and the 2D just in case it had something to do with the video, but does the same thing.  I swapped another hard drive in and installed windows 2000 pro and windows xp both, and both ran fine with no problems.  If I have to, I can just use windows on this box, but I must tell you I've hated windows for 20 years, so if I can avoid that, I'd prefer ubuntu.

---

### Post by spiky001 on 2011-12-27
I know it might get overlooked but could the screensaver be causing a problem Just a thought sorry if you have checked it. Or the stanby some way.

---

### Post by d.vanheeckeren on 2011-12-27
One of the first things I do in any operating system is disable all power management and screensavers....simply because I don't ever leave a system running, and if I do, I'll be back in a minute or two. :)

[EDIT] I should also mention that all power management is disabled in system BIOS.

---

### Post by QIII on 2011-12-27
Can you install gkrellm or something like that and do something processor intensive to see if your processor activity drops off, or would gkrellm stand by, too?  I would have suspected power management, but apparently that's not it.

---

### Post by d.vanheeckeren on 2011-12-30
> **QIII said:**
> Can you install gkrellm or something like that and do something processor intensive to see if your processor activity drops off, or would gkrellm stand by, too?

Yup...ran as much as I could at the same time, including audacity, winff converting videos, and unreal tournament 2004 in windowed mode, along with system monitor...Processor pegged at 100%, after about 1-1/2 minutes, everything stops...including system monitor and clock....and just sits there.  When I move the mouse, everything resumes.  I've never had this happen before, I'm stumped.  On impulse, I threw in another hard drive and installed 10.04LTS, and it ran flawlessly.  Because all other operating systems on other hard drives worked, I thought maybe it was the hard drive that it was installed on...but everything tests fine, including all combinations of options on/off (s.m.a.a.r.t. monitoring, different ATA speeds (it's an EIDE), etc.).  Well that produced no 'hanging', so I installed 11.10 on a different hard drive just in case linux had a problem with that particular one (yes, I have about 50 hard drives laying about.  *LOL*), and SAME problem.  It's gotta be something between 11.10 and somthing in my motherboard.  Memory tested out with no errors with memtest86+, Processor burn-in program went flawlessly (no drives attached to eliminate possibilities).

So my conclusion is, there's either a conflict with my motherboard or a component in it is bad that 11.10 tries to use but 10.04 doesn't.  At this point, I'm in over my head, I'm no engineer, and certainly no programmer....so I've decided to stop wasting my time and just use 10.04, it plays well with the others on the network and does everything fine.  Cuz after all, with a full-time job, a wife working overnight, and six boys, I have enough to do...no sense in losing the little sleep I have for a personal challenge.  It's beaten me, I forfeit.  *LOL*  :)

---

