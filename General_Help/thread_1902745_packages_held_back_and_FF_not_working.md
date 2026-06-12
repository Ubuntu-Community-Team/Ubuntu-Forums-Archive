---
title: "packages held back and FF not working"
date: 2011-12-31
forum: General Help
---

### Post by iconoclast hero on 2011-12-31
Last night I suddenly had a problem with Firefox starting to load some pages and then crash before I cold really do anything.  I want to post something about this over on the mozilla forum, but one of the first steps they want me to take, reasonably enough, is to update firefox (their method of doing that in the about section of 10 doesn't work, but i'll worry about that later).  The next step is to do all of the updates to linux.  I just switched to the PAE last week when I hit 4 GB of RAM, kernel 2.6.35-31-generic-pae on 10.10 and GNOME 2.32.0... 

So I'm trying to update and I get a whole list of packages held back and I hadn't worried about it until now when firefox broke, lost all of my addons and won't work, plus the list keeps getting steadily longer.

```
@ruth-pc:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-control-center gtk2-engines-pixbuf launchpad-integration libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev liblaunchpad-integration1.0-cil libmtp8 libplymouth2 plymouth
  python-launchpad-integration python-software-properties software-properties-gtk tomboy usb-creator-common usb-creator-gtk virtualbox-4.1 yelp
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 12:56:35
@ruth-pc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gnome-control-center gtk2-engines-pixbuf launchpad-integration libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin libgtk2.0-dev liblaunchpad-integration1.0-cil libmtp8 libplymouth2 plymouth
  python-launchpad-integration python-software-properties software-properties-gtk tomboy usb-creator-common usb-creator-gtk virtualbox-4.1 yelp
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
```

Now, as far as I know the only goofy thing I have done is pin libmtp8 to a version from karmic so that Gnomad 2 would work with my creative zen.  Should I be worried about these 20 held-back packages?  Anyone else seeing issues with Firefox like this?  It appears that I am in the FF Beta channel if that helps, but I don't believe that the about page is saying it is beta.

Oh in case this helps:

```
Add-ons: {0538E3E3-7E9B-4d49-8831-A227C80A7AD3}:2.0.21,{3d7eb24f-2740-49df-8937-200b1cc08f8a}:1.5.16a1,{0FED7D55-65D4-47b6-A6DE-9A4ADB55355F}:1.0.1,https-everywhere@eff.org:1.2.1,firefox@ghostery.com:2.6.2,ubufox@ubuntu.com:0.9.3,compatibility@addons.mozilla.org:1.0.2,{972ce4c6-7e08-4474-a285-3208198ce6fd}:10.0,jid0-YsfoH9UOyD2AHLMzoKlEDy5AZBg@jetpack:1.1.2,jid1-rVWl1u7MJL7d2g@jetpack:3.0.5
BuildID: 20111223001750
CrashTime: 1325357446
EMCheckCompatibility: true
Email: iconoclasthero@gmail.com
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1324685812
Notes: OpenGL: Tungsten Graphics, Inc -- Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2 -- 2.1 Mesa 7.9-devel -- texture_from_pixmap

ProductName: Firefox
ReleaseChannel: beta
SecondsSinceLastCrash: 15070
StartupTime: 1325357373
Theme: classic/1.0
Throttleable: 1
URL: about:addons
Vendor: Mozilla
Version: 10.0

This report also contains technical information about the state of the application when it crashed.
```

---

### Post by iconoclast hero on 2012-01-01
happy new year bump!

---

### Post by iconoclast hero on 2012-01-04
Any help on this?

---

