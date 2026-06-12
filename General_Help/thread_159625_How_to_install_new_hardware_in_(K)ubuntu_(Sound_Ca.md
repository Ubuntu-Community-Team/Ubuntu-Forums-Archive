---
title: "How to install new hardware in (K)ubuntu? (Sound Card Installation)"
date: 2006-04-13
forum: General Help
---

### Post by Koprocessor on 2006-04-13
Hello friends,

this is my first post in this forum and also my first (and last) disclaimer: I'm spanish so please don't hit me because of my english. ;) 

I've got the following question: does anybody know if there is or will be some kind of tool that detects if you have a some new hardware installed? Like in Windoze when you install something new it detects it automagically.

Kubuntu is working extremely well, especially compared to other distributions I've used. I've been using linux sporadically for about 5 years or so, but know I think I'm REALLY switching to it, thanks to this great distro. It works GREAT on my laptop (Acer Travelmate) as well as on my desktop PC.

The only issue I've had was installing an additional soundcard. When I installed the computer setup was the following:

Motherboard nForce2 Infinity
Seagate Barracuda 160 GB HDD
1 Gb Elixir RAM (works great for me on Dual Channel - 2x 512MB)
PCI Cards:
- Geforce 6800
- Hauppauge TV Theater (Bt878 )
- Audigy LS

**THEN** I wanted to **ADD** my old(er) SoundBlaster Live! - Here is where the problems began. At first the problem only was my MoBo which didn't assign the card a correct IRQ. Till I found out that Slot 4 was working well with that card (I didn't want to mess up my BIOS with assigning IRQs by myself).

But although "lspci" indicated everything as being correct ALSA wouldn't detected my card. So after reading through Zillions (well ok ... about 10 or 20 ;)) of How-Tos and other documents, checking alsamixer, alsa-utils and alsactl (why isn't there **alsaconf** on (K)Ubuntu?) nothing worked.

I decided to go the not-so-elegant-way, I made a partition Image of the root-partition so that I could restore it if necessary and **installed Kubuntu from zero.** Voilá, it happend what I suspected - it detected my SB Live! and ALSA put up all my cards showing me this

> 0 [Live           ]: EMU10K1 - SBLive! Player 5.1 [SB0060]
                     SBLive! Player 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xc000, irq 17
1 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xe0001000, irq 19
2 [CA0106         ]: CA0106 - CA0106
                     Live! 7.1 24bit [SB0410] at 0xc800 irq 18
3 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x300, irq 5

Now the main question is: **How do you do that WITHOUT reinstalling everything? **Especially for people that don't have lot's of time.

I hope anyone wants to read through all this and give me his opinion. I would be VERY thankful. :)

Greetz and long live (K)ubuntu. ;)

---

