---
title: "Outrageous CPU Usage"
date: 2009-09-23
forum: General Help
---

### Post by terrorhawk on 2009-09-23
Hey guys I'm just wondering if someone could answer some questions and maybe provide a fix (*if at all possible*) to an issue I've been noticing...

Lately, when I go on YouTube to watch videos (*on Chrome and Firefox alike*) they both make my CPU usage skyrocket.

I know that when loading pages, opening large(r) documents, doing work, etc, that can make the CPU usage spike for a second while it works... but this is continuous. I'll load a video all the way through (*I even used to do that in Windows, cause I have a semi-slow internet connection I guess*) and the "problem" still persists.

I'm using an Intel 82845G integrated graphics card. Might that have anything to do with it? I've seen people on other non-Ubuntu forums say "change blah blah blah in the xorg file" or something, but I'd rather get a more straightforward answer on a personal level.

My computer isn't too slow by any means. Ever since completely switching to Ubuntu 9.04 I've seen performance go back to normal on even this older model Dell Dimension when, with Windows, it would bog down over time. I'm happy, overall, but I'm just curious to see if anyone can help.

Thanks for any help!

---

### Post by Compintuit on 2009-09-23
Flash videos take a ton of resources. It looks like you have a nice system, but they are flash... When watching a video elsewhere, doesn't it take a lot of resources there too? Flash is usually about twice (the resources) a video in mplayer, for me. I'm not sure if flash even uses graphics chips - I always though it was just done with the cpu. Loading the video is quite easy compared with playing it. 

Also, at least for me, flash performance improved about 50% when I switched to karmic. You could try that, though it's broke thrice on me.

---

### Post by terrorhawk on 2009-09-23
Damn it... I always forget to add certain, maybe useful, information.

EDIT:

I also have noticed that with certain websites (MySpace, certain ComputerWorld pages, etc) the CPU usage stays high. I notice that when that happens it seems to be because of the large amount of Flash ads/content that continuously plays on that page and that it may overload it.

Is that normal? Am I wrong? If I'm not, how can I fix these issues?

---

### Post by terrorhawk on 2009-09-23
> **Compintuit said:**
> Flash videos take a ton of resources. It looks like you have a nice system, but they are flash... When watching a video elsewhere, doesn't it take a lot of resources there too? Flash is usually about twice (the resources) a video in mplayer, for me. I'm not sure if flash even uses graphics chips - I always though it was just done with the cpu. Loading the video is quite easy compared with playing it. 

Also, at least for me, flash performance improved about 50% when I switched to karmic. You could try that, though it's broke thrice on me.


Yeh I just added that I think it's Flash stuff that's causing my high CPU usage problems. When you switched to 9.10, did you honestly see better Flash performance on your system?

---

### Post by Compintuit on 2009-09-23
Yes, much better - I benefited from some new intel drivers, though. If you don't like the adds (and who does?) install the addblock extension. It does wonders for performance. If it is .gif's hit escape to stop them. It's normal for flash to take a ton of CPU; it does on windows, though not quite as much.

---

### Post by terrorhawk on 2009-09-23
> **Compintuit said:**
> Yes, much better - I benefited from some new intel drivers, though. If you don't like the adds (and who does?) install the addblock extension. It does wonders for performance. If it is .gif's hit escape to stop them. It's normal for flash to take a ton of CPU; it does on windows, though not quite as much.

I heard that the 9.10 release was bringing new Intel drivers along with it. I'm hoping that my graphics card will FINALLY allow me to use Compiz and some of the neat effects I USED to be able to use. It's sad that I can't on 9.04, but did you have that problem, too?

And yeh I've heard of that. Will that AdBlock thing affect my YouTube watching experience? lol I go on YouTube to keep myself entertained in my downtime so I can't afford to go without it!

I'm gonna give that a try and see how it goes. Please reply and let me know how your Intel card is doing now with 9.10 vs 9.04. Did you have the same issues (no Compiz effects allowed to be enabled) that I did? If so, are they fixed now?

---

### Post by Vaphell on 2009-09-23
adblock allows you to filter stuff out, let's say annoying flash ads - it won't kill anything you didn't want to kill
you can subscribe to a premade list or add entries manually
if you see that some annoying ads come from [www.someannoyingadserver.com](www.someannoyingadserver.com) you just add that to the list - from now on every object with that in its address is blocked and doesn't show. This reduces CPU load, as flash ads are notorious for being cpu heavy (not to mention that the internet becomes usable again).
Also you can install noscript addon - it let's you to disable javascript, not all are used to do fancy stuff on page (navigation, neat effects, ...) - there is a lot of them running for datamining purposes or to load ads etc.

