---
title: "No launch for Firefox"
date: 2011-06-12
forum: General Help
---

### Post by OpenSage on 2011-06-12
I am using Ubuntu 10.10 w/Firefox 3.6.?? and was trying to install Firebug 1.7.2  Today I was doing some html/css work and thought I would give the Firefox addon called firebug a try.  I went to the addon webpage to add that extension.  After doing so Firefox said it needed to restart like it does most of the time when adding new addons.  I clicked restart and it never did restart.  I then tried to launch it on my own and it would start to load and then quit before any window opened.  I did not do the addon from the Ubuntu Software Center, so I tried installing from there instead, but that didn't work either.  I then removed Firebug using the Software Center and that did not work.  I then looked in home/opensage/.mozilla/extensions and moved anything related to Firebug to the trash.  That didn't work, so I tried removing and reinstalling Firefox using the Software Center and that didn't work.  Then I went to home/opensage/.mozilla and moved anything related to Firefox to the trash and then reinstalled Firefox again.  As for right now if I install Firefox using the Software Center then I have a launcher icon in my panel and when clicked it starts to launch, but never completes, it just stops and closes.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
i attached the launcher (desktop file)
it should be in theses 2 folders
[FONT=Courier New]/usr/share/app-install/desktop/
/usr/share/applications/[/FONT]
firebug is a great addon i use it a lot
odds are your profile got damaged or a addon conflict
you can make a new one by running [FONT=Courier New]firefox -P[/FONT] from a terminal window 
you can open firefox with addons disabled with is command
[FONT=Courier New]firefox -safe-mode[/FONT]
to completely reset Firefox 
[FONT=Courier New]rm -rf ~/.mozilla/firefox[/FONT]
also you can update to Firefox 4 with this command
[FONT=Courier New]sudo add-apt-repository ppa:mozillateam/firefox-stable; sudo apt-get update && sudo apt-get upgrade
[/FONT]

---

### Post by OpenSage on 2011-06-12
Thanks, but I tried all you suggested and still not working. Before I created the new profile I had even put the old one back from when I moved it to the trash earlier, but nothing worked.  It looks like it was trying to launch in safe mode, but I could not read the whole title as it was loading and then it just stops the same as when not in safe mode.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
if a new profile and safemode and even scraping the profile folder did not fix it i would suggest reinstalling firefox
open synaptic search for firefox and mark it for installation then apply it
also try installing firefox-gnome-support, xul-ext-ubufox, and firefox-branding

---

