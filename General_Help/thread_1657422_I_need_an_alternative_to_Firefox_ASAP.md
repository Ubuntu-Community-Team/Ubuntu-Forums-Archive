---
title: "I need an alternative to Firefox ASAP"
date: 2011-01-01
forum: General Help
---

### Post by Jerriy on 2011-01-01
Firefox has become complete and utter garbage.

I've been using FF since day one of leaving Windows and jumping on ubuntu in 2008. But this recent version(s) of firefox that completely suck up all the memory despite having more than enough memory

Apparently my understanding is that this is all related to this new firefox system called "pluguin container" or whatever the hell it is. But I'm not interested in it any longer.

Cause right now I need access to my imgur.com account and (shockingly) I am _unable_ to use firefox to acces that account (it crashes every single time)........ so I need to get rid of this rubbish browser and need a decent alternative browser to access my account.

Thanks in advance

---

### Post by kostkon on 2011-01-01
Chrome?

---

### Post by Jerriy on 2011-01-01
> **kostkon said:**
> Chrome?Is the Chrome on synaptic? Or you telling me to go to google directly? I'm asking cuz I was thinking of browsers that are clearly made for ubuntu.

---

### Post by KdotJ on 2011-01-01
+1 for chrome
Though I actually use Chromium straight from the repos

---

### Post by cascade9 on 2011-01-01
Opera is worth a shot.

---

### Post by gabriella on 2011-01-01
> **Jerriy said:**
> Firefox has become complete and utter garbage.

I've been using FF since day one of leaving Windows and jumping on ubuntu in 2008. But this recent version(s) of firefox that completely suck up all the memory despite having more than enough memory

Apparently my understanding is that this is all related to this new firefox system called "pluguin container" or whatever the hell it is. But I'm not interested in it any longer.

Cause right now I need access to my imgur.com account and (shockingly) I am _unable_ to use firefox to acces that account (it crashes every single time)........ so I need to get rid of this rubbish browser and need a decent alternative browser to access my account.

Thanks in advance

Epithany, Midori, Seamonkey... There are lots of options out there.

But please folks don't abandon the Plugin-container or Firefox-bin problem because I get that annoying problem to (and others as well) There has to be a fix out there somewhere....I hope!!!

---

### Post by I'mGeorge on 2011-01-01
Chromium much faster and lightweight than firefox. It also has a lot of extensions that you can install just as firefox has add-ons

---

### Post by Jerriy on 2011-01-01
What? There's 'Chrome' and also 'Chromium'?

Interesting. I need to spend more time here.

---

### Post by Jerriy on 2011-01-01
> **KdotJ said:**
> +1 for chrome
Though I actually use Chromium **straight from the repos**You just sold me Chromium on that point.

I'm gonna head to synaptic.

Thanks all of you for your suggestions!

---

### Post by gabriella on 2011-01-01
> **gabriella said:**
> Epithany, Midori, Seamonkey... There are lots of options out there.

But please folks don't abandon the Plugin-container or Firefox-bin problem because I get that annoying problem to (and others as well) There has to be a fix out there somewhere....I hope!!!

OK I guess it's time to start a clean thread for this one!

---

### Post by cyb3r_sn4k3 on 2011-01-01
Try Chromium(chrome)

Its in the repos you can get it by...

```

sudo apt-get update && sudo apt-get install chromium-browser

```

And I use firefox from a long time back but I never had any problems with it.

---

### Post by cascade9 on 2011-01-01
> **Jerriy said:**
> What? There's 'Chrome' and also 'Chromium'?

Interesting. I need to spend more time here.

Yeah, google playing licence games. 

Long story short- google writes some code for the chrome browser, releases it as open source 'chromium'. Because chromiums code is under a BSD licence, they can take code from it and incorporate it into the closed source chrome.

---

### Post by gerowen on 2011-01-01
After reading this thread I installed epiphany and holy cow it's fast compared to Firefox.  It's Chrome fast with even less gui.  The address bar isn't even there by default you just hit ctrl+l and it comes up temporarily.  Appears to be a lot better than it used to be at rendering pages too, plus it supports the mozilla plugins for Flash and Java.

Edit: AND it supports HTML 5.

---

### Post by lovinglinux on 2011-01-01
You should try [Firefox 4]("http://www.webgapps.org/firefox/installing-firefox-4"). A lot faster, very cool features.

Firefox runs like a charm as long as you do some maintenance. See [my tutorials on optimization]("http://www.webgapps.org/blogs/firefox-tutorials").

I also recommend Opera 11, which now support Chrome-like extensions. Opera is my primary browser now, but I also use Firefox for development, because nothing beats Firefox extensions.

Chrome? No way. It doesn't even have rss feed support.

---

### Post by TeoBigusGeekus on 2011-01-01
Opera all the way.
I've been using it since it had ads and even with them, it was still faster than firefox.
Version 11 supports extensions; small number of them available at the moment, but it's due to change in the immediate future.

---

