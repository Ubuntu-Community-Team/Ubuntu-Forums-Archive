---
title: "Flash crashing issues"
date: 2010-04-03
forum: General Help
---

### Post by SeanCly10 on 2010-04-03
Hello all,

After endless hours searching the forums and Google, I am no closer to solving my issue than I was when I started...the current, apparently rampant problem of Flash objects crashing Firefox, Chrome, Galeon, Seamonkey, etc. to desktop, and sometimes logging me out entirely.

This shows up most often with Facebook games, to which my wife is currently addicted and the source of the frustration. Every one of them has crashed the browser or logged the system out at some point, and I'm tearing my hair out trying to find a solution.

*Is* there a solution out there somewhere, or one in the works? For that matter, just what is causing this foolishness?

Thanks all,
Sean

---

### Post by TheNerdAL on 2010-04-03
Which flash do you have Adobe or Linux?

---

### Post by SeanCly10 on 2010-04-03
I'm using flashplugin-nonfree. Although, to be fair, I've tried the open source one too, with the same results.

---

### Post by SeanCly10 on 2010-04-03
Update: Thing somehow managed to crash Opera from Gmail too. WTH?

---

### Post by TheNerdAL on 2010-04-03
Hmm.. It could be your video card or something other than Flash, just a thought though.

---

### Post by SeanCly10 on 2010-04-03
I suppose it's possible, although it's an entirely new flavor of error if it's true. I'm running an Nvidia card with the restricted driver, and no issues up until now.

---

### Post by TheNerdAL on 2010-04-03
Try updating the drivers if you haven't.

---

### Post by SeanCly10 on 2010-04-03
I am to the best of my knowledge. Synaptic tells me plugin version 10.0.45.2-1karmic1.

---

### Post by skunkbad on 2010-04-03
From my experience, it's not just Ubuntu that has problems with Flash. I have Windows and Mac computers, and I feel Flash is bad for all of them. I know that doesn't help you, but I don't know what else to say.

---

### Post by TheNerdAL on 2010-04-03
I mean update your video card drivers if you haven't.

---

### Post by SeanCly10 on 2010-04-03
Seems they are, if I'm looking at the right thing.

---

### Post by TheNerdAL on 2010-04-03
Nvidia.com and download drivers.

---

### Post by SeanCly10 on 2010-04-03
Updated to Nvidia's most recent version. Let's see how it goes.

---

### Post by lovinglinux on 2010-04-03
> **SeanCly10 said:**
> I'm using flashplugin-nonfree. Although, to be fair, I've tried the open source one too, with the same results.

Perhaps because you still have the open source version installed and it is taking over the flash content.

> **SeanCly10 said:**
> I am to the best of my knowledge. Synaptic tells me plugin version 10.0.45.2-1karmic1.

Synaptic won't tell which version is being used by the browser, only which version is installed by the package manager. Type **about:plugins** in the address bar of Firefox and check the version displayed there. If it says something like 9.xxxx, then see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by SeanCly10 on 2010-04-07
> I mean update your video card drivers if you haven't. 

Ten-four. Updated to latest version.

> Perhaps because you still have the open source version installed and it is taking over the flash content.

Uninstalled everything and installed just the flashplugin-nonfree, but no apparent effect. About:plugins also shows the latest version.

The problem is still going on, and it's gotten weird. Some days, it'll cut off only once a day, or maybe not at all, other days it'll be every minute or so. The randomness is crazy. Any news about WTH is going on?

---

### Post by lidex on 2010-04-07
Close your browser (copy this info somewhere first). Run these commands:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get remove flashplugin-installer
```

Now these:
```
sudo updatedb
locate libflashplayer.so
```

Delete any instances that are still found.
To check they are gone, run the last two commands again. With no libflashplayer.so on your system run this:
```
sudo apt-get install flashplugin-installer
```

Open your browser and check "Tools>Add-ons>Plugins"

---

### Post by SeanCly10 on 2010-04-08
I'd love to say that it helped, but it hasn't. * sigh * Wife was on youtube today, and the browser crashed out 4 times in 2 minutes.

Something else to add, though: running Google Chrome restricts the crash to just the object that crashed, keeping the rest of the browser running. It comes back with a message saying that 'libflashplugin.so' crashed. A clue, maybe?

---

### Post by lidex on 2010-04-09
Post the output of these commands:
```
sudo updatedb
locate libflashplayer.so
```

Also, what is reported in firefox: "Tools>Add Ons>Plugins"?

---

### Post by SeanCly10 on 2010-04-09
> Post the output of these commands:

```
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so
```

Under "Tools>Add Ons>Plugins", we have plugins for:
Adobe Reader 9.3
DivX Web Player
Quicktime
Shockwave Flash (version 10.0 r45)
VLC Multimedia Plugin
Windows Media Player Plugin 10

---

### Post by lovinglinux on 2010-04-10
See [this](http://ubuntuforums.org/showthread.php?t=1450678).

---

### Post by robertneville777 on 2010-04-10
> **SeanCly10 said:**
> I'd love to say that it helped, but it hasn't. * sigh * Wife was on youtube today, and the browser crashed out 4 times in 2 minutes.

Something else to add, though: running Google Chrome restricts the crash to just the object that crashed, keeping the rest of the browser running. It comes back with a message saying that 'libflashplugin.so' crashed. A clue, maybe?

Yeah, I'm in the same boat as you're in: I thought I was the only one having this problem.

Anyway, I think it's the libflashplayer.so crashing everything. Before I tried the Flash beta like everyone suggested, Youtube would not respond to my clicks, i.e. not being able to pause or fast-forward in the video. Now that I have "upgraded" to the 64-bit beta version, flash crashes all my web browsers, about 75% of the time.

Is this a bug, or are we both the only users facing this problem? :confused:

---

### Post by SeanCly10 on 2010-04-10
I simply cannot believe that this is anything short of a major bug; I have seen countless people experiencing many different varieties of the same problem, with varying degrees of severity. 

That libflashplayer.so does seem to be the root of the problem, and I must say that my problems began with the fresh install of Karmic, though it seems to have expanded to Jaunty as well from what I read, so no use downgrading.

I just hope that someone figures this one out soon, because Flash is everywhere now, and being unable to run it with consistency makes the 'Net well nigh unusable.

lovinglinux: I'll give that a try straight away. Thanx.

---

### Post by SeanCly10 on 2010-04-12
Okay, running the Lorentz build, instead of crashing to the desktop or just crashing the current tab, I was logged out. :(

Update, part deux: Wife does the testing, so to speak, while I'm at work during the day, and she reports that Lorentz does fine with most websites, but with certain sites, particularly Flash-heavy sites, it'll lock up and never fully load. Facebook, one of her most visited sites, won't work for Flash games at all, and she has to go back to Chrome.

---

### Post by SeanCly10 on 2010-07-10
Anything new to report from anyone? Still having regular crashes, though with FF 3.6 at least it's isolated.

---

### Post by jdorenbush on 2010-07-12
I continue to experience this problem when trying to upload photos on Flickr.com. I frequently get the plugin crash error message.

My system:
Ubuntu 10.04 64-bit
Google Chrome 5.0.375.99 beta

---

### Post by SeanCly10 on 2010-07-14
It happens with me just as often in Firefox as it does in Chrome, maybe even a little bit more so. It doesn't happen as often as it used to, but it didn't used to happen *ever*. Something has got to be wrong.

---

