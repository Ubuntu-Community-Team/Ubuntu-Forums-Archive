---
title: "Can't get acidrip to rip to Mpg"
date: 2006-04-12
forum: General Help
---

### Post by koolguynet on 2006-04-12
I want to use acidrip to rip my dvd's to mpeg to use on my Nokia 770 Internet Tablet.  Everytime I select mpg in acidrip, it appears it is working fine, but the file it produces has choppy audio only.  Is there someone out there that has successfully ripped a movie to mpeg?

---

### Post by hw-tph on 2006-04-13
Did you notice that when you select .mpg container, in capital letters at the bottom of the screen it says "Filetype changed to .mpg - READ DEBUG COMMENT!"?

Anyhow, here is that comment:
> [i]AcidRip message - ********************
MPEG container selected. Please note that you MUST use a compatible mpeg1 video stream, select lavc video output, using vcodec=mpeg1video. For a useful output you will probably want to choose a suitable encoding matrix.for example, create a kvcd file with vcodec=mpeg1video:keyint=25:mbd=2:vrc_minrate=300:vrc_maxrate=2400:vrc_buf_size=320:intra_matrix=8,9,12,22,26,27,29,34,9,10,14,26,27,29,34,37,12,14,18,27,29,34,37,38,22,26,27,31,36,37,38,40,26,27,29,36,39,38,40,48,27,29,34,37,38,40,48,58,29,34,37,38,40,48,58,69,34,37,38,40,48,58,69,79:inter_matrix=16,18,20,22,24,26,28,30,18,20,22,24,26,28,30,32,20,22,24,26,28,30,32,34,22,24,26,30,32,32,34,36,24,26,28,32,34,34,36,38,26,28,30,32,34,36,38,40,28,30,32,34,36,38,42,42,30,32,34,36,38,40,42,44
And don't forget to set VALID scale values etc...[/i]

Or short version: Make sure you know your way around mencoder.


Håkan

---

### Post by koolguynet on 2006-04-13
That's the problem...I don't know my way around mencoder.  For instance, I don't know what a kvcd file is or what it does.   Any resources you could recommend on this?

---

### Post by hw-tph on 2006-04-13
Actually...no. I don't know my way around mencoder. I use AcidRip for ripping to Xvid (the default) with subs, and that's about it. There is [extensive documentation](http://www.mplayerhq.hu/DOCS/HTML/en/index.html) but I haven't tried to get my head around it.

For ripping to mpg I use [dvd::rip](http://www.exit1.org/dvdrip/) instead. It is very easy to use once you have it up and running (which can be a pain in the butt!).


Håkan

---

