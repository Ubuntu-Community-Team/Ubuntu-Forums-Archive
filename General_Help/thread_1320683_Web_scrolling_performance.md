---
title: "Web scrolling performance"
date: 2009-11-09
forum: General Help
---

### Post by bug2k9 on 2009-11-09
What is it with scrolling performance on many web pages in Ubuntu (although this may be a general Linux issue?). Many graphic intensive websites can get very frustrating with laggy and unresponsive up/down scrolling.
I don't want to compare to other OS but I have never had any issue within MS Windows (any recent version), I have even tried running OSX within a virtual machine on MS Windows and the web scrolling is far far better than my experience with Ubuntu.

I would have thought these days 2D performance should not be an issue, obviously not.

I'm running the latest nvidia drivers for my 7600GT and all other areas of the dekstop are fine, but as I use the web a lot this issue is very frustrating and is keeping me dual booting with XP for the time being.
 
The browsing application doesn't seem to make much difference, although Konqueror maybe slightly quicker but still not good enough.

Any ideas would be appreciated (I have trawled the net and tried many of the common fixes, but none seem to actually fix this problem).


Thanks in advance.

---

### Post by 6205 on 2009-11-09
If you wanna have really fast scrolling in Firefox, first you must disable smooth scrolling in preferences. Next step is to tweak Firefox through about:config page.. Search for mousewheel, like on attached printscreen. Sysnumlines set to **false** and numlines to whatever you want. Higher number gives you faster scrolling, but mine **7** is already really fast..

Btw.: It's not graphics card issue. I believe that it's a general Linux issue, like you mentioned..

---

### Post by Giblet5 on 2009-11-09
Nvidia cards kick posterior in the 3D department. They suck frozen roadkill mandrill snot in the 2D department though...

2D is barely acceptable on this 280 GTX (a few steps up the performance ladder from that 7600 of yours...) but the 3D perf is sweet.

That isn't what causes this though... It's the way that Firefox implements rendering, plus the way most 'intense' sites overuse javascript.

Install NoScript so you can block the retarded little script-kiddies' kindercode and watch your performance skyrocket.

---

### Post by onyxwolf on 2009-11-09
Two words Google Chrome!!! For browsing experience it is UNBEATABLE! Current Ubuntu/.deb build has some issues with higher end functions (some java apps, other such needed plugins, but flash works Great) but is getting worked on and can register with google to have an email sent when stable is finalized. I'm using the .deb current unstable build.
For package...
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

