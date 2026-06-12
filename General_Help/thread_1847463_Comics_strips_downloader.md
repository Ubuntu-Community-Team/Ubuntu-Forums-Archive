---
title: "Comics strips downloader?"
date: 2011-09-20
forum: General Help
---

### Post by nll on 2011-09-20
Hey!

I've been searching for a gnome application which is able to download and view comics strips (just some classics like Calvin and Hobbes, Garfield, Peanuts) but I had no success. It looks like KDE has a widget like that, but I am a happy Unity user. I found out about  Buoh Comic Reader, but it looks that it's completely dead now.

Does anyone know of such an app?

---

### Post by nll on 2011-10-04
Well, I found out that in Natty we can install Comic Strips 0.3 (from [http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Comic-Strips-41327.shtml](http://linux.softpedia.com/get/Desktop-Environment/Screenlets/Comic-Strips-41327.shtml)), which works with the package Screenlets, available from the Ubuntu repositories.

In CompizConfig Settings Manager, I enabled the plugins Regex Matching and Widget Layer and, in the latter, I added name=Screenlet.py in the Widget Windows box under the Behavior tab. This allowed me to show/hide the Comics with the F9 key. (I got this tip from Ubuntu Geek.) To show the Comics in whatever workspace I'm in, I added widget=1 to the Sticky box in the Window Rules plugin for Compiz.

I also found some related stuff for Firefox: the Daily Dilbert add-on ([https://addons.mozilla.org/en-US/firefox/addon/daily-dilbert/](https://addons.mozilla.org/en-US/firefox/addon/daily-dilbert/)), the Comics.com search ([https://addons.mozilla.org/en-US/firefox/addon/comicscom-search/](https://addons.mozilla.org/en-US/firefox/addon/comicscom-search/)), the Comic Aggregator Notifier ([https://addons.mozilla.org/en-US/firefox/addon/comic-aggregator-notifier/](https://addons.mozilla.org/en-US/firefox/addon/comic-aggregator-notifier/)), and Hilarious Webcomic Manager ([https://addons.mozilla.org/en-US/firefox/addon/hilarious-webcomic-manager/](https://addons.mozilla.org/en-US/firefox/addon/hilarious-webcomic-manager/)).

Now I'm trying to figure out how to config the Comic Strips screenlet.

---

### Post by Manyette on 2011-10-04
Might load "Daily Dilbert" in Firefox if you use it.  It has those you mentioned.

---

