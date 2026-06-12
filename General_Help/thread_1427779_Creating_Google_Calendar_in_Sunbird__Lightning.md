---
title: "Creating Google Calendar in Sunbird / Lightning"
date: 2010-03-11
forum: General Help
---

### Post by Bradtek on 2010-03-11
I have tried following the how to at google calendars but no matter what I enter for my calendar ID I get this

```
An error was encountered preparing the calendar located at https://www.google.com/calendar/dav/[bunch of numbers-letters here]/events for use. It will not be available.
```

Details

```
Error Number : 0x80004005
Description:
[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [calICalendar.uri]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: file:///usr/lib/sunbird/components/calItemModule.js -> file:///usr/lib/sunbird/js/calCalendarManager.js :: cmgr_createCalendar :: line 536"  data: no]
```

Tried it in both Lightning extension for Thunderbird and stand alone Sunbird

Any help appreciated

Ubuntu 9.10 64bit

---

### Post by Bradtek on 2010-03-11
Grrr happens every time I make a post, I work it out within minutes

I selected wrong calendar type 

Had to select CalDAV not Google Calendar

---

### Post by go_beep_yourself on 2010-03-19
Thanks for posting the solution. That solved the problem for me.

---

