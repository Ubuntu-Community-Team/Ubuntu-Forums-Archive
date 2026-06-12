---
title: "Network Manager?"
date: 2006-06-01
forum: General Help
---

### Post by russianbandit on 2006-06-01
I thought the network manager was suppose to be a part of the Dapper Drake. Yet I don't see it anywhere. Am I suppose to do something to enable it, or did the Network Manager not make it into this release?

---

### Post by cbudden on 2006-06-01
sudo apt-get install network-manager-gnome

Should do the trick.

---

### Post by NeoChaosX on 2006-06-01
Have the Ubuntu CD in your drive, then do this

```
sudo apt-cdrom add
sudo apt-get install network-manager-gnome
```

---

### Post by shuttleworthwannabe on 2006-06-01
In xubuntu, install the same, and launch it 
[COLOR="Red"]nm-applet[/COLOR]

---

### Post by russianbandit on 2006-06-01
Don't I have to configure it a little. I rememeber there being a guide a couple of month ago, but I can't find it now. Like the network manager isn't working after installing it.

---

### Post by David Corrales on 2006-06-01
You'll have to go and comment the lines in **/etc/interfaces** referring to the interfaces you want Network Manager to manage. And yes, I agree that this shouldn't be in Dapper final...

---

### Post by Game_Ender on 2006-06-03
How do I get the applet to startup autmatically when I start gnome?

---

### Post by testube_babies on 2006-06-03
[QUOTE=Game_Ender]How do I get the applet to startup autmatically when I start gnome?[/QUOTE]

In System -> Preferences -> Sessions go to Startup Programs and add nm-applet.

---

