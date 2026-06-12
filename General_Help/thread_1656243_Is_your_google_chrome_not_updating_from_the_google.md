---
title: "Is your google chrome not updating from the google repo?"
date: 2010-12-30
forum: General Help
---

### Post by jetpeach on 2010-12-30
I have the following added to my sources

## Google repositories
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main  # has many programs but not all
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

The repo would update fine and google programs are listed, but when I checked my version of Google Chrome is was still version 7.0.517.44, yet google's website says it has updated the stable version for all operating systems to 8.0.552.224.

So I downloaded the DEB file for the stable version of Chrome directly from Google and installed, and now I'm updated to 8.0.552.224. But I have 4 other computers running Ubuntu and the whole point of repos is to not have to update programs this old-fashioned way!

I checked the Beta version in my computers' repos, and it's version 8.0.552.20, which is older than the stable version I just downloaded - question:
Can somebody with Google Chrome installed from the repos check their version and see if the stable version of Chrome is simply out of date by quite a bit?

Thanks!

---

### Post by b0b138 on 2010-12-30
mines 8.0.552.224-r68599

in synaptic, highlight the google-chrome-stable package, then in the menu bar click Package-->Force Version  and check that 7.x.x.x wasn't forced for some reason

---

### Post by wangsuda on 2010-12-30
I believe I am fully updated, and my version of Chrome stable is 8.0.552.224

---

### Post by jetpeach on 2010-12-30
strange indeed. checked and nothing like force version seems to be holding it back, its simply that the newest version in the repos for me is 7.0.517.44 so it just doesn't think it needs updating.

well, i'll just download the version manually from google for now, hopefully it will auto-update in the future.

thanks!

---

### Post by b0b138 on 2010-12-30
Do you have this

[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

---

### Post by jetpeach on 2011-01-03
thanks everyone and bob, i think the problem was that the main google repo wasn't updated but with the repo bob mentioned it is updating now...
cheers,

---

