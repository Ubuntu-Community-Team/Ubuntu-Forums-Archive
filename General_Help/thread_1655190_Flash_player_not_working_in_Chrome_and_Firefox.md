---
title: "Flash player not working in Chrome and Firefox"
date: 2010-12-29
forum: General Help
---

### Post by Ghost_Mazal on 2010-12-29
Lo guys ,

My Flash doesn't want to work. I checked and flash is installed and even when I go to about:plugins in Chrome it shows the flash plugin. But still it don't work. When I go to "create photo album" in Facebook for example I just keep getting the error that flash is not installed.

Can someone help me on how to get flash working please ?

---

### Post by karthick87 on 2010-12-29
Have a look at the following link,

[http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions) 

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by gandaran on 2010-12-29
> **Ghost_Mazal said:**
> Lo guys ,

My Flash doesn't want to work. I checked and flash is installed and even when I go to about:plugins in Chrome it shows the flash plugin. But still it don't work. When I go to "create photo album" in Facebook for example I just keep getting the error that flash is not installed.

Can someone help me on how to get flash working please ?
chrome uses its own built in flash, check if the flash plugin is enabled as usually its disabled when you install chrome.
for firefox install only the 'flashplugin-installer' package from package manager, remove any other flash if installed.
and ensure you don't have any flash blocking addon installed either in firefox or chrome.

---

### Post by Ghost_Mazal on 2010-12-29
> **karthick87 said:**
> Have a look at the following link,

[http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions) 

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

That don't work. Crashes at the very first command

```
mazal@ubuntu64:~$ sudo apt-get purge lightspark
[sudo] password for mazal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lightspark
mazal@ubuntu64:~$
```

> **gandaran said:**
> chrome uses its own built in flash, check if the flash plugin is enabled as usually its disabled when you install chrome.
for firefox install only the 'flashplugin-installer' package from package manager, remove any other flash if installed.
and ensure you don't have any flash blocking addon installed either in firefox or chrome.

I already tried that. Like I said it is installed and enabled in chrome and for firefox that installer is already installed as well.

---

### Post by gandaran on 2010-12-29
do youtube flash videos work?

---

### Post by Ghost_Mazal on 2010-12-29
> **gandaran said:**
> do youtube flash videos work?

Went and tested. Opened 2 youtube videos and both worked.

---