---

### Post by ajgreeny on 2009-09-23
Also try the FF add-on flashblock.  You then need to click on the advert, if you want to see it, or the main flash screen to start it.  I find it very useful. I have no help to give you about chrome, as I've never seen or used it.

---

### Post by Compintuit on 2009-09-23
I don't recommend noscript. It requires you to either whitelist things, or offers pretty much no security. Install the addblock plus firefox extension, and all your add troubles will go away. Compiz had always been very slow for me before 9.10. Now I have the full set. Cube, fire, previews, crazy transparency settings. But there are a few settings that always crash it. So not quite so much fun. New intel drivers really make a massive difference.

---

### Post by t0p on 2009-09-23
> **terrorhawk said:**
> 
Will that AdBlock thing affect my YouTube watching experience? lol I go on YouTube to keep myself entertained in my downtime so I can't afford to go without it!


I use **Flashblock** (a Firefox addon similar to AdBlock) and it doesn't stop me from watching Flash videos (I like Youtube too).  Flashblock prevents Flash objects from loading: instead of the picture, ad or whatever, you'll see a little button with an arrow on it; click on the button and the Flash object will load as normal.

It's great because it lets me choose which Flash objects I want to see.  At the moment, you go to a Flash-heavy site like Myspace or ComputerWorld, and all those adverts and other Flash objects automatically load and play.  Flash is extremely resource-intensive, hence the sharp rise in CPU load.  But if you install Flashblock or AdBlock, those Flash objects won't play and your CPU load will stay low.  If you decide there is a Flash object on the page that you'd like to see (a video, an image, a particular ad), you click the appropriate button and that object will play.  *Just* that object.  All the other Flash objects on the page will remain blocked, and the CPU load will remain relatively low.

Flashblock does take some getting used to - websites initially seem very different with all the ads and images blocked - but you'll soon learn which buttons to click, which objects to enable.  And you'll be *in charge* of your web browsing experience.  No longer will some faceless website designer force you to accept unwanted drains on your resources.  You'll see what you want to see, and the rest will stay invisible.

---

### Post by terrorhawk on 2009-09-23
> **t0p said:**
> I use **Flashblock** (a Firefox addon similar to AdBlock) and it doesn't stop me from watching Flash videos (I like Youtube too).  Flashblock prevents Flash objects from loading: instead of the picture, ad or whatever, you'll see a little button with an arrow on it; click on the button and the Flash object will load as normal.

It's great because it lets me choose which Flash objects I want to see.  At the moment, you go to a Flash-heavy site like Myspace or ComputerWorld, and all those adverts and other Flash objects automatically load and play.  Flash is extremely resource-intensive, hence the sharp rise in CPU load.  But if you install Flashblock or AdBlock, those Flash objects won't play and your CPU load will stay low.  If you decide there is a Flash object on the page that you'd like to see (a video, an image, a particular ad), you click the appropriate button and that object will play.  *Just* that object.  All the other Flash objects on the page will remain blocked, and the CPU load will remain relatively low.

Flashblock does take some getting used to - websites initially seem very different with all the ads and images blocked - but you'll soon learn which buttons to click, which objects to enable.  And you'll be *in charge* of your web browsing experience.  No longer will some faceless website designer force you to accept unwanted drains on your resources.  You'll see what you want to see, and the rest will stay invisible.

I've heard of that, too! I'm going to look into that! Thanks for that suggestion.

I appreciate all of it, so thanks guys... but really, another main question of mine is still unanswered.

Aside from the websites alone, is that behavior normal on all computers with all Linux variants and all types of window managers? Basically what I'm asking is, is someone with a nice 512MB NVIDIA graphics card and an Intel Core 2 Duo CPU experiencing sharp inclines of CPU usage just as much as I am, with my single-core lulzy mediocre system?

Thanks for the suggestions though, guys. I've tried out AdBlock Plus, and so far I like it. I've already blocked a lot of MySpace ads and crap and it seems to stabilize the CPU usage a lot. I'm gonna look into that FlashBlock thing, too!

---

### Post by Vaphell on 2009-09-23
Faster boxes render flash with lower cpu load, but it's not like it's invisible. Fullscreen will kill almost any pc.
Flash on linux sucks, that's the harsh truth. It's Adobe's fault really, only they can make their plugin to use some sort of hardware acceleration. That's one of the proprietary software pitfalls - if the creators don't bother to fix it, nobody will because only they can.

---

