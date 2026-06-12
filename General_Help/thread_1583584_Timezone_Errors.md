---
title: "Timezone Errors"
date: 2010-09-28
forum: General Help
---

### Post by sauravg on 2010-09-28
On Karmic, every once in a while this error pops up near the notification area at the top right (also see attachment):

Timezone Errors
See Error Console: Unknown timezones are treated as the 'floating' local timezone.

But the 'date' command shows the correct date/time and timezone. /etc/timezone is also set correctly.  The machine is running ntpd and is connected to the net 24/7 via ethernet.  I also don't see any 'timezone' errors in /var/log/*

My questions are:

1. Which software is complaining?
2. What is the problem?
3. What is the "Error Console" it is referring to?

Thanks,
Saurav.

---

### Post by sayantandas on 2010-09-29
try 
```
sudo dpkg-reconfigure tzdata
```

in the terminal

---

### Post by sauravg on 2010-09-30
That didn't help.  I went through the configuration screens, where it looked as if everything was already set properly.  But I'm still getting the same pop-up.

---

### Post by P4man on 2010-09-30
Google reveals this code when you search for the error message:
[http://bitbucket.org/tymofiy/l10n-mozilla-191/src/c9f07c8cde39/calendar/chrome/calendar/calendar.properties](http://bitbucket.org/tymofiy/l10n-mozilla-191/src/c9f07c8cde39/calendar/chrome/calendar/calendar.properties)

Is that some calendar plugin you installed?

---

### Post by sauravg on 2010-10-01
Yes, I have Thunderbird + Lightning plug-in installed.  So "Error Console" is TB's error console, which actually has an error saying "timezone is not defined".  But it *is* defined explicitly under Lightning tab in TB Preferences.  May be its having problems with some remote calendars I've added.

But I now know that I should go ask in TB forums.  And also that its not a system misconfiguration in some way.  Thanks for your time on this.

Regards,
Saurav.

---

### Post by bamboodragonfly on 2010-10-11
I have the exact same error. Do you by any chance use Davmail to integrate with Exchange? I seem to only see this error when Thunderbird/Lightning is trying to sync my Exchange calendar via Davmail. Have you found a solution?

---

