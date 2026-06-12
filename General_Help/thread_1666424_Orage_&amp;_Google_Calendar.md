---
title: "Orage &amp; Google Calendar"
date: 2011-01-13
forum: General Help
---

### Post by oaxacamatt1 on 2011-01-13
Hi All,
Is there a way to have Orage use Googles calendar thru sms or some other means?  It did not look completely intuitive when I opened Orage.  Does anyone know if I need to 'import' the google calendar or can I add a 'foregin' file system to be read in to Orage?
Cheers,
M

---

### Post by joedoe4 on 2012-01-05
*bump*

---

### Post by LewisTM on 2012-05-18
Sorry for posting this late, the solution just came to mind.
Orage doesn't read .ics directly from the Web, which would be the solution for accessing Google Calendar info. You can still emulate this by following these steps:

First go to your Calendar's settings page and copy the private iCAL address to the clipboard.
Install gnome-schedule if not done already and add a new task.
1) Name = Update Google iCal
2) Hourly recurrence
3) Command =
```
wget -N -P ~/.local/share/orage <your private ical address.ics>
```
You may need to escape the % in %40 (@) with a \

This will download your calendar every hour, if newer.

Now enter a new Foreign File in Orage's Exchange Data dialog 
/home/<user>/.local/share/orage/basic.ics

That's basically it! You won't see changes immediately and you won't be able to add or change Google Calendar events but that's as good as it gets.

TIP
Save the basic.ics in a shared drive or a Dropbox folder to access it from multiple desktops running Orage.

Cheers!

---

### Post by oaxacamatt1 on 2012-05-21
Let me give it a try but thanks for getting around to answering this question!
Cheers,
M

---

