---
title: "CPU load seems really high"
date: 2010-07-21
forum: General Help
---

### Post by DManX04 on 2010-07-21
I've been having some problems with my system consistently lagging lately, and I was wondering if anyone could give me any advice.

Here are my symptoms:
1) CPU usage after a reboot is consistently between 20-30%, even when no other programs are running. It gets as high as 70-80% if I've got a few programs running (typically OpenOffice, Firefox, File Browser, and Skype or a PDF viewer).
2) Approximately every 10-30 seconds I get some type of screen freeze up that lasts a second or two. For example, I'll be moving my mouse, and it will stop for a moment before jumping across the screen, or I'll be typing something and the letters will stop appearing on the screen briefly and then suddenly the entire sentence will show up. This happens most frequently when I'm scrolling up or down in windows, whether I'm using the scroll bar on the window or on my touchpad.
3) I've run top, and, even with Firefox running two windows with a few tabs each, only 5 or 6 programs are using the CPU, with none listed at more than 7%. Most are typically shown below 4%. Earlier I did have one Firefox window with like 10 or 12 tabs open, and npviewer.bin was using 80-100% CPU.

This all started a few weeks ago, and it has been getting worse. I can't think of anything I've added, but I did remove a bunch of the alternative flash players one day (gnash, swfdeck, etc.) and re-installed just Adobe Flash. That was several weeks ago, though, and the problem has only gotten out of hand in the last week or so.

---

### Post by mike555 on 2010-07-21
more info on make , etc. might help us help you ........ also does it run hot ? is swap being used ?

---

### Post by DManX04 on 2010-07-21
> **mike555 said:**
> more info on make , etc. might help us help you ........ also does it run hot ? is swap being used ?

I'm not sure what all you need to know, but if I leave anything out, just let me know.

Lucid 10.04 on:
Dell Inspiron 1720
2.2GHz Intel Core 2 Duo
NVidia graphics card with proprietary driver enabled
2GB RAM
20GB available on 30 GB partition
Dual booting Windows Vista
2.2GB Swap Partition

I don't know how to tell if it's running hot other than by feel. At times it does feel quite a bit warmer than it used to, but other than that I don't know.

Is there anything else I can tell you that might help?

---

### Post by DManX04 on 2010-07-21
Any ideas?

---

### Post by DManX04 on 2010-07-28
So I just experienced a rough bout of lagging and unresponsiveness, and I ran top to see what was up. The high CPU users were firefox-bin, X-org, and npviewer.bin. Each is using at least 20-25%, and at times one or two will jump to 70-80%.

Any suggestions? Is there any hard disk maintenance I could try or temp files I could clear.

---

