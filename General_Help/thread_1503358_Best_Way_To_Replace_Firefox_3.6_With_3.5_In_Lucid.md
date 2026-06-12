---
title: "Best Way To Replace Firefox 3.6 With 3.5 In Lucid?"
date: 2010-06-06
forum: General Help
---

### Post by Andysan on 2010-06-06
Hi folks,

I have recently installed Lucid 32 bit on my PC and Firefox 3.6 is ridiculously slow.  It's not just rendering pages, simply switching between static tabs (i.e. no pages loading) can take over five seconds sometimes.  I have tried all of the fixes that have been suggested around the net relating to pipelining and IPV6 but these have had no noticeable effect (many others said the same but seemingly no resolution).

I would like to install Firefox 3.5 but cannot find a deb/repository.  I would simply like to know the best way of installing this so that, if possible it picks up my existing preferences from my current version of Firefox and is recognised by apt so can receive updates etc... in the future which I can choose to apply if I wish.  I cannot find out if my prefs and extensions will be picked up if I install via .bzr archive - will this be the case?

How that makes sense - please correct me where I have talked fizz.

Thanks in advance!

---

### Post by Smart Viking on 2010-06-06
If you are aiming for speed, install "chromium" browser, open source version of google chrome(that same thing really except it is open source and easier to install on ubuntu.

It is no doubt that is the fastest of the most popular browsers, and it is also very on the edge on new technology(html5). The only downside is that it looks a little ugly.

Install it from the sofware center, or

sudo aptitude install chromium

I hope Chromium is running faster on your computer, and i apologize if it is important that you use Firefox. :)

---

### Post by Andysan on 2010-06-06
> **Smart Viking said:**
> If you are aiming for speed, install "chromium" browser, open source version of google chrome(that same thing really except it is open source and easier to install on ubuntu.

It is no doubt that is the fastest of the most popular browsers, and it is also very on the edge on new technology(html5). The only downside is that it looks a little ugly.

Install it from the sofware center, or

sudo aptitude install chromium

I hope Chromium is running faster on your computer, and i apologize if it is important that you use Firefox. :)

Hi Smart Viking,

Thanks for taking the time to reply and help me out.

I am a big chromium fan and love its speed and performance so I appreciate and understand your tip, yet there is one small thing that keeps me from moving to it full time; in Firefox I have an extension called SimpleDelicious that appears on the toolbar as a drop down menu categorizing my bookmarks by page and allowing me to bookmark new pages.

Chrom(ium)e seems to have many Delicious extensions but not one that will allow me to easily bookmark and visit my Delicious bookmarks without first navigating to the Delicious web page.  I can add things to Delicious with the extensions that I've tried but to visit an existing bookmark I seem to have to go manually to Delicious.

Hopefully someone will release a cool addon soon that implements this - I've just finished my computing degree so maybe I will write it myself!:)

---

### Post by XSAlliN on 2010-06-06
I use IceCat instead of FF - but basically, in terms of functionality should be the same.

- Try this Addons, see if it helps:

**[Vacuum Places Improved]("https://addons.mozilla.org/en-US/firefox/addon/13878/")** (set it to Auto Clean - every 5 - 7 times you start FF)

[B][URL="https://addons.mozilla.org/en-US/firefox/addon/59745/"]
FasterFox[/URL][/B]

-If you don't like the speed with defaults settings, you could try this:

[IMG]http://img9.imageshack.us/img9/5639/screenshotcln.png[/IMG]

-that's what I use and fore me is real fast (click and load - rarely have to wait). Yet I must admit, i also have good connection from my ISP right now... If you loose tons of packets with yours then is IPS related, not browser.

---

### Post by Andysan on 2010-06-06
> **XSAlliN said:**
> I use IceCat instead of FF - but basically, in terms of functionality should be the same.

- Try this Addons, see if it helps:

**[Vacuum Places Improved]("https://addons.mozilla.org/en-US/firefox/addon/13878/")** (set it to Auto Clean - every 5 - 7 times you start FF)

[B][URL="https://addons.mozilla.org/en-US/firefox/addon/59745/"]
FasterFox[/URL][/B]

-If you don't like the speed with defaults settings, you could try this:

[IMG]http://img9.imageshack.us/img9/5639/screenshotcln.png[/IMG]

-that's what I use and fore me is real fast (click and load - rarely have to wait). Yet I must admit, i also have good connection from my ISP right now... If you loose tons of packets with yours then is IPS related, not browser.

Thanks, I had forgotten IceCat and may give it a try.  Ideally though I would like to go back to Firefox 3.5 if possible however.  Its not so much that I'm dissatisfied with Firefox, rather I just seem to have issues with 3.6 on my machine.  Its more that the app itself runs dreadfully slow than the connection speed.

Thanks for your suggestion.

---

### Post by wojox on 2010-06-06
Download it, unpack it, and move it to /opt.

---

### Post by Andysan on 2010-06-06
> **wojox said:**
> Download it, unpack it, and move it to /opt.

Wow - that easy huh?  Picked up all my extensions and everything too.  I loves Linux.

One question though, anyway I can "register" this so it shows up in synaptic and checks for updates etc...? Thanks!

---

### Post by wojox on 2010-06-06
You'll just have to update yourself when they are made available through Mozilla. Actually it will check for you periodically and update itself. Yeah, Linux rocks. :)

---

### Post by XubuRoxMySox on 2010-06-06
SeaMonkey 2.0 may support all your extensions and add-ons. It's an integrated browser/email suite that works just like good ol' Firefox 3.0 and Thunderbird 2.0 (including support for POP3 and the way-cool Lightning calendar). It's my new "default" app for e-mail and web browsing. Available in the repositories so it's easy to install.

Enjoying the simplicity,
Robin

---

### Post by Andysan on 2010-06-07
> **dixiedancer said:**
> SeaMonkey 2.0 may support all your extensions and add-ons. It's an integrated browser/email suite that works just like good ol' Firefox 3.0 and Thunderbird 2.0 (including support for POP3 and the way-cool Lightning calendar). It's my new "default" app for e-mail and web browsing. Available in the repositories so it's easy to install.

Enjoying the simplicity,
Robin

Thanks Wojox, Robin - I'll be sure to check that out!

---

