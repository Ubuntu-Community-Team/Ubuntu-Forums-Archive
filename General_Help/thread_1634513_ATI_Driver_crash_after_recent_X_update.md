---
title: "ATI Driver crash after recent X update"
date: 2010-11-30
forum: General Help
---

### Post by Hack.The.Pow. on 2010-11-30
Hello everybody.

I just installed an update through the update manager and when I restarted instead of being greeted with a login screen I saw a black screen.

After some troubleshooting I've narrowed it down to a xserver-xorg-core update.  This update conflicted with my ATI drivers and caused them to stop working.  

After checking the /var/log/apt/term.log file I saw this is what was exactly updated.
```
Setting up xserver-xorg-core (2:1.9.0-0ubuntu7.1)...
```

I tried reinstalling the ati drivers from their site and it caused the same black screen to come up.  It says on their site that they support Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5, or 7.6.  Did this recent update take me out of compatibility?  

When I run ```
man xorg | grep xorg-server
```

I get this:
```
X Version 11                   xorg-server 1.9.0                       Xorg(1)
```

Are there more recent ATI drivers I'm just not aware of?

And if all else fails is there a way to revert back to the older version of xorg where the ATI drivers still worked?

Thanks

---

### Post by Hack.The.Pow. on 2010-12-01
bump anybody?  This default drivers are killing me.  No full screen flash or any 3d effects......

---

