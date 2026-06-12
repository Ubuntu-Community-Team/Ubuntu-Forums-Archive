---
title: "blank screen on running live cd etc"
date: 2012-03-21
forum: General Help
---

### Post by Thorsen V on 2012-03-21
(I'm prefixed this "xubuntu" but this seems to be a general problem on my eMachines e525 which has been running ubuntu 10.04 from new)

Occasionally in fairly recent times I've tried varoius live distros (covers from Linux Format) and have been getting a common problem: It sounds like the system is booting off the CD but the screen remains blank (Fedora 14 was the most resent distro that I've tried that actually booted properly)

Anyway, as it wasn't very important I put this down to a problem with the cover disks and never bothered pursuing it further.

Well now I'd like to upgrade my system to xubuntu 11.10 so I downloaded the iso and now discover the exact same issue is present with this too.

In the help on the CD it mentions an option for "laptops with screen display issues" use vga=771

I added this to the boot line (before the --) and hit enter ... same problem.

Help would be appreciated.

~ Thorsen

---

### Post by Zimmer on 2012-03-21
It may not be a display issue, but a hardware one . Your CD/player  may be dirty, or the player may be faulty.

If you still have 10.04 running why not create a Live USB install from one of the ISOs you have downloaded and see if your machine will boot from that...

---

### Post by brainwash on 2012-03-21
You could try it with the *nomodeset* boot parameter.

---

### Post by Thorsen V on 2012-03-22
> **brainwash said:**
> You could try it with the *nomodeset* boot parameter.
thank you. That worked...

That's "working" in the sense that booting the live CD got me a thoroughly sh*tty text mode boot process with lots of screen text unreadably overwriting itself (some message about there being no driver for my wireless? Funny 'cos there was when 10.04 came out) and ending with a thoroughly sh*tty vga display which on my widescreen means squashed washed-out fuzzy looking pixels. 

I have 10.04 ubuntu that works fine and had a beautiful install experience (as I recall anyway, and definitely managed the arduous job of detecting the graphics), and this on a very ordinary low end machine with bog-standard intel graphics that's only a couple of years old ...

Hugely disappointed by these "improvements"

I'll leave actually trying to install until after the 12.04 and hope the graphics and wireless detection works as well as it did 2 years ago [/sarcasm]

---

