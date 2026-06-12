---
title: "Google Calendar and Evolution"
date: 2006-04-13
forum: General Help
---

### Post by rverrips on 2006-04-13
Is there anyway to import (or even better, import and export) a [Google Calendar]("http://www.google.com/calendar") into Evolution?

---

### Post by Sef on 2006-04-13
> Does Google Calendar connect to other calendar applications and devices?
Yes. Google Calendar uses open calendar standards to give you more choice when it comes to accessing your calendar. You can view your schedule using any application or device that accepts iCal or XML files.

Yes, it does.  From the gnome website evolution website: > iCalendar support  

[http://www.gnome.org/projects/evolution/]("http://www.gnome.org/projects/evolution/")

---

### Post by cstudent on 2006-04-13
To export from Google Calendar

[http://www.google.com/support/calendar/bin/answer.py?answer=37111&topic=8566](http://www.google.com/support/calendar/bin/answer.py?answer=37111&topic=8566)

---

### Post by rverrips on 2006-04-13
Is there a way to "connect" to Google Calendar without import/export, i.e. updating Evo' directly using the iCal or XML URL's?

---

### Post by AndyM on 2006-04-18
Yes.  Click calendar settings for each of your Google calendars that you want to connect, then, under "Private Address" copy the link given by the green ICAL icon.  Then, for each one, add a new calender to Evo "on the web" using that address.  I set mine to cache a local copy as well, for offline viewing.  I'm pretty sure you can't add events through Evo, but they'll be updated at the frequency you choose.

---

### Post by nocturn on 2006-04-18
[QUOTE=Sef]Yes, it does.  From the gnome website evolution website:   

[http://www.gnome.org/projects/evolution/]("http://www.gnome.org/projects/evolution/")[/QUOTE]

Evo does have icalendar support (which is it's internal storage), but cannot write to remote calendar files.

For that you need a server that speaks CalDAV (mainly Hula).

---

### Post by rverrips on 2006-04-18
[QUOTE=AndyM]Yes.  Click calendar settings for each of your Google calendars that you want to connect, then, under "Private Address" copy the link given by the green ICAL icon.  Then, for each one, add a new calender to Evo "on the web" using that address.  I set mine to cache a local copy as well, for offline viewing.[/QUOTE]

Thanks AndyM - This is exactly what I was looking for - I kept trying to add it using the "publish calendar" under Evo' preferences - Didn't think to simply add it.

---

### Post by cyaconi on 2006-04-19
Works nice... but I'm having problem with special characters. 
For example, in google calendar I have a meeting called "Reunión xxx...." and Evolution only reads "Reuni", so I suspect is having troubles with the "ó".

Is there any way to avoid this problem??

Thank you!

---

### Post by dlai on 2006-05-19
well the google calendar api has been released, that means that we can change in the calendar from any other application... but now we just have to find out how to implement it in evolution.

---

### Post by nocturn on 2006-05-22
[QUOTE=dlai]well the google calendar api has been released, that means that we can change in the calendar from any other application... but now we just have to find out how to implement it in evolution.[/QUOTE]

If evolution would just support webcal writes (WebDAV), we would be fine with Google calendar and many others until CalDAV servers start appearing.

For now, the CalDAV plugin is nice and shiny, but apart from Hula, there are no servers for it, so it is basicly useless.

---

