---
title: "Accessing Camera in Firefox"
date: 2010-05-21
forum: General Help
---

### Post by RyanfromtheShire on 2010-05-21
I'm using a Lenovo Ideapad s10e on Ubuntu 9.10 Karmic Koala, and when I go to certain sites I cannot access my webcam. When prompted to ask if I "allow" the site access to my camera, it won't let me click allow. Basically, I click the left mouse button and it doesn't respond (and nothing is wrong with my mouse buttons). It lets me right click, but that doesn't help me at all.

Here is an example of what is happening:

[http://img256.imageshack.us/img256/7030/screenshotil.png](http://img256.imageshack.us/img256/7030/screenshotil.png)

Anyways, anyone know why this is happening?

Thanks,
Ryan

---

### Post by ragtag on 2010-05-21
I was having the same trouble after I installed 64bit Lucid Lynx. In fact, I had trouble clicking all kinds of Flash stuff, not only those that accessed the camera. The reason seemed to be that the version of Flash I was using was not 64bit. So if you're running 64bit Karmic, it might be an idea to try and install 64bit Flash too. [Here]("http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/") are some quick instructions for how to I found with a quick search (note, I haven't tested them).

The other option you have, is to change the settings for the sites using Adobe's settings tool, rather than the pop-up on each page. If you got to [this page]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html"). You'll see a small Flash settings dialog box, which lists sites that have tried to access your camera or microphone. You can click on the site you want to change the settings for, and set Flash to always allow that site to access your camera. Next time you go to the site, it won't ask and the camera should just work. If you have problems clicking on the settings tool, follow the instructions in the first paragraph. :)

 Cheers.

---

### Post by RyanfromtheShire on 2010-05-21
Yeah I'm on 32bit, but the link works! Thanks!



If anyone else knows the actual fix, I'd still be interested on how to fix it!

---

