---
title: "32-bit or 64-bit?"
date: 2010-11-16
forum: General Help
---

### Post by sharath.puranik on 2010-11-16
My friend wanted to install ubuntu on his acer aspire 4738Z. It has the following chipset.

> Intel® Pentium P6100 processor (3 MB L3 cache, 2.0GHz, 1066 MHz FSB, 35  W, supporting Intel® 64 architecture, Intel® Smart Cache Mobile Intel®  HM55 Express Chipset)

What I wanted to know was which version of ubuntu should I install, 32-bit or 64-bit?
He says he doesn't care about it...

---

### Post by kerry_s on 2010-11-16
64bit

---

### Post by TNT1 on 2010-11-16
32Bit.

---

### Post by mastablasta on 2010-11-16
depends on what he wants to do.
 
64 bit is fatser on 64 bit processors, however most applications are still 32 bit and might run even slower using 64 bit version.
 
for compatibility i would suggest 32bit, but you might also give 64 bit a go. depends really on what you/he will be doing in ubuntu.

---

### Post by yinji on 2010-11-16
i think he can choice 32bit

---

### Post by TNT1 on 2010-11-16
with only 3mb RAM, unless you are doing high end computations, you wont see much benefit by going 64bit. You will see a degradation in flash and such with 64bit during everyday use.

---

### Post by kerry_s on 2010-11-16
> **TNT1 said:**
> with only 3mb RAM, unless you are doing high end computations, you wont see much benefit by going 64bit. You will see a degradation in flash and such with 64bit during everyday use.

that's just fud. my flash has been perfect, the amount of ram you have don't matter. a lot of 64bit apps are just faster.

---

### Post by cascade9 on 2010-11-16
> **TNT1 said:**
> with only 3mb RAM, unless you are doing high end computations, you wont see much benefit by going 64bit. You will see a degradation in flash and such with 64bit during everyday use.

Ummm...3MB CPU cache, not RAM. With 3MB of RAM, your not going to do very much at all. 

BTW +1 to kerry_s, flash is running justfine in 64bit here. Though RAM does matter, and if there was only a limited amount of RAM, 32bit might be better (due to slightly lower RAM use by 32bit programs). How limited the RAM would need to be for 32bit to get in front is debatable.

---

### Post by TNT1 on 2010-11-16
> **cascade9 said:**
> Ummm...3MB CPU cache, not RAM. With 3MB of RAM, your not going to do very much at all. 

BTW +1 to kerry_s, flash is running justfine in 64bit here. Though RAM does matter, and if there was only a limited amount of RAM, 32bit might be better (due to slightly lower RAM use by 32bit programs). How limited the RAM would need to be for 32bit to get in front is debatable.

Ah, right, sorry, my mistake, read to quickly. 

On the flash thing, just search here and see the problems people have had.

---

### Post by migs73 on 2010-11-16
I would say you should look at the 64bit support for the peripherals you are going to use.

My PC can do 64bit but I use 32bit because the drivers for my printer are only 32bit and when forced on a 64bit are a bit flaky. 

I don't do any high end processing so 32bit satisfies all my other needs.

---

### Post by kerry_s on 2010-11-16
> **cascade9 said:**
> Ummm...3MB CPU cache, not RAM. With 3MB of RAM, your not going to do very much at all. 

BTW +1 to kerry_s, flash is running justfine in 64bit here. Though RAM does matter, and if there was only a limited amount of RAM, 32bit might be better (due to slightly lower RAM use by 32bit programs). How limited the RAM would need to be for 32bit to get in front is debatable.

i ran 64bit with 512mb ram when i first built this pc, it ran just fine, later i upgraded to 1gb & just last month i maxed it to the 2gb.
the kernel is adaptive, it will use less if theres less to use & more when available. at 512mb it was around 200mb used, 1gb & 2gb ram use has been around 300mb.

---

### Post by sharath.puranik on 2010-11-16
I tried to install 64-bit Meerkat, didn't wok, was only going to command line, tried a few workarounds, none of them worked, so I dumped it and installed 64-bit Lynx. I set it up beautifully for him and was feeling really happy about it.
I went through all this trouble and now he tells me that he is going to use ubuntu only to prevent viruses from breaking into his system. :mad:

I was this close to breaking his nose. ](*,)

Now if he tries to do something that only works in 32-bit, I hope he struggles a bit to realize what is going on :D

---

### Post by TBABill on 2010-11-16
He should be fine like that. 64 bit used to be flaky but with flash improvements and a good 64 bit version of flash (compared to older Linux versions) it works great for me on several machines with different hardware configurations. He may never even notice which he has unless he searches.
 
By the way, if you installed ubuntu-restricted-extras, you did NOT install the 64 bit version of Flash so it's a 64 bit OS using a 32 bit version of flash...not the greatest. Lovinglinux's Flash-Aid Firefox extension takes care of swapping them out and keeping the flash version up to date....just mentioning in case he calls asking about Flash.

---

