---
title: "memory increase/change hangs boot"
date: 2010-03-30
forum: General Help
---

### Post by waldick on 2010-03-30
i'm running 9.10 mythbuntu on a dell 4550 2.4 with 640 meg ram

when i try to increase that the box hangs on boot, just after the setting resolution screen and just keeps flashing...

i tried to put in just one 1Gig stick, two 512's, 1Gig + 512...all with the same result.

when i go back to the 512 and the 128 it works just fine.

i have tried the other sticks in other machines and vice versa.

the bios detects the ram just fine on start-up...

any ideas or suggestions ?

---

### Post by waldick on 2010-04-04
nobody  has any ideas ?

---

### Post by john newbuntu on 2010-04-05
If I understand you correctly, you are getting past the BIOS but booting into Ubuntu seems to be the problem. If so, boot from the liveCD and run memtest.

---

### Post by waldick on 2010-04-05
well it starts to boot into mythbuntu. Then it says something like "spalsh" something with resolution numbers, then ntpd server stopped and then it just flashes...

if i run memtest, what am i looking for. I have never run memtest before...

---

### Post by john newbuntu on 2010-04-06
Boot in with your liveCD and run the memtest option (something like memtest86).  Allow it to run for as long as it takes.  If you have a bad memory, you will find some messages highlighted in red that gives you memory addresses that are failing.  Also, the errors column indicates a number > 0.  Start with the 2 512 GB sticks and if the memtest goes ok, swap and retest.

---

### Post by -humanaut- on 2010-04-06
That much memory failing (im assuming it's all different brands speeds etc...) It's extremely unlikely all that memory is bad sounds like your DIMM's are failing to me. Like someone said above me boot the livecd and run memtest.

---

### Post by waldick on 2010-04-06
can i run memtest off the grub menu or do i have to run it off the live cd. I can get to the grub menu before it hangs...

---

### Post by JoelOl75 on 2010-04-07
Either run memtest from grub OR the live cd, it doesn't matter.

As for what to look for?  Anything with bright red lines showing errors.  All the bad memory I've ran into shows up fairly quickly (Within 10 secs or so) so A run of 5 mins should tell the tale.

---

