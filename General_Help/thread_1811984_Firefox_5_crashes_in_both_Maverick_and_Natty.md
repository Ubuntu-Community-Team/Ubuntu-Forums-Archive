---
title: "Firefox 5 crashes in both Maverick and Natty"
date: 2011-07-25
forum: General Help
---

### Post by 3602 on 2011-07-25
Yesterday I opened a thread about this. Yeah.

It can happen anywhere, anytime. Just opening Firefox, loading a tab or just reading a loaded page of text.

Back on Maverick, the severity of the problem augmented exponentially. It eventually led to kernel panics when opening bookmarked pages.

So I installed Natty Narwhal 64. It is a clean install using a burnt disc. Unity UI is fine, by the way.

I thought I've escaped the problem, but no. Just a while ago I got another crash.

On Maverick, I have all four channels open. Here on Natty, I have only the two default channels open.

[Here's the crash report]("https://crash-stats.mozilla.com/report/index/bp-018f4bee-df7a-4968-8e3d-c74452110725") if an expert would be so kind to check it out.

I thought about a hardware, specifically a RAM problem. Memtest86+ has all tests complete, no errors.

I am running FGLRX 11.5 installed through X Updates PPA. My graphics card is AMD MobilityRadeon HD4250 on AMD M880G (HP 1442) with 320MB of shared VRAM.

In terms of Firefox I have Java 6u26 downloaded through the legit Java site, so it is not IcedTea or anything.

So I see some causes.

1. Hardware acceleration within Firefox. I have this disabled and am waiting for another crash to happen in the next few hours. If it doesn't happen, hopefully problem solved.
2. Flash somehow. I use the Adobe Beta version installed by Flash-Aid. I have since disabled Flash-Aid.
3. A rootkit that was retained through a drive format.
4. A fault in RAM that is not detected/detectable by Memtest86+.
5. A fault in other hardware.
6. Ubufox.

I'm not used to Chromium since I am unfamiliar with its general layout and the add-on system. But, if this is purely a Firefox problem (as in nothing wrong with my Natty/hardware), I will switch.

Thank you all very much.

---

### Post by waffen on 2011-07-26
I have the same problems in Ubuntu 10.04 64 bits, FF crash with no reason at any time.

Any solution?

---

### Post by 3602 on 2011-07-26
Try disabling Hardware Acceleration in Preferences.

EDIT: Nope, scratch that. Just crashed.
Crash page [here]("https://crash-stats.mozilla.com/report/index/578adbd5-604b-4b7d-9f92-4d9be2110726"). Seems like something to do with *libxul.so*. Funny how I don't have xulrunner installed.

EDIT II: Try having it run in *firefox -safe-mode* for a while. If it still crashes... If it doesn't, it's an add-on. Which is good news.

---

### Post by Frogs Hair on 2011-07-26
The 64 bit beta version of flash is working well for some users and can be installed via with flash aid if you have it . I have been running the Nightly  build for months which is currently  Firefox 8 alpha one and have not had any problems. :confused:

---

### Post by 3602 on 2011-07-26
Nope. That's not the cause because Firefox *just crashed in Safe Mode*.
Crash [thread]("https://crash-stats.mozilla.com/report/index/bp-5e11d399-aae6-4f98-8d0c-287452110726"). Xul again?

---

### Post by Gyokuro on 2011-07-26
Does Firefox crash only on certain sites? I have Ubuntu 10.04.3 with firefox 3.6.18 and 11.04 with firefox 5.0 and no crash; plugins: flash and addon: adblock plus. All 64-Bit workhorses :-)

---

### Post by 3602 on 2011-07-26
No idea, I don't think so. CNN, Cracked, Ubuntu Forums, XKCD, YouTube, Head-Fi...

---

### Post by waffen on 2011-07-30
Running in safe mod the same problem, here the console report any idea?

```

mario@mario-laptop:~$ firefox -safe-mode
###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 5 requests ago: file /build/buildd/firefox-5.0+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199
###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 5 requests ago: file /build/buildd/firefox-5.0+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199


```

