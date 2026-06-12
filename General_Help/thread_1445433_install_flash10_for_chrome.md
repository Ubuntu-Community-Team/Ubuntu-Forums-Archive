---
title: "install flash10 for chrome"
date: 2010-04-02
forum: General Help
---

### Post by ELD on 2010-04-02
Okay so i downloaded and installed flash10 but i need to get google chrome to pick it up, can anyone point me a way to do it, any guides i have found have different folders to the latest download/install of chrome5.x

I am on 64bit.

Okay i managed to solve it, i needed to sudo into nautilus and copy libflashplayer.so (i wander why search couldn't find it?!) and make a "plugins" folder in /opt/google/chrome and copy it to there. Odd that the folder didn't exist and that no search other than browsing myself in the filesystem could find the flash so file, can anyone shed light on this?

Would be nice if the flash installer in the software centre supported google chrome since it is available for some time now, wander if this is solved in lucid?

---

### Post by kerry_s on 2010-04-02
yeah, sounds like you do it the hard way.

flash installer is in the repo. just open synaptic & type "flash" in the search.
the latest chromium is a ppa away. you'll get the latest features, before google-chrome gets them.
```
sudo add-apt-repository ppa:chromium-daily
```

since there in your update system they get updated like everything else as soon as the new 1 hits the repo.

---

### Post by ELD on 2010-04-02
Like i already said, flash installer does not yet support google chrome. Which is the whole reason i posted.

Adding that command gives me this error btw:
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures were invalid: BADSIG 5A9BF3BB4E5E17B5 Launchpad PPA for chromium-daily


---

### Post by Vadi on 2010-04-27
Strangely enough, this isn't working out for me - I put the so into that folder (created it and all), but Chrome is just refusing to see it.

---

### Post by SnickerSnack on 2010-04-28
> **ELD said:**
> Odd that the folder didn't exist and that no search other than browsing myself in the filesystem could find the flash so file, can anyone shed light on this?

Did you do

```
sudo updatedb
```

after installing?

---

### Post by ELD on 2010-04-30
> **SnickerSnack said:**
> Did you do

```
sudo updatedb
```after installing?

Why would i need to do that? It was a standard install via software centre. I have gone back to firefox anyway so it doesn't really matter to me anymore.

---

### Post by ennui. on 2010-05-01
I am having similar problems getting the flash plugin to work but for chromium. I have the so in the plugins folder. but now with the latest chromium build pages with flash just hang and will not load while before the flash item would just display 'missing plug-in'.

---

### Post by erlend_sh on 2010-05-01
I'm in the same boat. Not gonna push the red button just yet though... I'm gonna wait for that magic update :)

---

