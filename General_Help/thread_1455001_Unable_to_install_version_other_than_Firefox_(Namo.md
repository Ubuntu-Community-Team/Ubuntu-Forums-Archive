---
title: "Unable to install version other than Firefox (Namoroka) and it constantly freezes"
date: 2010-04-15
forum: General Help
---

### Post by king0 on 2010-04-15
Since yesterday firefox (Namoroka) has been constantly freezing; prior to yesterday it worked perfectly. I've tried un-installing and re-installing, but that didn't fix it. I even tried un-installing Namoroka and installing firefox 3.5 (via apt-get install firefox-3.5), but somehow I continue to get firefox 3.6 (aka Namoroka). Anyone know how to resolve my Namoroka issues or how to install the seemingly more stable 3.5 version? Thanks.

I don't know if this makes a difference, but I originally had installed ubuntu and then installed kde (kubuntu-desktop) desktop on top of it. And yes, I've checked my sources.list to make sure mozilla-daily repository is not listed.

---

### Post by lovinglinux on 2010-04-15
How did you install Namoroka? If you don't have a ppa installed, then there is no reason why you still get Namoroka after installing firefox-3.5.

Close Namoroka and start Firefox with this command:

```
firefox-3.5
```

I would check your sources again, remove any firefox related ppa and reinstall firefox.

Also, have you ever launched Firefox with gksudo to enable Firefox built-in auto-update? That could give you Namoroka.

You can also stick with Namoroka and temporarily fix the problem. See quote below:

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

[*]**Tags:** [[color="DarkSlateGray"]namoroka 3.6.4pre crash flash problem[/color]]("http://www.google.com/search?q=namoroka+3.6.4pre+crash+flash+problem+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by webtechquery on 2010-04-23
Hi..

You can install Firefox, to get rid of using Namoroka.

For detials, check out the website:
[http://www.webtechquery.com/index.php/2010/03/install-firefox-3-5-ubuntunamoroka-firefox/](http://www.webtechquery.com/index.php/2010/03/install-firefox-3-5-ubuntunamoroka-firefox/)

Thanks

---

### Post by lovinglinux on 2010-04-23
> **webtechquery said:**
> Hi..

You can install Firefox, to get rid of using Namoroka.

For detials, check out the website:
[http://www.webtechquery.com/index.php/2010/03/install-firefox-3-5-ubuntunamoroka-firefox/](http://www.webtechquery.com/index.php/2010/03/install-firefox-3-5-ubuntunamoroka-firefox/)

Thanks

You can disable compatibility check, so extensions that are not yet compatible with Namoroka will probably work. I have 52 extensions installed and they all work with Namoroka 3.6.5pre. For more info see [this](http://lovinglinux.megabyet.net/?page_id=220#Extension-Compatibility-2).

---

