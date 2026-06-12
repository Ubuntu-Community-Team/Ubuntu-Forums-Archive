---
title: "Evolution + Google Calendar"
date: 2009-11-05
forum: General Help
---

### Post by hambone79 on 2009-11-05
This is absolutely driving me insane, but it is one of the many, many, many reasons I don't use Evolution as my primary e-mail client any more (I did for 8 years).

I am currently using Thunderbird for e-mail and calendar (since it just works better with Google's services), but I am trying to setup my Google Calendar in Evolution so that my appointments will show up in the Gnome clock/calendar applet. Here is the best part: when I go to File->New->Calendar and select Google, then fill out the basic info and select Retrieve List of Calendars, it pulls a freakin list of my calendars without a problem! However, when I click ok to add the calendar, it keeps asking for the damn password and never retrieves the calendar! No matter what I do!

I have tried adding the calendar as the type Google and CalDav and it still asks for a password. What is the secret/magic/vodoo I have to do to make this work????????

---

### Post by akvik on 2009-11-06
I have exactly the same problem, but haven't found a solution, unfortunately.

---

### Post by Aearenda on 2009-11-06
It works for me, both 'Google' and CalDav. You have clicked the 'Use SSL' box, right (on CalDav)?

Update: Just tried it again, and it fails to resolve the hostname using the 'Google' method. But CalDav still works, and I read elsewhere that this is the preferred way. I tick 'Use SSL' and fill in my username with @gmail.com at the end. The URL is caldav://www.google.com/calendar/dav/myusername@gmail.com/events.

---

### Post by akvik on 2009-11-06
Thanks,

I tried with CalDav as you described, but I get exactly the same error.. Will try again.

---

### Post by hambone79 on 2009-11-06
Same here...double checked everything and it still fails.

---

### Post by AldenIsZen on 2009-11-06
I spent a little time this morning and can say while I only had it working halfway before, it seems to be working for me in CALDAV as far as I can tell. Perhaps you have something set incorrectly.. though I do remember there being an issue with certain accounts at certain times, especially if Google account for another domain, etc.

---

### Post by megamania on 2009-11-06
> **hambone79 said:**
> This is absolutely driving me insane,

I had the same problem some time ago, but it's been working for a long time now.

I tried re-creating the calendar just to check if anything went wrong, and it worked in literally 1 minute.

This is what I did:
File -> new > calendar

Type: google
name: anything
username: your google account without @gmail.com
click "get list" (could be slightly different, i'm using a different language)
enter your password
on the left of the "get list" button, you should see the calendar(s)
click ok
done!

I just re-created it once again, and it works.

Let me know if this helps you solving the problem.

---

### Post by akvik on 2009-11-06
That worked!

The difference in my case was to omit @gmail.com for the username. 

Finally the calendar in gnome is working :-)

---

### Post by megamania on 2009-11-06
> **akvik said:**
> That worked!

The difference in my case was to omit @gmail.com for the username. 

Finally the calendar in gnome is working :-)
Glad it worked!

Now that you have a calendar, can you try creating another one (even the same one, bu with a different name) **with** *@gmail.com* in the username and let me know if it works? 

I understand it didn't work for you before, but I'm curious to see if it works now. It does work for me...

---

