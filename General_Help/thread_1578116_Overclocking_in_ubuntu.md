---
title: "Overclocking in ubuntu"
date: 2010-09-19
forum: General Help
---

### Post by timinator94 on 2010-09-19
Hey all I have an ASUS G50VT-x1 my pll # is ICS9LPR363DGLF is there any way to change the fsb in ubuntu? I did it in windows 7 and got it up to 2.8ghz stable. Im running Ubuntu 10.10 x64

Thanks
Timinator94
P.S. No I dont have the bios options

---

### Post by cascade9 on 2010-09-20
As far as I know, nope. There arent any software overclocking tools for linux. 

Overclocking laptops is always more risky than desktops anyway, and does sort of defeat the purpose of a laptop in a lot of ways. ;)

---

### Post by timinator94 on 2010-09-20
Well its possible for the asus eee pc [http://www.sampletheweb.com/2007/12/30/overclock-your-asus-eee-pc-fsb-on-ubuntu/](http://www.sampletheweb.com/2007/12/30/overclock-your-asus-eee-pc-fsb-on-ubuntu/)

I realize the risk but you have to understand I only use a computer to optimize it and push it beyond the breaking point then putting it back together and pushing it again. THATS why I use linux. Not because I fear Bill Gates but because I love to be challenged. I play very few games and spend 99% of my time putting my computer back together again because of the consequences  of my latest experiment. So to overclocking I say HECK yeah give me a challenge! Let it burn than I'll fix it then burn it again! My computer is far from necessary in my life. School can be done on paper. Most games waste time. So whats a computer for? LEARNING through experimentation! You break it that just makes you want to learn to fix it. I LOVE trial and error it just makes success even sweeter!
The purpose of saying all this is because I understand the risk and am passionate about my computers and want to push them beyond the breaking point and getting maximum performance. Not for gaming just because I can.

timinator94

---

### Post by cascade9 on 2010-09-20
> **timinator94 said:**
> Well its possible for the asus eee pc [http://www.sampletheweb.com/2007/12/30/overclock-your-asus-eee-pc-fsb-on-ubuntu/](http://www.sampletheweb.com/2007/12/30/overclock-your-asus-eee-pc-fsb-on-ubuntu/)

Not really an 'overclock', its just moving it back up to 100Mhz FSB/900MHz CPU it 'should' have run at, not the 70MHz/630Mhz it came from the factory at. 

IIRC, there was a BIOS update that did the same thing. 

> **timinator94 said:**
> I realize the risk but you have to understand I only use a computer to optimize it and push it beyond the breaking point then putting it back together and pushing it again. THATS why I use linux. Not because I fear Bill Gates but because I love to be challenged. I play very few games and spend 99% of my time putting my computer back together again because of the consequences  of my latest experiment. So to overclocking I say HECK yeah give me a challenge! Let it burn than I'll fix it then burn it again! My computer is far from necessary in my life. School can be done on paper. Most games waste time. So whats a computer for? LEARNING through experimentation! You break it that just makes you want to learn to fix it. I LOVE trial and error it just makes success even sweeter!
The purpose of saying all this is because I understand the risk and am passionate about my computers and want to push them beyond the breaking point and getting maximum performance. Not for gaming just because I can.

timinator94

"Putting it back together again"? Huh? 

I've never had to rebuild any computer I've over(or under) clocked. 

BTW, once a CPU, or your chipset/RAM/etc, is 'burned' you not going to fix it. Also, if you push "beyond the breaking point" you have, by definition, broken it :lolflag:

---

### Post by timinator94 on 2010-09-20
> **cascade9 said:**
> Not really an 'overclock', its just moving it back up to 100Mhz FSB/900MHz CPU it 'should' have run at, not the 70MHz/630Mhz it came from the factory at. 

IIRC, there was a BIOS update that did the same thing. 



"Putting it back together again"? Huh? 

I've never had to rebuild any computer I've over(or under) clocked. 

BTW, once a CPU, or your chipset/RAM/etc, is 'burned' you not going to fix it. Also, if you push "beyond the breaking point" you have, by definition, broken it :lolflag: yup thats why I have 2 replacement mobos and 4 core2duos and TONS of ddr2 ram lying around in case of such an event. and actually the first time i tried overclocking it was a socket 939 and it cooked itself. but thats what pushed me to buy a laptop lol
so changing fsb not possible then huh? setfsb wont work in wine?

---

### Post by WorMzy on 2010-09-20
Have you tried [eee-control]("http://greg.geekmind.org/eee-control/")?

There's also [eeepc-linux]("http://code.google.com/p/eeepc-linux/"), which is apparently a kernel module deigned to give you similar functionality

---

### Post by Simian Man on 2010-09-20
> **cascade9 said:**
> Overclocking laptops is always more risky than desktops anyway, and does sort of defeat the purpose of a laptop in a lot of ways. ;)

Also, without many performance-intensive games, there are few reasons to overclock with Linux in the first place :).

