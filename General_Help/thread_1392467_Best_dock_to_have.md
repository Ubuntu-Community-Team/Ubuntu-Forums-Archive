---
title: "Best dock to have"
date: 2010-01-28
forum: General Help
---

### Post by nikef on 2010-01-28
Hi all i have the awn dock installed , but it is playing up i have double of everything on my bar and when it loads up its slow to position its self , is there any better docks out there ?

---

### Post by timgood on 2010-01-28
There are a variety of docks available - Docky which comes with Gnome Do is in the repositories, as is Cairo Dock. I use AWN without problem and it is very good. Have you tried running "gconftool-2 --recursive-unset /apps/avant-window-navigator" in terminal? This will reset your AWN configuration and may solve your problem.

Hope this helps.

---

### Post by Leppie on 2010-01-28
i'm using wbar, very light and nice dock (osx style). works without compiz and is in the repos ;)
```
sudo apt-get install wbar wbarconf
```

---

### Post by nikef on 2010-01-29
> **timgood said:**
> There are a variety of docks available - Docky which comes with Gnome Do is in the repositories, as is Cairo Dock. I use AWN without problem and it is very good. Have you tried running "gconftool-2 --recursive-unset /apps/avant-window-navigator" in terminal? This will reset your AWN configuration and may solve your problem.

Hope this helps.

Thanks but this did not work , how do i get my dock  back ?

---

### Post by timgood on 2010-01-29
> **nikef said:**
> Thanks but this did not work , how do i get my dock  back ?

I don't understand. Is your dock loading (but still broken) or is it not loading at all? Have you tried purging AWN and then re-installing? Have you tried any of the other docks? Are you getting an error message when running AWN from terminal? Without specific information you are unlikely to get specific help.

---

### Post by JTwigg on 2010-01-29
Hello.
I would recommend cairo-dock. get it here: [https://launchpad.net/cairo-dock](https://launchpad.net/cairo-dock)
I have removed the bottom panel and i put cairo dock at the bottom but autohide.
I then changed where the mouse has to be to make the dock pop up to something like 100 width and 20 height (in pixels) and finally i went into gconfig and made the top panel autohide in the shortest amount of time and to only show 1px of it. it also takes a good second to pop up so its not constantly popping up when you mouse wanders up the top of the screen. 
My system is awesome now.
Hope this helps :)

---

### Post by nikef on 2010-01-29
> **timgood said:**
> I don't understand. Is your dock loading (but still broken) or is it not loading at all? Have you tried purging AWN and then re-installing? Have you tried any of the other docks? Are you getting an error message when running AWN from terminal? Without specific information you are unlikely to get specific help.

Awn loads up , but my dock style has gone , here is what i had before

---

### Post by nikef on 2010-01-29
And here is what i have now

---

### Post by nikef on 2010-01-29
Grrrrr none of the icons will go on to the dock , when i drag an icon to the dock it will not stay on there :(

---

### Post by nikef on 2010-02-02
Bump

---

### Post by Yingy on 2010-02-02
Try going to your dock preferences and go to applets and select the Launcher/Taskmanager.  Highlight and activate.  Hope it helps.

---

### Post by nikef on 2010-02-02
Thanks i have installed awn 4 instead and i nearly have my dock back to normal

---

