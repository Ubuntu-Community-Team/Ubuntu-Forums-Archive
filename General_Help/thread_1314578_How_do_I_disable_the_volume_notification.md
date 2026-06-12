---
title: "How do I disable the volume notification?"
date: 2009-11-04
forum: General Help
---

### Post by lagamemnon on 2009-11-04
As you guys might have experienced, when I change the volume while I'm watching a full screen flash video, the volume meter popup seems to kick the video out of full screen. I figure if I could turn off the volume meter notification, I might be able to get around this problem, how do I do that?

I'm using Ubuntu 9.10 Karmic Koala.

Thanks!

---

### Post by lagamemnon on 2009-11-06
bump

---

### Post by RavenHollow on 2009-11-28
Did you guys figure out how to do this?  It is very frustrating because it seems as if it should be simple...

Using 9.10 with latest updates, Dell Inspiron 1720, NVidia GeForce 512Mb, 4GB, 2x320GB.  I have been successful at disabling the "original" volume notification by issuing this command:  sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled
  Turn it back on with:  sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled /usr/share/dbus-1/services/org.freedesktop.Notifications.service

This does the trick nicely, but wouldn't you know it there is yet ANOTHER volume notification applet behind that one which remains, leaving it impossible to watch full screen video using the nice remote control that came with my Dell laptop.  Fortunately there is a partial work around for Hulu by using the pop-out feature.

There must be some documentation on how this all works.  Anybody out there have advice on where to look next?

Thanks,
Jake

---

### Post by zoubidoo on 2010-05-16
I'm having this problem in Lucid, so I'd be interested in a solution too.

I miss when volume was simply controlled by a hardware dial.

Z.

---

### Post by pepsifx357 on 2010-06-06
I am having the same frustrations.  Anyone know a fix?

---

### Post by pepsifx357 on 2010-06-14
bump

---

### Post by smoosh on 2010-07-24
I'm looking for the same fix... seems so simple, but it ain't.

---

### Post by benjamin222 on 2011-01-04
...bumping an old thread because I was about to post the same complaint. Any fixes yet? Disabling the volume notification bar every time I change volume would also fix Ubuntu closing out of full-screen flash video every time I change the volume, something I know is an annoyance for a lot of people.

---

### Post by jasker on 2011-03-08
This is a bug in Adobe's Flash Player, not in Ubuntu or notify-osd.  

Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/224475](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/224475)

Adobe has known about it for 2 years but still hasn't fixed it.
Adobe bug report: [https://bugs.adobe.com/jira/browse/FP-902](https://bugs.adobe.com/jira/browse/FP-902)

Your best bet is to keep haranguing Adobe about it until they fix the bug (if you read the comments on Adobe's page, it's not even a terribly complicated fix!!)

---

