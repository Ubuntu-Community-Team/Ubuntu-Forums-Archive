---
title: "Azureus problems..."
date: 2006-04-13
forum: General Help
---

### Post by exodus on 2006-04-13
hi ppl..

i've got two wierd problems.. both with azureus...

1)
i normally use the root account.. everything worked fine in that.. but true to ubuntu spirit.. i've ditched the root and made myself a user account...

and i've managed to get almost everythin working... only azureus is giving me trouble...

first thing is my DHT and NAT is always firewalled.. i've done the port forwarding in my router through 192.168.1.1.. it works fine in XP.. only ubuntu is giving me problems... not in root though.. in the ordinary user account..

i've also allowed it in firestarter... i've attached a screenshot... my default port is 65534..

i've also uninstalled firestarter and tried it.. i get the same error...

2)
when in root.. azureus auto update works fine..

but now i get permission denied error.. plz advice.. i've attached screenshot for this too..

[[IMG]http://img124.imageshack.us/img124/1143/prob14tm.th.png[/IMG]](http://img124.imageshack.us/my.php?image=prob14tm.png)

plz see to the bottom right hand corner for the error message.. 
[[IMG]http://img101.imageshack.us/img101/7649/prob26cn.th.png[/IMG]](http://img101.imageshack.us/my.php?image=prob26cn.png)

---

### Post by csk on 2006-04-15
yeah i got a similar problem!!! i get a permission denied screen just like the one in screen 2 everytime i try to install a plugin
someone please help

---

### Post by Perfect Storm on 2006-04-15
```
sudo chown -R <username>:<username> /opt/azureus
```

Make the updates and install the plugins you need. 

Afterwards:

```
sudo chown -R root:root /opt/azureus
```

---

### Post by PriceChild on 2006-04-15
Thanks AI :)

btw do we really need to give it back to root afterwards?

---

### Post by Perfect Storm on 2006-04-15
Well if you want safty you'll do. But it's up to you, now you're warned!

---

### Post by PriceChild on 2006-04-15
safty?

---

### Post by csk on 2006-04-15
thanks my plugins now get installed but when i try to install speed scheduler i get  
"Error initialising plugin 'Speed Scheduler' ExceptionInIntitializeError"

and there are no blocked ip's when i installed safepeer

---

### Post by Perfect Storm on 2006-04-15
The easy solution will be installing Azureus on your /home then there's not so much hassle.

---

### Post by csk on 2006-04-15
lol sorry to bother u like this but how do i do that...i am a complet newbie at this . i only got azureus through automatix so i am not too sure about installing packages at specific folders

---

### Post by Perfect Storm on 2006-04-15
Uninstall first your previous Azureus.
Then: grab azurus linux here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) to your Desktop.

```
cd Desktop
tar jxvf Azureus_2.4.0.2_linux.tar.bz2 -C /home/**<username>**/
sudo gedit /usr/share/applications/Azureus.desktop

```

add:
```
[Desktop Entry]
Name=Azureus
Comment=P2P Client
Exec=/home/**<username>**/azureus/azureus
Icon=/home/**<username>**/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```

Should do it.

---

### Post by csk on 2006-04-15
sweet works like a charm
thanks heaps
csk

---

### Post by engineering.concepts on 2006-04-15
Thanks everyone!:D 
My Azureus stopped working 2 weeks ago (I would click on the icon, and my hard drive would be busy for 10 seconds - and then nothing) I tried to reinstall but it would not work. 
This tutorial helped out!
Thanks,
................now if only we could have utorrent for Ubuntu........................

---

### Post by exodus on 2006-04-15
k i got around by that permission denied problem...

how about that NAT FIREWALLED problem??? :(

am havin no luck.. i even removed firestarter...

---

### Post by Perfect Storm on 2006-04-15
You should properly start a new thread about the router problem as it seems it's not the fault in azureus.

---

### Post by Metallinut on 2007-05-17
Artificial Intelligence,

I followed your guide in another thread to install Azureus manually (to /opt/azureus).  I'm trying to do an update and am getting this error:
```
Version 2.1.4 of plugin 'azplugins' failed to install - /home/jp/.azureus/plugins/azplugins/azplugins_2.1.4.jar (Permission denied)
```

Now I've gone and checked ownership of both that directory: ~/.azureus as well as /opt/azureus.  my jp account is listed as owner of both, but I'm still getting these errors...

I planned on doing the update, and setting the owner of /opt/azureus back to root afterwards.

Any idea why it's not letting jp do these updates?

Thanks,

JP

---

### Post by Paqman on 2007-05-21
Thanks AI, I didn't realise it was that easy to switch permissions temporarily. I'll file that one away in my brain's "useful terminal stuff" drawer.

---

