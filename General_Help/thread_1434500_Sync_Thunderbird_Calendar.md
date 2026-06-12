---
title: "Sync Thunderbird Calendar?"
date: 2010-03-20
forum: General Help
---

### Post by Roasted on 2010-03-20
I run Ubuntu on my home PC and work laptop. I just got a hold of the Lightning extension for Thunderbird with the whole calendar set up, and it's pretty friggen awesome.

I'm curious if I can sync the calendars between my work laptop and my home desktop. Both using Thunderbird from the repos and the Lightning extension from the Software Center.

Any ideas?

---

### Post by colorlessprism on 2010-03-20
i think the easiest way would be to sync using "google calendar" as an intermediary. you will need this addon on both computers:
[https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)
now add your new Google Calendar. (in Thunderbird, it's File -> New -> Calendar)
work through the wizard choosing "Google Calendar" as the calendar type. The Location field requires  the XML version of your calendar's Private Address (open google calendar and click settings, then the "calendar" tab, then click on your calendar name (mine is my email) and scroll down until you see[IMG]file:///tmp/moz-screenshot.png[/IMG]:
[IMG]http://www.lifehacker.com/assets/resources/2008/07/private-address1.png[/IMG]
Click/Copy the XML link and paste it into the Location field in thunderbird
Click Continue and you'll be asked for your Google Calendar username  (mine is my Gmail address) and password. 
give your new  calendar a name, Click Continue.
repeat on other computer
From now on, any event you add to any calendar calendar will automatically sync  to google and vice versa. You can reload the calendar to get the most  up-to-date information at any time by clicking "reload"
good luck...

---

### Post by Roasted on 2010-03-20
Oh really? I figured it'd be a stretch asking for thunderbird to sync with an iphone, outlook 2007, and evolution, but thunderbird to thunderbird I figured it would be relatively easy...

---

### Post by colorlessprism on 2010-03-20
having everything sync to/from google calendar is pretty simple, once this is set up you should be able to find a number of different programs that will sync to google for your iphone, outlook, etc, then when a change is made from any system all others are updated...

---

### Post by Roasted on 2010-03-20
Hm, I'll have to give this a shot. I guess I just expected a way to sync my laptop to my desktop directly instead of having a third party.

---

### Post by Roasted on 2010-03-21
Wow, it was simple. I just tested it out and it works great. It'll be nice having my work calendar here at home with me, taking away the need to bust out the work laptop each time I need to check my calendar when I'm already on the desktop doing stuff.

Thanks much!

---

### Post by Nicolas_Agro on 2010-05-06
Hi,
I'm trying to use a google calendar to manage a class room planning with other persons thanks to lightning. The idea was to be able to see class room use during the scholar year. One person has all the rights to edit modify and manage the google calendar, and other just have the right to consult this calendar...
So I created the proper google calendar, this later was declared as Public, and I send the public URL address to other user who want to only consult the calendar.
When I created the new Google calendar in lightning,  every thing worked properly. But when I stop and restart Thunderbird, ligthning asks me a password to access to the google calendar...  But I don't want to give the password at all the people other wise they'll be able to modify its content...
Does any body know why lighting ask me a password (I just want to see the calendar, not to change it) ?
I can I manage to be able to consult the calendar without any password ?

Thanks !

Nicolas

---

### Post by adad on 2010-05-09
> **colorlessprism said:**
> 
From now on, any event you add to any calendar calendar will automatically sync  to google and vice versa. You can reload the calendar to get the most  up-to-date information at any time by clicking "reload"
good luck...

I think only the calendar under the type "Google Calendar" would update this way. If you have a standard offline calendar, it won't be updated to Google Calendar.

Does someone know a way to either merge both types of calendar (offline and network)?

How about exporting an ICS file and sharing it over Ubuntu One, and then importing the file to Google? Is there a way to periodically run such an update/reload?

---

