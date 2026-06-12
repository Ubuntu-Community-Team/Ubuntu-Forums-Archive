---
title: "windows partitions disc"
date: 2011-05-26
forum: General Help
---

### Post by gene simmons on 2011-05-26
hi all,hope this hasnt been asked many time,i installed ubuntu 11.04 a few months ago via install cd dual booting with my windows 7 on my acer netbook,i had sum issues and uninstalled it and formatted the ubuntu partition and then reisntalled 11.04 via wubi this time,with the old install my acer disc was accesable on the lelft menu under file system,now with the wubi install its not there,how can i accses my windows files using wubi,i will search this topic at my lunch break so i appologize if its already been awsered.thanx

dave

---

### Post by DanneStrat on 2011-05-26
> **gene simmons said:**
> hi all,hope this hasnt been asked many time,i installed ubuntu 11.04 a few months ago via install cd dual booting with my windows 7 on my acer netbook,i had sum issues and uninstalled it and formatted the ubuntu partition and then reisntalled 11.04 via wubi this time,with the old install my acer disc was accesable on the lelft menu under file system,now with the wubi install its not there,how can i accses my windows files using wubi,i will search this topic at my lunch break so i appologize if its already been awsered.thanx

dave

You can access your windows partition from the "/host" directory in the root of the ubuntu filesystem.

Just go to "Places > Computer > File system > host"

and you'll have it there.

Other partitons(not the one you run wubi from)will be

available under "Places > Removable media"

Good luck.

---

### Post by gene simmons on 2011-05-26
thanx so much.is there a way to put the whole partition in the left menu labled acer like it was on the other install.thanx again.

---

### Post by DanneStrat on 2011-05-26
> **gene simmons said:**
> thanx so much.is there a way to put the whole partition in the left menu labled acer like it was on the other install.thanx again.

Yes, you can actually make a shortcut to the "host" directory

and put it in the left unity bar.

Now, I'm using the swedish locale on my system, but I will try

and translate as accurate as I can.

Try this:

Right-click on your desktop.

Select "new application launcher"

In the "type" box select "terminal application" or

"run in terminal" or something similar.

In the "name" box, put "Acer" without the qoutes or whatever you

want to call it.

Put this in the "command" box:

```
nautilus /host
```

Now you want a nice icon for your shortcut.

Click on the "icon" button and browse to "/usr/share/icons/gnome/256x256/

devices/harddrive.png"

and there you have a nice icon.

Now you're done with your shortcut so you can close the launcher window.

Drag your new shortcut into your home folder for storage. And then drag 

the shortcut from the home folder to your unity bar.

Right-click the icon in the unity bar and make sure

the lower option "keep in..." is selected.

You can now delete the shortcut on the desktop if you don't want it there.

There you have it.

Note: you need to keep the shortcut in the home folder because if you

delete it there it will also disappear from the unity bar.

Good luck.

---

