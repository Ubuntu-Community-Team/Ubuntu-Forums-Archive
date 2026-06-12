---
title: "Unity Notification Area (systray) Help"
date: 2011-05-20
forum: General Help
---

### Post by eisenwyrm on 2011-05-20
So, Unity lacks a real notification area.

I have tried serveral methods to "fix" this.

One was this link: [Enable notification area for all applications in Ubuntu 11.04 ]("http://linux-software-news-tutorials.blogspot.com/2011/05/enable-notification-area-for-all.html")

Which did not work for me.

Second step was using either cairo-dock or awn. Cairo's notification area doesn't show everything, i.e transmission. So it doesn't have a true "systray".

So I tried awn's. It worked till I rebooted and I got the duplicate systray error.

After some reading, I decided to give gnome-panel a try. When gnome-panel launched I noticed that its systray was already active. So I removed it and awn's systray started working. Till I rebooted.

Awn's notification area quit working again with error cannot launch notification area due to one already running. So I tried enabling/disabling it in gnome-panel again. Still will not work in awn.

So I am trying to figure out what exactly is causing the conflict. If Unity doesn't have a systray and Cairo and Gnome's systrays are not active, why will Awn's systray not launch?

*Currently I am using the defualt Unity panel, cairo-dock for its applets, awn for its media control applets and gnome-panel for its sytem applets and notification area (systray) [Screenshot]("https://lh3.googleusercontent.com/_52XePepH3bg/TdbQoDyEGII/AAAAAAAAAV0/fb175urf5M0/s800/Workspaces_001.png")*

---

### Post by eisenwyrm on 2011-05-20
Don't know what changed.

Rebooted twice due to transmission freezing up.

Transmission and a some other apps are now showing in Unity's "notification area"

See [screenshot]("https://lh5.googleusercontent.com/_52XePepH3bg/Tdbk6gfwJeI/AAAAAAAAAWI/S_eB0Q1nc0I/s800/Workspaces_002.png")

Unity's notification area is now working properly. Don't know what happened, I don't recall doing an update or anything.

The link I shared in original post now works: [Enable notification area for all applications in Ubuntu 11.04]("http://linux-software-news-tutorials.blogspot.com/2011/05/enable-notification-area-for-all.html")


I will mark as solved. Will assume awn/gnome-panel's notification area(s) were in conflict with Unity.

---