### Post by Jerriy on 2011-01-01
> **lovinglinux said:**
> You should try [Firefox 4]("http://www.webgapps.org/firefox/installing-firefox-4"). A lot faster, very cool features.

**Firefox runs like a charm as long as you do some maintenance. See [my tutorials on optimization]("http://www.webgapps.org/blogs/firefox-tutorials").**

I also recommend Opera 11, which now support Chrome-like extensions. Opera is my primary browser now, but I also use Firefox for development, because nothing beats Firefox extensions.

Chrome? No way. It doesn't even have rss feed support.But does Firefox 4 solve the memory/plugin-container/whatever problem? 

And also this: does installing Firefox 4 *while *having repos-origin Firefox 3.6.13 cause me problems like it did when late last year (I mean two years ago now that it's 2011 already:>) when Firefox-jaunty couldn't be updated without the browser being renamed "Shiretoko" instead of "Firefox" (remember that?)

I remember all that hussle and now this latest Firefox-memory cockup! It's seriously getting tiring to use Firefox for just basic things! I'm using Chromium now just so that I can access imgur.com which firefox 3.6.13 is patheticaly NOT capable of without crashing and shutting down everything
.

---

### Post by sanderd17 on 2011-01-01
just delete your firefox settings, history ... and it will be fast again:

```

rm .mozilla

```

You will have to redownload your add-ons and do your settings again. But with a new browser, you would have to do that too.

If you install firefox 4: get it from the website: [http://www.mozilla.com/nl/firefox/beta/](http://www.mozilla.com/nl/firefox/beta/)
download the archive, unpack it somewhere and execute the firefox file from it. The worst thing that can happen is that it messes up your profile (certainly if it's an old profile) and if you don't like it, just delete the archive and the unpacked archive.

---

### Post by lovinglinux on 2011-01-01
> **Jerriy said:**
> But does Firefox 4 solve the memory/plugin-container/whatever problem?

The plugin-container is what allows the browser to launch some plugins like flash as a separate process and thus not crashing the browser if the plugin crashes. It is very useful. However, you can turn it off if you need. See [http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins#Disabling_crash_protection](http://kb.mozillazine.org/Plugin-container_and_out-of-process_plugins#Disabling_crash_protection)

Opera has a similar container, called operapluginwrapper. Plugin performance in Opera is worse than Firefox, but Opera is much faster in regard to javascript.

The issues with the plugin container are more likely to be caused by the plugin itself, rather than the container. After all, flash uses too much CPU and lags like a turtle. However, recent versions of flash are getting better. If you are using 64bit, you should try the square preview.

Get my extension [Flash-Aid]("http://www.webgapps.org/addons/flash-aid"), to install the proper flash beta version, get rid of conflicting plugins and apply some performance tweaks.

Also, get rid of flash on Youtube, Vimeo and Metacafe, by using my extension [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer"). You will be able to see HD videos without flash eating your CPU. Make sure you get versions 2.0.x of both.

In regard to memory issues, if you are experiencing memory leaks, is more likely to be an extension causing this.Start Firefox in safe mode to see if the problem persists and apply some [memory tweaks in the preferences]("http://www.webgapps.org/firefox/preferences-tweaks").

If you are switching to Chrome because of memory issues, then you will probably get frustrated soon. Chrome is not a miracle maker and it also tend to eat memory over time. Besides, it lacks too many features.

About Firfefox 4 solving your issues, I don't have enough data to determine what is the source of your problems. However, Firefox 4 javascript engine is a lot faster than 3.6. It is not as fast as Chrome and Opera, but you will be surprised (3 times faster than 3.0). Besides, in the real world, with a properly maintained browser profile, there is not much difference between the three browsers.

> **Jerriy said:**
> And also this: does installing Firefox 4 *while *having repos-origin Firefox 3.6.13 cause me problems like it did when late last year when Firefox-jaunty couldn't be updated without the browser being renamed "Shiretoko" (remember that?)

That's because a lot of people recommend the ubuntu-mozilla-daily ppa, which also updates Firefox 3.6 with unstable packages, which has no branding.

I prefer to download Firefox directly from Mozilla and install it into the /opt folder. [This tutorial]("http://www.webgapps.org/firefox/installing-firefox-4") explains how to do it. You can also use the SilverWave ppa, that does not interfere with FF 3.6 or you can use my [FoxTester]("http://www.webgapps.org/addons/foxtester") extension, to easily install and launch any number of Firefox versions. Although the extension is intended to be used for testing various versions, you can use the "Make Default" option to install any version permanently into the /opt folder. Is very easy to use and no commands are required.

Yes, I remember the "Shiretoko" drama. Tons of endless threads complaining about the logo and name. That was exactly the time when I decided to create my tutorials.

> **Jerriy said:**
> I remember all that hussle and now this latest Firefox-memory cockup! It's seriously getting tiring to use Firefox for basic things! I'm using Chromium now just so that I am able to access imgur.com which firefox 3.6.13 is patheticaly NOT able to do!
.

You need to figure out what is causing these problems. Firefox 3.6 used to run pretty well on my Core2 Duo machine, even with more than 60 extensions installed.

See [http://www.webgapps.org/firefox/general-troubleshooting](http://www.webgapps.org/firefox/general-troubleshooting)

---

### Post by lovinglinux on 2011-01-01
> **sanderd17 said:**
> just delete your firefox settings, history ... and it will be fast again:

```

rm .mozilla

```

Although that usually solves several profile issues and make Firefox fast again, there are less destructive methods to achieve the same results. For instance, [optimizing the databases]("http://www.webgapps.org/firefox/database-optimization") would be a good start.

---

### Post by scouser73 on 2011-01-01
> **cascade9 said:**
> Opera is worth a shot.

I agree, install Opera 11 and see how fast it is.

---

### Post by lovinglinux on 2011-01-01
> **scouser73 said:**
> I agree, install Opera 11 and see how fast it is.

I do agree and I love it. However, Opera is the worse of the three browsers in regard of memory usage and plugin performance.

---

### Post by marbertone on 2011-01-01
Lynx, man!
It is THE browser: fast and uncrashable.
Cheers,
M.A.

---

### Post by TeoBigusGeekus on 2011-01-01
> **marbertone said:**
> Lynx, man!
It is THE browser: fast and uncrashable.
Cheers,
M.A.

Can you watch porn in lynx? :biggrin:

---

### Post by perspectoff on 2011-01-01
Rekonq (previously Konqueror) is the default for KDE (Kubuntu). It is similar to Firefox but not as bloated. It uses the Gecko/Firefox plugins, too, which is a big, big advantage over other browsers.

---

### Post by marbertone on 2011-01-01
> **TeoBigusGeekus said:**
> Can you watch porn in lynx? :biggrin:

L.O.L. !!!!! 
:lolflag:
):P
M.A.

---

### Post by veggen on 2011-01-01
Open 10+ tabs in Opera and anything else, and you'll see for yourself how awesome Opera is. It will happily keep working with 40 tabs open while Firefox will crawl after the fifth. The leanest, meanest, most feature packed browser ever.

---

### Post by jcolyn on 2011-01-01
> **gabriella said:**
> 
But please folks don't abandon the Plugin-container or Firefox-bin problem because I get that annoying problem to (and others as well) There has to be a fix out there somewhere....I hope!!!

Since most Linux computers running Firefox mine included don't have this problem I would suspect something else. Maybe addons??

---

### Post by TeoBigusGeekus on 2011-01-01
> **veggen said:**
> Open 10+ tabs in Opera and anything else, and you'll see for yourself how awesome Opera is. It will happily keep working with 40 tabs open while Firefox will crawl after the fifth. The leanest, meanest, most feature packed browser ever.
^This.

Seriously, try this at home: open 15~20 tabs in opera and then open the same tabs (same sites) in firefox and chrome/ium.
Then watch your system resources (htop) and be enlightened...:p

---

### Post by MARP1961 on 2011-01-01
I think Chrome for Windows is called Chromium in it's Linux version. Anyway, whatever the name, this browser from Google is excellent! Just install it from the Ubuntu Software Centre.

---

### Post by A_M_S on 2011-01-01
> **MARP1961 said:**
> I think Chrome for Windows is called Chromium in it's Linux version. Anyway, whatever the name, this browser from Google is excellent! Just install it from the Ubuntu Software Centre.

Chromium is the open source version of chrome for more information read [this link]("http://news.softpedia.com/news/Google-Chrome-vs-Chromium-Understanding-Stable-Beta-Dev-Releases-and-Version-No-140060.shtml")

---

### Post by Bitrate on 2011-01-01
Firefox does have a memory leak issue which can cause slowdowns and unresponsive behavior. This was supposed to be fixed but its presence still remains and is more noticeable when opening large numbers of tabs and having many plugins active. Closing the browser and restarting usually fixes this.

I still prefer Firefox for its stability and web standards compliance, not to mention its great add on/plugin support. It might not be as fast as Chrome but it sure as heck is a lot safer and doesn't act in nefarious ways against the end-user (I'm looking at YOU Google!).

---

### Post by hawthornso23 on 2011-01-01
All the recent problems that I have had with Firefox have turned out to be because of bad memory. I have had a very bad run with three (count 'em) DDR2 sticks going bad on me over the last year. An expensive PITA.

Firefox is like the canary in the mine for memory problems, probably  because it is usually the most memory intensive application in daily use. It is usually the first application to start crashing when you have bad memory.

If you are getting frequent unexplained firefox crashes, my advice is to try running memtest.

---

### Post by gabriella on 2011-01-02
> **jcolyn said:**
> Since most Linux computers running Firefox mine included don't have this problem I would suspect something else. Maybe addons??

Possibly?
Personally I suspect a link with flash. 
You maybe correct in saying "most" dont have this problem but it seems to be a significant minority. Try googling  firefox-bin or Plugin-container.

---

