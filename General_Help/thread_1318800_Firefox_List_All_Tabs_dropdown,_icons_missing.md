---
title: "Firefox: List All Tabs dropdown, icons missing"
date: 2009-11-07
forum: General Help
---

### Post by Cobalto on 2009-11-07
Hi everyone.

The dropdown list of all open tabs that Firefox has in the upper right corner is not showing the correspondig favicons.

Curiously, the icons do show up on the address bar and the tabs themselves.

I've googled this extensively and haven't found anyone with the same problem, or the about:config setting that handles this.

Any ideas?

Thanks,

Cobalt

---

### Post by _Narcisse_ on 2009-11-09
Hi,

I just realized I got the same problem, if we can call it that way.
With Firefox 3.5.4 on Ubuntu 9.10, the favicons are missing in the dropdown "list all tabs".

Strange. Maybe I'll report this as a bug on Launchpad.

Anyone else experiencing this behavior ?

---

### Post by PrarieD0G on 2009-11-09
Yep, same goes for me (9.10 Ubuntu, 3.5.4 Firefox). I guess it's just something they didn't add.

Either that or an extension is messing things up...

---

### Post by _Narcisse_ on 2009-11-10
Ok, can you guys tell me which extensions you have installed, if any ?

If we got one in common, maybe we can find which one is messing up.
If one of you could test a fresh Firefox without any extension, that'd be great. I could do it myself but I have many extensions.

Thanks.

---

### Post by irishbreakfast on 2009-11-10
Same here. Plus I don't get favicons in the search drop down. I did a quick test by renaming my profile so that a plain firefox would start and I had the same behaviour in the search drop down. Didn't check the tab drop down.

Adblock Plus
ColorfulTabs
DownloadHelper
DownloadSort
FlashBlock
linkbrowser
Locationbar2
Multiple Tab Handler
NoScript
OpenBook
Shelve
Tor-Proxy.Net Toolbar 
Ubuntu Firefox Modifications
Xnet Usage Monitor
Zotero

Retested, disabled all addons and plugins, no favicon in list all tabs either.

---

### Post by _Narcisse_ on 2009-11-10
@irishbreakfast: I did not realize it but I don't have any favicons in the search bar either. We have only two extensions in common, Locationbar² and Adblock. Maybe it's the Ubuntu modifications. I think I'll report a bug on Launchpad later today.

---

### Post by Cobalto on 2009-11-10
I've got these:

- Adblock Plus 1.1.1
- Add Bookmark Here ² 3.5.20091103
- All-in-One Gestures 0.20.0
- AutoPager 0.5.3.5
- British English Dictionary 1.19
- Diccionario español Mexico 1.1
- Extension List Dumper 1.14.4
- Google Gears 0.5.32.0
- Greasemonkey 0.8.20090920.2
- Reload Tab On Double-Click 1.2
- Tabs Open Relative 0.4
- TimeTracker 1.2.5
- Ubuntu Firefox Modifications 0.8
- URL Link 2.03.3
- Xmarks 3.3.3

I disabled the lot and the favicons are still missing. 

I have another profile with only DownThemAll that I use for...um...research purposes, and it show the same problem.

---

### Post by fluffman86 on 2009-11-11
For some reason, Karmic does not enable icons by default.  I fixed this by going to System > Preferences > Appearance.  Flip to the Interface tab and check "Show Icons in Menus"

Notice that this affects *ALL* gnome apps, even your panels, not just firefox.

---

### Post by Cobalto on 2009-11-11
Who the hell is Occam and what is this razor doing here??

fluffman86, thank you very much.

---

### Post by fluffman86 on 2009-11-11
HaHaHa! :D

Don't forget to use thread tools to mark this thread as solved. :)

You're welcome.

Also, you still might want to look into filing a bug report.  I never saw an official announcement saying that this is *supposed* to be default.  I don't think it's a good idea, personally.

---

### Post by Cobalto on 2009-11-11
Marked as solved. Will file bug if _Narcisse_ doesn't. Thanks all.

Cobalt out.

---

### Post by _Narcisse_ on 2009-11-11
I just saw this. Thanks fluffman86.

I too think it's not a good idea to make this the default behavior. I'll report this as a "bug" even if it's not really one.

---