---

### Post by timinator94 on 2010-09-20
> **Simian Man said:**
> Also, without many performance-intensive games, there are few reasons to overclock with Linux in the first place :).
I know that I don't game I just wanna:mrgreen: lol

---

### Post by cascade9 on 2010-09-21
> **timinator94 said:**
> yup thats why I have 2 replacement mobos and 4 core2duos and TONS of ddr2 ram lying around in case of such an event. and actually the first time i tried overclocking it was a socket 939 and it cooked itself. but thats what pushed me to buy a laptop lol
so changing fsb not possible then huh? setfsb wont work in wine?

*blinks* You blew a Socket939 so that 'pushed you to buying a laptop'? For overclocking? 

Insanity. Laptops never overclock as well as desktops (just to tight, smaller heatsinks, less airflow, etc) and its rare to find laptops with decent overclocking options in the BIOS. BIOS overclocking is a much better way to do things than from software..... 

A decent Core2Duo motherboard would have been a much, much better option than any laptop if you want to overclock.

I dont know for sure if setFSB will work in WINE, but I'll give it virtually no chance. 

> **Simian Man said:**
> Also, without many performance-intensive games, there are few reasons to overclock with Linux in the first place :).

Ripping video, slow older machines that getting a CPU upgrade for would be not cost effective, just because you can.  Theres lot of reasons to overclock. Its never without risks though.

---

### Post by Joe of loath on 2010-09-21
If you're willing to pop CPU's and memory 'for fun', send some my way, I can make much better use of it.

---

### Post by TNT1 on 2010-09-21
> **Joe of loath said:**
> If you're willing to pop CPU's and memory 'for fun', send some my way, I can make much better use of it.

+ 1. Send the rest of your spares my way.

---

### Post by Black_Tanto on 2010-09-21
> **cascade9 said:**
> As far as I know, nope. There arent any software overclocking tools for linux. 

Overclocking laptops is always more risky than desktops anyway, and does sort of defeat the purpose of a laptop in a lot of ways. ;)


There seems to be overclocking tools for Nvidia video cards which is usually more of a bottle neck than CPU in gaming.

---

### Post by cascade9 on 2010-09-21
> **Black_Tanto said:**
> There seems to be overclocking tools for Nvidia video cards which is usually more of a bottle neck than CPU in gaming.

Theres been NVClock for linux for years. Tools like NVclock are the only way to play with clocking on the nVidia cards, unlike CPUs that have BIOS overclocking.

---

### Post by timinator94 on 2010-09-21
> **cascade9 said:**
> Theres been NVClock for linux for years. Tools  like NVclock are the only way to play with clocking on the nVidia cards,  unlike CPUs that have BIOS overclocking.Ok will look into it  thanks. and my computer is a tool/toy I learn by messing things up. I  dont purposely cook stuff but sometimes thats what happens heck my droid  is overclocked and ive never fried it. Runs fast with my custom rom for  it. anyways dont think that im not careful but I am willing to take  risks on my personal computer. But I always have a backup when i need it  for school/work so all my experimenting happens on my asus. and i  needed to go to laptop anyways I moved into a trailer and dont really  have room for a desktop the cooking was just a push to get it faster

---

