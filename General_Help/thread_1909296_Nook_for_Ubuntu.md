---
title: "Nook for Ubuntu"
date: 2012-01-15
forum: General Help
---

### Post by sharpertongue on 2012-01-15
So Barnes & Noble has a Nook app available for anyone to download free, but of course I can't install it because I have Ubuntu. Will someone tell me if it's possible to install Nook and how to do it?

---

### Post by duke.tim on 2012-01-15
I don't know about getting the android app to work, but it looks like the windows version will work under wine.

Download nook for PC
[http://www.barnesandnoble.com/u/free-nook-apps/379002321/](http://www.barnesandnoble.com/u/free-nook-apps/379002321/)

If you need to install wine you can search for it in the software center, or

```
sudo apt-get update
```
```
sudo apt-get install wine
```

This page has some instructions and tips to get nook to run.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818)

---

### Post by sharpertongue on 2012-01-15
> **duke.tim said:**
> 
If you need to install wine you can search for it in the software center, or

```
sudo apt-get update
``````
sudo apt-get install wine
```This page has some instructions and tips to get nook to run.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818)

Thanks. I do already have wine :) I'm still confused, though, how to get Nook installed even after reading the notes on that website, blah. I need more detailed instructions I think.. am I supposed to install Nook through terminal somehow after I download the .exe file? Idk :/

---

### Post by sharpertongue on 2012-01-15
I'm using Ubuntu 10.04, if that is important to know.

---

### Post by sharpertongue on 2012-01-15
Nevermind. I just learned about Calibre.

---

### Post by duke.tim on 2012-01-16
Hmm lol the solution you found sounds a lot simpler.

 Some basic instructions on how I install from wine are below (just incase anyone else reads the thread)

The way I normally install and exe is I either right click and select open with wine or 

select wine from the menu and tell it where to install from

|uninstall/install programs or something like that my laptop charger is dead and I haven't bought a new one yet so i'm not currently using ubuntu :( |

winetricks should be in the software repository now, and just select the things that are required for the software.

---

