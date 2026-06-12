---
title: "Clock Applet 2.30.2 delay when clicked after Maverick upgrade"
date: 2010-10-21
forum: General Help
---

### Post by ClintSwiney on 2010-10-21
After upgrading from Lucid to Maverick my Clock applet is acting up. When I click it there is a delay of about 1 minute 16 seconds before it responds. The time display does not change while this delay is taking place. I had several locations setup and I figured it may be causing the issue so I removed the Clock applet from the panel and then re-added it. Even with default settings and no extra locations defined it still has the delay but only when clicked. If I leave it alone it chugs along with the current time. I have applied all updates and restarted. I have killed all the gnome panels and let them reload but nothing seems to effect this behavior.

All of my other gnome panel applets are working fine.

Does this ring any bells? Is anyone else having similar issues? Please help.

Thanks,

Clint

---

### Post by skeve on 2010-10-21
I'm having the same issue, it takes about 30 seconds for the calendar to appear. I don't have any locations setup, if that matters.

---

### Post by ClintSwiney on 2010-10-25
Bump.... Anyone?

---

### Post by ClintSwiney on 2010-10-25
I solved my own problem....

I really don't know exactly what fixed it but here goes...

I noticed that gnome-panel was up to version 2.32.0.2 but I had 2.30.2 installed.

I downloaded the new version of gnome-panel from [http://ftp.gnome.org/pub/GNOME/sources/gnome-panel/2.32/](http://ftp.gnome.org/pub/GNOME/sources/gnome-panel/2.32/)

I then followed the directions to compile and install it.

I then ran 

```
killall gnome-panel
```

This messed everything all up, the gnome panel applets would not run and the clock applet would not add to panel. So....

I opened Synaptic Package Manager and searched for gnome-panel

I "marked for complete removal" all the gnome panel related items, data and all. Then Applied that change. 

Then I reinstalled gnome-panel and all it's dependencies with Synaptic Package Manager. I then went to terminal and did:

```
sudo apt-get install ubuntu-desktop
```
and
```
killall gnome-panel
```

After doing all this the fonts on the panel are not what they used to be when I first upgraded and the general look and feel are different. But the problem with the clock delay when being clicked it gone and all the applets work. The indicator Applet changed from the Switch icon to the old Power Button too. It looks like it reverted to the look and feel from Lucid.

The other strange thing is that when I go to Add to Panel there are two Clock applets listed. 

When I do an About Panels I get returned 2.32.0.2. Somehow this retained the new version I got from GIT even though I installed it from Synaptic!

Whatever, it's working now even though it looks a little funny. I may have to wipe out my install and reload 10.10 from the DVD in order fix it 100% but I can deal with an old looking gnome-panel.

---

