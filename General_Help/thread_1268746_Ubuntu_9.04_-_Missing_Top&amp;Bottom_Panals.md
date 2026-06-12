---
title: "Ubuntu 9.04 - Missing Top&amp;Bottom Panals"
date: 2009-09-17
forum: General Help
---

### Post by dopey_tracy on 2009-09-17
I uninstalled Evolution today and now find that when i log on, i no longer have the top and bottom panals on my desktop.
I had Jaunty set up to run a log in screen and then upon authentification, the desktop would load up.
The Recycle bin is missing too?
 
So i have to use the terminal command via Ctrl-ALt F2
 
I tried gconftool --recursive-unset/apps/panal
pkill gnome-panal
 
No luck *-(
 
I even tried reinstalling Evolution but that didnt bring back the missing panals and icons?
 
I dont want to re-install - anyone help please?
 
(I am up-to-date with latest versions)
 
thanks:confused:

---

### Post by sedawk on 2009-09-17
From what you have written I guess you tested that gnome-panel is
running and restarting it doesn't solve the problem?

What you can always do (without reinstalling) is to
create a new user and this new user should have a fully
working desktop. Then (after doing a backup of your
home folder) you can compare gnome configuration files
and try to overwrite files that look changed (and broken)
in your home folder.
I'm not sure which directories to start with  - there
are so many ... ( ~/.gconf ~/.gconfd ~/.gnome ~/.gnome2)

(I lost the "Places" and "System" entries on the top bar and
 the best workaround I have is that they are now located
 in the Main Menu but I still don't know how to get them
 back on the top panel ... May be I should try the above
 solution myself ...)

---

### Post by jerrrys on 2009-09-17
[http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)

---

### Post by dopey_tracy on 2009-09-17
> **jerrrys said:**
> [http://ubuntuforums.org/showthread.php?t=1158042](http://ubuntuforums.org/showthread.php?t=1158042)


Thanks but it didnt really help me...

It would appear that as a result of removing Evolution, these problems have been caused.

Really need a fix..... 

**Update**

One user recommended adding another user and that would give me the panals back - well this didnt work, all i got here when i added another user was a blank desktop...doah!!

Tracy

---

### Post by jerrrys on 2009-09-17
i use backup and thats the only thing that saved me from a fresh reinstall.  if you are like me and like playing with your OS, you will find that there are many ways to break it.  you really need a backup plan...

---

### Post by fooman on 2009-09-17
> **dopey_tracy said:**
> I uninstalled Evolution today and now find that when i log on, i no longer have the top and bottom panals on my desktop.
I had Jaunty set up to run a log in screen and then upon authentification, the desktop would load up.
The Recycle bin is missing too?
 
So i have to use the terminal command via Ctrl-ALt F2
 
I tried gconftool --recursive-unset/apps/panal
pkill gnome-panal
 
No luck *-(
 
I even tried reinstalling Evolution but that didnt bring back the missing panals and icons?
 
I dont want to re-install - anyone help please?
 
(I am up-to-date with latest versions)
 
thanks:confused:

i am not sure if you just misspelled it here,  or if it will even help,  but in the commands you posted...it should be "panel", not "panal":

```
gconftool --recursive-unset/apps/panel
``````
pkill gnome-panel
```another thing you could try is pressing the alt - f2 keys and see if that brings up a run dialog box...if it does,  type this into it and then click "run":

```
gnome-panel &
```see if that helps.

---

### Post by dopey_tracy on 2009-09-17
[quote=fooman;7965190]i am not sure if you just misspelled it here,  or if it will even help,  but in the commands you posted...it should be "panel", not "panal":

Wow!! Seems my spelling was at fault...doah!!!!

After tearing my hair out all evening, I now have it restored...

I tried suso apt -get install gnome-panel and it was restored after a reboot...

Thanks again Fooman:P

xx

---

