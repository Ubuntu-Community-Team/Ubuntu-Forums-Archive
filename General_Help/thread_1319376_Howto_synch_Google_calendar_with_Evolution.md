---
title: "Howto synch Google calendar with Evolution"
date: 2009-11-08
forum: General Help
---

### Post by notbitmonk on 2009-11-08
This is how I made it.  I'm using 9.10 and have not tried to enter a recurring appointment but any appointment and whole day events entered synchronize OK.  We'll be using caldav Evolution support to do the synch.  Google's page that explains caldav support is at [http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird](http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird)

[LIST=1]
[*]You will need your calendar address.  According to Google it will be something like: ```
https://www.google.com/calendar/dav/YOURGOOGLECALENDARID/events
```  YOURGOOGLECALENDARID will be your email (ex. [email]email@gmail.com[/email]).
[*]In Evolution, go to File --> New --> Calendar.
[*]On the New Calendar Dialog, type will be CalDAV.
[*]Name is the name that you will use to identify the calendar (only used for presentation purposes on the side bar).
[*]If you will not be connected to the internet all the time but would like to see you events, select the "offline operation" option and if you would like to make Google Calendar your default calendar select the "Mark as default" option.
[*]This is the important part.  The URL box will have ```
caldav://
``` in it.  Do not remove it.  You will need to paste the ```
www.google.com/calendar/dav/YOURGOOGLECALENDARID/events
```right after "caldav://".  DO NOT INCLUDE ```
https://
```
[*]Select the "Use SSL" option and enter your username for Google Calendar.
[*]Click "OK".  Evolution will ask for your password.  To make life easier, select "Remember password" before clicking "OK".
[/LIST]
Evolution will take a moment to update the screen with your events.  If you did not opted to make a local copy for offline use, every time you open Evolution Calendar (for the first time of an Evolution session) it will take a while to update your events.  I believe that the time it takes to update the events will depend in the size of your calendar and your internet connection.  Also, when saving an event from Evolution, it takes a little while to close the event window.  I assume that it is uploading your event to the Google Calendar server and the time it takes is related to your internet connection.

---

### Post by xc8 on 2009-11-27
good idea, but due to a dammit bug evolution does not keep the google calendar offline! even using the CalDav.. if you go offline and restart  the Evolution , there would be NO calendar..

---

### Post by PhilGil on 2010-02-25
> **xc8 said:**
> good idea, but due to a dammit bug evolution does not keep the google calendar offline! even using the CalDav.. if you go offline and restart  the Evolution , there would be NO calendar..
Sorry to resurrect an old thread, but I'm having the same problem - has anyone been able to get this to work as it should?  My Google calendar set up in Evolution via CalDav.  I have "make available for offline use" selected.  If I click on the Work Offline button in the bottom right corner of the Evoluton window, a read-only version of the Google calendar will persist until I close Evolution.  When I re-open the program, the Google Calendar is gone until I reconnect to the web.  I'm using Ubuntu 9.10 with Evolution 2.28.1.

---

### Post by nourathar on 2010-11-04
Apparently this problem still persists ? 
I found what seems like a partial response here:
[http://ubuntuforums.org/showpost.php?p=9736019&postcount=5](http://ubuntuforums.org/showpost.php?p=9736019&postcount=5)

but i'm hesitant to move to an unstable release for my daily email..

---

### Post by notbitmonk on 2010-12-01
I moved to 10.04 and will check later to see if things have changed.

---

