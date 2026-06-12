---
title: "is there any performance/stability differences between Google Chrome and Chromium?"
date: 2011-03-11
forum: General Help
---

### Post by nrundy on 2011-03-11
are the differences between Google Chrome and Chromium (as released through Ubuntu repo) essentially "cosmetic." Or does the testing that Google does on Chrome further its stability and performance as compared to Chromium?

I keep reading how Chromium is unstable and more of a test bed. Does Ubuntu "refine" Chromium before distribution kinda like Google refines Chrome?

---

### Post by davidmohammed on 2011-03-11
I presume you've read the [wiki]("http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome") on this?

---

### Post by nrundy on 2011-03-11
Yes, I've read it, thanks.

Actually this document was kinda the source of my question because it doesn't say whether Chromium receives any kind of stability testing like Chrome. It says Ubuntu tracks the same version number--but it says nothing about if this is a refined version or if it's just the unstable "nightly" chromium build that Google refined and release as a Stable.

---

### Post by davidmohammed on 2011-03-11
as far as I understand it - ubuntu takes a cut of the source code at the point chrome changes its version number.  ubuntu then compiles its own specific changes - some of which is described in the wiki, before releasing it.

So, in theory, ubuntu chromium is just as stable as chrome but without all the chrome build specifics (in the wiki).

---

### Post by nrundy on 2011-03-11
david, does your "Preferences" open into a new window or a tab? If I navigate to Wrench > Preferences a new window opens up. 

Chrome on Windows opens into a Tab.

---

### Post by davidmohammed on 2011-03-11
I use chrome primarily because it has its own custom flash rather than depending on the flash installed with ubuntu.  Preferences behaves the same as windows i.e. opens in a new tab.

---

### Post by nrundy on 2011-03-11
mine must be messed up. 

I prefer the old Preferences setup. I can't even sort by Block/Allow in JavaScript and Cookies anymore. blah.

---

### Post by nrundy on 2011-03-11
> **davidmohammed said:**
> I use chrome primarily because it has its own custom flash rather than depending on the flash installed with ubuntu.  Preferences behaves the same as windows i.e. opens in a new tab.

So you download Google Chrome? It updates versions automatically too, right? I'm using Chromium.

---

### Post by davidmohammed on 2011-03-11
Suggest rename your profile/cache folders (see the wiki) and restart chrome/chromium

---

### Post by uRock on 2011-03-11
> **nrundy said:**
> So you download Google Chrome? It updates versions automatically too, right? I'm using Chromium.
Yes, you will get updates as soon as Google loads them on their repo server.

---

### Post by davidmohammed on 2011-03-11
... and I use [this ppa]("http://www.ubuntuupdates.org/ppas/8") to keep up with the latest stable builds.

---

### Post by nrundy on 2011-03-11
I renamed the config and restarted but Preferences still opens into a new window.

You use PPA? So the Google Chrome does not auto-update itself on Linux like it does on Windows?

I just installed Google Chrome. It opens Preferences into a Tab. Maybe a bug in Chromium?

---

### Post by uRock on 2011-03-11
> **nrundy said:**
> I renamed the config and restarted but Preferences still opens into a new window.

You use PPA? So the Google Chrome does not auto-update itself on Linux like it does on Windows?

I just installed Google Chrome. It opens Preferences into a Tab. Maybe a bug in Chromium?
When you install Chrome, the installer adds the PPA.

---

### Post by nrundy on 2011-03-11
> **uRock said:**
> When you install Chrome, the installer adds the PPA.

ah, yes I see that it now shows the PPA in my update manager. Wow Chrome is already updated again to 133.

So do most Ubuntu people run Chrome (instead of Chromium)? uRock are you running Chromium? does your Preferences open in a new Tab?

---

### Post by kerry_s on 2011-03-11
> **nrundy said:**
> I renamed the config and restarted but Preferences still opens into a new window.

You use PPA? So the Google Chrome does not auto-update itself on Linux like it does on Windows?

I just installed Google Chrome. It opens Preferences into a Tab. Maybe a bug in Chromium?

check "about:flags".

---

### Post by nrundy on 2011-03-11
> **kerry_s said:**
> check "about:flags".

what am I looking for? everything in my about:flags is "disabled"

---

### Post by nrundy on 2011-03-11
I figured it out: if the browser (chrome or chromium) starts by default in Incognito mode then Preferences will open in its own window instead of a Tab. Remove incognito and then Preferences always opens into a tab.

---

### Post by uRock on 2011-03-11
> **nrundy said:**
> ah, yes I see that it now shows the PPA in my update manager. Wow Chrome is already updated again to 133.

So do most Ubuntu people run Chrome (instead of Chromium)? uRock are you running Chromium? does your Preferences open in a new Tab?
I haven't used Chromium in quite some time. For the past few days I have been using Firefox 4.0 in the the not yet released version of Xubuntu and I am liking both, a lot. I will be really happy when the end of April gets here.

---

### Post by nrundy on 2011-03-11
> **uRock said:**
> I haven't used Chromium in quite some time. For the past few days I have been using Firefox 4.0 in the the not yet released version of Xubuntu and I am liking both, a lot. I will be really happy when the end of April gets here.

I'd prefer to use Firefox but I can't stand its instability any longer. Chromium is so much more stable and quick especially when browsing with several tabs open. Firefox hangs, takes forever to start, tells me its already running when it isn't. It drives me nuts. The multi-process/modular aspects of Chromium won me over the same way Linux modular is preferable to Windows.

I'm hoping Firefox will get better when they implement their modular process with Electrolysis. Plus I hope Firefox can get rid of the Titlebar like Chrome does.

---

### Post by nrundy on 2011-03-14
I came across this info which answers my questions about this topic. Here's a link for others who are interested:

[http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta](http://askubuntu.com/questions/6253/whats-the-difference-between-google-chrome-and-or-chromium-what-are-the-advanta)

---

