---
title: "Toshiba laptop will not work beyond Kernel 2.6.31 (9.10 default)"
date: 2010-11-17
forum: General Help
---

### Post by patman023 on 2010-11-17
Hardware: [Toshiba Satellite C650D (Model PSC16C-00P00M) -]("http://www.futur*****.ca/en-CA/product/toshiba-toshiba-satellite-15-6-amd-athlon-x2-p320-laptop-c650d-00p-black-future-shop-exclusive-c650d-00p/10145890.aspx?path=f0bfcfbaadf87afc1bc15b8114552d49en02") 

As the title says - Anything past 2.6.31 will not work - I get somewhere from .5 to 10 seconds into boot, and get the string <c0104087> kernel_thread_helper+0x7/0x10

It freezes. cursor flashes, but will not take input. I can't do the standard Alt-PrScr REISUB so I know it hasnt even booted... 

i understand there's a Toshiba setting somewhere in the kernel, and that i'd have to compile my own to enable it, but I've also read that it does not work on a Phoenix BIOS (what i have).

I was directed at kernel.org to do a git-bisect between 2.6.31 and .32, but I figured SOMEONE would have knowledge of a fix here...

Help? 

P

---

### Post by Vigh on 2010-11-17
you using 32-bit or 64-bit, i am successfully running maverick 10.10 on an oldish cheap Toshiba successfully but when I ran 64-bit it would report a bios feed-back loop error and fail to boot, installing 32-bit solved this problem

---

### Post by patman023 on 2010-11-17
good question - it's a 64-bit processor (the link above is to Future Shop's website), I've tried both 32 and 64-bit variants...

---

### Post by Vigh on 2010-11-17
could try a bios-update, which from experience, is a real head-ache with Toshiba, if its not running a windows OS, if you can and have a windows machine, log-on to that and try to make a bios update cd, so you dont have to do it from within windows, update by booting from the cd, hopefully it fixes the problem, not 100% sure what else you could do

Toshiba Models I have successfully run Ubuntu on->

Toshiba PORTEGE M800- no problems
Toshiba L500D- network problems- fixable

---

### Post by patman023 on 2010-11-17
it's a brand-newish model, released late August... no BIOS updates I've found, but it's a dual boot at the moment for school (i MUST run AutoCAD, no opensource allowed :-( )

---

### Post by gandaran on 2010-11-17
> **patman023 said:**
> it's a brand-newish model, released late August... no BIOS updates I've found, but it's a dual boot at the moment for school (i MUST run AutoCAD, no opensource allowed :-( )
try contacting Toshiba, I think you do need to update BIOS, I had the same problem with my Toshiba netbook which would work only up to Ubuntu 8.10
updating BIOS solved the problem for newer kernels and was in fact very easy to do, just run the .exe BIOS file in windows.

---

### Post by patman023 on 2010-11-17
FIXED! they released a BIOS update right in the middle of my mid-terms...

---

