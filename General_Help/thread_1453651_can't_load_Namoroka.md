---
title: "can't load Namoroka"
date: 2010-04-13
forum: General Help
---

### Post by dluzius on 2010-04-13
[B]I can't load Namoroka ever since I let the system do an auto update last week. Now when I click on the Namoroka icon it says session manager loading, then freezes up, and tells me Namoroka is not responding.
I did a search on this site, and tried all the suggested fixes, but still have the same problem. Should I just continue using Opera, in the hope that when I update to 10.4 everything will magically be fixed for me? I really prefer to use Firefox or Namoroka. Terminal reports "Serious FD usage error 14 and 12"
Is there a definitive fix for this?
I'm running Kubuntu 9.10 :(
Thanks, Dave[/B]

---

### Post by TheSqueak on 2010-04-13
Open Firefox in safe mode

Go to about:config

Enter "ipc" in the filter box

Change dom.ipc.plugins.enabled.libflashplayer.so to false

Restart Firefox

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

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by vcax on 2010-04-14
I had the same problem with Namoroka - the browser was freezing or crashing when I open any page that contains flash dynamic components (youtube, gmail, yahoo mail...).  Few times it even froze the whole system. Also, since Firefox 3.6.2 (I believe) the sound in Flash videos was broken (I use Pulseaudio).

First I followed the codeseer instructions from this page (his first post on the page):
[http://ubuntuforums.org/archive/index.php/t-1128720.html](http://ubuntuforums.org/archive/index.php/t-1128720.html)

Than, I used the second option that Lovinglinux - it is the easiest one, I've just followed the instructions from the link:
[http://ubuntuforums.org/showpost.php?p=9104945&postcount=19](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)

Now, my Namoroka works as a charm. It doesn't crash, the sound is playing again in Flash videos and it even seems to work slightly faster.

Thanks guys!

---

