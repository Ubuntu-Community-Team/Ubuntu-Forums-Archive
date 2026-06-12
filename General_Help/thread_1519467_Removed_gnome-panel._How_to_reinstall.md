---
title: "Removed gnome-panel. How to reinstall?"
date: 2010-06-28
forum: General Help
---

### Post by BK201 on 2010-06-28
Hi everyone,

I'm totally new to Ubuntu and have a stupid question, I think.. but I've not found a solution yet and don't want to reinstall the whole system. 

I were using Ubuntu lucid, but after playing with wine gnome-panel started to use 100% cpu at startup and filling the swop (seen on conky which started first) the system didn't boot properly, actually I couldn't do anything. Searching the internet gave me no solution so, beeing in a bad mood, I booted up into root terminal using "rw init=/bin/bash" (already used it to reset my passwd :oops:) and just removed the gnome-panel with apt-get.

Now I can not login (because gnome requires the package perhaps?) and can not reinstall the package because of missing internet-connection when booted into terminal. 
Is there a way to get back the pakage without formatting the drive and reintalling a clean Ubuntu?

---

### Post by nothingspecial on 2010-06-28
To get an internet connection from the console
```

sudo ifconfig eth0 up
sudo dhclient
```

Then ```
sudo apt-get install gnome-panel
```

This is assuming you have a wired connection.

---

### Post by BK201 on 2010-06-28
I have a wireless connection only, and I've not managed to bring it up using "ifconfig wlan0 up". Actually "ifconfig" doesn't show any interfaces at all...

---

### Post by Jakiejake on 2010-06-28
> **BK201 said:**
> I have a wireless connection only, and I've not managed to bring it up using "ifconfig wlan0 up". Actually "ifconfig" doesn't show any interfaces at all...

Shouldn't need internet just run
apt-get install gnome-panel
But first how the hell did you remove it
Synaptic?

---

### Post by Jakiejake on 2010-06-28
> **BK201 said:**
> I have a wireless connection only, and I've not managed to bring it up using "ifconfig wlan0 up". Actually "ifconfig" doesn't show any interfaces at all...

But If you do need internet for some reason
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by BK201 on 2010-06-28
> **Jakiejake said:**
> Shouldn't need internet just run
apt-get install gnome-panel
I tried it first, but it didn't worked saying something like "can't connect to xyz...(some internet source)"

> **Jakiejake said:**
> But first how the hell did you remove it
Synaptic?
> **BK201 said:**
> I booted up into root terminal using "rw init=/bin/bash" (already used it to reset my passwd :oops:) and just removed the gnome-panel with apt-get.
As already said, I couldn't do anything at normal boot, Synaptic just wouldn't start... even the  default terminal did not..

---

### Post by BK201 on 2010-06-28
> **Jakiejake said:**
> But If you do need internet for some reason
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
Thanks for the link. I'll try it later at home. have to rush to work now..

---

### Post by nothingspecial on 2010-06-28
Have you got it in /var/cache/apt/archives/ 

ls /var/cache/apt/archives/ | grep gnome-panel

If you have, you can ```
sudo dpkg -i gnome-panel_1%3a2.30.0-0ubuntu2_amd64.deb
```

Or whatever the correct name of the deb is on your system.

---

### Post by BK201 on 2010-06-28
> **nothingspecial said:**
> Have you got it in /var/cache/apt/archives/ 

ls /var/cache/apt/archives/ | grep gnome-panel
unfortunately I found only the wine packeges there..

will try to set up a wireless conecction now. wish me luck :p

---

### Post by BK201 on 2010-06-28
OK, since I couldn't set up a connection using the How-To mentioned above, because my wireless device had no logical name to use, I had to go a completely another way.

Just typed the url's apt-get could not connect to into firefox, downloaded the packages manually and used a livecd to copy them to hard drive (the try to mount a usb-stick directly caused reading many manpages for nothing). Then dpkg.. and finally gnome-panel is back. 
Remains the problem to boot properly, because of that cpu-usage-issue, but this isn't the topic of this thread anymore. At least now I know what I should NOT do to fix it..

Thanks to everyone for quick help and good ideas.

---

### Post by nothingspecial on 2010-06-28
Getting cross with linux and breaking it on purpose in a futile attempt to get even with it, (this is the important bit), and having to fix it, has been my most valuable learning tool.  ;)

---

### Post by Jakiejake on 2010-06-28
> **BK201 said:**
> OK, since I couldn't set up a connection using the How-To mentioned above, because my wireless device had no logical name to use, I had to go a completely another way.

Just typed the url's apt-get could not connect to into firefox, downloaded the packages manually and used a livecd to copy them to hard drive (the try to mount a usb-stick directly caused reading many manpages for nothing). Then dpkg.. and finally gnome-panel is back. 
Remains the problem to boot properly, because of that cpu-usage-issue, but this isn't the topic of this thread anymore. At least now I know what I should NOT do to fix it..

Thanks to everyone for quick help and good ideas.

Thats Okay
Make sure you don't go deleting it again!
FYI heres a tip if you ever want to reset the gnome-panel to default
> rm -rf .gconf/apps/panel Then log-out and log back in!

---

### Post by BK201 on 2010-06-29
> **Jakiejake said:**
> FYI heres a tip if you ever want to reset the gnome-panel to default
I haven't thought about that possibility yet. Will give it a try, though meanwhile I think, that the issue is caused by the session-manager in combination with wine. Reconfiguring the panels should be much easier than the sessions.

---

### Post by dino99 on 2010-06-29
there are plenty ways to repair your config, but i think the fastest one is to reinstall a clean distro

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by BK201 on 2010-06-29
OK.```
mw ~/.gconf/apps/panel ~/.gconf/apps/panel_backup
```solved it. Still had some graphic problems solved by reinstalling the nvidia driver, but I'm writing logged in to Ubuntu now :)

only the default shutdown-logout button (that one linked with the status from the Instant messenger) isn't there nor in the Add-To-Panel-List. Any Ideas how to get it back?

> **dino99 said:**
> there are plenty ways to repair your config, but i think the fastest one is to reinstall a clean distro
I didn't want to reinstall, cause too many hours were spent customizing the current installation. But now it's fixed beside the little thing above.


Edit: the "indicator-applet-session" is back after reenabling compiz and putting some other configurations and settings to their previous state. Solved. Completely.
Thanks again!

---

