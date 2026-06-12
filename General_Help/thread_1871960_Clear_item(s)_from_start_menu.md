---
title: "Clear item(s) from start menu"
date: 2011-10-29
forum: General Help
---

### Post by altjx on 2011-10-29
I've just failed at installing iTunes in Ubuntu - looked like trash. Now when I press my Windows key and bring up the menu, iTunes is still showing in the list.

What file can I edit to remove items from this list?

---

### Post by altjx on 2011-10-29
Or better yet, is there a way to purge it using a command or something?

---

### Post by LinuxFan999 on 2011-10-29
> **altjx said:**
> I've just failed at installing iTunes in Ubuntu - looked like trash. Now when I press my Windows key and bring up the menu, iTunes is still showing in the list.
 
What file can I edit to remove items from this list?
I am assuming you used Wine to install iTunes. Is this correct?
iTunes generally does not work well under Wine. Most versions are rated Garbage or Bronze. If you are trying to mount an iPod, iPhone or iPad, there are native Linux programs which support them. if you just want a media player program, try VLC or another open source media player.

---

### Post by altjx on 2011-10-29
> **LinuxFan999 said:**
> I am assuming you used Wine to install iTunes. Is this correct?
iTunes generally does not work well under Wine. Most versions are rated Garbage or Bronze. If you are trying to mount an iPod, iPhone or iPad, there are native Linux programs which support them. if you just want a media player program, try VLC or another open source media player.

I would've liked to had it organize my folders for me. I'm using Rhythmbox right now to play songs from my iPhone, but i don't want to drag F01, F02, F03, F04 and all the way up to F50 to my Musics folder though.

How can I remove it from the applications list?

---

### Post by altjx on 2011-10-29
Also, I just uninstalled WINE and PlayOnLinux, and stuff like iTunes, About iTunes, Apple Software Update is still appearing in the start menu! (ubuntu's dash home).... Anyone?? :(

---

### Post by alquery on 2011-10-29
I also find that previous apps that I have uninstalled from within wine are showing up in the dash... where is the list of applications stored? There should be a right click -> remove from dash or something like that...

---

### Post by altjx on 2011-10-29
> **alquery said:**
> I also find that previous apps that I have uninstalled from within wine are showing up in the dash... where is the list of applications stored? There should be a right click -> remove from dash or something like that...

Agreed, that can be very disturbing.

---

### Post by alquery on 2011-11-17
Bump. Is there a way to remove applications? I have about 10 wine applications that I've uninstalled through the wine uninstaller and are still cluttering up the list, and I have to tab through them.

---

### Post by alquery on 2011-11-23
Bump

---

### Post by alquery on 2011-11-24
Finally found the answer: the solution is to look through ~/.local/share/applications/wine for applications that you want to remove. Simply remove their files and the problem should be fixed.

Source: [http://askubuntu.com/questions/75214/how-can-i-remove-un-installed-wine-programs-from-the-unity-dash-menu]("http://askubuntu.com/questions/75214/how-can-i-remove-un-installed-wine-programs-from-the-unity-dash-menu")

---

