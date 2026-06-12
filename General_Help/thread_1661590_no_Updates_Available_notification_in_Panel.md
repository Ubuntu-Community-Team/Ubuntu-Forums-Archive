---
title: "no Updates Available notification in Panel"
date: 2011-01-06
forum: General Help
---

### Post by markMDW on 2011-01-06
I use to have an applet in my Panel that prompted when I had Updates available for download.  I believe it turned red when there were Important security updates available, and then disappeared or turned off when all the updates had been applied.   That has completed disappeared from my Panel.

I thought I could add the Item back to my panel manually.  I [<Right Clicked>Panel] and added the item Update Manager to it.  Now I can click a box to install updates from the Update Manager but the item doesn't change color to RED when Important Security Updates are available and it doesn't turn off when everything is up-to-date.  Instead it just shows a static square Box with a orange arrow pointing upwards... all the time.  I have to periodically click on it to see if I need to install updates.

How to I turn back on the automated Item so that I get the notifications when there are Important Security Updates and it then turns off after I install them.
Thanks

---

### Post by Pollox on 2011-01-06
It sounds like you added a launcher for update-manager. This is just a button that launches the program, and is something you could do with any program.

There used to be an icon that would appear in the notification area, which I believe is what you are describing. To my knowledge, they got rid of that, and now the same setting in update manager just launches the update-manager window when there are updates. It's a step backwards in my opinion, and I'd love to know of a fix. I assume this was a step towards moving this information to the indicator applet.

---

### Post by markMDW on 2011-01-06
That's what happened.  I added the launcher.  I don't believe I get any notifications period now.  I'll install the current batch of updates and wait a week to see if anything happens.  I had already done that much though, and I don't recall having anything pop up letting me know about the important security updates that were available.  This is definitely a step backwards compared to the nifty little notification in the Panel.  Just click and download when convenient otherwise there is a little reminder all the time.  That was perfect!

I also I have XUbuntu installed on two laptops and they both have functioning notification in the panel, exactly the way that seems most useful.   Despite spending more and more time with GNOME I'm still not finding it as intuitive as the Xfce way.  

I'll mark the tread solved once I get some sort of notification that I need to install the important security updates that I found out about only because I was looking for them.

---

### Post by Pollox on 2011-01-06
> **markMDW said:**
> I also I have XUbuntu installed on two laptops and they both have functioning notification in the panel, exactly the way that seems most useful.

Really? Hmm, that gives me hope that there could be some way to get this to work in Gnome (well, I think it's actually an Ubuntu specific thing), but I haven't found any information on that. It sounds like this is all handled by the "update-notifier" process, so you should check your process list (in system monitor, or top) and make sure that is running.

Edit: Try this
Alt+F2
gconf-editor
apps
update-notifier
uncheck auto_launch
source: [http://www.youtube.com/watch?v=2rkzKObuKkw](http://www.youtube.com/watch?v=2rkzKObuKkw)

I am going to try this out too. Now just to play the waiting game.

---

### Post by Krytarik on 2011-01-06
```
gconftool-2 -s --type bool /apps/update-notifier/auto_launch false
```
Greetings.

---

### Post by Pollox on 2011-01-06
> **Krytarik said:**
> ```
gconftool-2 -s --type bool /apps/update-notifier/auto_launch false
```
Greetings.

Well that's certainly concise. Awesome, thanks.

---

### Post by Krytarik on 2011-01-06
> **Pollox said:**
> Well that's certainly concise. Awesome, thanks.
:lolflag:

---

### Post by markMDW on 2011-01-10
I've ran the code above and checked the system monitor, "update-notifier" is running.   I wish I would have checked the monitor *BEFORE* I ran the code to see if there was a change.  Anyhow, I'm going to wait for a notification now.   :popcorn:

Thanks

---

### Post by markMDW on 2011-01-11
I checked this morning and receive a Red Arrow with Exclamation Point notifying for updates.  Problem Solved.  Thanks everyone!

---

