---
title: "Lucid Triple Monitor - 2nd GPU not recognized"
date: 2010-05-14
forum: General Help
---

### Post by erflol on 2010-05-14
Hello all
I have recently upgraded to Lucid with a clean install. I have two NVIDIA GeForce 7300GT cards with 3 21" monitors connected to them (two to card 1, 1 to card 2 although sometimes I plug in my projector so its 2 to both).

I previously had Karmic installed and was able to use all three (or four) monitors without any problems. Now, however, Nvidia-settings only recognizes the one GPU. It will only recognize one or the other. If I edit xorg.conf so that Screen0 is on PCI:3 instead of PCI:1 (where my two cards are located) It will switch over to that GPU, but I can not get both to work together at the same time.

I have tried using my old xorg.conf but it does not work. I've tried editing the current xorg to have one monitor running off of each card and it will not work. 

When I run lspci it does recognize the cards:
01:00.0 VGA Compatible Controller
03:00.0 VGA Compatible Controller

Any insight would be appreciated. Just ask if you need more information, or need me to post log files or my xorg.

Thanks
Cheers

---

### Post by n1wil on 2011-03-05
I too am having this same exact problem on Lucid.  Can anyone please help?  Would like to get my 3rd screen running again.  

I have a similar config as this guy.  3 monitors (2 on first GPU, 1 on 2nd GPU) and the second GPU is not able to activate.  

This worked in the previous release: 9.10

Thanks

---

### Post by erflol on 2011-03-05
The problem, if I remember correctly was with the nvidia drivers. I ended up downgrading back to 9.10. I am still currently using 9.10

My intentions are to upgrade to 11.04 when it is released. 10.10 works beautifully on my other two computers and my laptop, it's just a shame there were so many difficulties getting the triple monitors to work on 10.04, and the timing was wrong for me to upgrade to 10.10.


Cheers
eRflol

---

