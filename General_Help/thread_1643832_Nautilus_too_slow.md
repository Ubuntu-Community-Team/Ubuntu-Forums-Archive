---
title: "Nautilus too slow"
date: 2010-12-12
forum: General Help
---

### Post by pranavk_uict on 2010-12-12
My nautilus is running very slow especially opening some particular folders. Let me explain in detail.
If I try to open the Music folder from the links on the left panel, it will be lightning fast. The same thing, if I tried to open from browsing my home folder will take some time. 
Another example- When I try to open my Windows/Program files folder then nautilus is not able to open it only....it freezes and then I have to do a force quit. Same thing if I open it through terminal saying "nautilus /media/sda2/Program\ Files/", it will take time but will atleast open the folder. 
I tried switching to nautilus elementary, but no use.
Also, i turned off the thumbnail view, preview and all the fancy features that nautilus provides, but still no use.
Please, help. If nothing else, is there any way that I can reset my nautilus to its original state? (without reinstalling Ubuntu of course). The reason is I dont want to switch fron nautilus...

---

### Post by Rytron on 2011-01-13
I too have noticed that it takes too long to open certain folders.

---

### Post by Rytron on 2011-01-16
Consider deleting:
```
.gnome
.gnome2
.gconf
.gconfd
.metacity
```

This will reset GNOME to its default but it did solve the slow opening of folders.

---

### Post by Rytron on 2011-01-16
Remember to log out and back in again for the changes to take effect.

---

### Post by pranavk_uict on 2011-01-17
> **Rytron said:**
> Consider deleting:
```
.gnome
.gnome2
.gconf
.gconfd
.metacity
```This will reset GNOME to its default but it did solve the slow opening of folders.

but will deleting these folders will delete my other settings like some nautilus plugins that I have installed? Deleting these folders will remove all my customizations made in the appearance of my desktop look....

---

### Post by aaaantoine on 2011-01-17
> **pranavk_uict said:**
> but will deleting these folders will delete my other settings like some nautilus plugins that I have installed? Deleting these folders will remove all my customizations made in the appearance of my desktop look....

Yes, most likely.  Try moving them instead of deleting them.  If it solves the speed problem, then you can try to compare the two sets of folders for differences, and try to isolate the problem that way.  And if it doesn't solve the problem, delete the new instances and move your old stuff back.

---

### Post by anoop999 on 2011-03-12
I read on another thread that this may be a problem with **appmenu-gtk**. I fixed the problem of slow nautilus by uninstalling this package and restarting nautilus.

---

### Post by Rytron on 2011-03-13
> **anoop999 said:**
> I read on another thread that this may be a problem with **appmenu-gtk**. I fixed the problem of slow nautilus by 
uninstalling this package and restarting nautilus.

Thank you anoop999 for the tip. What exactly is **appmenu-gtk**?

---

### Post by pranavkaranjkar on 2011-03-16
Thank you guys for your help. But I seemed to have figured out the problem.
I tried removing the package "python-nautilus", and now everything is back to normal.....
I was using that package for a nautilus plugin to enqueue songs to rhythmbox but I figured that it could be done using nautilus actions also.

---

### Post by sergiodlc on 2011-05-10
I'm having the same speed problems with Nautilus. I removed the python-nautilus package and the problem persists. Appmenu-gtk is not installed in my system. It's worth noting that running Nautilus as root it performs very fast (I guess something around 10 times faster). I don't really understand why.

---

### Post by sergiodlc on 2011-05-10
After typing in a terminal the command ```
rm -r ~/.local/share/gvfs-metadata
``` Problem gone! I found the solution [here]("http://ubuntuforums.org/showpost.php?p=9006570&postcount=11").

I read in another thread that this latency problems could be related with Ubuntu One. Do you have Ubuntu One installed?

---

### Post by loopduplicate on 2011-06-19
The link above should point to [http://ubuntuforums.org/showthread.php?p=9006570#post9006570](http://ubuntuforums.org/showthread.php?p=9006570#post9006570)

---

### Post by outleradam on 2012-02-11
I was having this problem too!  
Before doing this, I found it quicker to launch sudo nautilus than to just launch nautilus... I'd have to change permissions of any files manually... 

This worked....
> **Rytron said:**
> Consider deleting:
```
.gnome
.gnome2
.gconf
.gconfd
.metacity
```This will reset GNOME to its default but it did solve the slow opening of folders.

All i had to do was remove ~/.gnome2 and ~/.metacity...
```
rm -Rf ~/.gnome2
rm -Rf ~/.metacity
```

Then everything just worked fine..  No more freezing on the Ubuntu One folder and no more waiting 5 minutes for nautilus to launch.    

In the future, is there a way to tell what process is holding things up?

---

### Post by Rytron on 2012-02-12
> **outleradam said:**
> ...I found it quicker to launch sudo nautilus than to just launch nautilus

Only run **sudo nautilus** when you need to. For normal use just run **nautilus**.

---

### Post by SeQueNceR on 2012-11-09
This Fixed My Problem :) THANKS :)

> **anoop999 said:**
> I read on another thread that this may be a problem with **appmenu-gtk**. I fixed the problem of slow nautilus by uninstalling this package and restarting nautilus.

---

