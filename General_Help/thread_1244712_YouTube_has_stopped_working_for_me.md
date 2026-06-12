---
title: "YouTube has stopped working for me"
date: 2009-08-19
forum: General Help
---

### Post by forgotten_hell on 2009-08-19
I installed flash player and it was working a couple of hours ago. Now when I click the video the page loads, but the video player doesn't load at all. Using Shiretoko (FF3.5). Help?

---

### Post by Post Monkeh on 2009-08-19
```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

type that into a terminal.

---

### Post by speedwell68 on 2009-08-19
> **Post Monkeh said:**
> ```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

type that into a terminal.

Copy and Paste also.

---

### Post by Post Monkeh on 2009-08-19
> **speedwell68 said:**
> Copy and Paste also.

but if he types it, not only will he be fixing his problem, he'll also be exercising his fingers.

---

### Post by forgotten_hell on 2009-08-19
Hmm... Thanks, I tried it but it didn't work... I already had flashplayer installed (if that was part of the code?) and the other stuff I didn't have installed so it didn't do anything... I think... Here's what happened.

```
andrew@ubuntu:~$ sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@ubuntu:~$ 

```

---

### Post by Post Monkeh on 2009-08-19
strange.

i take it you've tried the usual clearing your history/cache?

you could try using synaptic to reinstall the flash player, or remove it altogether and use one of the other ones to see if they work.


don't use two at once, that will cause problems.  check your tools - addons menu to make sure there aren't 2 flash players in there.

---

### Post by pqwoerituytrueiwoq on 2009-08-19
is javascript enabled are you using noscript and no know how to use it?

---

### Post by forgotten_hell on 2009-08-19
Yeah, clearing the history/cache didn't work and I don't believe I have another flash player installed... A bunch of other plug-ins, but only one says flash.

JavaScript is enabled and I am not using NoScript. I have before, on a Windows system, but am not currently.

---

### Post by forgotten_hell on 2009-08-19
Got it to work. Unistalled the transitional flash thing in Synaptic (can't remember which it was, but that was the description). Thanks for the help.

---

