---
title: "Debugging X lockups- i915 driver, intel 82845G"
date: 2006-04-19
forum: General Help
---

### Post by KrakensDen on 2006-04-19
Alright. I'll start out with my card:> 
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
I've had two hard crashes in the past two days, not under heavy load (IE, no 3d). When I say `hard crash', I mean X freezes, no cursor response, I'm unable to switch to another virtual console.

If this isn't a known bug, how should I go about logging this? /var/log/Xorg.0.log doesn't have anything interesting. If I install and setup sshd, how should I kill X so it spits out useful data? I'd like to help fix this problem if I can :).

---

### Post by shof2k on 2006-04-26
Same card, same issue here.  I can't see anything obvious in Xorg.0.log, or kernel.log

---

### Post by Rashid584 on 2006-06-09
Hmm, I have the same card, but I've never experienced such a spontaneous "hard crash". Its crashed before where I've had to kill X and start again, but only when I've been "over loading" it i.e. having firefox with 20 tabs, XMMS, Kaffeine, Kopete with 5 conversations and the GIMP etc

But I use the i810 driver, not i915. Maybe thats your problem? As far as I know, you're meant to use i810 with this card.

-Rashid

---

