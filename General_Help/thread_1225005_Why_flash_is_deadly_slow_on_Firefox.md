---
title: "Why flash is deadly slow on Firefox?"
date: 2009-07-28
forum: General Help
---

### Post by aneganov on 2009-07-28
Hi all! 

I'm using Linux (Ubuntu) for work (I'm a web developer) and for browsing the internet. Then problem is that I can't smoothly browse websites which use Flash. This is just crazy, as these sites makes my computer alsmost dead. So I also can't continue work if a website with many flash banners is opened. 

Visiting a website with Flash banners or Flash content makes FF to eat about half of CPU and Xorg is eating the rest on my system (with Intel integrated 82945G/GZ  Controller). My system is:

Ubuntu: 9.04
Firefox: 3.5.x
Flash: 10, Adobe
CPU: Intel(R) Pentium(R) D CPU 3.40GHz
RAM: 3Gb

Same applies to previous versions of Ubuntu, Firefox and Flash plugin and computers - 
I have two more - both with Ubuntu, one with AMD Athon 4k+ and another is a brand new Acer notebook with Intel CPU. 

To understand, feel, estimate, realize what I'm talking about, please visite this page: [http://www.gq.ru/magazine/?year=2009](http://www.gq.ru/magazine/?year=2009) and see how your computer behaves. Try for example to scroll page down and up, upon page loading, hehe...

Question is - why flash is slow and who is in charge - Firefox or Adobe or Ubuntu? 
How to get this FIXED?

---

### Post by QIII on 2009-07-28
If you are sure you have Adobe Flash installed, remove gnash and swfdec as they will cause conflicts.

You can do that via Synapic if you are interested in the GUI method.  If you are at all familiar with the terminal, you should be able to do this from there with apt-get remove --purge filebelow

Search for swfdec-gnome and swfdec-mozilla and remove them.

Search for the gnash components and remove them.

Make sure that flashplugin-installer is checked.  That will install the Flash plugin when you hit a Flash site.

---

### Post by Aizawa on 2009-07-28
Not the most helpful reply coming up, but just to confirm that it doesn't have anything to do with Firefox, I went to that site and I didn't get a performance hit.

---

### Post by aneganov on 2009-07-28
> **QIII said:**
> If you are sure you have Adobe Flash installed, remove gnash and swfdec as they will cause conflicts.

Thank you, QIII, for quick reply.

I have neither swfdec-gnome nor swfdec-mozilla or gnash installed. And never had, actually.

---

### Post by aneganov on 2009-07-28
> **Aizawa said:**
> Not the most helpful reply coming up, but just to confirm that it doesn't have anything to do with Firefox, I went to that site and I didn't get a performance hit.

Thanks for test. Have you checked `top`? Have you any flash/Ad blockers enabled?

---

### Post by Aizawa on 2009-07-28
I have no such plugins, it works perfectly well :)

---

### Post by aneganov on 2009-07-28
Hello again, Lucky Aizawa

> **Aizawa said:**
> I have no such plugins, it works perfectly well :)

Ok, please tell you results on this test:

[http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html](http://www.craftymind.com/factory/guimark/GUIMark_Flex3.html)

(After loading the page, press Run Test button to the upper left, and wait about 10 seconds, a page with results will open)

My results: [http://www.onlinedisk.ru/view/186801](http://www.onlinedisk.ru/view/186801)

And what CPU you own?

---

### Post by Aizawa on 2009-07-28
Sorry for the slow response, was doing other things.

I get around 30fps.

EDIT: I have a core 2 duo, overclocked to 3.6ghz.

EDIT2: I'm not awfully good with computers, but wouldn't the graphics card play a bigger role? I use proprietary drivers, ATI HD4850.

---

### Post by aneganov on 2009-07-28
> **Aizawa said:**
> Sorry for the slow response, was doing other things.

I get around 30fps.

Nice, congratz! :)

(Of course, not like on Windows where test runs on 50fps on avarage machine, but much better then my results)

> EDIT: I have a core 2 duo, overclocked to 3.6ghz.And this looks like the key difference for me.

> EDIT2: I'm not awfully good with computers, but wouldn't the graphics card play a bigger role? I use proprietary drivers, ATI HD4850.

I'm not a guru either :) I'm using intergrated Intel with free drivers and graphics suffer here all the time, more or less. But I personally guess the total impact is about several percents - with better card my 15fps becoming 20fps at max or so :)

---

