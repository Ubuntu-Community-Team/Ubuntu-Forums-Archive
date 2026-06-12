---
title: "Opening Thunderbird to an Extension"
date: 2012-08-20
forum: General Help
---

### Post by Rikeshar on 2012-08-20
I have Thunderbird with an extension installed called "Google Calendar Tab." This basically opens up a new tab in the program and points it to Google Calendar, so that I can use Thunderbird to handle such things. 

I've also gone into dconf-editor and made it so that, on Gnome 3, when you click on the date/time in the top bar, and then on "Open Calendar," it opens Thunderbird.

Originally this button pointed to Evolution, and in the dconf-editor option for it performed the commaned "evolution -c calendar" which I assume opened Evolution to the calendar section.

Does anyone if there's a way to open Thunderbird to a specific extension, so that when I click this button it'll open it directly to the Google Calendar Tab extension?

---

### Post by pqwoerituytrueiwoq on 2012-08-20
```
thunderbird https://www.google.com/calendar/render?pli=1
``` might work
you could use lightening to handle your calandar  there is a addon to help with this called "provider for google calandar"

---

