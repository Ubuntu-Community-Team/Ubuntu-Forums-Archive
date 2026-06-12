---
title: "Partial Distribution Upgrade leads to Broken Terminal"
date: 2012-09-27
forum: General Help
---

### Post by BlinkinCat on 2012-09-27
Hi all,

This morning, Update Manager indicated that I needed to do a Partial Distribution Upgrade. I went along with it and as a result there were many changes with about a dozen packages being removed as well.
The end result is that I am no longer logged into Gnome Shell. There are now two panels, the one at the top showing Applications and Places with a bottom panel showing Workspaces. The Update Manager now shows system as being up to date.

Is there any way I can get back to Gnome Shell from here?

Thank you - :p

---

### Post by BlinkinCat on 2012-09-27
Sorry for the delay but I have been chasing up other problems.

I eventually worked out that I was connected to "Gnome Classic". "Gnome" is not an option in logon screen.

However I can log on to Unity - Present problems -

1. Terminal not working - see Screenshot.

2. Software Center displaying distorted graphics.

3, Still no Gnome Shell.

As it stands at the moment I am unable to add any input inside terminal as the writing appears on top of box and will not accept any input. I attempted to reinstall terminal via Synaptic but received error Fix broken packages first. I am at a loss as to what to do.

Any input will be appreciated. Thank you - :p

---

### Post by OrangeCrate on 2012-09-27
**I'm offered a partial upgrade, what should I do?**

> During the past few Ubuntu development cycles, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager, which hinted to a poor understanding of package management and the way updates happen in the development branch.

In an effort to help with this situation, this document aims to clarify what a Partial Upgrade is, and why, in most cases, you'll want to avoid it.

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

Edit:

Another recent thread on the same topic:

[http://ubuntuforums.org/showthread.php?t=2063234](http://ubuntuforums.org/showthread.php?t=2063234)

---

### Post by BlinkinCat on 2012-09-27
Thanks OrangeCrate - That is indeed a lesson learned.

I will bookmark and take note for the future.

Therefore then can I assume a complete re-install is the only solution?

Another question -

/home appears undamaged - ? O.K. to reinstall?
  
Thank you.

---

### Post by OrangeCrate on 2012-09-27
> **BlinkinCat said:**
> Thanks OrangeCrate - That is indeed a lesson learned.

I will bookmark and take note for the future.

Therefore then can I assume a complete re-install is the only solution?

Another question -

/home appears undamaged - ? **O.K. to reinstall?**
  
Thank you.

Sure. One of the nice things about Linux is that it's free, making reinstallation an easy fix when something gets borked. Years ago, I learned the same lesson by taking a partial upgrade. Now, when I see one, I make it a point to sit on my hands until the urge to do it again goes away.

---

### Post by BlinkinCat on 2012-09-27
Hi OrangeCrate if you're still aound,

I just did a reinstall assuming /home was not damaged but found errors with the terminal persist. It seems I may have to start again using my backup media which is a little crude consisting of regular backups to several flashdrives weekly.

Unless anybody can suggest any solution to terminal problem in the next half hour I will go down that path.

Thanks for your input OrangeCrate - :p

Edit - In the throes of performing a reinstall with backup media now.

---

### Post by OrangeCrate on 2012-09-27
> **BlinkinCat said:**
> Hi OrangeCrate if you're still aound,

I just did a reinstall assuming /home was not damaged but found errors with the terminal persist. It seems I may have to start again using my backup media which is a little crude consisting of **regular backups to several flashdrives weekly**.

Unless anybody can suggest any solution to terminal problem in the next half hour I will go down that path.

Thanks for your input OrangeCrate - :p

Edit - In the throes of performing a **reinstall with backup media** now.

You're doing exactly what I would do.

I put all of my documents in the home folder into "master" folders, that I then drag to a stick for backup. I have a couple of hundred docs or more, that are in approximately ten master/category folders.

If you are at all confused with what to backup, forget about all of your settings, since you're looking for a fresh install, and only backup files that do not have a "." in front of them (ie: your own personal files). When you're done with the reinstall, simply drag and drop your files/folders back into the home folder. Quick and easy. Then lock up the stick in a safe place.

---

