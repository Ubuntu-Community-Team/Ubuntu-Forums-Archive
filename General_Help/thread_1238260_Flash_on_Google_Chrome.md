---
title: "Flash on Google Chrome"
date: 2009-08-12
forum: General Help
---

### Post by michael.yahav on 2009-08-12
I've just installed Google Chrome, it works fine.
The only problem is Flash, in some sites on the web they refer to a directory called "chromium-browser" I can't fint it in usr/lib.
How can I install flash ?
Here is a link where I saw it:

[http://linuxologist.com/apps/howto-chromium-browser-on-linux-with-flash/](http://linuxologist.com/apps/howto-chromium-browser-on-linux-with-flash/)

---

### Post by exsapientiasalus on 2009-08-12
If you have flash installed for Firefox (sudo apt-get install adobe-flashplugin), then run Chromium (not Google Chrome -- they are not the same) with chromium-browser -enable-plugins from the command line or set up a shortcut to launch it. This is what I did:

From the command line:

1. sudo nano /usr/bin/chrome.sh

2. within the editor, placed this:

#! /bin/sh
chromium-browser -enable-plugins

3. saved and confirmed with control x and yes.

4. sudo chmod +x /usr/bin/chrome.sh

5. Now you can launch via alt-f2 or by adding a new item to the menu.

---

### Post by Greenwidth on 2009-08-12
.

---

