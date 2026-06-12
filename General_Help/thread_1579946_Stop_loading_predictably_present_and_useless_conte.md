---
title: "Stop loading predictably present and useless content?"
date: 2010-09-22
forum: General Help
---

### Post by psifunk on 2010-09-22
Just asking.. Have you noticed that the frequency of the messages "waiting facebook.com", "waiting twitter.com" etc has increased enormously these past few years on your firefox status bars? I know the obvious reason for that but what I want to ask, since I never use the modern "tweet it" or "post it on facebook" capabilities of websites, is [I]if I can tell firefox to stop loading them and their like so that it will be snappier.

[/I]This could be a non ubuntu question, but since I have been a very happy Ubuntu addict err i mean user for some years I am really interested in whether this can happen for Ubuntu or linux generally. This is actually a poser, I don't have many hopes it can be done in a practical way *but it should be *(darn i hate those happy f and t buttons everywhere arghh!). 


p.s. If I did had any real technical knowledge about websites I would not need to also ask these two questions 

1. Is the code (or whatever) for these things identical or easily and unambiguously recognisable?
2. If true, can one instruct (and i dont mean like for example, a dog) his browser to pass on them? 

p.s. p.s. will send flowers to the one bearing the answer (noticed the nested ps?)

---

### Post by SeijiSensei on 2010-09-22
Install the [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") add-on for Firefox.  You can blacklist files and sites with ease.  Just create a custom rule for facebook.com, and Firefox won't attempt to load any files from there again.

System-level solutions can be built using things like the Squid web proxy software.  I've built Squid filters for clients who want to limit the types of sites and types of files their users can access over the web.  In these cases, though, we're talking about enforcing rules at the firewall for an entire network.  For individual users, Adblock Plus is the the best choice.

---

### Post by Christian Knudsen on 2010-09-22
There's this one for blocking Facebook content:

[https://addons.mozilla.org/da/firefox/addon/212323/](https://addons.mozilla.org/da/firefox/addon/212323/)

Haven't tried it myself, though.


PS: Oh, and it's "PPS" not "PSPS". Post post scriptum. :D

---

### Post by psifunk on 2010-09-22
Wow this was pretty fast. Easier that I could imagine although the practicality is still debatable. 

HOWEVER! In these 55 minutes since SeijiSensei answered only 4 minutes after I posted (I am waiting for the address for the flowers) I did try something out. So, I do visit huffington post for example very often. That would be [www.huffingtonpost.com](www.huffingtonpost.com).  After figuring out how adblock works I quickly added these filters (with some experimenting do not ask me what each one does ) :

[IMG]http://i51.tinypic.com/wvrbic.png[/IMG]

So I tried to see If it made any difference. First I loaded the site normally (with adblock deactivated). So I hit refresh and count (yes with the stopwatch of my mobile phone). 
RESULT: 11 something seconds

Then I activate adblock and hit refresh again:
RESULT: 6 something seconds

(I was counting until the status bar said it has finished downloading stuff)

It felt faster too. The ads were missing amongst other useless things

On my limited resources eee pc (which I love) the result is pretty important since scrolling in firefox before it finishes downloading the hole page is very sluggish? Try it out people let me know what you think! I am wondering of how heavy this plug-in could be.

---

### Post by Quackers on 2010-09-22
It's all French to me.

---

### Post by psifunk on 2010-09-22
Ok, about the french part... this is just the page where adblock lists the urls it will block ([http://ww.ubuntu.com*](http://ww.ubuntu.com*) will also block [http://www.ubuntu.com/images](http://www.ubuntu.com/images) etc)

---

### Post by Quackers on 2010-09-22
I was being facetious.......my apologies

---

### Post by SeijiSensei on 2010-09-22
I don't know what your definition of "heavy" is, but at about 300K AdBlock isn't very big, and even if it increases the browser's processing time by a couple of milliseconds, that's trivial in comparison to the speed increases you see from not waiting for ads and scripts to be downloaded and displayed.

As for the flowers, I'd prefer a financial contribution to my numbered account in Zurich.

---

### Post by psifunk on 2010-09-22
Ok so I tried the "test" again with the economist homepage. For anyone reading this in the future it took me like ten minutes to figure out how to throw all the ads away and some irritating pop ups and features of the site. Now it reloads (load meaning the status bar thing i described before) at half the time (8 vs 16 seconds). So I am convinced enough not to use the stopwatch again, I will certainly use adblock for the 10 or so websites I always visit whenever I connect to the internet. That is really cool, thanks!

---

### Post by lovinglinux on 2010-09-22
> **psifunk said:**
>  For anyone reading this in the future it took me like ten minutes to figure out how to throw all the ads away and some irritating pop ups and features of the site. 

Adblock has a subscription feature, that allows you to get rules automatically. Subscribe to the EasyList and forget about it. It blocks most of the stuff.

You might also want to install [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/"), which is primarily a security tool, but can also block some ad related stuff. For instance, it blocks ads in videos on TerraTV.

You might also like [Ghostery]("https://addons.mozilla.org/en-US/firefox/addon/9609/"), which blocks tracking stuff.

---

