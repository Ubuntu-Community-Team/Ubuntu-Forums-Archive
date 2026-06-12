---
title: "Epiphany problems"
date: 2009-11-06
forum: General Help
---

### Post by jon.reeve on 2009-11-06
Does anyone know anything about the following problems I've been having with epiphany? It's such a fast browser, and I really want to use it, but there are all of these annoying bugs. 

* Favicons? Two thirds of them are missing. 
* Third-party extensions don't work, though they appear in tools->Extensions. The package epiphany-extensions-more doesn't work with the current epiphany extensions package. 
* There doesn't appear to be a way to have new browser windows open in new tabs, meaning that popups and other annoying windows litter the window list with garbage
* Spell check doesn't work

---

### Post by claracc on 2009-11-07
Hallo, i have epiphany webkit browser 2.28.0 installed in karmic koala. I installed from synaptic the package epiphany extensions 2.28.0-1.

It works for me, there you can select the way the lids (pestañas in spanish) behave when browsing. Now there is not an extension for favicons in this package, but browser takes into account automatically, they appear in the address bar.

The only problem, i cannot see applets with epiphany, i suppose it is a problem with java but i am not sure and other problem is when you click on edit --> actions the browser crashes.

I hope it helps

---

### Post by Jr.Muffin on 2009-11-07
If you like Epiphany, you might like Midori as well. You can install it from the Software Center.

---

### Post by nortexoid on 2009-11-22
I'm having the same problem regarding spell check, even after fiddling with the Language setting. Technically I don't see anything in the feature list that says 2.29.x is to even have inline spell check so this may just be an assumed feature that doesn't exist. I'd like to know.

(I'm using 2.29.1.)

---

### Post by claracc on 2009-11-23
After using epiphany 2.28.0 with epiphany extensions 2.28.0.1 for two weeks I have encountered the following problems:

* There is not extension for flavicons, previous to epiphany webkit, i had using epiphany gecko and i has flavicons, when i upgraded to karmic, epiphany webkit was installed, when i deleted the cache i lost the flavicons.

* I cannot see java applets with epiphany unless i have installed sun java 6 and it works for java applets in firefox 3.5. It seems epiphany is not aware of java plugin .

*When i write about: config or about:plugins in epiphany addres bar, nothing happens.

* When i click on help, index or help, extensions, nothing happens. There is not any help.

*Also, as i said in previous post, when i click on edit, actions, epiphany crashes.

* Trying to install epiphany-extensions-more 2.26, which is in the karmic repositories, doesn't wok, since there are dependencies not satisfied.

* Not spell-checking extension too.

* I have added the ppa repositories for epiphany 2.29 : [https://launchpad.net/~webkit-team/+archive/epiphany](https://launchpad.net/~webkit-team/+archive/epiphany), but when i try to install from synaptic, it says there are not satisfied dependencies witk epiphany-extensions, and i cannot install.

Neither i have found any workaround for fixing these problems, i hope they can be fixed soon because i liked a lot epiphany (lightweight, simple, easy, quick..).

Regards

---

### Post by fragos on 2009-11-23
Some differences are because of the change to webkit -- about:config for example. I've also noticed that open in tab is no longer in the drop down from links. Apparently clicking the scroll wheel will open in tab.

---

### Post by jan-12 on 2009-11-25
Actually, I would like to continue to use epiphany but it's so flaky in karmic (epiphany 2.28) compared to jaunty version (2.26.1) which was very stable.  Am wondering if you experiece a crash when you clear the cache. It happens everytime I clear cache-just dies.  Any suggestions appreciated.

---

### Post by claracc on 2009-11-25
No, my epiphany webkit doesn't crash when i delete cache but it crashes when i click on actions or on inspect element in ads in web pages with web inspector enabled in preferences. 

I at least got epiphany 2.29.1 installed from synaptic, i had to add the following repositories to the sources list:

[http://ppa.launchpad.net/webkit-team/epiphany/ubuntu](http://ppa.launchpad.net/webkit-team/epiphany/ubuntu) karmic
[http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) karmic

Some problems are fixed: clicking right click you can open link in a new tab, more responsive browser, but crashes on actions or inspect element continues, also no java applets

I think you can avoid the crash deleting the cache doing the following:

Rename the epiphany folder in /home/user_name/.gnome2/ to epiphany_back for example. Close epiphany and run it again and try to delete cache to see if it crashes. You have your bookmarks in the epiphany_back folder.

I hope it can help.

---

