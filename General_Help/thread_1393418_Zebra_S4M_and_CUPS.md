---
title: "Zebra S4M and CUPS"
date: 2010-01-29
forum: General Help
---

### Post by tpmoney on 2010-01-29
So I have a Zebra S4M label printer that I have managed to get mostly working under CUPS. To make that work, I have the printer upgraded with the latest firmware, CUPS 1.4.1 with its AppArmor profile disabled and the Zebra EPL/ZPL ppd file that's floating about the internet loaded into cups.

The printer is connected via USB to the computer, and is set up in cups using ZPL. The computer acts as a print server for other computers, and everything seems to work ok, with one exception.

When the printer runs out of paper or runs out of ink ribbon, the printer stops and displays an error on screen, but CUPS never stops. It keeps taking jobs, sends them to the printer and reports that everything is A-OK. It appears at a certain point, the printer's memory gets full and then CUPS sort of hangs, but it still doesn't display and errors or stop the quque, it just starts this weird behavior where it eats jobs or combines them into one giant job that it just sits on.

What I need is for CUPS to know that the printer is out of paper or ribbon and pause the queue until the error status is clear. I know that this printer is communicating its status in some way, as when it's connected to a windows machine, the print queue stops when the paper runs out.

Does anyone have any ideas on getting CUPS to recognize the printer status so that I'm not losing jobs? I've tried digging through the debug logs but there doesn't seems to be much help there. I do notice that from time to time CUPS says it's discarding "unused printer status changed" and "unused job progress" events but other than that, nothing I see of interest.

---

### Post by ghreyes71 on 2010-04-05
@tpmoney:

Have you solved this problem?

GHReyes

---

