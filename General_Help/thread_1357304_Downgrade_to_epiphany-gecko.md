---
title: "Downgrade to epiphany-gecko"
date: 2009-12-17
forum: General Help
---

### Post by 987poiuytrewq on 2009-12-17
Hi, as all you epiphany users probably know, in karmic, epiphany-webkit is the default version of epiphany installed. In my opinion, released way too early, it's a bit buggy with videos and flash and pdfs. I'd really like to continue to use epiphany-gecko (the old version, used in jaunty) in my karmic system. Does anyone know how to do this, in synaptic epiphany-gecko is just a dummy package? Will I have to downgrade a whole load of dependencies as well? I'm prepared to have a go at building from source if it will work with newer versions of the dependencies. Anyone have any ideas on how to get epiphany-gecko back?

---

### Post by nibirumarduk on 2009-12-17
> **987poiuytrewq said:**
> Hi, as all you epiphany users probably know, in karmic, epiphany-webkit is the default version of epiphany installed. In my opinion, released way too early, it's a bit buggy with videos and flash and pdfs. I'd really like to continue to use epiphany-gecko (the old version, used in jaunty) in my karmic system. Does anyone know how to do this, in synaptic epiphany-gecko is just a dummy package? Will I have to downgrade a whole load of dependencies as well? I'm prepared to have a go at building from source if it will work with newer versions of the dependencies. Anyone have any ideas on how to get epiphany-gecko back?

