---
title: "QEMU mouse problem"
date: 2006-05-15
forum: General Help
---

### Post by snaga on 2006-05-15
I started using QEMU and Windows XP, without KQEMU, a few weeks ago. I couldn't get kqemu to work right away, so I just went without for awhile. I am only using it for access to Outlook 2003, and once in a while IE.

Late last week I decided I needed to install KQEMU, so I installed that, along with a 686 kernel. I had been using the 386 kernel prior.

Previously, QEMU worked fine, if a little slowly. Now, since I installed the 686 kernel and KQEMU, I have a really weird mouse problem. When moving the mouse, it sometimes comes to a point where it stops moving, like it has found the edge of the screen, even though the edge is an inch or two away. It will move along the edge of that imaginary line, just as if it were at the edge of the screen. This can happen vertically or horizontally. Moving the mouse around enough will make that imaginary line move to a different place.

I'd assume it was a general mouse problem, but it only happens in QEMU.

This is hard to explain, so let me know where I am unclear. I have tried messing with mouse settings in XP, to no avail. I think it happened after the upgrade to the 686 kernel, because I used that for a little while before making KQEMU work, and it had this problem.
QEMU is extermely useful, I just need help getting past this problem.

I have not tried to re-install XP since upgrading my kernel. I am just pointing at the same xp image that I previously created.

thanks

dave

---

### Post by snaga on 2006-05-16
This solved it for me:
[URL="http://qemu.dad-answers.com/viewtopic.php?t=1474&highlight=mouse"]
http://qemu.dad-answers.com/viewtopic.php?t=1474&highlight=mouse[/URL]

I used the usb mouse solution rather than the patch.

---

