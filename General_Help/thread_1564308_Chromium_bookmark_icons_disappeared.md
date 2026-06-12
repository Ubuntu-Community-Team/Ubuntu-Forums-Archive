---
title: "Chromium bookmark icons disappeared"
date: 2010-08-30
forum: General Help
---

### Post by Optimus_Jazz on 2010-08-30
Like the title says my bookmark icons have disappeared and have been replaced with blank white pages:

[IMG]http://img834.imageshack.us/img834/6719/screenshotqpc.png[/IMG]


Initially I thought they would come back if i did a fresh install and imported the bookmarks, but when I reinstall chromium they are already there, and again without the proper icons.Has anyone an idea as to what may be causing the problem or a solution to fix?

---

### Post by Optimus_Jazz on 2010-08-30
bump

---

### Post by ean5533 on 2010-08-30
What version of chromium are you running? You can find the version number by opening the menu and clicking "About Chromium".

---

### Post by Optimus_Jazz on 2010-08-30
running on version 5.0.375.125 (53311) Ubuntu 10.04

---

### Post by ean5533 on 2010-08-30
If you create a new bookmark does it have a proper favicon and text? If you open the bookmark manager do the items listed under bookmark bar have proper favicons and text?

If only new bookmarks look correct then it's possible that somehow your bookmarks got corrupted (not sure what would cause that). Without a backup I don't know any way to restore them without re-bookmarking things by hand. You might try exporting them and importing into firefox to see if things are any better there.

If all bookmarks look wrong (including new ones) then I'd say it's some sort of bug with chromium. You're running a stable version so I'd be surprised if a bug like that got through their screening. If this bug persists, you might try reporting it at [their bug tracker]("http://code.google.com/p/chromium/issues/list"). They're usually very responsive as long as you include all the necessary info.

---

### Post by Optimus_Jazz on 2010-08-30
All bookmarks whether old or new are missing the icon, and it is the same story in the bookmark manager.I would report it to the bug report but it doesn't seem to be a problem for anyone else.

---

### Post by ean5533 on 2010-08-30
> **Optimus_Jazz said:**
> I would report it to the bug report but it doesn't seem to be a problem for anyone else.

Unless there's 10 other people with the same problem that are all staying quiet because they think it isn't a problem for anyone else. :-)

Honestly, I would report it if I were in your shoes. Just give whatever information you can. The devs will be able to tell you how to find out whatever info they need, and they're always polite (I've reported a couple bugs to them before).

In any case, this almost certainly seems like a chromium-specific bug to me.

---

### Post by Shpongle on 2010-08-30
try add the chromium daily build ppa as its more current than the one in the repos 

sudo apt-add-repository ppa:chromium-daily/ppa

sudo apt-get update && sudo apt-get install

if that doesn't work , uninstall the current one in the repos and try again , best to purge it to remove botched up config files 

sudo apt-get purge chromium

---

### Post by Optimus_Jazz on 2010-08-30
good lookin shpongle and ean thanks for the help i will report the bug if problem persists!

---

### Post by Shpongle on 2010-08-30
any time man :-)

---

### Post by jbeamz on 2012-12-16
I have the same issue. Chrome Version 23.0.1271.97

Going to try purging and reloading.

---

### Post by overdrank on 2012-12-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

