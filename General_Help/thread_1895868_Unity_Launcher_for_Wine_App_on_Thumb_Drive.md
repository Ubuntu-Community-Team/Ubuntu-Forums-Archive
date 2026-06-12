---
title: "Unity Launcher for Wine App on Thumb Drive"
date: 2011-12-15
forum: General Help
---

### Post by Ronco Pizatto on 2011-12-15
I have a couple of portable apps that I run off a thumb drive using Wine. I can right click and use the command "open with wine" to run the apps.

Can I make a Unity type launcher for this? Will I need a symbolic link?

I am running Ubuntu 11.10 with Unity.

---

### Post by jamesisin on 2011-12-15
It's not so hard.  You just need the path to the executable (which might be something like /media/thumbdrive/coolprogram.exe).  Here is the information for a Wine application's launcher (in Gnome).

```
env WINEPREFIX="/home/[username]/.wine" wine C:\\windows\\command\\start.exe /Unix /home/[username]/.wine/dosdevices/c:/users/[username]/Start\ Menu/Programs/Exact\ Audio\ Copy/Exact\ Audio\ Copy.lnk
```

Obviously you'll want to use your username where I have marked it.  It's a little confusing but I think if you play with it it ought to come around for you.

---

### Post by Ronco Pizatto on 2011-12-15
Thanks for pointing me in the right direction. I'll give it a shot.

---

### Post by jamesisin on 2011-12-16
I noticed afterwards that the link I used as an example is a link to a link, so take that into account as you sort out how to create a link to your executable.

---

### Post by Ronco Pizatto on 2011-12-16
Yes. I figured that it might need to be multiple links. Thanks for reminding me.

---

