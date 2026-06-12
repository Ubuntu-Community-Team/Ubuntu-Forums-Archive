---
title: "Help me making my Ubuntu Firefox 3.6 fonts look like IE7 or IE8"
date: 2010-01-29
forum: General Help
---

### Post by pimseb on 2010-01-29
Hello,

Almost everything is in the title :)
I'm  coming from windows and now I've switched to ubuntu. I find firefox 3.5  (and now 3.6) very hard to read.
I'd like to have the same font  rendering on my ubuntu than on my windows xp, using internet explorer with cleartype enabled.
I've  searched A LOT on Internet, tested like 20 different .fonts.conf. However I still can't get what I want. 
Take a look at my screenshots :
[http://box10.pulsradio.com/~pim2/enabled.png]("http://box10.pulsradio.com/%7Epim2/enabled.png")
[http://box10.pulsradio.com/~pim2/disabled.png]("http://box10.pulsradio.com/%7Epim2/disabled.png")

On  the left : ubuntu (Firefox 3.6) - on the right : XP (Internet Explorer  8)
I'd like to have the same fonts than on the right. 

Picture "enabled.png" is the closest display I can get. But it's still not perfect.
I took the .fonts.conf from this site : [http://notebook.andrewabogado.com/a-better-font-rending-in-ubuntu-0](http://notebook.andrewabogado.com/a-better-font-rending-in-ubuntu-0)

I've also tried the fonts from the site [sharpfonts.com]("http://ubuntuforums.org/sharpfonts.com")
Look here : [http://box10.pulsradio.com/~pim2/copie.png]("http://box10.pulsradio.com/%7Epim2/copie.png")
(this one is different : IE8 is on the left)

My  fonts config in firefox is the same than on windows (Times new roman,  arial, courrier new). And of course I've installed the ttf mscorefonts package.

I don't say that IE is the best thing in the world :) It's only because I've used it a lot and now it's hard to browse sites with different fonts.

I hope someone can help me ... :) thx

---

### Post by scouser73 on 2010-01-29
View the help on this page for getting a better rendering of fonts; [http://www.killertechtips.com/2008/04/10/how-to-turn-on-cleartype-in-ubuntu-linux/](http://www.killertechtips.com/2008/04/10/how-to-turn-on-cleartype-in-ubuntu-linux/)

---

### Post by pimseb on 2010-01-29
Hi,
Thank you but I know that and it's enabled.
But for some reasons, the changes made there don't apply in firefox browsing window.
It only applies in ubuntu menus

---

### Post by todak on 2010-01-29
Open a terminal and run the following: ```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by pimseb on 2010-01-29
the fonts are already installed like I wrote in the 1st post :)

---

### Post by todak on 2010-01-29
> **pimseb said:**
> the fonts are already installed like I wrote in the 1st post :)

Oops!:oops: Missed that part! I also just noticed that you are using firefox 3.6. I have found that the font rendering is not very good in firefox if you install from outside the ubuntu repositories. Look here [http://ubuntuforums.org/showpost.php?p=8739169&postcount=31](http://ubuntuforums.org/showpost.php?p=8739169&postcount=31) to see if this might help.

---

### Post by pimseb on 2010-01-29
I've recompiled my firefox using this thread : [http://ubuntuforums.org/showpost.php?p=8739169&postcount=31](http://ubuntuforums.org/showpost.php?p=8739169&postcount=31)
It's better but not perfect :)
screencap : [http://box10.pulsradio.com/~pim2/fonts.png](http://box10.pulsradio.com/~pim2/fonts.png)
Which one do you prefer ? I find the fonts too "bold" on the left
I don't know what exactly differs between both. Maybe it's a dpi problem ?
I attach my ~/fonts.conf

---

### Post by todak on 2010-01-29
Have a look at my screenshots. These settings work the best for my LCD monitor. Try them and see how they work for you. Just changing to **Best contrast** improved the fonts dramatically for me.

---

### Post by pimseb on 2010-01-29
thx :)
But got that already

---

### Post by The Cog on 2010-01-29
One thing to note is that when you change the font settings, although the Ubuntu application fonts change immediately, the fonts in firefox don't change to match the new settings until you close and restart firefox.

---

### Post by pimseb on 2010-01-29
I can make all the fonts changes I want in system/display, nothing is changing in firefox, even when I close and re-open the application.
Fonts are only changing if in firefox edit/preferences I uncheck the box "allow webpages to use their own fonts" (sorry my ubuntu is in french), which I don't really want to do :)

---

### Post by pimseb on 2010-01-29
> **todak said:**
> Have a look at my screenshots. These settings work the best for my LCD monitor. Try them and see how they work for you. Just changing to **Best contrast** improved the fonts dramatically for me.

Todak : where can I get the same fonts than you ? They are not included in my ubuntu. And I can't find them in the depots

---

