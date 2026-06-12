---
title: "[Ubuntu 12.04]Software center not opening(urgent)"
date: 2012-05-06
forum: General Help
---

### Post by sainyamkapoor on 2012-05-06
Hey guys i was not able to find any similar thread.
i am a noob so please be gentle
Whenever i open software center it hangs and the crashes without any error.(it darkens and then crashed)
when i open it through terminal following code appers
> 2012-05-06 18:44:55,050 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-05-06 18:44:55,055 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-05-06 18:44:55,369 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-05-06 18:44:55,904 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
^C^CBus error (core dumped)i have tried removing and installing using apt-et through terminal
i have just installed the ubuntu and havenot installed anything yet

---

### Post by carl4926 on 2012-05-06
```
sudo apt-get update
```

Check and make sure the updater applet isn't running, it's not always obvious I find

---

### Post by sainyamkapoor on 2012-05-06
i dont know how to check i just rebooted it and still getting same and i have not opened any updater applet(unless it starts itself)
if it starts itself how to close it

---

### Post by carl4926 on 2012-05-06
pressing Atl+TAB will show any unseen apps

try installing synaptic

```
sudo apt-get install synaptic
```see if that works

---

### Post by sainyamkapoor on 2012-05-06
okay i have installed symantic package installer it is working but still i am not able to access the software centre ..
i have closed all update appleate
any other idea?

---

### Post by carl4926 on 2012-05-06
Try reinstalling the software centre via synaptic

Try starting it from a terminal with: ```
software-center
```
Post any errors that feedback in the terminal

Yes, that spelling is correct

---

### Post by sainyamkapoor on 2012-05-07
i am still gettting same as in first post..
no change ..

---

### Post by carl4926 on 2012-05-07
But when you started it form the terminal, when feedback did you get.
Post it here

---

### Post by sainyamkapoor on 2012-05-07
i get
```
Bus error (core dumped)
```

---

### Post by oklokl on 2012-05-07
[http://packages.ubuntu.com/precise/synaptic](http://packages.ubuntu.com/precise/synaptic)
[http://packages.ubuntu.com/precise/i386/synaptic/download](http://packages.ubuntu.com/precise/i386/synaptic/download)
deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe


First
 Change the update server


```
sudo sh -c 'echo "deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) precise main universe" >> \/etc/apt/sources.list.d/cambrium_precise.list'

sudo apt-get update
sudo apt-get install synaptic
```[COLOR=#FF0000]
[/COLOR]

---

### Post by carl4926 on 2012-05-07
These are what I have installed when searching software-center in synaptic

[[IMG]http://thumbnails6.imagebam.com/18889/5a196e188885070.jpg[/IMG]](http://www.imagebam.com/image/5a196e188885070)

---

### Post by sainyamkapoor on 2012-05-07
okay nothing is working..
will try reinstalling whole of ubuntu when i get time..
thanks for helping..

---

