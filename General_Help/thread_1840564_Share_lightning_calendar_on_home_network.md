---
title: "Share lightning calendar on home network"
date: 2011-09-07
forum: General Help
---

### Post by Benchrest on 2011-09-07
I have two home machines both running Natty.  Each have Thunderbird and Lightning.  I would like to use the lightning calendar for one of the machines for both, with both able to update the single calendar and receive the same notifications.

If I go to from Thunderbird if I go EDIT / CALENDAR PROPERTIES I see Calendar name HOME and Location moz-storage-calendar://

I think on the one machine I can set a new calendar name  "REMOTE" and the location of my other machines calendar.  But I have no idea what that should be.  I have tried a few things.  I have found examples for accessing calendars on web sites, but not another Ubuntu machine on the same home network.

Any ideas?

---

### Post by Azdour on 2011-09-08
Hi,

I believe the simpliest answer is that you need some other software (or website like google calender) in order to share the calendar, see:

[http://www.mozilla.org/projects/calendar/faq.html#share](http://www.mozilla.org/projects/calendar/faq.html#share)

There is another section in that FAQ:

[http://www.mozilla.org/projects/calendar/faq.html#local_calendar](http://www.mozilla.org/projects/calendar/faq.html#local_calendar)

This describes sharing a calendar between different software on the same machine but it was only intended for viewing. So even if you could take this route and mount a samba share on the other machine where the calendar is, you would probably run into data loss issues as described in the FAQ.

---

### Post by Benchrest on 2011-09-09
I'd be happy if I could just update from one but be able to share the view.  But no where tells me how to define to point to the other calendar. The location for the calendar on each machine is "moz-storage-calendar://"

I attempt to create a new calendar and select "On the network"

Next it ask if ICS, CALDAV, WCAP or Google calendar.  I'm not sure it is any of these. I think the calendar is in .thunderbird/calendar-data/local.sqlite . But somehow as a local calendar it is found by "moz-storage-calendar://"  I have tried searching for this defined location and it doesn't exist.

I have tried using the definition for SSH to access the other computer, "sftp://loveafair65@192.168.1.101/moz-storage-calendar://" And it is not rejected as an invalid address, but still can't find the calendar on the other machine.

It seems strange I can find information on accessing a calendar on Google but not on another Ubuntu machine in my home network.  What format do I need to access the calendar on my other machine?

---

### Post by Benchrest on 2011-09-09
I just reread the links I was referred to by Azdour. I missed entirely what they said. Thankyou for you post.  Looks like I can't get from here to where I want to be easily. I will close this for now, and do some more research as to which way I want to go from here.

---

### Post by Rattle1 on 2011-09-21
> If I go to from Thunderbird if I go EDIT / CALENDAR PROPERTIES I  see Calendar name HOME and Location moz-storage-calendar://Hi,  I was looking for same issue and found that for Location you must enter  "file:///[COLOR=Blue]server-name\folder-name\file-name[/COLOR].ics". For me it worked, although I'm  running Windows on both systems. I will try this with my Linux system home, see if it works, but I don't think there will be any issues.

---

