---
title: "Is there any browser based on Firefox for Linux?"
date: 2012-03-29
forum: General Help
---

### Post by emptycoder on 2012-03-29
Hi, I'm looking for a browser which is based on Firefox, I want to do that because I want to use TOR Project (For anonymous browsing)  and I need to install Torbutton so I can use it, but it will disable all my addons and will delete all my cookies, I'm using some addons such as Diggit, Delicious and other ones that required sign in, it will be a pain to sign in all of them on every time I start my Firefox.
I tried multi-profile method but somehow it doesn't work well, it causes glitches and the system suddenly falls back to classic mode.
I came across to another method which is for Chromium, that it needs some tweaking so I can use TOR but Firefox is much safer.
So is there any other browser based on Firefox that I can use? Thanks

---

### Post by davidvandoren on 2012-03-29
Opera is based on Mozilla.

Go to opera.com and download the deb package for Ubuntu.

Oh sorry I think it's based on Netscape same as Firefox

---

### Post by emptycoder on 2012-03-29
I don't think that I can install that extension on Opera, but thanks for reply.
Any other suggestions?

---

### Post by skatinjj on 2012-03-29
Look into getting iceweasel in my opinion.

---

### Post by bobman321123 on 2012-03-29
Google chromium?

```
sudo apt-get install chromium-browser
```

---

### Post by bobman321123 on 2012-03-29
Sorry, disregard. I'm quite certain Chromium isn't based on firefox. 
My bad :oops:

---

### Post by davidvandoren on 2012-03-29
I don't know if it's any help but opera and tor is discussed here [http://my.opera.com/community/forums/topic.dml?id=873732](http://my.opera.com/community/forums/topic.dml?id=873732)

You could install Firefox in wine and try to fit that one withe the extensions needed.
But better ask first how well that works (if it is stable)

---

### Post by davidvandoren on 2012-03-29
Or you set up a ubuntu in virtual box with it's own INTERNET connection for safe browsing.

That's the safest choice anyway.

---

### Post by stinkeye on 2012-03-29
This may help... 
[**_[COLOR="DarkRed"]install multiple versions of firefox in linux[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1907045")
There is also a [**_[COLOR="DarkRed"]FoxTester add-on[/COLOR]_**]("https://addons.mozilla.org/en-US/firefox/addon/foxtester/")

---

### Post by ofnuts on 2012-03-29
You can also define another userid. it will have its own Firefox profile (and its specific add-ons)

---

### Post by winh8r on 2012-03-29
If you really need to use tor ,
Then save yourself the hassle of messing around with your everyday system and download this:

[https://tails.boum.org/]("https://tails.boum.org/")


Much easier than all that reconfiguring, and you won't have to get it all back to where it was, when you find that Tor is too slow for what you need!!!

---

### Post by emptycoder on 2012-03-29
> **winh8r said:**
> If you really need to use tor ,
Then save yourself the hassle of messing around with your everyday system and download this:

[https://tails.boum.org/](https://tails.boum.org/)


Much easier than all that reconfiguring, and you won't have to get it all back to where it was, when you find that Tor is too slow for what you need!!!

Seems very interesting, I think that's will do the trick, Thanks a lot Winn8r.
And thanks for everyone for helping, before marking this thread as SOLVED, let me update some info for those who didn't try TOR Project yet.

TOR is relying on Firefox and doesn't guarantee any result on other browsers, so it's highly recommend to use Firefox if you want to protect your privacy.
TOR will delete cookies and disable all addons, your Firefox would be a miss if it's your default browser so it's recommended that you use another browser as default (Chromium for example) and Firefox for anonymous browsing, unless you found another browser that based on Firefox and accept addons, still... Firefox would be much better.
Two different Firefox Profiles could be a good idea, to use one as default browsing and the second one for anonymous browsing, but it didn't work well on my PC, so I really can't tell.
Now I will stick with Tails.Boum, if anyone got any more ideas, please share.
Thanks again.

---

### Post by winh8r on 2012-03-29
No problem.

Makes life much easier.

Good Luck.

---