I couldn't agree less. All the issues you mentioned plus a ton more including missing functionalities like 'Open in tab', 'Copy Image Address' (both resolved in 2.29), epiphany deciding it's best to open the directory where I have an image to without fail every time; encoding issues with East Asian languages e.g. Chinese GB and Chinese BIG5 (see [http://www.imgplace.com/viewimg405/7641/62encodingissues228gnom.png](http://www.imgplace.com/viewimg405/7641/62encodingissues228gnom.png)), etc. Bug reports were filed with both launchpad and GNOME upstream: 
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/475174](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/475174)
[https://bugzilla.gnome.org/show_bug.cgi?id=600917](https://bugzilla.gnome.org/show_bug.cgi?id=600917)
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/476525](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/476525)
[https://bugzilla.gnome.org/show_bug.cgi?id=600981](https://bugzilla.gnome.org/show_bug.cgi?id=600981)

While the missing options issues on the right click menu may have been fixed for the 2.29 series, the encoding one remains. It got to a point where I couldn't tolerate the nonsense anymore and purged epiphany altogether. Hmm why do I have this sneeky feeling that this is exactly the intention of the Ubuntu devs in that they can't wait to see the back of epiphany and wants the browser dead, so that Firefox can reign supreme and unchallenged? Otherwise why include it for Karmic while these bugs, many of whom do affect the overall end user experience are unfixed? Or is this really an upstream GNOME issue i.e. in that they were overly eager to rush for the inclusion of raw, beta quality software and perhaps a hint that upstream GNOME may be abandoning its long-held conservative "not rocking the boat unnecessarily" approach to incorporating changes to its DE? Or is it a combo of both i.e. the fault is both an Ubuntu's as well as upstream GNOME's?

I admit I have a soft spot for epiphany. A love affair that began in 2003 i.e. even before the advent of Ubuntu while I was using Debian Sid. While this tiny little browser often had problems handling certain flash-heavy webpages and was crashy (both), it was hyper fast and way less resource hungry as compared to the similarly gecko-powered Firefox. 

But I guess all good things must come to an end, epiphany is history and in it place for the last 2 weeks at least is google-chrome-beta. I must say, all other browsers have better pull up their socks for not only is it only about half the size of firefox, it is way more responsive than even Opera at its prime. Chrome also renders most of the East Asian pages correctly. While there are still some minor glitches and irritations e.g. some extensions e.g. session saver and adblock+ not fully working but I suppose these are but some of the trade-offs that comes with using what is still beta software. Thus I'm otherwise a most satisfied customer.

---

### Post by pt123 on 2009-12-17
me too epiphany gecko was great at being my second browser,

but this epihany webkit is awful, it is slow and there are so many bugs. 

I am looking for a way to install Epiphany Gecko back too

---

### Post by 987poiuytrewq on 2009-12-18
The reason for not offering a version of epiphany-gecko for karmic is that the epiphany devs have very little time and would prefer to concentrate on epiphany-webkit as this backend is vastly superior in many ways, is acid3 compliant and is generally the shape of web browsers of the future. However, the user interface is not ready and many useability bugs still remain. I'm not interested if firefox is better than epiphany or if you believe epiphany-webkit is bug free. The fact is that I find it buggy and annoying to use and I just want epiphany-gecko back on my system, as I preferred it.

Does anyone know how - even in principle - to downgrade to an old package through synaptic or if I compile from source, will it be compatible with the newer gnome libraries?

---

### Post by nibirumarduk on 2009-12-18
> **987poiuytrewq said:**
> The reason for not offering a version of epiphany-gecko for karmic is that the epiphany devs have very little time and would prefer to concentrate on epiphany-webkit as this backend is vastly superior in many ways, is acid3 compliant and is generally the shape of web browsers of the future.

This may indeed be the real reason yeah.

> However, the user interface is not ready and many useability bugs still remain. I'm not interested if firefox is better than epiphany or if you believe epiphany-webkit is bug free. The fact is that I find it buggy and annoying to use and I just want epiphany-gecko back on my system, as I preferred it.Does anyone know how - even in principle - to downgrade to an old package through synaptic or if I compile from source, will it be compatible with the newer gnome libraries?

Like I have said, you aren't the only user annoyed with the haphazard manner in which the migration was handled with the bugs and all. But if you are desperate to have the gecko-powered one back, you may have to roll your own deb and of course take care of the deps, whatever they may be. For starters, you will need to have a deb-src line for Jaunty (as like you have yourself mentioned in the preceeding para, epiphany-gecko isn't being developed nor is it actively maintained anymore) in your sources.list, so that you can at least download the source archive and then work with scripts, manipulate the control files and then have it rebuilt against the Karmic libs. As stated, there will be files that you will need to manipulate among other not too trivial things which would require you to know Debian packaging internals (search the Ubuntu wiki and/or read up on [http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/) and [http://www.debian.org/doc/manuals/developers-reference/](http://www.debian.org/doc/manuals/developers-reference/)). 

Also have you check the ppas i.e. [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) to see if someone has already packaged and is maintaining epiphany-gecko for Karmic? Hmm maybe just maybe, you can try the ppas as a first step even before undertaking the rather tedious task of rolling your own deb.

On a sidenote, for those who do not want to see the back of epiphany-gecko, do not want to see the browser die, have you guys considered sounding other epiphany-gecko browsers from other distros and perhaps do a Seamonkey (ala the reborn Mozilla) II? Do take note though that this will entail a massive investment in time and effort though as other than the non too trivial things you'l need to do already mentioned above, you'll also need to track e.g. upstream xulrunner development.

---

### Post by pt123 on 2009-12-18
what I ended up doing was using the mozilla daily PPA to install FF 3.6. 
Which let's it be my second browser to Firefox (3.5). 

FF 3.6 is very fast, incl. start up. 

Chromium kills epiphany-webkit in every manner.

---

### Post by yester64 on 2009-12-20
yea, one thing thats annoying is to have to use 2 browsers.
I like epiphany. Very fast browsers, but with the current engine (i assume) flash is buggy.
got to go to the bug page

---

### Post by 987poiuytrewq on 2009-12-27
Alright all, I solved how to downgrade to epiphany-gecko (2.26.1). It's actually a trivial exercise. First, remove all epiphany related packages from your system (note you will keep all your personal data i.e. passwords, bookmarks etc):
```
sudo apt-get remove epiphany-browser-data epiphany-browser
```
Then go to packages.ubuntu.com and download the jaunty deb's:
[http://packages.ubuntu.com/jaunty/epiphany-browser-data](http://packages.ubuntu.com/jaunty/epiphany-browser-data)
[http://packages.ubuntu.com/jaunty/epiphany-gecko](http://packages.ubuntu.com/jaunty/epiphany-gecko)

You need to install the first one first as it is a dependency. Ignore any messages saying that there is newer version in the repos. If there any errors; just remove the offending package as it is probably a newer, conflicting package. 

All other dependencies were already installed for me. I've successfully installed my old version of epiphany, and I'm typing this from epiphany-gecko running in karmic right now!!

Also, if you want to install extensions, you must remove the existing extensions:
```
sudo apt-get remove epiphany-extensions
```
and install the old extensions package:
[http://packages.ubuntu.com/jaunty/epiphany-extensions](http://packages.ubuntu.com/jaunty/epiphany-extensions)

---

### Post by funnylife_ma on 2010-03-10
epiphany-2.26.3 works well with gecko-1.9.2 ( the same rendering engine used by firefox-3.6 ). I found also a gmail-notifier extension which i got to work after some patches. Epiphany-gecko is still one of the best choices on GNOME !

---

### Post by McCleod on 2010-05-05
> **funnylife_ma said:**
> epiphany-2.26.3 works well with gecko-1.9.2 ( the same rendering engine used by firefox-3.6 ).

How did you get Epiphany to work with Gecko?

I really need Epiphany-Gecko on my PC. Webkit is not supportet by netbanking and FF sucks in terms of netbanking. Epiphany just works as a charm - worked, I should say.

I am stuck on 8.10 until I get Epiphany to work with Gecko.

If it works, don't fix it - Cannonical listen to this, dammit!

---

### Post by darolu on 2010-05-10
> **McCleod said:**
> How did you get Epiphany to work with Gecko?

I really need Epiphany-Gecko on my PC. Webkit is not supportet by netbanking and FF sucks in terms of netbanking. Epiphany just works as a charm - worked, I should say.

I am stuck on 8.10 until I get Epiphany to work with Gecko.

If it works, don't fix it - Cannonical listen to this, dammit!

Well it is not Canonical's responsibility, Epiphany is not made by Canonical or Ubuntu developers but by GNOME developers, it is the default web browser in GNOME. And also remember that (at least in my 2.30) the Epiphany-browser package is not even created by Ubuntu developers but by Debian, 2.30 was taken from the squeeze/sid branch of Debian; judging by its HTTPUserAgent that is: "Mozilla/5.0 (X11; U; Linux i686; es-mx) AppleWebKit/531.2+ (KHTML, like Gecko) Safari/531.2+ **Debian/squeeze/sid** () Epiphany/2.30.2"

I am so very glad Epiphany no longer uses Gecko and that it has nothing to do with XULRunner anymore, but I have to agree with you all that it is still a bit buggy  (although I have only found one bug in 2.30) and that it lacks A LOT of functionality compared to 2.26.3 and previous (when gecko was the default engine).

If you can get 2.26.3 to work in 9.10 or newer versions of Ubuntu, chances are good it's already running with gecko.

Anyways, the reason I'm posting here is to find if it is possible to access the "about:config", I can't see anything when I go to "about:config"; Epiphany documentation say we can change settings there but it doesn't open anything so I suppose it is a Ubuntu/Debian-exclusive issue.

I know two workarounds to change the settings I wanted, but I don't think it is the right approach as this issue should be fixed.

If you are wondering, I wanted to change the search engine as Google is extremely annoying now it changed its looks and feel, I just hate the left-panel in search results; so to be able to change it (to altavista) I had to edit with gconf-editor (apps-epiphany-general). The other way to change it is editing ~/.gnome2/epiphany/mozilla/epiphany/prefs.js

---

### Post by 987poiuytrewq on 2010-06-01
On the upgrade to lucid, I found that my epiphany-gecko was broken again. Here's what to do to get it back:


First run 
```
sudo apt-get remove xulrunner-1.9
```
this removes a dummy package that actually does nothing, but will prevent you from the next steps, which is to download an older version of xulrunner. These can be found in the debian repos. You need these packages, in this order:

[http://packages.debian.org/lenny/libmozjs1d](http://packages.debian.org/lenny/libmozjs1d)
[http://packages.debian.org/lenny/xulrunner-1.9](http://packages.debian.org/lenny/xulrunner-1.9)
[http://packages.debian.org/lenny/amd64/xulrunner-1.9-gnome-support](http://packages.debian.org/lenny/amd64/xulrunner-1.9-gnome-support)

Download and install the appropriate ones for your architecture.
Then you need to do the same things you did before:

> **987poiuytrewq said:**
> First, remove all epiphany related packages from your system (note you will keep all your personal data i.e. passwords, bookmarks etc):
```
sudo apt-get remove epiphany-browser-data epiphany-browser
```
Then go to packages.ubuntu.com and download the jaunty deb's:
[http://packages.ubuntu.com/jaunty/epiphany-browser-data](http://packages.ubuntu.com/jaunty/epiphany-browser-data)
[http://packages.ubuntu.com/jaunty/epiphany-gecko](http://packages.ubuntu.com/jaunty/epiphany-gecko)

You need to install the first one first as it is a dependency. Ignore any messages saying that there is newer version in the repos. If there any errors; just remove the offending package as it is probably a newer, conflicting package. 

Also, if you want to install extensions, you must remove the existing extensions:
```
sudo apt-get remove epiphany-extensions
```
and install the old extensions package:
[http://packages.ubuntu.com/jaunty/epiphany-extensions](http://packages.ubuntu.com/jaunty/epiphany-extensions)

This should get you up and running with epiphany 2.26 (gecko backend) in ubuntu karmic.

One further thing I forgot to mention - you should lock the old packages in synaptic or they will be replaced by the newer ones when you next update your system.

---

