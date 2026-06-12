---
title: "does it matter where i put Firefox 3.5 when i install it manually(not via terminal)"
date: 2009-07-10
forum: General Help
---

### Post by eival on 2009-07-10
i havent had much practice with manual installs cause the default installer normally gets the job done, but when installing Firefox 3.5 last night using the .tar file from mozilla.com i expected the files to be placed automatically in one of those folders in Computer>File System , but apparently everything is in the folder that i use as my download folder for Firefox 3.0.

did i do something wrong, or does it not matter where i place it?

will it still update properly?

- Ubuntu 8.04

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi,

I wish someone would tell me what the big rush is for 3.5........

I feel like there is a big secret that I am not privalidged to know :(

My current, supported by canonical, and the auto updates from Ubuntu are quite happy with what I have.

Are there any major security problems with it ? [Don't know]
Is it causing Ubuntu 9.04 to crash ? [Nope]

Does 3.0.11 do & handle all the sites I point it at ? [Yes]
Does 3.0.11 support all the web site safety add-ons ? [Yes]

So, will someone PLEASE tell me why I should abandon the usual upgrade path & download something NEW to replace something that works fine ?!!!!

Regards,

Phill.
P.S. - I am asking, to me, a simple question - not starting a flame war off.




[/FONT][/SIZE]

---

### Post by darco on 2009-07-10
> **eival said:**
> i havent had much practice with manual installs cause the default installer normally gets the job done, but when installing Firefox 3.5 last night using the .tar file from mozilla.com i expected the files to be placed automatically in one of those folders in Computer>File System , but apparently everything is in the folder that i use as my download folder for Firefox 3.0.

did i do something wrong, or does it not matter where i place it?

will it still update properly?

- Ubuntu 8.04

You can still run FF from that folder, just run in a terminal as ./firefox

darco

---

### Post by JohnLau on 2009-07-10
> **phillw said:**
> [SIZE=2][FONT=Arial]Hi,

I wish someone would tell me what the big rush is for 3.5........

I feel like there is a big secret that I am not privalidged to know :(

My current, supported by canonical, and the auto updates from Ubuntu are quite happy with what I have.

Are there any major security problems with it ? [Don't know]
Is it causing Ubuntu 9.04 to crash ? [Nope]

Does 3.0.11 do & handle all the sites I point it at ? [Yes]
Does 3.0.11 support all the web site safety add-ons ? [Yes]

So, will someone PLEASE tell me why I should abandon the usual upgrade path & download something NEW to replace something that works fine ?!!!!

Regards,

Phill.
P.S. - I am asking, to me, a simple question - not starting a flame war off.




[/FONT][/SIZE]
Firefox 3.5 is much faster. I suppose we all like faster broswers :lolflag:

---

### Post by JohnLau on 2009-07-10
> **eival said:**
> i havent had much practice with manual installs cause the default installer normally gets the job done, but when installing Firefox 3.5 last night using the .tar file from mozilla.com i expected the files to be placed automatically in one of those folders in Computer>File System , but apparently everything is in the folder that i use as my download folder for Firefox 3.0.

did i do something wrong, or does it not matter where i place it?

will it still update properly?

- Ubuntu 8.04
I think it won't replace your old firefox 3.0.
Eival, Why don't you use a PPA to install that?
Add this into your software source ([Don't know how?]("http://compustorm.no-ip.org/useful-ubuntu-skills/add-a-software-source/"))
```
deb http://ppa.launchpad.net/fta/ppa/ubuntu hardy main 
```

And install the package
[URL="apt:firefox-3.5"]
firefox-3.5[/URL]

John

---

### Post by rainwalker on 2009-07-10
You can install the package "firefox-3.5" in Synaptic and it will install the final version of Firefox 3.5, but under the name "Shiretoko" (same code, but not gone through the branding process to be included with Ubuntu). It will install alongside the included Firefox 3 in Ubuntu, add a menu entry, and use the profile already created. All of your installed plugins will be detected, too.

---

### Post by t0p on 2009-07-10
> **rainwalker said:**
> You can install the package "firefox-3.5" in Synaptic and it will install the final version of Firefox 3.5, but under the name "Shiretoko" (same code, but not gone through the branding process to be included with Ubuntu). It will install alongside the included Firefox 3 in Ubuntu, add a menu entry, and use the profile already created. All of your installed plugins will be detected, too.

I installed "shiretoko" yesterday by using apt-get

```
sudo apt-get install firefox-3.5
```

and it was clearly labelled as "beta".  This is why I scrapped that install, and instead got the version of firefox-3.5 that you don't install but run from your home directory instead. The one you get from [www.getfirefox.net](www.getfirefox.net) and comes in a bzipped archive **firefox-3.5.tar.bz2**

---

### Post by rainwalker on 2009-07-10
> **t0p said:**
> I installed "shiretoko" yesterday by using apt-get

```
sudo apt-get install firefox-3.5
```

and it was clearly labelled as "beta".  This is why I scrapped that install, and instead got the version of firefox-3.5 that you don't install but run from your home directory instead. The one you get from [www.getfirefox.net](www.getfirefox.net) and comes in a bzipped archive **firefox-3.5.tar.bz2**

Odd...I installed it yesterday as well and it is most definitely not the Beta version. It was updated to the final release a few days ago, I think.

---

### Post by eival on 2009-07-11
thanks for the replies, it works fine, i also figured out how to change the properties of the Firefox Icon in the toolbar to load up 3.5 rather than 3.11:popcorn:

it had all my addons an bookmars passwords loaded up, only TabMixPlus needed to be updated to a new beta version for 3.5

it loads everything very fast, an i havent even fooled around with the about:config settings cause im sure the Delay settings could be lowered even further just like all previous FF versions(works in Opera too)

---

