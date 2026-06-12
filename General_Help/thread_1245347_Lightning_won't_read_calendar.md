---
title: "Lightning won't read calendar"
date: 2009-08-20
forum: General Help
---

### Post by SaxMeister13 on 2009-08-20
Hi all, I'm dual-booting between XP Pro and Jaunty.  Recently I decided to create a single shared profile for Firefox and Thunderbird, so I placed each on a NTFS partition to which both OS's had read/write access.

Firefox works beautifully, so I know I got the process right.  Thunderbird works like a charm, too, except for the Lightning extension.  It refuses to share the calendar no matter how hard I try.  I have compiled an xpi containing both the Windows and Linux versions of Lightning according to [this tutorial]("https://wiki.mozilla.org/User:Ssitter/UnifiedLightning"), and as far as I can tell it is working (the addon functions in both OS's), but the actual data just won't share.  I put in several events on the Windows side and Ubuntu comes up blank.

I've been searching for a solution, and it seems that many people have this problem, but no one seems to have gotten it to work.  The closest I've found are two different methods [here]("http://forums.mozillazine.org/viewtopic.php?f=39&t=606758&start=0") for sharing the calendar across two profiles.  I'd really like to keep just the one profile, because for everything else - mail, contacts, even extensions - it shares the data.  Does anyone know how I can make this happen?

Thanks in advance for the help.

---

### Post by SaxMeister13 on 2009-08-20
I'm an idiot.

It turns out I didn't have the prerequisite packages for Lightning - specifically, libstdc++5.  I assumed since I had libstdc++6 installed I wouldn't need the older version.  Installed libstdc++5 via Synaptic, re-installed Lightning and everything works fine.

---

