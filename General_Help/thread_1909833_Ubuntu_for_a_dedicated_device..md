---
title: "Ubuntu for a dedicated device."
date: 2012-01-16
forum: General Help
---

### Post by sagar_322 on 2012-01-16
Hi all, I want to use Ubuntu for a dedicated device. I just want open Firefox on start up in a full screen mode. I don't want to load gnome I mean to say no tool bar, no desktop nothing just want to show up Firefox.
Any help would be appreciated. Thanks in advance.

---

### Post by mikewhatever on 2012-01-16
What you are looking for is called a "kiosk mode". If you must have Ubuntu, search for "ubuntu kiosk", but setting it up may be somewhat non-trivial. If that's the case, try a ready made kiosk OS, for example: [http://www.h-online.com/open/news/item/Webconverger-11-browser-only-OS-adds-Firefox-9-1413090.html](http://www.h-online.com/open/news/item/Webconverger-11-browser-only-OS-adds-Firefox-9-1413090.html)

---

### Post by ajgreeny on 2012-01-16
It could be easier to install ubuntu using the minimum-install CD from [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and then adding only what you need.

There is quite a lot of info available for that install method and when you install it there are guides about what to do during the installation with the tasksel option.

Also have a sift through the search results at [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal+CD&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal+CD&as_qdr=all&sa=Google+Search&lang=en) which may lead you in the right direction.

---

### Post by sagar_322 on 2012-01-17
Thanks for the reply.. But is there is method where I can customize ubuntu instead of again installing mini-install or use any ready made web kiosk. I mean to say any changes in the xinitrc file where I can make only firefox to load and remove unwanted gnome desktop things..

---

### Post by mastablasta on 2012-01-17
i guess you would need to uninstall all the things you don't need.
 
i don't see why you would want to complicate things instead of simply using a ready solution that installs in couple of minutes. way faster than you would need to remove/reprogramme/test etc...

---

### Post by dlinuxh on 2012-04-06
I am also new to kiosks. Done some reading , research on web, and downloaded few distros to test. So far what i did was to install mini ISO with few commands i was able to start it to firefox. But need to edit prefs.js file for mozilla.
Try this , [http://ksenryo.blogspot.com/2012/02/debian-opera-kiosk-mode.html#comment-form](http://ksenryo.blogspot.com/2012/02/debian-opera-kiosk-mode.html#comment-form)

I got a question, mini iso requires to be connected to internet, wired in. 
Is there a way to install mini iso with wireless LAN settings. 
In other words, when i boot from mini iso, can i edit or add settings that it could turn on the adapter, scan for SSID, and connect to internet and then continue boot up?
Anyone knows?
Thanks, 
dlinuxh

---