I dont know what that means, but FF are crashing in the same page: [http://www.fishermanslog.com/](http://www.fishermanslog.com/) Chromiun open the same tabs with no problem including that website.

Heres the other crash report:

```

Add-ons: grabthemall@zelazko.info:0.6.1,externalip@erik.morlin:0.9.9.6,{d37dc5d0-431d-44e5-8c91-49419370caa1}:2.9.35,{81BF1D23-5F17-408D-AC6B-BD6DF7CAF670}:7.3.0.0,gic2@getinformer.com:1.1,{c45c406e-ab73-11d8-be73-000a95be3b12}:1.1.9,senseo@nicosteiner.de:1.5.5,{aba3f5c2-35d5-4960-bdfc-de9c162e39ce}:2.0.1.1,{2e710e6b-5e9d-44ba-8f4e-09a040978b49}:1.3.2,{EF522540-89F5-46b9-B6FE-1829E2B572C6}:5.0.3,{37E4D8EA-8BDA-4831-8EA1-89053939A250}:3.0.0.2,silvermelxt@pardal.de:1.4.2,{75CEEE46-9B64-46f8-94BF-54012DE155F0}:0.4.9,{02450954-cdd9-410f-b1da-db804e18c671}:0.96.3,{5F260DF0-AE97-4f7c-96FE-BC87D4FBC422}:3.0.0,backendinfo@chris.hager:1.2.8.0,kosa@kallout.com:2.1.2,{3e9bb2a7-62ca-4efa-a4e6-f6f6168a652d}:1.0,{8BCA0E8A-E57B-425b-A05B-CD3868EB577E}:0.2,codeburner@tools.sitepoint.com:1.6,{5C46D283-ABDE-4dce-B83C-08881401921C}:2.1.6,foxyseotool@foxyseotool.com:0.8.6,{1A2D0EC4-75F5-4c91-89C4-3656F6E44B68}:0.4.6,{b2a4706f-c26d-40ff-abfa-d96aa7a3fa34}:1.0,firebug@software.joehewitt.com:1.7.3,{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}:0.9.8,321tux@arcor.de:1.5.0,joomla-admin@mozilla.org:1.4,{311ece6e-ea6a-442f-a02a-a362e561d892}:3.2,faviconizetab@espion.just-size.jp:1.0.5,siteinfo@wmtips:1.2,{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}:1.3.9,{0FED7D55-65D4-47b6-A6DE-9A4ADB55355F}:1.0.1,firefoxnotify@abhishek.mukherjee:1.5.4,{66E978CD-981F-47DF-AC42-E3CF417C1467}:0.4.3,yslow@yahoo-inc.com:3.0.3,hidemenubar@moztw.org:4.0.20110415,{d57c9ff1-6389-48fc-b770-f78bd89b6e8a}:1.36,{b9db16a4-6edc-47ec-a1f4-b86292ed211d}:4.9.3,langpack-es-MX@firefox.mozilla.org:5.0,langpack-en-GB@firefox.mozilla.org:5.0,langpack-es-AR@firefox.mozilla.org:5.0,langpack-es-CL@firefox.mozilla.org:5.0,langpack-en-ZA@firefox.mozilla.org:5.0,langpack-es-ES@firefox.mozilla.org:5.0,ubufox@ubuntu.com:0.9.1,bindwood@ubuntu.com:1.0.4,compatibility@addons.mozilla.org:0.8.7,{1018e4d6-728f-4b20-ad56-37578a4de76b}:4.1.5,{4BBDD651-70CF-4821-84F8-2B918CF89CA3}:7.0.1,silvermel@pardal.de:1.4.2
BuildID: 20110622131247
CrashTime: 1312047114
EMCheckCompatibility: false
Email: mlacunza@gmail.com
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1308955016
Notes: X_ShmPutImage: BadMatch (invalid parameter attributes); 5 requests agoxpcom_runtime_abort(###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 5 requests ago: file /build/buildd/firefox-5.0+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199)
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 302
StartupTime: 1312046836
Theme: silvermel
Throttleable: 1
URL: http://www.fishermanslog.com/
Vendor: Mozilla
Version: 5.0

This report also contains technical information about the state of the application when it crashed.

```

By now I'll need to setup Chromium like my default browser until this crashing are corrected I cant work with FF crashing again and again.

---

### Post by 3602 on 2011-07-30
Yep. I've purged Firefox and is using Chromium.

---

### Post by waffen on 2011-07-31
But Chromium eat a lot of memory loading the same pages than FF :confused:

so? any help or bug report to check?

---

### Post by 3602 on 2011-07-31
I don't find any "more memory chewing" with Chromium.
But I don't know. I will be distro-hopping to OpenSUSE.

---

### Post by Markmental on 2011-07-31
Don't use firefox. Chrome is a lot better. get it here [http://www.google.com/chrome/](http://www.google.com/chrome/)
Good luck with chromium but i think chrome is more stable

---

### Post by Vinas on 2011-08-01
Edit: the work around for me was to _uninstall_ each extension. Now when I enable Ad Block Plus, or try to enter the Sync menu (Tools -> Setup Up Sync...) it crashes. But the other plugins like Flash and HTTPS everywhere are working again.
 
-----


Ever since the Firefox 5.0 upgrade was released and pushed out it refuses to open with any plugin enabled. So I have been running in safe mode ever since then. So no plugins can be enabled unfortunately.

Running Ubuntu 10.04 amd64...



  Application Basics

        Name
        Firefox

        Version
        5.0

        User Agent
        Mozilla/5.0 (X11; Linux x86_64; rv:5.0) Gecko/20100101 Firefox/5.0

---

### Post by ottosykora on 2011-08-01
So I was kind of lucky or not depends on which way.

I have been running 32bit ubuntu on intel M520 based HP probook 6550b up to 10.10.

But then any attempts to run 11.04 on it resulted in permanent crashing of any mozilla items and frequent crashing of chromium as well. Flash did work on it only abt 2 seconds before it crashed, regardless of version. Yes also the 64bit version did not survive.

Simply no internet possible, not even possible to read this forum. With cromium I was able to read the forum, but when I came to things like search...buuum crash.

Now in the progress of reinstalling 64bit ubuntu on it, so far no real problems apart from that this and that software might not be compatible.

---

### Post by 3602 on 2011-08-01
You might want to post that waterfall on MozillaZine.

---

### Post by Vinas on 2011-08-01
> **3602 said:**
> You might want to post that waterfall on MozillaZine.Yeah. I edited the post anyway because I found that completely uninstalling each addon allowed me to use some basic add ons. Before I had the addons disabled, but firefox would crash regardless if I enabled _anything_ else. Now that every add on was uninstalled I am able to use some add ons. Firefox Sync and Ad Block PLus still crash, however.

---

### Post by waffen on 2011-08-09
Running FF5 from the console show me this error in the last crash:

###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 288 requests ago: file /build/buildd/firefox-5.0+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199
###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 288 requests ago: file /build/buildd/firefox-5.0+build1+nobinonly/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 199

any idea?
I cant use Chrome 13 because it eat a lot of memory....

---

### Post by 3602 on 2011-08-09
Yeah my Chrome 13 is eating a whopping 1.3GB of RAM.
Anyway I used to have 8GB but I am RMAing one of them.
It isn't the RAM, Firefox would just crash and crash no matter what. I think I'm shifting to Chrome for good. You even get free Angry Birds.

---

### Post by waffen on 2011-08-09
> **3602 said:**
> Yeah my Chrome 13 is eating a whopping 1.3GB of RAM.
Anyway I used to have 8GB but I am RMAing one of them.
It isn't the RAM, Firefox would just crash and crash no matter what. I think I'm shifting to Chrome for good. You even get free Angry Birds.

I know the error is not memory, the error message is clear is a problem in a C file, a programming stuff. Like Im not a C dev maybe one of here can help with some recommendation.

Yes Angry is great... my son capture my android tablet for that game :P

---

### Post by 3602 on 2011-08-09
Angry Birds also promotes genocide but that's a matter for another day.

Chrome 13 just crashed on me with no errors to report. It might just be a freak accident since both my RAM and HDD checks out.

---

### Post by waffen on 2011-08-10
I just update to Aurora and the same stuff FF crashing again (in save mode too)... I have installed FF 8 and for now not crash but the lack of extensions available for this version make unusual this version (not firebug for example)

---

### Post by 3602 on 2011-08-11
...Whoa.
Well I'm immensely GLaD that this is not just me who has this problem.
But if it's a C error then everyone should get crashes...Right?

---

