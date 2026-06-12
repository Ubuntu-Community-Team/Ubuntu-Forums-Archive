---
title: "Can't add Google Calendar to Evolution in 10.04 beta"
date: 2010-03-23
forum: General Help
---

### Post by Zaphrod on 2010-03-23
I have searched the Ubuntu Forums and Google but have not found any relevant help for this issue.

I have previously used Evolution as a Google Calendar client without problem but previous to this release I have had a *Google *option in the drop down when adding a new calendar. In the latest beta release when I try to add a calendar I only get *CalDAV*, *On This Computer*, *On The Web* and *Weather* options so I tried following [[COLOR="DarkRed"]these instruction[/COLOR]]("https://help.ubuntu.com/community/GoogleCalendarWithEvolution") to add the calendar using the CalDAV option as follows.

[FONT="Courier New"]This method allows the user to create a new calendar that synchronises with Google Calendar.

[LIST=1]
[*]On the Evolution Calendars window, select the New drop-down menu and choose Calendar. The New Calendar window will appear.

[*]Ensure that Type is set to CalDav.

[*]In the Username field, enter your Google username. This will be something like [email]username@gmail.com[/email].

[*]Check Use SSL.
   
[*]In the URL field, enter the following URL: [https://www.google.com/calendar/dav/](https://www.google.com/calendar/dav/)[ your Google Calendar ID ]/events/
[/LIST][/FONT]

But this method doesn't work as evolution seems to change the @ in the Username to %40. I am not sure whether this is a bug or just that Evolution has not been written to work with an @ in the user name or possibly this isnt the issue at all but there is some other underlying problem. I have tried sharing the calendar on Google but this wasn't necessary before and didnt help in any case. 

Does anyone have any insight into this? Do you think I should report this as a bug?

---

### Post by e24ohm on 2010-03-23
> **Zaphrod said:**
> I have searched the Ubuntu Forums and Google but have not found any relevant help for this issue.

I have previously used Evolution as a Google Calendar client without problem but previous to this release I have had a *Google *option in the drop down when adding a new calendar. In the latest beta release when I try to add a calendar I only get *CalDAV*, *On This Computer*, *On The Web* and *Weather* options so I tried following [[COLOR="DarkRed"]these instruction[/COLOR]]("https://help.ubuntu.com/community/GoogleCalendarWithEvolution") to add the calendar using the CalDAV option as follows.

[FONT="Courier New"]This method allows the user to create a new calendar that synchronises with Google Calendar.

[LIST=1]
[*]On the Evolution Calendars window, select the New drop-down menu and choose Calendar. The New Calendar window will appear.

[*]Ensure that Type is set to CalDav.

[*]In the Username field, enter your Google username. This will be something like [email]username@gmail.com[/email].

[*]Check Use SSL.
   
[*]In the URL field, enter the following URL: [https://www.google.com/calendar/dav/](https://www.google.com/calendar/dav/)[ your Google Calendar ID ]/events/
[/LIST][/FONT]

But this method doesn't work as evolution seems to change the @ in the Username to %40. I am not sure whether this is a bug or just that Evolution has not been written to work with an @ in the user name or possibly this isnt the issue at all but there is some other underlying problem. I have tried sharing the calendar on Google but this wasn't necessary before and didnt help in any case. 

Does anyone have any insight into this? Do you think I should report this as a bug?
Do you have to use Evolution? I was a dedicated Evolution user; however, after I upgraded back with 9.xx I started having issues. From there, I moved onto the Zimbra Desktop. Out of the box it supports bidirectional communication with Gmail, inluding contacts, and calendar.

---

