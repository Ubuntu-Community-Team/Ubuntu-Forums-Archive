---
title: "Can't install flash in Firefox."
date: 2010-10-23
forum: General Help
---

### Post by VGF on 2010-10-23
I just switched back to Ubuntu a few days ago for the first time in about a year or so.  Running 8.04 (Hardy), because it was the disk I had around.  Don't want to bother upgrading to the newest version just yet, as I have a good deal of homework I want to get done.  

Anyways, I seem to have encountered an issue of not being able to run Flash in Firefox. For example, when I go to a youtube video, it tells me i need to install the plugin.  So i've gone to the Flash website, downloaded the appropriate .deb file, and installed that. No change. 

So I go back to a page that uses Flash, and click on the "Install Missing Plugins" button that appears.  The popup says "Press next to install these plugins", but lists no plugins, and nothing gets installed.  This kind of baffles me.  Any ideas?

Thanks!

---

### Post by Vaphell on 2010-10-23
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

use this plugin, it will do the dirty work for you

---

### Post by gandaran on 2010-10-23
> **VGF said:**
> I just switched back to Ubuntu a few days ago for the first time in about a year or so.  Running 8.04 (Hardy), because it was the disk I had around.  Don't want to bother upgrading to the newest version just yet, as I have a good deal of homework I want to get done.  

Anyways, I seem to have encountered an issue of not being able to run Flash in Firefox. For example, when I go to a youtube video, it tells me i need to install the plugin.  So i've gone to the Flash website, downloaded the appropriate .deb file, and installed that. No change. 

So I go back to a page that uses Flash, and click on the "Install Missing Plugins" button that appears.  The popup says "Press next to install these plugins", but lists no plugins, and nothing gets installed.  This kind of baffles me.  Any ideas?

Thanks!
you must update the package list or you will just install broken flash packages!
```
sudo apt-get update
```
installing the adobe flash plugin
```
sudo apt-get install flashplugin-nonfree
```
check that you dont install gnash or swfdec but just adobe flash

---

