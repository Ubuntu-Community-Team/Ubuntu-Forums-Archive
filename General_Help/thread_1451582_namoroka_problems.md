---
title: "namoroka problems"
date: 2010-04-10
forum: General Help
---

### Post by sigurnjak on 2010-04-10
This is error i get with my firefox today :
(firefox-bin:28437): GLib-WARNING **: g_set_prgname() called multiple times

** (firefox-bin:28467): WARNING **: Serious fd usage error 14

** (firefox-bin:28467): WARNING **: Serious fd usage error 12
It keeps freezing  and i have to kill it . I have been using it for months  without any troubles . 
Does anyone have any ideas ?

---

### Post by bstone17 on 2010-04-10
I started getting the same thing today, been running fine for months. In addition, sometimes it gives me WARNING **: Serious fd usage error 17 in addition to the error 12 and 14.

---

### Post by 4ll41 on 2010-04-10
Exact same problem here, after using for a long time with no problems. However, in my occasion happens only when I visit a site that needs flash/, or java.   

Seems like a known bug as you can see [https://bugs.launchpad.net/firefox/+bug/513887](https://bugs.launchpad.net/firefox/+bug/513887) , I do not know why it came up today though. 

Have you installed any updates regarding firefox today?

---

### Post by sigurnjak on 2010-04-10
Yes did update today . Will use Chrome for a while and wait it out , i guess .

---

### Post by okusi on 2010-04-10
ditto here. seems to have happened with an update less than 24 hours ago.

there may be some relation with opening tabs.  seems to freeze and grey over more quickly with multiple tabs when i'm using it.

---

### Post by bstone17 on 2010-04-11
I don't even get far enough for firefox to open, it just won't start.  When I start it again, it gives an error box telling me the running version must be closed.  Never gets far enough to open the screen.

---

### Post by lidex on 2010-04-11
> **bstone17 said:**
> I don't even get far enough for firefox to open, it just won't start.  When I start it again, it gives an error box telling me the running version must be closed.  Never gets far enough to open the screen.

You probably have it running in the background. Try killing it in System Monitor or terminal:
```
killall firefox-bin
```

---

### Post by h3n5y on 2010-04-11
Same problem here after today's patch run!

Is there a way to back out the patch? 

Someone has stuffed this one up pretty well....

What can we do to diagnose the problem?

Thanks,
henry

---

### Post by bjoost61 on 2010-04-11
The problem seems to be in 64 bits flashplayer and FF works if you uninstall all with flash in the name.

---

### Post by bstone17 on 2010-04-11
>>You probably have it running in the background. Try killing it in System Monitor or terminal:<<

I do kill it, but even after reboot, it never gets far enough to display a screen, 2nd try to start says already running, but the first one never comes up on the screen (although it is running, since I can kill it and see it in system monitor).

---

### Post by lovinglinux on 2010-04-11
It seems this is a bug affecting only *ubuntu-mozilla-daily* ppa users, due to new Lorentz technology that prevents flash from crashing the browser. If you download the latest [Lorentz](http://www.mozilla.com/en-US/firefox/lorentz/) from Mozilla this problem does not occur and the browser doesn't crash or lock, even if you browse a messed up flash video. Is a very nice technology.

See:
[http://ubuntuforums.org/showpost.php?p=9106945&postcount=27](http://ubuntuforums.org/showpost.php?p=9106945&postcount=27)
[http://ubuntuforums.org/showthread.php?t=1450678](http://ubuntuforums.org/showthread.php?t=1450678)

---

### Post by BoredOutOfMyMind on 2010-04-11
> **lovinglinux said:**
> It seems this is a bug affecting only *ubuntu-mozilla-daily* ppa users, due to new Lorentz technology that prevents flash from crashing the browser. If you download the latest [Lorentz](http://www.mozilla.com/en-US/firefox/lorentz/) from Mozilla this problem does not occur and the browser doesn't crash or lock, even if you browse a messed up flash video. Is a very nice technology.

See:
[http://ubuntuforums.org/showpost.php?p=9106945&postcount=27](http://ubuntuforums.org/showpost.php?p=9106945&postcount=27)
[http://ubuntuforums.org/showthread.php?t=1450678](http://ubuntuforums.org/showthread.php?t=1450678)

So FF is locked by an addon to stop FF locking on addons?

The irony is killing me... more toward Bloatware than before.

The first link and "voiding my warranty" fixed this.  Thank you lovinglinux!

---

### Post by donpedrodos on 2010-04-11
I am also strugling for the past day's to get my pre release working again as before the update from a few day's ago.

The 3.6.4pre freezes with any popup or javascript link voor a download.
Also freezes when page have javascript in them.
Disabeling all javascript solves the problem, but it looks like an old bug with the javastuff is back in town.
I hope they fix this problem soon if it is realy because of this new feature 'Lorentz' ... for now it has for me the name 'lockhim' ;-)


Fault messages are:> ** (firefox-bin:19129): WARNING **: Serious fd usage error 17

** (firefox-bin:19129): WARNING **: Serious fd usage error 14

But also seen Segmentation fault crashes

I went back to install a stable version 3.6.3 for now, everything works as a charm again.

BTW, I run for both the latest Java(TM) Plug-in 1.6.0_19.

---

### Post by lovinglinux on 2010-04-11
> **BoredOutOfMyMind said:**
> So FF is locked by an addon to stop FF locking on addons?

The irony is killing me... more toward Bloatware than before.

The first link and "voiding my warranty" fixed this.  Thank you lovinglinux!

Yes, is ironic indeed, but the problem is not the technology per se, but the package from ubuntu-mozilla-daily, which has some particular problem. If you test the Lorentz from Mozilla you will see that it works great. Additionally, this is a new feature, so we can expect some bugs.

---

### Post by lidex on 2010-04-11
I do not have this issue. You may want to switch to the stable PPA from Daily, at least for now. 
[https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=karmic]("https://launchpad.net/~mozillateam/+archive/firefox-stable?field.series_filter=karmic")

---

### Post by ajoliveira on 2010-04-12
I have the same problem on karmic 64 since the weekend, on namoroka 3.6.4 pre, and yes, if I disable the flash player the problem vanishes.

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
[*] some repositories like *mozillateam/firefox-stable* doesn&#8217;t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by thehouseofstar on 2010-04-21
GOT THE BROWSER GOT THE INVITE TO GOOGLE WAVE but my browser cant open the wave !


PREMATURE !! works fine xx

---

### Post by ajoliveira on 2010-04-21
Disabling flash or loading 3.6.4 has the very same effect: no flash. Use Konqueror when you want flash at least for a while. Interesting to note that after trying the 3.6.4 and even 3.6.3 I returned to 3.6.5-pre and it now works with flash...so my problem is solved. How? Don't have the faintest idea...

---

### Post by lovinglinux on 2010-04-21
> **ajoliveira said:**
> Disabling flash or loading 3.6.4 has the very same effect: no flash. Use Konqueror when you want flash at least for a while. Interesting to note that after trying the 3.6.4 and even 3.6.3 I returned to 3.6.5-pre and it now works with flash...so my problem is solved. How? Don't have the faintest idea...

The ubuntu-mozilla-daily has been updated with fixed packages. Everything works now with 3.6.5pre.

---

### Post by ajoliveira on 2010-04-22
Hi

Thanks for the tip, ll. Caprica City, hey? All the best to Alessandra. ):P

---

