---
title: "How to update Firefox to version 3.5?"
date: 2009-09-23
forum: General Help
---

### Post by zking on 2009-09-23
I am currently using Firefox version 3.0.14

I want to update to version 3.5

What's the easiest way to do this?

---

### Post by dj-toonz on 2009-09-23
goto [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and follow th walk though

---

### Post by wojox on 2009-09-23
Open Synaptic Package Manger. It's in there.

---

### Post by peculiar penguin on 2009-09-23
System > Administration > Synaptic Package Manager

Find and install the "firefox-3.5" package... it'll be named "Shiretoko Web Browser" in the menu and have a different icon, but it is Firefox 3.5.

---

### Post by dj-toonz on 2009-09-23
The problem with running the 3.5 browser from the jaunty repos is it's a beta version & some web sites won't work with it just like extensions & add-ones the one from Ubuntuzilla (in the link given)  is the official browser from Mozilla, updates the version what Jaunty comes with

---

### Post by peculiar penguin on 2009-09-23
> The problem with running the 3.5 browser from the jaunty repos is it's a beta versionNo, not really (see [http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)). It's at version 3.5.2 right now and 3.5.3 is in proposed.
> some web sites won't work with itBroken ones that expect certain user agents maybe?
> just like extensions & add-onesMy usual suspects all seem to work fine, fortunately.

---

### Post by Yellow Pasque on 2009-09-23
Change Shiretoko's user agent: Start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the general.useragent.extra.firefox key. Modify the *Shiretoko* part of this key to say Firefox. You may need to restart the browser for the change to take effect.

---

### Post by lovinglinux on 2009-09-24
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

### Post by kaibob on 2009-09-24
> **peculiar penguin said:**
> No, not really (see [http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)). It's at version 3.5.2 right now and 3.5.3 is in proposed.
Broken ones that expect certain user agents maybe?
My usual suspects all seem to work fine, fortunately.
I originally installed Firefox 3.5 from the repo's. I just got the latest jaunty updates, and they included Firefox 3.5.3. After updating, I checked Firefox Help > About, and it does indeed show version 3.5.3.

BTW, I do not have a check mark in Synaptic next to jaunty-proposed updates.

---

### Post by peculiar penguin on 2009-09-24
> **kaibob said:**
> I just got the latest jaunty updates, and they included Firefox 3.5.3.
[...]
BTW, I do not have a check mark in Synaptic next to jaunty-proposed updates.

Same here. Wasn't available when I wrote that post, so it was just pushed out to updates...

edit: "4 hours 20 minutes             ago" according to launchpad :)

---

