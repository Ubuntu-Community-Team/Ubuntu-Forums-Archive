---
title: "NTB Fast New Desktop -- Ubuntu friendly"
date: 2010-12-08
forum: General Help
---

### Post by wannabegeek on 2010-12-08
Hi all

I have another part time job setting up a network of new computers in a research 
lab. I have limited experience but since they pay so little I feel qualified :)

Main point:

I am charged with buying a brand new desktop machine. It's primary use will be to run
MATLAB and FFTW. Ubuntu appears well supported for FFTW and I plan to use it 
rather than centOS, which the rest of the science department uses.

My plan is to buy a fast 2 core desktop machine.

I need some advice as to what high end machines run Ubuntu 10.01 out of the box and 
are considered highly reliable.

thank you,
wbg

---

### Post by cascade9 on 2010-12-08
'High end' machine with a dual-core? Not anymore. They have all gone quadcore (or higher). 

Can you build your own machine (thats almost always better, you can pick exactly what you want)? If not, can it be a custom built machine, or does it have to be a 'corporate' machine (dell, compaq, HP, etc)?

---

### Post by wannabegeek on 2010-12-08
thanks for reply Casade9,

I have never built a computer myself or had one built for me. That maybe a good idea.
Perhaps I should not have written 'high end' since one might think were doing some hardcore simulations.

The machine I need to buy in the near future is mainly for running long MATLAB jobs and processing a lot of FFT's using FFTW.

Do you know if MATLAB's parallel toolbox and FFTW work well out of the box with a quad core ?

thank you very much,
wbg

---

### Post by wannabegeek on 2010-12-08
Anybody ever bought a n Acer Veriton core i5 650 3.2 GHz machine and ran Ubuntu on it ?
 [URL="http://reviews.cnet.com/desktops/acer-veriton-x498g-ui5650c/4505-3118_7-34147117.html"] 
 [/URL] 
 [B][U][URL="http://reviews.cnet.com/desktops/acer-veriton-x498g-ui5650c/4505-3118_7-34147117.html"] [B]
[/B]

[/URL][/U][/B][ ]("http://reviews.cnet.com/desktops/acer-veriton-x498g-ui5650c/4505-3118_7-34147117.html")

---

### Post by cascade9 on 2010-12-09
> **wannabegeek said:**
> thanks for reply Casade9,

I have never built a computer myself or had one built for me. That maybe a good idea.
Perhaps I should not have written 'high end' since one might think were doing some hardcore simulations.

The machine I need to buy in the near future is mainly for running long MATLAB jobs and processing a lot of FFT's using FFTW.

Do you know if MATLAB's parallel toolbox and FFTW work well out of the box with a quad core ?

thank you very much,
wbg

Honestly, I'm finding tracking down FFTWs and MATLABs features a bit difficult. Its not as clear as most other things if they will use multipule cores, but I'll do a bit more digging later. 

As fr the Acer Veriton i5 650...I wouldnt. Its a tiny case (hard to do any expansion later), tiny power supply (220watts) and the prices I found for it was $700 odd. 

I'd look at something from ibuypower- 

[http://www.ibuypower.com](http://www.ibuypower.com)

You can get a better spec machine from them for the same, or even less money. 

 BTW, even if MATLAB and FFTW wont use quadcores, the newer quad core i5s still mightnt be a bad idea. They have twice the CPU cache of teh older models (4MB for i5 x2, 8MB for i5 x4). Even though they max frequnce is lower on the quad cores (i5 760 X4 =2.8GHz, 3.33GHz in 'turbo' mode, i5 650 = 3.2GHz, 3.46GHz in 'turbo' mode) the extra cache should help with heavy number crunching.

---

### Post by wannabegeek on 2010-12-09
good advice....I was worried about the case size, then kinda forgot about it...that would suck b/c
I'm pretty sure I'm gonna need to put in some data aquisition cards at some point...

ibuypower not an easy site to navigate...

I'm thinking quad core partly because I envision MATLAB, MPB/FFTW and some other program running simultaneously...even though one would think they would run in serial.....to keep the analysis 
moving along, parallel instances might be what happens in the end...

if that even makes sense...I'm definitely using my 'instincts' on this...which could be wrong

cheers
wbg

EDIT: I tried reading about MATLAB's parallel processing toolbox...not clear to me if it will automatically use two cores on routine functions like FFT or 
plots withs lots of data points.

---

### Post by cascade9 on 2010-12-12
> **wannabegeek said:**
> ibuypower not an easy site to navigate...

I'm thinking quad core partly because I envision MATLAB, MPB/FFTW and some other program running simultaneously...even though one would think they would run in serial.....to keep the analysis 
moving along, parallel instances might be what happens in the end...

if that even makes sense...I'm definitely using my 'instincts' on this...which could be wrong


If you're thinking about running MATLAB, FFTW, and poissibly other programs, I'd be looking at a quadcore for sure. 

I tried to track down more information on MATLAB and FFTW, but I failed. Pity, its always good info to have. Besides that, some programs run better on intel, some on AMD. Since the AMD chips are a fair bit cheaper, its always good if you can get a cheap AMD performing the same, or beter, than a intel chip. 

Hmm, the ibuypower site doesnt seem that confusing to me. Maybe I've poked far to many hardware sites :S 

Easy way to get a decent system from intel from ibuypower is to mouse over "desktop-> intel-> core P55 i5/i7" then click on  "core p55". Then click on "customise" on the top left system (Inel Core P55 i5/i7) and you can customise the system. 

For an AMD system its a bit more complicatied, if you've got any intrest in a AMD system I'll post directions.

---

### Post by wannabegeek on 2010-12-12
you've done quite a bit for me, thank you cascade...
I found out that a local shop in SF, Central Computers, has a government account 
and many professors get there 'semi custom' built computers there for a reasonable price..

So I'm thinking of an i5 with big power supply (550W was a suggestion) big case etc...

I'm very excited to run the lab on Ubuntu 10.04 ! and a wondoze machine for GPIB interfacing
some bench equipment...

thanks again for your efforts and advice,
wbg

---

### Post by cascade9 on 2010-12-12
No problems.

One last thing- its a really good idea to have a good power supply. Currently I think that the seasonic or corsair power supplies are the best.Well IMO anyway and out of what is easily avaible and dont cost stupid amounts.....If you really want 'the absolute best' power supply you can get, "PC power and cooling" used to be it , but you really paid for them.

---

