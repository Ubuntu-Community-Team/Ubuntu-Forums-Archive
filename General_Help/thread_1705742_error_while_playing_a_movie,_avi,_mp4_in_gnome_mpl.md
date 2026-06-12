---
title: "error while playing a movie, avi, mp4 in gnome mplayer"
date: 2011-03-12
forum: General Help
---

### Post by hunterkasy on 2011-03-12
I am running 10.10 ubuntu 64 and I have been using gnome mplayer from the USC for quite some time, but lately I have been getting a error when I try to play a movie I took a screen shot of the error and I am attaching it to this thread

---

### Post by Joe of loath on 2011-03-12
Do you have an nVidia card and the nVidia proprietary drivers installed?

If not, check if there's an option like 'use vdpau' in the preferences menu.

---

### Post by hunterkasy on 2011-03-12
> **Joe of loath said:**
> Do you have an nVidia card and the nVidia proprietary drivers installed?

If not, check if there's an option like 'use vdpau' in the preferences menu.

I didn't find any option for (use vdpau) 

the computer I am using is Toshiba  L305-S5915

Graphics8
• Mobile Intel Graphics Media Accelerator 4500M with 128MB-830MB
dynamically allocated shared graphics memory

Processor and Chipset
• Intel Celeron Processor 575
o 2.0GHz, 1MB L2, 667MHz FSB
®
• Mobile Intel GL40 Express Chipset

Memory
• Configured with 2GB PC6400 DDR2 SDRAM

---

### Post by hunterkasy on 2011-03-13
anyone else have any other solutions?

---

### Post by mc4man on 2011-03-14
Try opening gnome-mplayer -> edit -> preferences and set the Video Output to xv, then close and retry on a vid

If still no go with same error (vdpau) then post 
~/.mplayer/config

---

