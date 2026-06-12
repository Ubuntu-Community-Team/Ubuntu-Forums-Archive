---
title: "Reinstall firefox 3.5.8"
date: 2010-04-08
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-04-08
anyway to reinstall firefox 3.5.8?

it seems no matter what i install from the synaptics, 3.6 will be installed. they are all "dummy upgrade" packages i see.

3.6 is really really bad.

---

### Post by lovinglinux on 2010-04-09
Probably because you have a ppa installed. Go to "System  >> Administration >> Software Sources >> Other Software", disable the ppa related to Firefox and re-install it.

BTW, Firefox 3.6 is not bad. In fact it works great for me. Perhaps you just need to optimize it. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

What are the problems you have with 3.6?

---

### Post by NiGhtMarEs0nWax on 2010-04-10
Thanks, yes you were right i did. and yes again you are right, it isn't that bad actually, i just had some cpu issues with video playback using flash, tuns out it was the "ubuntu firefox modifications 0,8" addon, i just disabled it and it is running as good as 3.5.

Thanks for your time. :)

---

### Post by NiGhtMarEs0nWax on 2010-04-11
hmm, firefox is crashing when atgempting to play flash content, even in safe mode. i fell back to 3.5.9 until 3.6 or 7 os stable. :)

Thank you.

---

### Post by lovinglinux on 2010-04-11
> **NiGhtMarEs0nWax said:**
> hmm, firefox is crashing when atgempting to play flash content, even in safe mode. i fell back to 3.5.9 until 3.6 or 7 os stable. :)

Thank you.

See [Firefox Lorentz](http://ubuntuforums.org/showthread.php?t=1450678).

---

### Post by pcdave98 on 2010-04-11
Don't mention Flash and Firefox to me!

Grrrrrrrr

:(

---

### Post by steveneddy on 2010-04-11
> **pcdave98 said:**
> Don't mention Flash and Firefox to me!

Grrrrrrrr

:(

Grrrr? .... ok

I don't have any issues with FF or Chrome with Flash.

Who mentioned these things to you?

---

### Post by pcdave98 on 2010-04-11
Apologies - I was being too cryptic.

I was simply sharing the OP's frustration with the Flash problem. It took me several days of Googling, and getting help on this forum, to get Flash and Firefox working on my desktop. After installing Ubuntu on my laptop, and discovering Flash and Firefox didn't work, I though - no problem, I've been here before. 

No such luck. Several more days of Googling followed.

:P

This doesn't help the OP. I should probably have kept quiet.

Sorry.

---

### Post by lovinglinux on 2010-04-12
> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn’t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by guybryant on 2010-04-14
hmm so I don't have the ppa listed under the other section of my software sources.
I also can't downgrade to 3.5.9

I just used my terminal to install 3.6.3 and I want to go back...too bad ctrl + z won't work.
Any suggestions?

---

### Post by lovinglinux on 2010-04-15
> **guybryant said:**
> hmm so I don't have the ppa listed under the other section of my software sources.
I also can't downgrade to 3.5.9

I just used my terminal to install 3.6.3 and I want to go back...too bad ctrl + z won't work.
Any suggestions?

How did you install 3.6.3?

---

### Post by Karmic Alice on 2010-04-16
> **guybryant said:**
> hmm so I don't have the ppa listed under the other section of my software sources.
I also can't downgrade to 3.5.9

I just used my terminal to install 3.6.3 and I want to go back...too bad ctrl + z won't work.
Any suggestions?


Yeap.```
$ sudo aptitude update
``` after you deleted that PPA, then try to reinstall. I just did it now. blue icon gone and a beautiful firefox showed up. (3.5.9)

By the way, having this problem for a almost an hour :P:) made me search for alternatives. I was amazed by how fast, light, simple yet powerful chrome is. (never been a fan of google, but this time they got to do something "safari alike".

---

