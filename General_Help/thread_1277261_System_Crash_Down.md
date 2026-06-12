---
title: "System Crash Down"
date: 2009-09-28
forum: General Help
---

### Post by GCkid7 on 2009-09-28
Yesterday I removed cairo-dock (it's bugged) from my system and I ticked for complete removal. 
After re-start all I got was a black screen with text and nothing worked. I don't know why I ticked for complete removal in "synaptick package manager", but I did not except for complete crash down. I did not know how to re-store it.

Is this normal in Ubuntu? should I avoid that particular command?
When should I use that command: "complete removal"?


I am still learning Ubuntu. Thanx to anyone who replies & answers my questions....

---

### Post by ajgreeny on 2009-09-28
I have never used cairo-dock, so can't answer that particular question, but in general there is no problem with using "Completely remove" in synaptic, it just removes the config files for that application, though if they are still needed for something else, they will not be removed.

Did you do anything else in the same session that involved installation of an application, removal of anything or any updating, as it is possible that the problem relates to another applcation, not cairo-dock at all.

Try booting to failsafe gnome from the login window Options button, bottom left on my screen, and see if you can get a gui instead of terminal.  If you still can't get a gui, login at terminal with your username and password as usual (p'word will not show as you type) and then use the command ```
startx
```If nothing still happens try ```
sudo /etc/init.d/gdm start
```Report back any errors you see from these two commands.

---

### Post by GCkid7 on 2009-09-28
That was the only thing I did. There was no updates or donwloads.
Cairo-dock & Avant were running at the same time, that's way I wanted to remove it, coz it was bugged & did not work properly..
What I did, was re-instaltion of the whole OS. 
There was no other way. I did not know what to do.

---

