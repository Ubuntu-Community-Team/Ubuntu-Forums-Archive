---
title: "Firefox Flash Player Crashes Firefox"
date: 2006-04-04
forum: General Help
---

### Post by benjammin on 2006-04-04
Hey all, I installed the latest version of the Mozilla/Firefox flash player that's on the packages site, but any time I try to visit a site with a flash animation, I completely crash. I don't get a plugin not installed message, just a total Firefox crash. What do I do? I'm using Breezy and pretty new with Linux, so dumb it down if you don't mind ;) Thanks!

---

### Post by trent dillman on 2006-04-04
open ff and go to ```
about:plugins
```

post the list here

sounds like a conflict??

---

### Post by benjammin on 2006-04-04
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by aysiu on 2006-04-04
You may have a corrupt profile. Try [this](http://www.ubuntuforums.org/showthread.php?t=103930).

---

### Post by benjammin on 2006-04-05
I couldn't seem to get that to work, where exactly is the ~./mozilla directory? I'm a bit confused on how this could be a conflict with any extensions I have running, as I'm only running two (ForecastFox and Gmail Notifier).

---

### Post by aysiu on 2006-04-05
~/.mozilla essentially means /home/benjammin/.mozilla

.mozilla is a hidden directory.

So if you open up /home/benjammin in Nautilus and press Control-H, you should see it.

---

### Post by benjammin on 2006-04-05
Ok, I removed my profile and removed the mozilla-flashplayer package, then tried reinstalling the flash plugin from within Firefox and still have the same problem. Firefox just closes any time I browse to a site with Flash. What the heck is going on?

---

### Post by DeadEyes on 2006-04-05
I have the same problem, ended up using flashblock as a workaround.

---

### Post by aysiu on 2006-04-05
[QUOTE=benjammin]then tried reinstalling the flash plugin from within Firefox and still have the same problem.[/QUOTE] How about not installing the Flash plugin from within Firefox? Try [enabling the Multiverse repositories](http://www.psychocats.net/ubuntu/sources) and then installing Flash from there: ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree flashplayer-mozilla
```

---

### Post by benjammin on 2006-04-05
No dice, I removed the flash plugin, deleted my user profile, then ran the console commands and it still crashes trying to load any Flash page.

---

### Post by aysiu on 2006-04-05
Don't know what else to try.

---

### Post by benjammin on 2006-04-06
Anywhere else I can post this to get help? Maybe on an official bug reporting site or something? It seems other people have the issue.

---

### Post by aysiu on 2006-04-06
[QUOTE=benjammin]Maybe on an official bug reporting site or something? It seems other people have the issue.[/QUOTE] Try this:
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by benjammin on 2006-04-06
I tried using Automatix to install Firefox 1.5.0.1 w/Plugins and it still crashes, so Flash crashing has to be a conflict with other software, right? I went to the packages page for flashplayer-mozilla to check it's dependenicies against what versions I'm running, but all my version were either the same or higher than what was given.

---

### Post by aysiu on 2006-04-06
Just wanted to state for the record that I'm using Firefox 1.5 on Breezy (installed from the Mozilla website manually, not via Automatix), and Flash works just fine. I know that doesn't help you, but I'm pretty sure it's not a conflict with other packages unless you have some strange or obscure packages installed.

---

### Post by pelle.k on 2006-04-19
Try disabling composite in xorg.conf (by commenting it out (#)if it's enabled that is )

---

### Post by moon_dog on 2006-04-19
i've got the same problem.  if i install the flash plugin, everytime i login to my yahoo email account, firefox just shutsdown automatically.

---

### Post by hanexar on 2006-04-19
[QUOTE=pelle.k]Try disabling composite in xorg.conf (by commenting it out (#)if it's enabled that is )[/QUOTE]

I had the same problem and this work perfectly.  Thank you.  

If you want to keep composite enabled and still have flash working in firefox, try this work around I found here: [http://www.ubuntuforums.org/showthread.php?t=142721](http://www.ubuntuforums.org/showthread.php?t=142721)


[QUOTE=chrisrx]Flash doesnt like the composite extension being used

Add
Code:

export XLIB_SKIP_ARGB_VISUALS=1

to /usr/bin/firefox before the last line (which should be the launch line) and everything should be fine[/QUOTE]

---

### Post by moon_dog on 2006-04-19
everything works fine after i commented out the extension line in xorg.conf.  however, i'd still like to be able to use compiz, since i find the transaparent terminals very useful.  is there some workaround to this problem?  i've tried adding the extra line by chrisx to the firefox script, but it doesn't seem to work for me.  is there some other way to use transparent terminals besides throught compiz and the transset command?

---

### Post by hanexar on 2006-04-20
Weird, it worked perfect for me.

Try this instead:

Type "sudo gedit /usr/bin/firefox" and add the line so your file now should look like this:


```
export XLIB_SKIP_ARGB_VISUALS=1 
MOZ_DIST_BIN="/usr/lib/mozilla-firefox" 
MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"
```

Got this from: [http://www.ubuntuforums.org/showpost.php?p=939781&postcount=420](http://www.ubuntuforums.org/showpost.php?p=939781&postcount=420)

---

### Post by eeried on 2006-05-01
Many thanks, hanexar but could you be a little more explicit?

> Type "sudo gedit /usr/bin/firefox" and add the line so your file now should look like this:


Code:

export XLIB_SKIP_ARGB_VISUALS=1 
MOZ_DIST_BIN="/usr/lib/mozilla-firefox" MOZ_PROGRAM="/usr/lib/mozilla-firefox/firefox-bin"


This is how my file ends:
```

## Stop addon scripts
moz_pis_startstop_scripts "stop"

exit $exitcode
# EOF.
```

Where exactly do you insert the three lines (is the two lines following "export..."  need to inserted)? :-? 

Cheers

---

### Post by arnieboy on 2006-05-01
try the following to solve this problem:
[http://ubuntuforums.org/showthread.php?t=89827](http://ubuntuforums.org/showthread.php?t=89827)

---

### Post by hanexar on 2006-05-02
[QUOTE=eeried]

Where exactly do you insert the three lines (is the two lines following "export..."  need to inserted)? :-? 

Cheers[/QUOTE]

I put it right before the last line, which is suppose to be the exec line.  Like this.  Btw, I only use the export line, and it work great for me.  

```

export XLIB_SKIP_ARGB_VISUALS=1

exec_verbose ${MOZ_PROGRAM} "$@" 
```

Try to find the exec line and put it before.  

Arnies, nice Howto, but it doesn't seems to work for.  Thanx anyway.

---

### Post by phorque on 2006-05-20
Firefox started crashing recently for me. I found that if I uninstalled **libflash-mozplugin** in synaptic, that solved the problem. To watch flash I use **flashplugin-nonfree** (which I reinstalled just incase). 

I had both installed before and it didn't do anything like this, but it seems that having both installed at their current versions causes a crash. Could that maybe be your problem too?

---

### Post by phyzome on 2006-05-24
phorque: I second that.  Firefox started crashing every time I viewed a page that contained flash, until I uninstalled the libflash0c2 package and the two packages that depended on it (libflash-mozplugin and libflash-swfplayer).

---

### Post by mgmiller on 2006-06-07
I had a crazy time getting flash to work with firefox in ubuntu 6.06.  I could make it work with mozilla, but with firefox, it either crashed or gave me sound and no video.  I tried uninstalling and reinstalling from various sources.  I finally figured out that, since I had done an upgrade from Breezy to dapper, I had a few conflicting packages installed.  Here is what I did:
From syaptic package manager:
1) uninstall flashplugin-nonfree
2) uninstall libflash-mozplugin (this should also unistall libflash0c2)
3) uninstall libflash-swfplayer
and finally,
4) reinstall flashplugin-nonfree

After restarting firefox, there was finally joy in mudville!

Hope This Helps!!!

---

### Post by shizeon on 2006-09-11
So I was having the same problem with Flash crashing in Firefox whenever I viewed a flash enabled page on an dapper aiglx-ati setup (with compiz enabled or disabled).  I like to check out the occasional youtube vid so I was really wanting to get this working.  After playing around with installing/uninstalling libraries and reviewing the forums, the following worked for me.  Thought I would share in case someone is still having this issue.  

In Firefox type 'about:plugins' in the URL area.  For me I had two libraries both registered for swf.  One at the top of the list and one at the bottom.  I manually disabled the libflash-mozplugin.so and left the libflashplayer.so (mozilla-nonfree on I think) one alone, restarted firefox and all is well now.

```

sudo mv /usr/lib/mozilla/plugins/libflash-mozplugin.so /usr/lib/mozilla/plugins/libflash-mozplugin.so.old
```

Hope this helps someone.

Ubuntu Dapper 6.06 user

---

### Post by itaintover on 2008-05-07
Had the same problem on ubuntu 8.04 firefox 3 beta 5, tried all of those fixes/mozilla flash plugins, nothing worked, flash was crashing firefox randomly. Finally I removed all mozilla flash plugins so flash didn't work, went to some site with flash on it, ff wanted me to install flash and I chosed GNASH. Since that ff haven't crashed once. The minus of Gnash is that I can't fast forward or backward flash videos and volume change +/- in those video flash players is not working and volume is always 100% so sometimes when it's too loud I have to use sound mixer icon on my Gnome panel to turn it down. Works for me.

---

### Post by eeried on 2008-05-08
hello,
I'm glad to hear thet Gnash is working, that's great news!

What I've done recently is uninstall the ubuntu flash package and remove the libflash thing installed through the ubuntu flash package and download the flash tar.gz from Adobe, extract and copy  libflashplayer.so to /usr/lib/firefox/plugins

Thus you have the layest flash plugin version and you don't install flash on your computer (a useless thing for most of us).

But I'm going to try Gnash, I'd love to get rid of Adobe.
cheers

---

### Post by xr1c3x on 2008-06-06
Hi I also get firefox crashes when viewing flash but its not everytime I open a window with flash. Usually its when I have one open already and I click a link with another flash video is when it crashes. 

ie I'm on youtube watching a video then I click a link for another and once it started to load the page it crashes. 

I was about to uninstall some of the plugins installed and reinstall them but found it was already done like everyone said.

flashplugin-nonfree is already installed
libflash-mozplugin is uninstalled so is the libflash0c2

I'm running ubuntu 8.04 with firefox 3 beta 5

any ideas?

---

