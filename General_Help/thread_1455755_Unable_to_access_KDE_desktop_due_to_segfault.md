---
title: "Unable to access KDE desktop due to segfault"
date: 2010-04-16
forum: General Help
---

### Post by jdb2 on 2010-04-16
For the past few weeks my system has been exhibiting some strange behavior. The first of these instances has been in the form of a total system lockup necessitating a power cycle -- ie. no kernel panic or oops, but cessation of all on-screen activity and an unresponsive mouse and keyboard. ( The first lockup occurred when the monitor was powered down)

Just a few days ago, I started noticing something else : Launching Firefox (3.6.4pre) resulted in it locking up near start-up especially if I was logged into Gmail. After that I experienced a total system lockup and then another one which has placed me in the situation as suggested in the title.

Specifically, KDM and the KDM login manager will start-up and I will be allowed to type my password. Immediately after that when the first of the icons in the KDE start-up animation starts to come into focus the screen goes black and I am returned to the KDM login manager -- I can enter my password again and continue this process ad infinitum.

Trying to diagnose the issue, I attached GDB to KDM. It seems that after I enter my password one or more of the KDE start-up processes dies with signal 1 or to be more specific : 

```
Program received signal SIGUSR1, User defined signal 1.
0x00007f4ae742d3c3 in select () from /lib/libc.so.6
(gdb) bt full
#0  0x00007f4ae742d3c3 in select () from /lib/libc.so.6
No symbol table info available.
#1  0x000000000040fe90 in ?? ()
No symbol table info available.
#2  0x0000000000410b3f in main ()
No symbol table info available.

```

The full gdb session is attached in gdb.log .

Also, in my .xsession-errors one or more of the KDE start-up processes segfaults as can be seen in this excerpt :

```
Xsession: X session started for jdb2 at Fri Apr 16 09:20:27 CDT 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
grep: /home/jdb2/.kde/share/config/plasma-desktop-appletsrc: No such file or directory
Segmentation fault
```

The full .xsession-errors is attached.


If anyone can offer any advice in how I might go about tracking down this problem I would be most grateful.


As of now, I am at a total loss as to what the specific problem is.


Thanks,

jdb2

EDIT : Seems I forgot to peruse kdm.log . The following might be of interest :

```
Thread tried to wait on itself
QThread: Destroyed while thread is still running
KCrash: Application 'kdmgreet' crashing...
ddxSigGiveUp: Closing log
drkonqi: cannot connect to X server :0.0
```

Looks like there's a problem with kdmgreet. kdm.log is attached.

---

### Post by lovinglinux on 2010-04-16
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

### Post by jdb2 on 2010-04-16
Thanks for the tip.

Oh and after installing some updates ( I'm using KDE 4.3.5 ) which included updates to chromium, firefox and libboost, whatever was wrong seems to have "fixed itself" -- ie. I was able to log in after the apt-get upgrade. 

Strangely though, all my KDE specific settings were wiped/nuked -- it took about 20 minutes to restore them.

Regards,

jdb2

---

### Post by TheNerdAL on 2010-04-16
Mark thread as [SOLVED] if solved. :)

---

