---
title: "Firefox, flash not working."
date: 2009-06-25
forum: General Help
---

### Post by StealthMode on 2009-06-25
Hey everyone, I'm new to the board, and pretty new to Linux. I have a Dell Dimension 2100 and was running Debian, and switched to Ubuntu 8.04 Hardy. I'm loving it so far! 

Anyway, I did some searching around the forums yesterday, and was looking at the threads about my issue with flashplayers not working in Firefox. I followed a few steps that were outlined by other members, and I also tried to go my own way in uninstalling adobe flash plugin, and installing it on my own. I have not been able to get flash to work. YouTube videos KINDA work, but others won't. Many times I'll get a window saying I need to download the latest version of Adobe flash, with a link. I've followed the link, saved the package, changed the permissions of it to run as an executable file, and installed it that way. I've tried the command line methods as outlined in other threads. On most flash videos, I'm getting a gray box with a circle and triangle (for "play"). The box floats above other things on the page, and when I click, it usually doesn't load. I also can't get Pandora to work. 

Is there something I have overlooked that would change this? What about installing Ubuntu 9.04?

---

### Post by philcamlin on 2009-06-25
go to the flash website downlod it and restart firefox

voila ! :popcorn:

---

### Post by rushikesh988 on 2009-06-25
why don't you allow firefox to search and download  plugin for himself automatically

---

### Post by StealthMode on 2009-06-25
I tried going to the website and downloading it, but it says that I already have a newer version installed. I've already done this before, and restarted Firefox with the same result. I went into Preferences in Firefox and looked at my add-ons and I have a shockwave flash player, but no Adobe??

---

### Post by lovinglinux on 2009-06-25
The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

> **lovinglinux said:**
> 

**Problems:**

[list][*] 
[*] **Can't play streaming videos**
[*] **Flash videos display only a symbol and won't start**[/list]

**Solution:**

Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content. You can disable plug-ins through the Addons window. Open "Tools >> Addons", then select the "Plug-ins" icon, then select the plug-in you want to disable and click the "Disable" button. Unfortunately, this not work every time, so the best procedure is to remove the conflicting plug-ins.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```

To solve additional video issues, visit the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). It solves most of the problems related to video codecs and plug-ins.

---

### Post by Vicedi on 2009-06-26
The conflickers are gnash and Swfdec. Go to Synaptic Package Manger and see if they are enabled if so then disenable them. It work for Me!

---

