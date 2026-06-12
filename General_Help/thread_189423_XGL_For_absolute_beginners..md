---
title: "XGL For absolute beginners."
date: 2006-06-05
forum: General Help
---

### Post by Over Haze on 2006-06-05
Basically what the title says, I’m still new to Linux and find XGL a bit mystifying. I’m honestly not sure how to get it up and running when my Ubuntu discs arrive nor am I sure if my PC is up to running it (AMD 64 3200+, Radeon Xpress200 integrated graphics and 1g of RAM). Any advice you could give me would be greatly appreciated.

---

### Post by unf on 2006-06-05
[QUOTE=Over Haze]Radeon Xpress200 integrated graphics[/QUOTE]
buy nvidia

---

### Post by blackjack6.21.91 on 2006-06-05
I don't think XGL is supported by Radeon.  ~That doesnt mean you have to go buy nvidia, unless you bought your system specifically for XGL~

---

### Post by Over Haze on 2006-06-05
No I didn’t, Its just with Vista coming out next year I’m thinking of ditching Windows for Linux. So there is absolutely no way to get XGL running with a Radeon graphics card?

---

### Post by nicolastheadept on 2006-06-05
i've got it working on my Radeon x1600pro and quite easily I used easy ubuntu for the drivers and then this script:  [http://ubuntuforums.org/showthread.php?t=147049&highlight=xgl+ati]("http://ubuntuforums.org/showthread.php?t=147049&highlight=xgl+ati")

---

### Post by zitch on 2006-06-05
XGL can work on an ATI Radeon.  I've got it working mostly stably on my laptop, which has a ATI Mobility Radeon 9600.

I ended up following the following wiki to get XGL/Compiz just installed on my laptop: [https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl)

I'm not an absolute beginner, and it still took 4-5 days of debugging, reading articles and the forum, and experimenting to get it to a useable state.  It's not something that can be trivially installed and setup, especially for Radeon users, from what I'm reading around and my own experiences.  Remember that XGL is still under development and is not recommended for general use in a production environment (though I'm using it in one... ;) ).

I'm not trying to discourage you, though.  If you have the patience (and time!) to read these guides and the forums and are willing to experiment and even wiping your system to start over (I.E., it's not a production computer or you don't have important info that you have to have...), this hard work pays off with you having one of the most unique looking desktop among your peers (Well, your non-"Mac OS X"-using peers... :) At least they don't have the cube... well, out-of-the-box they don't.) and, more importantly, this sense of accomplishment that your hard work produces.

So, go ahead and try out the guides and see where you get to.  If you get stuck, don't be afraid to ask questions here.  If you find them lacking and manage to get your own system working with XGL, try contributing back to the community and writing your own "XGL for absolute beginners" guide... ;)  And most importantly, don't get discouraged.

---

### Post by Over Haze on 2006-06-05
Thanks for the advice. Hopefully this distribution of Ubuntu will run on my PC so I actually get the chance to experiment! (I never could get 5.10 to run). One of these days in going to have to buy a Mac but I dang sure want a Linux box as well.

---

### Post by onesojourner on 2006-06-05
provided your computer has a free agp slot you can get a cheap nvidia card. I swapped out my ati card for an nvidia 5200 (64mb) and that cost about 25 bucks. it really took about 15-30 minutes to have xgl compiz up and going. I have not gone in depth with it. but so far everything is running smooth. 

ps if you dont have any experience with computer hardware upgrades, dont let it scare you off. putting in a video card is one of the easiest things you can do. take the side panel off push it in and your done. if you want to know what your agp slot speed is (in windows) google cpuz. download the small .exe and run it.

---

### Post by Over Haze on 2006-06-05
No AGP slot. My PC features PCI-Express, way o’ the future!

---

### Post by denjin on 2006-06-05
[quote=Over Haze]No AGP slot. My PC features PCI-Express, way o’ the future![/quote]
It works with ATI anyway.  My work laptop has an x600 in it and I run Xgl.  But, it supposedly runs better and is more stable if you have an Nvidia card.

---

