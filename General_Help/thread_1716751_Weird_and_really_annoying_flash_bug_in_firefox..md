---
title: "Weird and really annoying flash bug in firefox."
date: 2011-03-28
forum: General Help
---

### Post by Dustin2128 on 2011-03-28
I'm getting artifacts from flash that's running in other tabs on every page I've got open, often rendering it unreadable/unusable. Anyone else had this problem? Firefox 4 with flash from adobe. 
EDIT: Possibly more disturbing, resetting resolution in nvidia x server settings eliminated an artifact on the desktop- and everywhere else it seems. Driver corruption or hardware troubles you think?

---

### Post by Dustin2128 on 2011-04-02
still unresolved, bump.

---

### Post by Jeffreybolle on 2011-04-06
I have the same problem, unfortunately I have no idea how to resolve it.

- Jeffrey

---

### Post by Jeffreybolle on 2011-04-06
I think that I have found a solution.

Shutdown Firefox.  Download a fresh copy of flash player for 64bit Linux here:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

Extract libflashplayer.so and copy it to:

/usr/lib/mozilla/plugins

I also removed the following bundled flash plugin:

/usr/lib/mozilla/plugins/flashplugin-alternative.so

Then start Firefox.

Let me know if that works for you, it seems to have worked for me.

- Jeffrey

---

### Post by ChrisWells on 2011-04-06
I had artifacts (giant white squares) in every flash video all of a sudden couple weeks ago. I'm on 64 bit Ubuntu and removed all flash and went to the 64 bit flash (sevenmachines ppa) and it's been working fine ever since.  Sorry if I'm not much help I'm no expert, you might not even be on 64 bit

---

### Post by lithopsian on 2011-04-06
flashplugin_alternative is a nightmare.  You're well rid of it.

Many artifacts of this type are due to hardware acceleration and can be difficult to diagnose and fix.  You can try turning off hardware acceleration in the browser and see if it helps.  You can also try changing your video drivers to a different version, or even from proprietary to open source or vice versa.  An up-to-date flash plugin is always helpful.

---

### Post by Dupointx on 2011-04-06
Did you try using the addon "[Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")"?

It is a addon written by LovingLinux (forum member) to resolve issues with Flash on Ubuntu.

---

### Post by Dustin2128 on 2011-07-23
It's been a few months, but I did do a full flash player re-install (dragged libflashplayer.so to the proper place). As for why I don't use flash aid, this bug persists among all linux distributions I use, my main one being arch.

---

### Post by shimoda on 2011-07-24
Same prob here, but since now I used FF3 without problems (It's yet default in Ubuntu LTS).

I installed latest FF5 from PPA and the problem appeared... In chromium all flash works fine...

---

### Post by CaptainMark on 2011-07-24
anyone running 64 bit needs to add the seven machines ppa```
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer
```The flash aid plugin only removes conflicting flash players you may have installed, this code will uninstall the 32bit version anyway

---

### Post by shimoda on 2011-07-24
Thanks CaptainMark...

But, what's the difference with Seven Machines PPA and standard Ubuntu Flash, or downloaded from adobe?

(is only to know what I'm installing :))

---

### Post by CaptainMark on 2011-07-24
the seven machines ppa is the same as the flashplugin thats in the standard repos, its just the 64bit version, i dont know why its not included in the repos yet, it will giev you the same packages you would install directly from adobe website but its easier through apt-get or synaptic as they automatically update where as manual installs wont

---

### Post by gandaran on 2011-07-24
> **shimoda said:**
> Thanks CaptainMark...

But, what's the difference with Seven Machines PPA and standard Ubuntu Flash, or downloaded from adobe?

(is only to know what I'm installing :))
the ubuntu repositories flash packages are 32-bits adobe flash only and can work on 64-bits system using a wrapper, its best to use the 64-bits beta adobe flash on 64-bits systems, ubuntu will include the 64-bits flash in the repositories when adobe releases a stable version.

---

### Post by bakegoodz on 2011-07-24
I had the same problem, but I tried Flash-Aid like Dupointx suggested. Works great now.

---

### Post by shimoda on 2011-07-25
Thanks for your answers... Works perfect!! ;)

---

