---
title: "help needed to setup remote desktop viewer"
date: 2012-02-17
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-02-17
Hi All,

I need a 'how to' guide to setup and run the remote desktop viewer. I don't need remote control of the sytem that is sharing the desktop, but it would be desirable.

Here's the poop........

I setup and administer 4 ubuntu systems, one of them is out to state and reachable only via the internet.

My system is 11.10 xubuntu, with a very old p4 processor. It runs well. I have my home folder encrypted. I do general purpose computing, nothing fancy. I came from windows, and have been windows free since May 2011 and I don't miss it in the lest.

The other system is a very modern Dell desktop with an i3 processor, which was purchased for it's compatibility with ubuntu. It runs unity (11.10) and the owner is a relative that I introduced to ubuntu after doing some training. It is only available via the internet.

Both systems are behind routers, so I believe firewalls might be an issue. 

On my xubuntu system, I have a program called vinagre remote desktop viewer, ver 3.2.1. The remote computer has the default remote desktop viewer that comes in the unity version of ubuntu.

I tried connecting to my daughters unity laptop that is on the same router as mine, assuming that I could start there and eventually learn enough to make the remote desktop function across the internet. I can connect to the modem directly, so I have all the needed ip addresses for systems connected to the same modem. But, even though both computers are sitting side by side and are connected to the same router, the remote desktop viewer fails, reporting an error after a few seconds.

The help file for the desktop viewer is usless and most of the posts in the forum are to technical for me to understand::>

What do I need to do to make the remote desktop function?

Do I need to o anything to the computer that is going to be sharing the desktop or can I just run the remote desktop viewer from my ststem without making changes to the remote computer itself? 

ty.

Art

---

### Post by Leppie on 2012-02-17
On your daughter's laptop go to System > Preferences > Remote Desktop:
[IMG]http://www.debianadmin.com/images/rds/3.png[/IMG]

Then select "Allow other users to view your desktop":
[IMG]http://www.debianadmin.com/images/rds/5.png[/IMG]

Verify the other settings and then click "Close". That should allow you to connect to her desktop.
More information here: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

