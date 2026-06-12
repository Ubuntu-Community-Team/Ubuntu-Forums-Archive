---
title: "Serial Port Problems"
date: 2006-06-24
forum: General Help
---

### Post by joeybc2001 on 2006-06-24
Ok - my newly-installed xubuntu system works great, or so I thought unil i tried to use my serial PIC Programmer (using both picprog with command-line and ktechlab GUI).

Nor I get "/dev/ttyS0 unavailable or device busy" error. This is the default serial port I always used before (Ubuntu) before changing to xubuntu for performance reasons

I also get unable to RTS/DTS on tty ttyS1-S7 (which I didnt use before anyway) when I try using another serial port.

BTW - if no-one knows how to help fix this, could you please point me to another resource who can - rather than just leaving this post unanswered - as this is a major issue which may force me back to windows - as I must be able to program pic's!!!

---

### Post by pro-rsoft on 2008-01-19
Try running the application as root. I can access my ttyS0 port when I run ktechlab as root.

About not being able to access RTS/DTS, it's really odd.
In ktechlab, I can access DTS, but not RD, RTS or DSR. There's just no connection pin for that in ktechlab where I can attach a wire to. Anyone knows a solution for that?

---

