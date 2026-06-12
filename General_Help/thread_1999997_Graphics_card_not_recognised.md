---
title: "Graphics card not recognised"
date: 2012-06-08
forum: General Help
---

### Post by Intzi1992 on 2012-06-08
Hi Guys...

I installed Ubuntu on my Laptop..
But i have a problem with the graphic card. Its not recognised
And i read on forums that my card is not supported any more.
Graphics Card Is : M56P [Radeon Mobility X1600].


I Show some posts about Downgrade and other.
Can i do something ?

---

### Post by BeenLikeFlynn on 2012-06-08
Getting an updated Graphics Card may solve the dilemma. Follow instructions on integrating the graphics card into ubuntu/linux is another, less costly option.:popcorn:

---

### Post by papibe on 2012-06-08
Hi Intzi1992.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```
Regards.

---

### Post by Intzi1992 on 2012-06-09
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M56P [Radeon Mobility X1600] [1002:71c5]
    Subsystem: ASUSTeK Computer Inc. A6J-Q008 [1043:10b2]
    Kernel modules: radeon

---

### Post by Intzi1992 on 2012-06-09
Any ideas?? pleasee :)

---

### Post by papibe on 2012-06-09
Your system is recognizing your card (Radeon Mobility X1600), and loading the correct driver to handle it (radeon).

Could you describe the problem you are having?

Regards.

---

### Post by Mark Phelps on 2012-06-09
I really wish Canonical would simply REMOVE System Info from Ubuntu ... there would be a lot fewer "my card isn't recognized" posts ...

Your card IS recognized, otherwise, you would not be seeing a desktop; you'd be stuck in a command line.

You have an OLD card, one for which proprietary ATI Linux drivers were dropped years ago.

You're running the generic open-source Radeon driver  That is the only driver that will work with your card.

---

### Post by Intzi1992 on 2012-06-09
"You're running the generic open-source Radeon driver That is the only driver that will work with your card."
Can you please tell me how can i install an open-source driver?


The problem with my Pc is that colors are awful
And i cant play very low graphics games, like facebook games
And last one at "System info" says that graphics card is : Unknown.

---

### Post by Intzi1992 on 2012-06-09
Nothing Guys ? :(

---

### Post by Cheesemill on 2012-06-09
> **Intzi1992 said:**
> "You're running the generic open-source Radeon driver That is the only driver that will work with your card."
Can you please tell me how can i install an open-source driver?
It's already installed, there is nothing for you to do.
> The problem with my Pc is that colors are awful
And i cant play very low graphics games, like facebook games
And last one at "System info" says that graphics card is : Unknown.
That's a bug with 'System Info', it always says that.

As stated above ATI stopped writing Linux drivers for that card years ago, and the old drivers it did write  will no longer work with modern Linux distributions. You are already using the only driver that is available for that graphics card.

---

### Post by Ubun2to on 2012-06-09
I think it's probably time to upgrade. I bought a new video card for $30 on Amazon.com for my desktop. Getting a new video card for a laptop I think would price about $40-50, plus a little install cost unless you can squeeze it into the laptop case (which is extremely cramped-very little expansion room, and it can be hard to figure out which card is for what).
Generic drivers are as good as it will get.

---

### Post by Intzi1992 on 2012-06-10
First of all i dont know if my laptop can change graphics card,
and second i think its time of buying a new laptop and not just graphics card. :)

---

