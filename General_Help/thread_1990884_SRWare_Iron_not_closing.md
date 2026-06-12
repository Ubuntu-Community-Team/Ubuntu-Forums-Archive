---
title: "SRWare Iron not closing"
date: 2012-05-30
forum: General Help
---

### Post by Bucky Ball on 2012-05-30
Hi All,

As the title says. 

I notice that, even though I had 'Reopen the pages that were last open' ticked in 'Settings', everytime I opened Iron it would come up with the tabs from last time missing and just one tab; my home page. 

Digging deeper, I open 'top' in a terminal, with Iron supposedly closed, and there it still was. I figure the reason I'm not getting my tabs from last time is that Iron thinks it's already open with them and so opens a whole new instance of the browser, which would logically come up with one tab; my home page.

Any ideas how I can kill it completely when I shut it down rather than have it lurking in the background???

* Not that this would have anything to do with it, but I have 'Continue running background apps when Iron is closed' unticked. ;)

---

### Post by wilee-nilee on 2012-05-30
Might just be a anomaly, use a killall "what ever the name is"

You can use htop as well to kill stuff, it has a f3 search and f9 kill, the f commands are at the bottom of the cli.

---

### Post by Bucky Ball on 2012-05-30
> **wilee-nilee said:**
> Might just be a anomaly, use a killall "what ever the name is"

You can use htop as well to kill stuff, it has a f3 search and f9 kill, the f commands are at the bottom of the cli.

Yea, guess it would be 'killall iron' but I don't fancy opening a terminal and issuing that everytime I want to close the browser. Clumsy. There must be a better way; must be some reason this is happening. It's weird, though, because I can't find Iron's config files or any trace of it anywhere so I can't really tweak it. iron.desktop tells me where it is launching from in the install on my 10.10 install (and it doesn't have this problem there or on another machine) but that file is nowhere to be found on 10.04. :-k

---

### Post by wilee-nilee on 2012-05-30
> **Bucky Ball said:**
> Yea, guess it would be 'killall iron' but I don't fancy opening a terminal and issuing that everytime I want to close the browser. Clumsy. There must be a better way; must be some reason this is happening. It's weird, though, because I can't find Iron's config files or any trace of it anywhere so I can't really tweak it. iron.desktop tells me where it is launching from in the install on my 10.10 install (and it doesn't have this problem there or on another machine) ;)

Yeah if it is happening every time not a great option. :)

I noticed that I could not even get it to run in 12.10, installed but would not run, I was a bit surprised.

---

### Post by Bucky Ball on 2012-05-30
Yea, I had trouble on a 10.04 box running Xfce. Minimal install though so I figured I was missing something. Installs but when you launch it, nothing. No GUI, no sign of it. And no 'iron.desktop' file there either so no idea where it even installs to (which is a puzzling question regarding 10.04 on this Xubuntu where it runs but have no idea where it's installed).

---

### Post by vasa1 on 2012-05-30
Did you look in ~/.config. That's where Chrome has the user profile.

Plus I'd turn off background apps in advanced settings. I'm not aware that Iron has any.

---

### Post by Bucky Ball on 2012-05-30
> **vasa1 said:**
> Did you look in ~/.config. That's where Chrome has the user profile.

Plus I'd turn off background apps in advanced settings. I'm not aware that Iron has any.

Turned off as I mentioned. Yes, there is a folder there called Chromium but the files are mumbo jumbo and unconfigurable. There is one there call 'Last\ Session' but it is nonsense text (probably not, I just don't understand it, lots of @s and random stuff). 

I've also discovered a file in ~/.config called 'Trolltech.conf'. What is that? It doesn't look particularly evil and seems to deal with a lot of Qt stuff ... but who knows??? Could be blissful ignorance on my part.

---

### Post by vasa1 on 2012-05-30
> **Bucky Ball said:**
> Turned off as I mentioned. Yes, there is a folder there called Chromium but the files are mumbo jumbo and unconfigurable. There is one there call 'Last\ Session' but it is nonsense text (probably not, I just don't understand it, lots of @s and random stuff). 

I've also discovered a file in ~/.config called 'Trolltech.conf'. What is that? It doesn't look particularly evil and seems to deal with a lot of Qt stuff ... but who knows??? Could be blissful ignorance on my part.
Under normal circumstances, we shouldn't need to fiddle with those.

Re. Trolltech.conf, I have it too but it seems to be related to the OS (qt stuff) rather than the browser.

And > Before the launch of the Qt Project, it was produced by Nokia's Qt Development Frameworks division, which came into being after Nokia's acquisition of the Norwegian company Trolltech, the original producer of Qt.
[http://en.wikipedia.org/wiki/Qt_%28framework%29](http://en.wikipedia.org/wiki/Qt_%28framework%29)
[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&p=5167](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&p=5167)

---

