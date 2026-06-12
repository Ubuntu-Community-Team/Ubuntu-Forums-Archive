---
title: "Adobe Flash not working with Firefox and Chrome"
date: 2012-03-31
forum: General Help
---

### Post by Mindrop on 2012-03-31
I am having problems getting Firefox and Chrome to use Flash. Adobe is up to date, but does not work on Chrome or Firefox. I have Silverlight and Gnash installed and have no idea what is going wrong. Adobe's page identifies that I have Flash too. 

Any help?

---

### Post by dragonfly41 on 2012-03-31
You can try this (I found this tip from another thread)

**locate libflashplayer.so**

1. If you have Flash player 11 installed, uninstall it. Otherwise go to step 2.
2. Install flashplugin-installer by executing in terminal sudo apt-get install flashplugin-installer
3. Download [http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml](http://linux.softpedia.com/get/Utilities/Adobe-Flash-Player-for-Linux-18853.shtml)
4. Extract libflashplayer.so and move it to /usr/lib/flashplugin-installer/

---

### Post by kc1di on 2012-03-31
if your using 12.04 or 11.10 then you can go to software center and add ubuntu-restricted-extras and ubuntu-restricted-addons and flash will be configured for you. works great. 

also there is an addon in firefox you can install and it will configure the flash-plugin for you also. it's called flash aid 2.2.3.

---

### Post by Lothsahn on 2012-05-02
I attempted to install flashaid, but it didn't fix the problem.  Flashaid just attempted to reinstall the same broken 11.2.202.233 version of the plugin.

I finally resolved the problem by manually installing the adobe-flashplugin_11.1.102.62-0lucid1_i386.deb package.

---

