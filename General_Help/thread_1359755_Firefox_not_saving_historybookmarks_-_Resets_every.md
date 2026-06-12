---
title: "Firefox not saving history/bookmarks - Resets every browser start"
date: 2009-12-20
forum: General Help
---

### Post by James78 on 2009-12-20
Now, before I begin, I would like to say that I am a fairly advanced user. I know how things work, and I troubleshoot. Therefore as such, I have deleted my profile, recreated it, tested new ones, deleted .mozilla, purging, reinstalling, checking about:config (and changing values which seem to contradict saving history).

.mozilla has ALL my user permissions. I made sure of this. Now, for some reason I don't even see history.dat; clearing history does NOT regenerate a new one. History is set to be remembered for 90 days, and is NOT set to clear when Firefox closes, I would have already checked something THAT simple!

Main issue: I open Firefox, I browse, and no history is ever saved when I restart the browser. No bookmarks get saved either. For some reason the history and bookmarks "reset". And it's also worth noting that the history resets holds onto one specific history entry from "yesterday", and everytime I restart, anytime, even a week from now, that entry is there as "yesterday" again, and nothing is saved as usual.

What does work. My preferences are saved, addons, configurations, downloads, don't know about form history since I don't use that.

I use Firefox 3.5.6 on the latest KDE with Kubuntu (formally Ubuntu) 9.10. I also use a Firefox-KDE OpenSUSE hack. This addon has never caused any of these problems, whether installed or not.
It is located at ppa:debfx/firefox-kde

Please help me, I've run out of options and ideas. Why in the world is this happening?!

---

### Post by muse3332 on 2009-12-20
:guitar:hmm  ok put this in terminal "firefox settings" then see if you have enough space to even save ur bookmarks and history

---

### Post by James78 on 2009-12-20
"Firefox settings" tries to open a URL to "settings", which is understandable. And I have a total partition size of 55GB, with 42GB free. I should have enough space...

---

### Post by muse3332 on 2009-12-20
ok i see well hm.. i dont understand the problem here buddy sorry but isnt it better to not have history on ur firefox?? i mean be like a ninja leave no trace xD

---

### Post by James78 on 2009-12-20
Except that I can't save a bookmark to this topic, so I have to look for it every single time, and I have to continually search for sites I go to that I can't remember the exact URL, when it could just be in the URL bar when I type up easy search terms (awesome FF3 feature).

Edit: Isn't that what Firefox's Private Browsing is for anyways..?

---

### Post by muse3332 on 2009-12-20
well this only happens when ur using kde ur suposed to use kfox its firefox made for kde.. but ur using buntu..

---

### Post by wojox on 2009-12-20
Close Firefox and delete the file places.sqlite from the profile folder. 

[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Treeh on 2009-12-20
> **muse3332 said:**
> ok i see well hm.. i dont understand the problem here buddy sorry but isnt it better to not have history on ur firefox?? i mean be like a ninja leave no trace xD

If that were the case, why would browsers even have history enabled by default?

---

### Post by James78 on 2009-12-20
Thanks. I'm on a livecd right now because I have to do some partitioning, but I'll get to that real soon. From the sounds of it, it might work.

---

### Post by James78 on 2009-12-20
Deleting that got rid of Firefox resetting to browser history from tons ago, but it still will not save any history or bookmarks. Any more suggestions..?

Nothing works. I checked the mozilla wiki, and deleting it should've worked. There can only be one thing left then. Everytime I use firefox, there's always another firefox zombie open, it must be locking the file somehow. I have no idea how to fix that. Creating new profiles don't even fix the problem.

^^ Scratch that. I don't have the zombie process anymore, and I still have the problem.

---

### Post by lovinglinux on 2009-12-20
> **James78 said:**
> Deleting that got rid of Firefox resetting to browser history from tons ago, but it still will not save any history or bookmarks. Any more suggestions..?

Nothing works. I checked the mozilla wiki, and deleting it should've worked. There can only be one thing left then. Everytime I use firefox, there's always another firefox zombie open, it must be locking the file somehow. I have no idea how to fix that. Creating new profiles don't even fix the problem.

^^ Scratch that. I don't have the zombie process anymore, and I still have the problem.

Close Firefox, kill the zombie,  then delete places.sqlite file. Also check if you have ownership of the profile folder.

---

### Post by durrenmatt on 2009-12-20
watch out when killing the zombie, many of them come back to life!
:lolflag:

---

### Post by lovinglinux on 2009-12-20
> **durrenmatt said:**
> watch out when killing the zombie, many of them come back to life!
:lolflag:

:lolflag: Indeed

---

### Post by James78 on 2009-12-20
> .mozilla has ALL my user permissions. I made sure of this.
I don't see how places.sqlite can be the problem when I can create a new profile and the same problem occurs.

> **durrenmatt said:**
> watch out when killing the zombie, many of them come back to life!
:lolflag:
Lol, nice one.

---

### Post by lovinglinux on 2009-12-20
> **James78 said:**
> I don't see how places.sqlite can be the problem when I can create a new profile and the same problem occurs.

You are right. If a new profile exhibits the same problem, then it can't be that file. Since you also has ownership of FF profile, then I don't know what else it could be. Perhaps you could try to re-install sqlite. The package is libsqlite3-0. Go to Synaptic an mark it for re-installation. If you remove it,  it will also remove lots of dependencies and probably will break stuff, so just re-install it.

---

### Post by James78 on 2009-12-21
Ya, that looks like the last thing to do. And when removing something removes tons of dependencies, I simply just use dpkg to force remove so that I can keep everything else, then a reinstall is just as simple. Thanks for trying anyways. Places.sqlite was a good idea, and in almost all cases should have been the culprit based on what I read. I posted something on getsatisfaction, maybe they can help me more. That is, if reinstalling sqlite doesn't fix it.

Edit: Nope...

---

### Post by James78 on 2010-01-10
No one has any ideas then.. Hmm. Songbird saves history perfectly fine. Just Firefox. This must be a bug or a very specific issue. I have no figured out how this is happening.

---

