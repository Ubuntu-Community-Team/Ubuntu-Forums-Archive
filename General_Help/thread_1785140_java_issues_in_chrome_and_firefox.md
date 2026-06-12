---
title: "java issues in chrome and firefox"
date: 2011-06-17
forum: General Help
---

### Post by velt on 2011-06-17
hi, im currently running the latest build of ubuntu (all updates), and I have the following issue with java elements in youtube (mostly in youtube video or embbeded youtube video form); sometimes the video doesnt appear and I have to reload. is pretty annoying since the video can go bad (and black), when watching the video and then you have to reload. 

Any ideas? I know there are some issues with ubuntu and flash, and I dont think is a browser thing since the issue is in both firefox and chrome (bot the latest builds).

---

### Post by wildmanne39 on 2011-06-17
> **velt said:**
> hi, im currently running the latest build of ubuntu (all updates), and I have the following issue with java elements in youtube (mostly in youtube video or embbeded youtube video form); sometimes the video doesnt appear and I have to reload. is pretty annoying since the video can go bad (and black), when watching the video and then you have to reload. 

Any ideas? I know there are some issues with ubuntu and flash, and I dont think is a browser thing since the issue is in both firefox and chrome (bot the latest builds).
Hi, fire fox and chrome use the same flash, open fire fox go to addons from the tools menu then type in flashaid in the search and install it, then follow the directions and see if that fixes it.

---

### Post by velt on 2011-06-18
> **wildmanne39 said:**
> Hi, fire fox and chrome use the same flash, open fire fox go to addons from the tools menu then type in flashaid in the search and install it, then follow the directions and see if that fixes it.

and something for chrome?
this seems to be a java issue with linux.

---

### Post by gandaran on 2011-06-18
32-bits or 64-bits ubuntu? if you have 64-bits ubuntu then you should install 64-bits flash, and chrome 32-bits uses built in flash not the system installed flash so if you are having the same problem in chrome and firefox could be due to having 32-bits flash installed in 64-bits system and youtube doesn't use java.

---

### Post by velt on 2011-06-18
> **gandaran said:**
> 32-bits or 64-bits ubuntu? if you have 64-bits ubuntu then you should install 64-bits flash, and chrome 32-bits uses built in flash not the system installed flash so if you are having the same problem in chrome and firefox could be due to having 32-bits flash installed in 64-bits system and youtube doesn't use java.

64 bit ubuntu. 
What should i do, install 64 bit ubuntu?

---

### Post by gandaran on 2011-06-18
> **velt said:**
> 64 bit ubuntu. 
What should i do, install 64 bit ubuntu?
try the [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") addon to remove whatever flash you have installed and install the appropriate flash.

---

### Post by velt on 2011-06-18
> **gandaran said:**
> try the [flash aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") addon to remove whatever flash you have installed and install the appropriate flash.

flashaid seems to be firefox only, im looking for something for chrome. Or for something that checks for conflicting flash versions in ubuntu 64bits.

---

### Post by gandaran on 2011-06-18
> **velt said:**
> flashaid seems to be firefox only, im looking for something for chrome. Or for something that checks for conflicting flash versions in ubuntu 64bits.
chrome 64-bits can automatically pick up the flash installed using the firefox addon, flash will work on all browsers.

---

### Post by lovinglinux on 2011-06-18
> **velt said:**
> flashaid seems to be firefox only, im looking for something for chrome. Or for something that checks for conflicting flash versions in ubuntu 64bits.

> **gandaran said:**
> chrome 64-bits can automatically pick up the flash installed using the firefox addon, flash will work on all browsers.

Although Flash-Aid only works in Firefox, the extension is merely a script generator, that will automate the process of downloading flash, installing it, removing conflicting plugins and applying common tweaks to improve performance. So all you need is to run the Flash-Aid wizard once. After restarting any browser, they will pickup the new flash like gandaran mentioned.

---

### Post by wildmanne39 on 2011-06-18
> **velt said:**
> and something for chrome?
this seems to be a java issue with linux.Hi, let us know if it fixed your problem.

---

### Post by velt on 2011-06-18
> **wildmanne39 said:**
> Hi, let us know if it fixed your problem.

it was a random error, i will give it a go for a couple of days. 
Thanks for the help guys!

---

### Post by wildmanne39 on 2011-06-18
> **velt said:**
> it was a random error, i will give it a go for a couple of days. 
Thanks for the help guys!Hi, ok your welcome I hope it works.

---

### Post by alienmindtrick on 2011-06-20
I'm having Java issues in both Chrome (my preferred browser) and in Firefox, too. I have the latest build of Java 6-26. I'm using Natty 11.04, updated (although I'm getting this error msg:  W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources) 404 Not Found, W:Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-i386/Packages) 404 Not Found, E:Some index files failed to download. They have been ignored or old ones used instead.

One site that fails to work is the crosswords page on Thinks.com. Oddly, older crosswords from, say, the January 2011 archive, work fine, but the current ones do not work. I have attached a screenshot.

Thank you all in advance for your help, and thank you all too, for the wonderful OS. I used Windows for years, Mac for a short while, and then found Ubuntu. Thank you!


21 June update:

I uninstalled Sun Java and installed IcedTea, et al, and I'm still having the same problems on the same websites. <shrug>

---

