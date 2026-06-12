---
title: "how to get 3d effects on my laptop?? please help"
date: 2011-05-31
forum: General Help
---

### Post by MYEM on 2011-05-31
Hi Everyone,

Noob here sorry but I'm a newbie, and I really need your help PLZZZZ.... Finally I got ubuntu on my laptop and this is my first 
experience with Linux platform so I'm complete noob over here :(

While roaming around on you-tube i found some very cool effects on users system. How can I get the same??? I did some search on my own and I found that I need to have compiz (but I'm not sure what exactly is compiz :$). So how do i get that? + What system requirements are? + I found that I need to have a graphic card on my laptop. SO HOW CAN I CHECK EITHER I HAVE GRAPHIC CARD OR NOT :$

Your help is much more than appreciated .... and plzz whatever u suggest please take me from basic level as I'm complete noob over here :( and I need your help PLZZZZ.

Your kind and quick reply will be highly appreciated.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Here are a couple of guides.. First you want to make sure you got your basics cover here:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

And here is a great setup for effects:

[http://cinderbox.net/2011/02/23/video-tutorial-perfect-ubuntu-10-10-desktop/](http://cinderbox.net/2011/02/23/video-tutorial-perfect-ubuntu-10-10-desktop/)

---

### Post by Hedgehog1 on 2011-05-31
The details vary depending on what version of Ubuntu you are running.

Compiz itself it likely already loaded on your system; you just need to turn on the effects (assuming your video card can support them).

In the Ubuntu Software Center, search for 'ccsm' - then load the compiz settings manager.

Be aware that you should be very careful changing this settings in Unity, as you can break it.  However changing them the classic work fine.

***The Hedge***

:KS

---

### Post by MYEM on 2011-05-31
Thank You dear for your kind and quick replies.

Please note I have Ubuntu 11.04 and I have just recently installed the same on my laptop. As per my finding Compiz is already on my system but when I'm going to change my background place I cannot find the same over there so do i need to do anything extra??

Can you please do me a favor if U could plz check my laptop is compatible to use compiz? and what additional i have to do? the link of my laptop specification is as below:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=3999411&prodTypeId=321957&prodSeriesId=3999411&objectID=c01966161](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=125&prodSeriesId=3999411&prodTypeId=321957&prodSeriesId=3999411&objectID=c01966161)

Appreciate your kind and quick reply.

---

### Post by nzjethro on 2011-05-31
You should have a graphics card in your computer, especially if it is relatively modern. However, you may have to download drivers for it. These aren't installed default, as they are proprietary, meaning they are owned by the graphics card maker. Thus, some Ubuntu users (who are part of the open-source community) do not want to use software unless it is free and open-source.
To get to Compiz, click on System on your top bar, then Preferences, then CompizConfig Settings Manager. The 3d effects can be enabled from in here. For example, to enable the desktop cube, search for "cube" in the search box in ccsm, then click the little box by Desktop Cube (you may need to disable some other effect such as the desktop wall to enable this).
If you get stuck, YouTube has thousands of helpful howto Linux videos. This one's good, plus the person has a sexy voice! Haha.
[http://www.youtube.com/watch?v=LGY9cwSjZsU](http://www.youtube.com/watch?v=LGY9cwSjZsU)

---

### Post by nzjethro on 2011-05-31
Ah, disregard my above post then, it was for 10.10. Unsure what to do for 11.04, I'm staying away until they sort out the Unity issues, but I imagine that if you can access the CompizConfig Settings Manager it'd be similar. As for the laptop, looks like it should be fine. You'll find out if you don't have the grunt to run 3d Graphics when you try to get them started.:p

---

### Post by coffeecat on 2011-05-31
> **MYEM said:**
> I found that I need to have a graphic card on my laptop. SO HOW CAN I CHECK EITHER I HAVE GRAPHIC CARD OR NOT :$

The important thing is that you'll have a graphics chipset in your laptop, otherwise you wouldn't have any display at all! :) Let's see what you have - it'll be easier to advise with this information. Open a terminal and post the output of this command:

```
lspci | grep VGA
```

---

