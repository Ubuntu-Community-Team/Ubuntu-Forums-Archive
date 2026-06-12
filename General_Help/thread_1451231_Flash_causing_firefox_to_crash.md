---
title: "Flash causing firefox to crash"
date: 2010-04-10
forum: General Help
---

### Post by aquafocus on 2010-04-10
Good afternoon,
I'm only relatively new to ubuntu and am having a problem with firefox.

There was an update waiting for me this morning to install some dummy package and since I've done that firefox falls down whenever I try to go to a page that requires flash. The screen turns grey and nothing happens.

With my limited knowledge (and inability to use any page that requires flash) I've tried to remove and re-install flash but nothing I do seems to work.

Can anyone help please because it's driving me insane.

Thanks

Si.

---

### Post by jwbrase on 2010-04-10
Have you tried Opera? I had similar problems with my first Ubuntu install (Flash + Firefox + 64 bit Linux is often painful), and found that Opera worked fine where Firefox choked. In fact, I still use Opera instead of Firefox even though Firefox works fine on my current machine.

---

### Post by aquafocus on 2010-04-10
Thanks for your reply. Ideally I wanted to try and keep firefox as it bugs me when things go wrong that can't be fixed.
None the less, Opera is now installed and working a treat. 

Thanks for your help.

---

### Post by vzomik on 2010-04-10
> **aquafocus said:**
> Thanks for your reply. Ideally I wanted to try and keep firefox as it bugs me when things go wrong that can't be fixed.
None the less, Opera is now installed and working a treat. 

Thanks for your help.

Search "Firefox Lorentz"

---

### Post by lovinglinux on 2010-04-10
If you are NOT using *ubuntu-mozilla-daily pp*a, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) and the [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) sections of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If you ARE using *ubuntu-mozilla-dail*y ppa, then see the quote below:

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
[*] some repositories like *mozillateam/firefox-stable* doesn&#8217;t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