For more info and channels info... 
[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

---

### Post by 6205 on 2009-11-09
> **Giblet5 said:**
> Nvidia cards kick posterior in the 3D department. They suck frozen roadkill mandrill snot in the 2D department though...

Wrong. Graphics card has nothing to to with Firefox scrolling.

---

### Post by 6205 on 2009-11-09
> **onyxwolf said:**
> Two words Google Chrome!!! For browsing experience it is UNBEATABLE! 

IMHO that is only your opinion. I don't need some beta browser from Big brother. Firefox is the best + AdBlock rules :)

---

### Post by P4man on 2009-11-09
> **6205 said:**
> Wrong. Graphics card has nothing to to with Firefox scrolling.

What, you think its the soundcard? Go change your xorg.conf to the VESA video  driver and tell me scrolling is as fast as it was before.


To the OP, do you have a good example of a slow website to test with? I got a similar card but I really cant say I have any scrolling issues. I got MX revolution mouse with that autocruise function that lest the scroll wheel turn freely (great feature btw) I can scroll any website just about instantly..

---

### Post by bug2k9 on 2009-11-09
I have tried the various smooth scrolling options for firefox, they don't make that much difference. I've tried firefox, opera, chromium and konqueror. Konqueror is probably the fastest but isn't as supported as firefox and others for plugins.

Try this link out:
[http://www.m5board.com/vbulletin/e39-m5-e52-z8-discussion/](http://www.m5board.com/vbulletin/e39-m5-e52-z8-discussion/)

This is just one of those usability issues that I can sometimes live with but on some sites it's just too slow. I really notice the difference after going back to ms windows where everything feels so responsive and direct.

I swapped back to ms windows for my main pc a while ago after getting fed up of the smoothed out chunky look of the linux desktop on my monitor (I used 1024x768 ), but after I swapped to a 24" 1080p set recently the linux desktop looks so good (with mscorefonts) when in windows everything is too small at that resolution and I'd hate not to be using the native resolution of such a nice display.

I think linux in general, especially ubuntu is getting far better on the desktop as far as features are concerned, but there is still work to be done on the 'feel' and responsiveness in some areas. 
I know that having the very latest and fastest multi core cpus and graphic cards will probably hide some of these issues, but there is still work to be done when an old athlon xp and nvidia 4200 can browse the web perfectly using ms windows and a core2duo, nvidia 7600gt just struggles on many sites.

---

### Post by bug2k9 on 2009-11-10
I presume there's no answer to this at present, I am surprised that so much effort went in to creating a slick rendered desktop with all its eye candy and something as basic as fast efficient viewing of web pages which must be something that everyone wants these days has been overlooked.

---

### Post by ericmitz on 2009-11-10
I was experiencing the same issue, across the entire OS (not just firefox). If you have an Nvidia graphics card, try either switching to at least the 185 driver, or, do what i did and install the new 190 driver.

[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

---

### Post by blueridgedog on 2009-11-10
The site scrolled fine on my setup with an nvidia 9800, with normal desktop effects.  What is the scrolling like if you select none for desktop effects?  I am using the 185 driver.

---

### Post by blueridgedog on 2009-11-10
> **bug2k9 said:**
> I presume there's no answer to this at present, I am surprised that so much effort went in to creating a slick rendered desktop with all its eye candy and something as basic as fast efficient viewing of web pages which must be something that everyone wants these days has been overlooked.

As you suspect, the answer is that it hasn't and that most users do not share your issue.  You may have to try a different driver version.

How much memory is in your card?  What desktop effects level to you have it set on?  The 7600 is a little light on performance, but should work if setup right.

---

### Post by bug2k9 on 2009-11-11
Thanks for the reply, but I'm already running the latest 190.42 drivers.

---

### Post by bug2k9 on 2009-11-11
The card has 512MB, I've tried with and without desktop effects enabled and there doesn't seem to me much difference in performance.

I used to think that the poor performance on the the Linux desktop was down to poor graphic driver performance (maybe still is?) but since proprietary drivers have been made available I would have expected this issue to be fixed.

The issue is obviously software, inefficiencies in either the environment or drivers, as I can go back 3 or 4 generations of nvidia card and install ms windows and have far superior web browsing performance than I currently have under Ubuntu. It seems the MS and Apple have spent a lot of time optimising their interface to give a fast responsive environment for the user.

---

### Post by JBAlaska on 2009-11-11
I tried the site you referenced with my GeForce 8200 -w-1Gb and had no issues.

---

### Post by 3rdalbum on 2009-11-11
Cannot reproduce here with the Nvidia 185 driver and a GTX260. The 'smooth scrolling' feature in Firefox makes the scrolling fast and pretty smooth - I never used to enable it because it was so slow on Windows. Nice. I get fast scrolling performance without the 'smooth scrolling' feature, on Firefox and Opera.

---

### Post by P4man on 2009-11-11
I tried that site on both windows 7 and ubuntu. In both cases withouh smooth scrolling in firefox it scrolls fast if you measure fast as scroll time to bottom, but perhaps indeed not entirely "smooth", which I think is related to that top javascript navigation bar there updating. Its exactly the same in windows as in ubuntu

Enabling smoothscrolling, who'd have thought, makes it smoother and slower when using the scroll wheel but there is no perceptible difference between windows and ubuntu. Truth be told its seems even a bit worse when using IE8

tested with firefox 3.5 ubuntu 9.10 / windows 7, nvidia 7900GS with 185 drivers.

---

### Post by blueridgedog on 2009-11-11
> **bug2k9 said:**
> The card has 512MB, I've tried with and without desktop effects enabled and there doesn't seem to me much difference in performance.

I have encountered the jagged scrolling issue before and it was only when I had an underpowered graphics card or a weak driver.  Can you try it in Opera or Chrome and compare?

---

### Post by bug2k9 on 2009-11-11
Ok, using Ubuntu I find browser performance in this order (fastest first), Konqueror, Opera, Firefox & Chromium.

I use 1920x1080 resolution, obviously setting a lower resolution such as 1024x768 does improve things, showing that graphic card performance is important.

As a comparison, I tried the same page on an athlon xp2000, nvidia 5200 and windows xp and that page works flawlessly at any resolution. 

I would use Konqueror which is very usable but there are issues with some plugins and doesn't support some of the features of either firefox or opera.

I rarely use the mouse wheel to scroll, preferring to grab the scroll bar to scroll up/down. If I could get performance in firefox to match konqueror I'd probably be happy with that, but there is a big difference, especially at higher resolutions.

---

### Post by pelle.k on 2009-11-29
> 
Nvidia cards kick posterior in the 3D department. They suck frozen roadkill mandrill snot in the 2D department though...

2D is barely acceptable on this 280 GTX (a few steps up the performance ladder from that 7600 of yours...) but the 3D perf is sweet.
I can totally relate to that. For years i haven't been able to enable "smooth scrolling" in firefox on linux because it simply hasn't been that "smooth" to me. More slow and jerky.
Now, i've just installed fedora 12, which uses the free nouveau driver out of the box, and boy can i tell the difference! Super smooth.
Kudos to the open source nouveau developers. If we only could have the best of both worlds...

---

