---
title: "Google Calendar integration w/ Gnome Shell"
date: 2011-10-31
forum: General Help
---

### Post by werewolves on 2011-10-31
I feel like I'm saying this a lot, but googled to no avail:

I am using Gnome Shell, and I would like to integrate my Google Calendar with the calendar application in the taskbar.  I've set up my Google account under "Online Accounts", and made sure calendar is "on" under "use this account for".  Unfortunately, none of my appointments seem to show in the popup calendar.

Thanks,

---

### Post by cbowman57 on 2011-10-31
Try this, open dconf-editor and navigate to the location in this image, paste in your url in front of your default web browser.

[ATTACH]206009[/ATTACH]

---

### Post by cbowman57 on 2011-11-01
You may want to add this to integrate it a little better. [http://www.technologystory.net/2011/10/04/how-to-integrate-google-calendar-into-gnome-shell/](http://www.technologystory.net/2011/10/04/how-to-integrate-google-calendar-into-gnome-shell/)

---

### Post by werewolves on 2011-11-01
> **cbowman57 said:**
> Try this, open dconf-editor and navigate to the location in this image, paste in your url in front of your default web browser.

That did not work.

> **cbowman57 said:**
> You may want to add this to integrate it a little better. [http://www.technologystory.net/2011/10/04/how-to-integrate-google-calendar-into-gnome-shell/](http://www.technologystory.net/2011/10/04/how-to-integrate-google-calendar-into-gnome-shell/)

OK, I'll try it out, thanks.

---

### Post by cbowman57 on 2011-11-01
Not sure if the python script updates on a schedule or if it needs to be run in a loop with wait states.

The script does update the desktop calendar though.

---

### Post by werewolves on 2011-11-01
> **cbowman57 said:**
> Not sure if the python script updates on a schedule or if it needs to be run in a loop with wait states.

The script does update the desktop calendar though.

OK, script worked great!  Thanks so much.

I'll have to add some events from the web and see if they sync.

---

