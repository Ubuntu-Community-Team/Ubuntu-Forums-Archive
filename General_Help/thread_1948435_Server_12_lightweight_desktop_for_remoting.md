---
title: "Server 12: lightweight desktop for remoting?"
date: 2012-03-28
forum: General Help
---

### Post by gcaplan on 2012-03-28
Hi folks

WHAT I NEED

I have a webserver on a data-centre VM (ie - no screen). I need to set up a lightweight desktop I can remote into with xrdp for occasional testing and admin tasks.

WHAT I TRIED: Lubuntu fails to install

I've tried installing Lubuntu but it hasn't worked. After rebooting & logging in with Windows Remote Desktop Connection I got an error dialog "Failed to load session gnome". Based on a forum post I tried purging and reinstalling gnome-session. Now I'm seeing the error "Failed to load session Ubuntu".

HOW YOU COULD HELP: please suggest a fix or an alternative

Is there any way I can get Lubuntu to work? Or would I be better to purge it and start again with another desktop? I don't care about features or looks, I'm just looking for something in the official distro that uses minimal resources...

---

### Post by Paqman on 2012-03-28
Sounds like a job for [webmin]("http://www.webmin.com/"). For some reason it's not in the Ubuntu repos, but it's actually pretty widely used.

---

### Post by gcaplan on 2012-03-28
> **Paqman said:**
> Sounds like a job for [webmin]("http://www.webmin.com/").

Thanks but doesn't meet my needs: I could do with an actual desktop so I can run some debugging and testing tools which are difficult to run remotely.

UPDATE - I've tried switching to ubuntu-desktop: that's loading but the 2D shell is crashing so it's not really usable...

Also, auto-remove has failed to find any dependencies for both Lubuntu and Ubuntu desktop so now I have a load of crud on my hard disk... I'd also welcome suggestions on how to clean up...

---

### Post by Paqman on 2012-03-28
Ok, what package(s) did you install when you tried to get LXDE installed?

---

### Post by lykwydchykyn on 2012-03-28
Sounds to me like you need to look at your xrdp configuration.  I haven't used xrdp, so I couldn't tell you what specifically to look at, but based on your errors it's trying to load the wrong session.

If you installed lubuntu desktop, there should be an lxde session under /usr/share/xsessions.  You want your xrdp to point to this instead of the others.

---

### Post by gcaplan on 2012-03-28
Hi folks

I simply installed with #apt-get install lubuntu-desktop and hoped the package would do the rest for me...

I'll reinstall and see if I can figure out the session configuration as suggested by lykwydchykyn.

I'm more of a bash guy myself, so know nothing about desktops - guess I'll have to do some googling. If anyone has some detailed advice it would be welcome.

---

### Post by gcaplan on 2012-03-28
This is turning nasty - I've tried uninstalling and purging the desktop meta-packages, but both have failed. Ubuntu-desktop is still loading even though apt says it's unstalled.

I'm going to open a new thread on the 12 beta forum to see if they can help me clean this up...

---

### Post by Paqman on 2012-03-28
If you just want a lightweight environment to run a couple of apps, don't install the -desktop metapackages, they're full of cruft like video players and word processors.

For a lightweight LXDE system I've found:
```
sudo apt-get install lxde lxsession xorg
```
will do the trick. That may be a little superfluous now since you'll have dragged in a lot more than that with lubuntu-desktop, but if you end up trashing it and starting from scratch I'd just install those packages.

---

### Post by gcaplan on 2012-03-28
In case anyone else runs into this, I cleaned the server with:

#apt-get remove x11-common

That seemed to pick up most of the dependencies that removing the meta-packages missed. Then I cleaned out the orphans with

#apt-get autoremove

Paqman, thanks for getting back - I'll try your suggestion!

---

### Post by gcaplan on 2012-03-28
Paqman you are my hero - worked out of the box after I cleaned up the old installs. Heartfelt thanks!

---

### Post by Paqman on 2012-03-29
> **gcaplan said:**
> Paqman you are my hero - worked out of the box after I cleaned up the old installs. Heartfelt thanks!

No worries!

---

