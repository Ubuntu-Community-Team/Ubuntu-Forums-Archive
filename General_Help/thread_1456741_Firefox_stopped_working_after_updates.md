---
title: "Firefox stopped working after updates"
date: 2010-04-17
forum: General Help
---

### Post by khopek on 2010-04-17
Hi there!

After some updates to Ubuntu approximately 1 week ago, Firefox completely stopped working. It freezes when attempting to load ANY site, and I have to kill it.

Luckily I had installed Chrome a day before just to try it, but it's not so good when I have to do web dev stuff. I need my Firefox back :D

Does anyone know anything about this? I've tried searching and haven't found anything in the Ubuntu forums. I thought this would resolve itself after more updates but it's been 2 weeks, and I hate using my Windows machine :(

---

### Post by wwarsin on 2010-04-17
did you try to reinstall it?

---

### Post by khopek on 2010-04-17
I'm still kind of a newb and not sure how to completely uninstall and reinstall Firefox while keeping my settings and/or addons.

Also, Firefox's name changed to Namaroka after the Ubuntu updates :D I don't think that matters though, but there has been updates for the 'Firefox Branding' every update these last 2 weeks.

---

### Post by lovinglinux on 2010-04-17
If you have Namoroka, then you have a ppa installed or enabled backports. See quote below (although it seems there is a new version where the problem has been fixed).

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

[*]**Tags:** [[color="DarkSlateGray"]namoroka 3.6.4pre crash flash problem[/color]]("http://www.google.com/search?q=namoroka+3.6.4pre+crash+flash+problem+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

