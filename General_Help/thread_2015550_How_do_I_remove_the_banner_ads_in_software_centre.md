---
title: "How do I remove the banner ads in software centre"
date: 2012-07-03
forum: General Help
---

### Post by Philip Gray on 2012-07-03
Good evening

I have installed Ubuntu 12.04 on my new hard drive and I am using the GNOME 3 classic Desktop because I dislike Unity and the GNOME Shell. I have noticed when I am connected to the internet banner Adverts popup in the Software centre. My question is:- how do I stop these adverts from being displayed. I find them very irritating and not something I was expecting to see.

Regards
Philip

---

### Post by msammels on 2012-07-03
Hey Philip, you have 2 options:

1) Refuse to use the USC until the "Remove advertisements" checkbox is active.
2) Try the following.

First of all, make a backup copy of:

```
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py
```

Once you have a backup of this file, type this:

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py
```

Find the line which defines MAX_HEIGHT = 200 (line 229, or there about), change MAX_HEIGHT to 10. Save the file, restart the USC, and the banner should no longer obtrusive.

---

### Post by vasa1 on 2012-07-03
> **msammels said:**
> ...
First of all, make a backup copy of:

```
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py
```

Once you have a backup of this file, type this:

```
sudo gedit /usr/share/software-center/softwarecenter/ui/gtk3/widgets/exhibits.py
```

Find the line which defines MAX_HEIGHT = 200 (line 229, or there about), change MAX_HEIGHT to 10. Save the file, restart the USC, and the banner should no longer obtrusive.
Interesting but won't they still load? For someone with a dodgy internet, the problem of slow response time will remain but the cause won't be visible.

I really think there should be a "lite" version for people who don't have decent bandwidth.

---

### Post by msammels on 2012-07-03
They would still load. I totally agree with you on that one. The other option is to use synaptic, or simply apt-get. :(

---

### Post by vasa1 on 2012-07-03
> **msammels said:**
> They would still load. I totally agree with you on that one. The other option is to use synaptic, or simply apt-get. :(
That's what most of us do once we're a little older (and wiser in the game). But keeping Canonical's commercial interests in mind, I think they should really consider making it lighter so that people wouldn't mind using it.

Just the other day, someone was claiming that [CPU usage was going crazy]("http://ubuntuforums.org/showthread.php?t=2014526") and things got unresponsive when USC was running.

If Canonical wants to popularize Ubuntu in countries like India they shouldn't be taking feedback from engineering colleges or wherever but from home users who mostly have poor bandwidth speeds or capped usage.

---

### Post by msammels on 2012-07-03
To be honest with you, I've never really liked USC. Despite the fact that it feels all App Storeish, you can actually buy apps from it... maybe I'm just set in my ways, coming from Fedora, but I prefer to have a package manager. If Canonical implemented some kind of command line argument or something into USC, so I can purge when I remove, and got rid of the ads, I'd use it.

On the other, if you uninstall USC, you need to use the command line to install .deb files, because double clicking opens them with archive manager... took me ages to figure that one out. Ugh.

---

### Post by Philip Gray on 2012-07-04
Hi msammels

Ubuntu 10.04 uses the gdebi package to install .deb files. In 12.04 I installed it from synaptic. To install .deb packages I just right-click on it and then select the 'Open with other app' option. The install window is then displayed. I have not worked out yet how to make gdebi the default program to open .deb packages.

Everyone thanks for your suggestions regarding the banner ads. I use USC when I cannot find what I am looking for in synaptic. Some packages have rather obscure names.

The USC in 12.04  is acting like Realplayer in Windows and some of the so called free websites that assault you with banner and popup ads until you register.

Regards
Philip

---

### Post by stinkeye on 2012-07-04
> **Philip Gray said:**
> I have not worked out yet how to make gdebi the default program to open .deb packages.
Right click on a .deb file.
**Properties > Open With**
and set the default application.

---

