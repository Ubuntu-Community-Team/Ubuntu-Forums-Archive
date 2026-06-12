---
title: "on tor network but can't access .onion 's"
date: 2012-05-22
forum: General Help
---

### Post by Forbees on 2012-05-22
i'm being stubborn because i know the browser bundle works, but i want something similar to the vidalia bundle that they only offer to windows


i want this because i want tor to be running, but not always have firefox running, and allow other apps to access tor


i'm pretty sure it's a problem with privoxy

when going to tor's check page i got firefox to use tor, every time i refresh it "appears" i have a new IP. but when trying to access a .onion i get a provoxy error about SOCKS5 not being configured right . .  but if it wasn't then how am i on tor? 


idk it took me about 4 hours to get this far and i'm officially stumped

---

### Post by roelforg on 2012-05-22
Right...
So if vidalia isn't for linux, explain how come my copy of the tor browser bundle has it?
Heck, it's the first entry on [https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)
EDIT:
One pitfall to watch out for: Never close vidalia with the x or the hide in systray as those break on unity, just keep it minimized and it'll work.

---

### Post by Forbees on 2012-05-22
> **roelforg said:**
> Right...
So if vidalia isn't for linux, explain how come my copy of the tor browser bundle has it?

[https://www.torproject.org/download/download.html.en](https://www.torproject.org/download/download.html.en)

browser bundle
vidalia bundle
relay bundle
exit bundle
expert bundle

> 
One pitfall to watch out for: Never close vidalia with the x or the hide in systray as those break on unity, just keep it minimized and it'll work.

no problems on that here. if you hide it in the system tray just reopen it from the system tray

all linux has is the browser bundle

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> [https://www.torproject.org/download/download.html.en](https://www.torproject.org/download/download.html.en)

browser bundle
vidalia bundle
relay bundle
exit bundle
expert bundle


all linux has is the browser bundle

The browserbundle can act as all of them.

I present you with evidence in the form of screenshots.

Note on screenshot one: Pay attention to the button to the right of the "Stop TOR" button

---

### Post by Forbees on 2012-05-22
i understand that


but the browser bundle requires firefox open

i don't always want firefox open

the vidalia bundle under windows installs tor and privoxy alone, allowing you to do firefox if you want it.

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> i understand that


but the browser bundle requires firefox open

i don't always want firefox open

So... Is it that hard to restart the bundle if you want to reopen firefox after closing it?
I took those shots after closing firefox (well, the tor one, not my main instance from which i'm typing this).

---

### Post by Forbees on 2012-05-22
i want to run tor without firefox

and only use firefox when i need it

i'm using tor for more then just looking at .onion pages, and only need firefox running when i want to goto an .onion

having to close firefox every time i start tor is annoying when all i need is a proper privoxy config to have it all run stand alone

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> i want to run tor without firefox

and only use firefox when i need it

i'm using tor for more then just looking at .onion pages, and only need firefox running when i want to goto an .onion

having to close firefox every time i start tor is annoying when all i need is a proper privoxy config to have it all run stand alone

If that's what you want, just install it natively.
But if you don't want that... Here's how to prevent it from autolaunching firefox:
In the dir you unpacked the bundle to, there should be a file Data/Vidalia/vidalia.conf
The third line will have:
```

BrowserExecutable=firefox

```
Change it to:
```

BrowserExecutable=/bin/true

```

---

### Post by Forbees on 2012-05-22
go back to the first post, i did install it natively, but i get a SOCKS error from privoxy

there's some line in the 1000 something comments in the privoxy conf that i either have wrong or still commented out, or in the torrc that i'm missing 

the browser bundle wasn't letting me have other programs run though it without privoxy so telling me to download the browser bundle is just putting me in the same spot...

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> go back to the first post, i did install it natively, but i get a SOCKS error from privoxy

there's some line in the 1000 something comments in the privoxy conf that i either have wrong or still commented out, or in the torrc that i'm missing 

the browser bundle wasn't letting me have other programs run though it without privoxy so telling me to download the browser bundle is just putting me in the same spot...

Sorry, you stated that vidalia is win-only and we went off-topic for a bit...
But we're back!
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)
It has some good info.

---

### Post by Forbees on 2012-05-22
> **roelforg said:**
> Sorry, you stated that vidalia is win-only and we went off-topic for a bit...
But we're back!
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)
It has some good info.

i meant the vidalia bundle, not vidalia the program lol


i thought when it came to linux privoxy was better than polipo?

it was about 2 years ago when i did this last on linux and everyone was saying privoxy

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> i meant the vidalia bundle, not vidalia the program lol


i thought when it came to linux privoxy was better than polipo?

it was about 2 years ago when i did this last on linux and everyone was saying privoxy

The vidalia bundle is nothing more than a prepackaged and precompiled vidalia!
So is the package in the ubuntu repos.

If you have an app for both windows and ubuntu, you create an installer for windows (e.g the vidalia bundle) and a deb-package for ubuntu (e.g sudo apt-get install vidalia).

If you still don't get it:
The vidalia bundle==the vidalia program

---

### Post by Forbees on 2012-05-22
in windows the vidalia bundle comes with Polipo and Vidalia

the browser bundler comes with Polipo, Vidalia, and Firefox

vidalia bundle =/= vidalia =/= browser bundle


the bundles come all preconfigured and working perfectly out of the box, which is why i'm upset that they only offer the browser bundle

---

### Post by Forbees on 2012-05-22
so far, all sites that host the preconfigured polipo conf file i can find are 404


edit

found one - polipo is now working, and so is everything


thanks, but i'm still confused as why privoxy wasn't working since the config for polipo looked the same

---

### Post by roelforg on 2012-05-22
> **Forbees said:**
> in windows the vidalia bundle comes with Polipo and Vidalia

the browser bundler comes with Polipo, Vidalia, and Firefox

vidalia bundle =/= vidalia =/= browser bundle


the bundles come all preconfigured and working perfectly out of the box, which is why i'm upset that they only offer the browser bundle

The same goes for ubuntu, it came preconfigured and working perfectly out-of-the-box on this computer, while it was a pain to get it to work correctly on another one...
It depends on the exact sw-setup you have if the vidalia works perfectly (another one of my systems worked perfectly by following [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)).

---

