---
title: "Website homepage fades and freezes."
date: 2010-04-13
forum: General Help
---

### Post by Silvernail on 2010-04-13
The reason for this post is to ask if anything similar to this is happening to anyone else.

My OS and Browser
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.4pre) Gecko/20100410 Ubuntu/9.10 (karmic) Namoroka/3.6.4pre

I have a favorite icon in my toolbar menu, when I click on it, after the home screen has been on display for about 10 seconds the screen turns monochromatic gray and freezes. Clicking the X (upper right corner) produces a 'Not responding -- Force quit' window. This is the [COLOR="Red"]only[/COLOR] icon/website affected.

Home page for this web site is addressed" ```
http://devilspanties.keenspot.com/
```
produces the above problem.

```
http://devilspanties.com/
``` Does not produce this problem.
```
http://keenspot.com/
``` produces this problem.

With [COLOR="Red"]Konqueror[/COLOR]  Everything works as expected.

From a terminal command line
```
firefox http://devilspanties.keenspot.com/
``` everything works as expected.

When I went to bed around 2 AM, everything was working.
When I booted  up this am, I had a message that 'Update Manager' was calling. For the last couple of weeks the Update Manager could not install some update to firefox because some file could not be found. Four oh four error as I recollect. Today those updates were installed.

So far I have:
```
sudo apt-get remove --purge firefox
```
```
sudo apt-get install firefox
```

I do not know of any more information I can provide, if you will ask I will make it available.

I just want to be sure the problem in not on my end before I contact the webmaster.

---

### Post by lovinglinux on 2010-04-13
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

### Post by Silvernail on 2010-04-14
Thank you for your very quick reply.

I read  your  post. After reading all the options, I elected to go with turning off the switch in about:config.  Worked like a charm.

Are future updates apt to turn this switch back on or is that one of the things where if it occurs again, check what you did before?

Thank you for the  help.
Dave

---

