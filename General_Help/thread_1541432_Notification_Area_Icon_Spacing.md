---
title: "Notification Area Icon Spacing"
date: 2010-07-29
forum: General Help
---

### Post by Vapourstreak on 2010-07-29
I noticed that the Notification Area icon's icons were closer together than the applet that shows rhythmbox, indicator-applet, and sound.  Is there any way to change the spacing so they're both the same?

---

### Post by Vapourstreak on 2010-07-29
Bump?

---

### Post by Vapourstreak on 2010-07-29
Anybody?

---

### Post by hansdown on 2010-07-29
Hi Vapourstreak.

Could you please post a screenshot?

---

### Post by felix-leg on 2010-07-29
Right Mouse Button on NA -> Move, and move your mouse until the NA will be placed where there is more space and click ;). Probably you would have also to move other things on these bars to make this "more space".

---

### Post by Vapourstreak on 2010-07-29
> **hansdown said:**
> Hi Vapourstreak.

Could you please post a screenshot?

I'm talking about the clear region in the screenshot:

---

### Post by Vapourstreak on 2010-07-29
Anyone?

---

### Post by everytimeref on 2010-07-29
I've noticed this and it bothers me too,

there are a couple of applets: the indicator applet and the notification applet (I think, from memory) that each display a number of icons, and, as stated the spacing is different on each. Moving them moves the entire applet ( a number of icons ) at the same time and so doesn't solve the issue.

---

### Post by philinux on 2010-07-29
I doubt it's possible. Most likely hard coded.

Best advice is to raise a bug.

```
ubuntu-bug indicator-applet
```

---

### Post by Zookalicious on 2011-02-12
Hi Vapourstreak, I know this is old but I found a solution to your (/my) problem. This is taken and translated from the Russian website [http://habrahabr.ru/blogs/ubuntu/93083/](http://habrahabr.ru/blogs/ubuntu/93083/)

It involves rebuilding the panel from source, but it seems like fairly simple instructions. Unfortunately I can't test it just yet since I'm in an area with limited connection, but I'll update this post once I have tried it. 


> To get this effect, we must do the following: 

1. Enable the source code repository. Ubuntu Software Center > Edit > Software Sources > and check Source Code.

2. In the console go to the appropriate directory (cd /usr/src) and type the command: 

sudo  apt-get update & & sudo apt-get build-dep gnome-panel &  & sudo apt-get source gnome-panel & & cd gnome-panel-2.30.2   

(Note: version might not be gnome-panel-2.30.2 by now. Just look for the folder with gnome-panel-2.30.[version number] and cd into that. Let me know if that requires clarification.) 


3. Now we need to fix the source code. Type: 

gksu gedit applets/notification_area/na-tray.c 


4. On line 35 we see (It might not be line 35 in current version, but just look for this phrase)

# Define ICON_SPACING 1 

Replace 1 with the desired number. I'm using 10. 

5. Built and install the package with the following command. 

sudo dpkg-buildpackage 



Now you can re-login to the system, or remove the applet and re-add it. This will update the changes.

Hope this helps!

---

### Post by shmup on 2011-04-01
> **Zookalicious said:**
> Hi Vapourstreak, I know this is old but I found a solution to your (/my) problem. This is taken and translated from the Russian website [http://habrahabr.ru/blogs/ubuntu/93083/](http://habrahabr.ru/blogs/ubuntu/93083/)

I went through everything, and it seemed to go smoothly. However, when adding the notification panel again, or even logging off, they're still spaced the same. Any idea why?

I'm stumped.

---

### Post by Zookalicious on 2011-04-01
hmm unfortunately not... If you ran an update afterwards, it might have overwritten your changes. (There's a way to freeze it but I don't quite remember off the top of my head).

---

