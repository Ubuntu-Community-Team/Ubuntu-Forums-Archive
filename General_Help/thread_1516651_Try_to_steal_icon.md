---
title: "Try to steal icon"
date: 2010-06-24
forum: General Help
---

### Post by elliotn on 2010-06-24
Ok here is my littlle problem, whenever I turn on my Pc after ubuntu is done loading everything, a message appears on the left top corner and it reads
TRYING TO STEAL ICONS
And the network Icon moves from the right notification area to the left under the menu

---

### Post by elliotn on 2010-06-24
Bump help

---

### Post by yeleek on 2010-06-24
Curious.

You using standard menu?  or additional menus/docks?

---

### Post by elliotn on 2010-06-24
I am using the default

---

### Post by yeleek on 2010-06-24
Only reference I can find is this.
[http://logs.ubuntu-eu.org/free/2009/09/29/%23ubuntu-uk.html](http://logs.ubuntu-eu.org/free/2009/09/29/%23ubuntu-uk.html)

And the person there, did have an additional dock installed.  So you sure no new menu applications, cario docks, or other docks installed?

---

### Post by elliotn on 2010-06-24
> **yeleek said:**
> Only reference I can find is this.
[http://logs.ubuntu-eu.org/free/2009/09/29/%23ubuntu-uk.html](http://logs.ubuntu-eu.org/free/2009/09/29/%23ubuntu-uk.html)

And the person there, did have an additional dock installed.  So you sure no new menu applications, cario docks, or other docks installed?

Couldnt figure anything out

---

### Post by _Mark_ on 2010-06-24
A screenshot may help

---

### Post by yeleek on 2010-06-24
> **elliotn said:**
> Couldnt figure anything out

quoted from the link i provided...

<sxx> it was a wba dock because one of the dock i tried in the install manger kept crashing and making weird images on the screen.. in that screen shot top left under the green icon (startbar) there is the firestarter icon and afew icons appear there at boot up with a text saying trying to steal icons??? i have tried to find answer and to move that icon and even the networking icon has moved to there????.

<Ng> sxx: in that it's probably trying to steal the notification icons for itself, but the gnome panel has them

---

### Post by fabounet on 2010-06-24
you can only have 1 notification area at once.
so remove the other one.

---

### Post by elliotn on 2010-06-24
The only dock I have is Cairo-dock and I see no option for notification.

Nor have another notification area

---

### Post by AlexFox on 2010-06-24
You could try the following:

```
rm -r ~/.gconf/apps/panel
```

Log out and log in again.

This will **reset** the Gnome panels to the default, any customisations will be lost.

---

### Post by elliotn on 2010-06-24
K will try that

---

### Post by elliotn on 2010-06-25
> **AlexFox said:**
> You could try the following:

```
rm -r ~/.gconf/apps/panel
```

Log out and log in again.

This will **reset** the Gnome panels to the default, any customisations will be lost.

That command only bring thing to default but couldnt fix the problem

---

### Post by elliotn on 2010-06-25
As mentioned, the problem was cairo dock DBUS plugin that was trying to steal system tray icons, I just disabled dbus and logged off and on. All worked now.

---

