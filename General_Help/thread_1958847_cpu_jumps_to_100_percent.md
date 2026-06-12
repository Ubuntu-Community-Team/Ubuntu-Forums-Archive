---
title: "cpu jumps to 100 percent"
date: 2012-04-15
forum: General Help
---

### Post by artfull dodger on 2012-04-15
hp p4 2.8ghz ht 
2.5 gigs of ram
ubuntu 10.04 

running only Firefox and cpu will jump from 7-8 percent to a drastic  100 % 

any ideas ?

---

### Post by 23dornot23d on 2012-04-15
When does it do it ..... running system monitor as Firefox starts up - you will see 100 %

But as everything loads in - then after this it will or should drop ....

are you saying it stays at 100 % constantly after that .....

Check which processes are running and do a screen shot ..... if its continuously 100 %
after everything is loaded in .....

HTOP may help too to check things ..... but System Monitor may be ok ....

---

### Post by ladasky on 2012-04-15
If I had to guess, I would say that you visited a web site which had Flash content, probably several of them.  You probably also have multiple tabs open.

I've run into this problem using both Firefox and Chromium.  If you open several tabs, you end up with lots of Flash running.  For reasons that aren't clear to me, Flash uses significant amounts of CPU power even when it ISN'T showing you a video.  

One good thing about Chromium is that it runs every process in a separate thread, and has its own task manager.  You can go into Chromium's task manager, select just Flash, and kill it.  You'll get a little sad face where there were videos running, but at least you won't crash your browser or, worse, your computer.

And if you want to reload a page with Flash content, Flash will start up again without the overhead.  At least, for a few minutes!  :confused:

---

### Post by artfull dodger on 2012-04-15
good point the flash video slipped my mind it is extreme how much cpu power that takes up. To some up closed firefox cpu dropped to around 2 % just have to be more mindful lol
thanks guys

---

### Post by lovinglinux on 2012-04-15
> **ladasky said:**
> One good thing about Chromium is that it runs every process in a separate thread, and has its own task manager.  You can go into Chromium's task manager, select just Flash, and kill it.  You'll get a little sad face where there were videos running, but at least you won't crash your browser or, worse, your computer.

Although Chromium/Chrome has separate process for tabs, Firefox and Opera also have separate process for plugins. So all you need is to open Systen Monitor and kill *plugin-container* and *operapluginwrapper-native* respectively.

Additionally, is a good practice to block plugins and only click-to-play the elements you need. You can do that with [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) in Firefox. Firefox 14 have this option built-in, which can be [enable through advanced configuration](http://arstechnica.com/open-source/news/2012/04/mozilla-may-make-flash-click-to-play-by-default-in-future-firefox.ars?utm_source=rss&utm_medium=rss&utm_campaign=rss). Opera has this feature built-in as well. Open "Preferences >>> Advanced >> Content" and tick the option "Enable plugins only on demand".

Another feature available in Firefox is the option to load tabs on demand. If you use that feature, then tabs won't be loaded when you start Firefox until you click them. To activate that, type *about:config* in the address bar, then search for **browser.sessionstore.restore_on_demand**, then double-click it to make it **true**. Firefox 12 also has an option to load pinned tabs on demand. The preference responsible for that is browser.sessionstore.restore_pinned_tabs_on_demand

---

### Post by 23dornot23d on 2012-04-16
I wonder if 

kill [I]plugin-container 

Should be made a option on the Firefox menu .... as I too have killed this many times
using HTOP .... once it grabs hold of a lot of the resources ....
[/I]

---

### Post by isa.dsouza on 2013-02-21
killing plugin-container does not work, any other options?

---

