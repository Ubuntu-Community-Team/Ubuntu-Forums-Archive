---
title: "Black bar in my screen"
date: 2009-07-10
forum: General Help
---

### Post by Glenn nl on 2009-07-10
Hello

I installed Ubuntu yesterday, everything was just fine.
And its awesome.
I noticed i had a beep when turning off.
I got the solution at the dutch ubuntu forum (im dutch).
Then i rebooted.
When it was booting, the logos of the companies were really big (everything is zoomed in) my Grub is really zoomed in and my Ubuntu AND windows xp have a blackbar at the right of my screen.
I deleted the solution of the beep, rebooted, still zoomed.
Ubuntu still works, Windows still works but they both have a black bar at the right of my screen.

My graphics card is an ATI radeon Xpress 200 worked fine for years.

Help!

---

### Post by Glenn nl on 2009-07-10
Anyone?

---

### Post by nikhilk on 2009-07-10
Do you mind sharing what was that you did that caused this problem. Anything related to the X windows sub-system?
It seems that resolution has been screwed up.

---

### Post by Glenn nl on 2009-07-10
I went to the terminal and wrote: sudo gedit /etc/modprobe.d/blacklist.conf
After that i added blacklist pcspkr at the end.
I rebooted and everything was zoomed in (like Grub) and XP and Ubuntu have a black bar (though XP and Ubuntu aren't zoomed in)

---

### Post by Glenn nl on 2009-07-10
OMG!
It was my screen.
I pulled out the cable and put it back in.
Its working fine again!

---

