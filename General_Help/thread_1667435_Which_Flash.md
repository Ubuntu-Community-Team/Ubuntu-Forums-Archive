---
title: "Which Flash"
date: 2011-01-14
forum: General Help
---

### Post by kipperman on 2011-01-14
Hi 
I have just installed 10.10 on a Sony Vaio Laptop and am very pleased with it.

Using firefox I can not see which FLASH version I should be using, there seemed to be a number of choices.

It recognises that it is a linux system but there is a drop down with about 8 types of flash and no help on which one to use.


Any ideas please?

david

---

### Post by efflandt on 2011-01-14
Use Synaptic to install **ubuntu-restricted-extras**, which includes **flashplugin-installer**, a java substitute, and various audio/video codecs.

Or if you have 64-bit, you could uninstall flashplugin-installer (which is 32-bit flash with wrapper) after installing ubuntu-restricted-extras, and then install real 64-bit flash from [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

Just extract it from that file and **mv libflashplayer.so /usr/lib/mozilla/plugins/**

---

### Post by kipperman on 2011-01-15
Thanks, got this sorted now.

---

### Post by ericrichards420 on 2011-01-15
[INDENT]sudo add-apt-repository ppa:sevenmachines/flash
 sudo apt-get update
 sudo apt-get install flashplugin64-nonfree 
[/INDENT]

---

