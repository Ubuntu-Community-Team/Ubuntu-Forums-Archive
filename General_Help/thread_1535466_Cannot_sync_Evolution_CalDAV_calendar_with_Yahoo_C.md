---
title: "Cannot sync Evolution CalDAV calendar with Yahoo Calendar"
date: 2010-07-20
forum: General Help
---

### Post by nmyrick on 2010-07-20
I cannot find a thread directly related to this problem, so I've posted this as a new thread.

The issue I am having is that I cannot sync my Yahoo calendar using CalDAV in Evolution.

The problem is that the link to the Yahoo CalDAV calendar is [https://caldav.calendar.yahoo.com/](https://caldav.calendar.yahoo.com/) , and in Evolution, it keeps inserting 'caldav://' at the beginning of the link when you click OK when setting up the calendar.

Does anyone know a fix for this?

---

### Post by Tur Third on 2010-08-16
:( I've had no luck either with Evolution.

I also tried Sunbird (and Yahoo's instruction state this should be
[https://caldav.calendar.yahoo.com/dav/your_username/Calendar/your_calendar_name](https://caldav.calendar.yahoo.com/dav/your_username/Calendar/your_calendar_name))

Didn't work either....

I have left feed back at yahoo. Lets all hold our breath !...:-&

---

### Post by nmyrick on 2010-08-21
Does anyone know if there is a way to go in to the Evolution source code and make it so that you can actually enter your own URL under Webcal or CalDav?  Maybe this would be a way around this issue.  

I think it is kind of stupid that it gives you the false sense that it will actually allow you to enter a URL, then it changes it to CalDav:// or WebCal:// !

Maybe there should be an 'Other' option under the type of Calendar, then it should allow you to enter all of your own information.

---

### Post by jimmybarcelona on 2010-09-14
i don't suppose you've found a fix to this? my issue is exactly the same.....

---

### Post by nmyrick on 2010-09-14
Nope.  Haven't found a fix yet. Sorry.

---

### Post by jimmybarcelona on 2010-09-14
We're in luck, I just got it working! Hours of searching for this fix, days trying to get davical up and running, and this little 30 second fix got evolution working. :D . Anyways, below is a link to the article I used to get it working, and beneath that the quick snippet that I used.

[http://www.mail-archive.com/evolution-list@gnome.org/msg13537.html](http://www.mail-archive.com/evolution-list@gnome.org/msg13537.html)

> I had evolution's proxy set the "system" the
system --> network proxy settings were set to the proxy I use for pidgin
etc. By setting the network proxy in Evolution (edit --> preferences -->
network preferences) to "direct" the calendar loaded up just fine.

---

### Post by nmyrick on 2010-09-15
Didn't work for me, but thanks.  I still get an unknown error when trying to create an appointment, and It won't sync with my yahoo calendar.

---

### Post by GammaQuantum on 2010-09-19
> **nmyrick said:**
> I still get an unknown error when trying to create an appointment, and It won't sync with my yahoo calendar.

I can see the appointments I create on the Yahoo! Website and the ones I create in Apple iCal, but I cannot save new ones in Evolution for the "unknown error".

Could you recommend some other program, that can do CalDAV client wise?

---

### Post by nmyrick on 2010-10-14
My solution to this is that I have completely switched to the Yahoo calendar.  I guess this isn't really a fix, is it.  But since the developers of Evolution seem to have chosen to completely ignore Yahoo Calendar, while creating a built in option for Google, I guess this is the only way to go for those of us who prefer the Yahoo calendar.

---

