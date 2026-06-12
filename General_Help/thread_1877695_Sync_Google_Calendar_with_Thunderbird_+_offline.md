---
title: "Sync Google Calendar with Thunderbird + offline"
date: 2011-11-08
forum: General Help
---

### Post by tomek_wap on 2011-11-08
Hi,

I'm struggling with having my Google calendar being synced and stored offline on my Ubuntu's 11.10 Thunderbird.

Currently I have:
Thunderbird 7.0.1
Lightning 1.0b7
Provider for Google Calendar 0.9pre

So far, the way I've been doing it on a Mac, using OS X Calendar, was to create events offline on the Mac, and then using Spanning Sync to sync with Google - this way I could sync with my Android phone.

PS. Luckily my contacts are being synced pretty nicely using the gContactsSync plugin for Thunderbird, and all stored offline.

The only solution for calendar I've found was to have the above mentioned plugins and to create a new calendar (on the network), then choose Google Calendar, and provide with the link. Either with CACHE or not, could not manage to have the events offline ... everytime I open the calendar tab it refreshesh/reverts to data which is online.

My Google Calendar is only for providing sync solution to my Android phone - I simply do NOT use the Google Calendar itself.

I've also found a solution where instead of choosing Google Calendar (in new calendar option), CalDAV ... but I do not understand what's the difference, and couldn't find the answer - also didn't find any difference between using those two.


**A long walkaround ...**
1. Sync Google Calendar with Thunderbird
2. Export each (out of 4-5) calendar to ICS file
3. Create new calendar (on my computer, NOT on network)
4. Import previously exported ICS file to newly created calendar (on my computer)

How bad and low can we get with such a simple solution needed??
I mean both Google Calendar and Thunderbird have been around for a very long time, and still no solution to this?


Is there a simple way to solve the problem with having offline events and also being able to sync them with Google?
Thnx!

**BTW**, it doesn't have to be with Thunderbird ... on Mac I've used two separate apps, one for email and another for calendar/events - so it doesn't have to be integrated. Tried Evolution, but it simply doesn't work good, especially with syncing address book with Google Contacts.

---

### Post by M.Thulin on 2011-11-16
ehh  i just looked into this for other reason..
obviosly you cant sync google offline.. however it is possible to sync you phone containing same information

[http://android.stackexchange.com/questions/10085/how-to-sync-calendar-with-android-without-google](http://android.stackexchange.com/questions/10085/how-to-sync-calendar-with-android-without-google) for google droid part.. 

[http://www.mailserverblog.com/2009/03/how-to-use-caldav-with-thunderbird-and.html](http://www.mailserverblog.com/2009/03/how-to-use-caldav-with-thunderbird-and.html)

this is actually not the page you need but if you continue to look for your mail / outlook whatever calender program , it can sync with it

it seems to work almost whatever os you use

GL

---

### Post by tomek_wap on 2011-11-28
Problem seems to be solved, at least for now.
I think there was a recent update to Thunderbird/Lightning plugin, where CACHE option seems **NO** longer "experimental" - which gives a thought that it is now fully supported.

And, it **does** actually work :)
Syncs locally, and when turning WLAN off, all Google Calendar data stays offline in Thunderbird's cal.

All nicely :)

---

