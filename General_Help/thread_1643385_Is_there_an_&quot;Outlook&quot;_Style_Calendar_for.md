---
title: "Is there an &quot;Outlook&quot; Style Calendar for Ubuntu?"
date: 2010-12-11
forum: General Help
---

### Post by bradRNstyle on 2010-12-11
The only reason I keep a dual-boot on my computer is because I need the calendar in Outlook.  

Is there a outlook-style calendar I can use in Ubuntu 10.04?  Here is the catch, it MUST be able to sync with my Google calendar.  Because I use an android phone that syncs with Google.  I would love to totally leave windoze behind me.  Maybe I can use Wine to install the entire 2007 MS office suite into Linux?

Best idea wins my appreciation!

---

### Post by Bitrate on 2010-12-11
Evolution should do the job.

[http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html](http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html)

---

### Post by tekkidd on 2010-12-11
Evolution is supposed to imitate Outlook 2000 and is compatable with google calendar out of the box (not to mention it ships with Ubuntu by default). Thunderbird with the lightning extension also supports google calendar very well. Thought if you are totally in love with Outlook, you can always run it through crossover (not wine as it does not work with outlook very well).

---

### Post by PhilGil on 2010-12-11
+1 for Evolution. Plays very nicely with Google calendar and should take no time to learn for someone familiar with Outlook. I've been using Evolution+Google Calendar for several months now without incident.

---

### Post by bradRNstyle on 2010-12-11
I like evolution, but when I try to setup synchronization I get this error:

"The GNOME Pilot tools do not appear to be installed on this system."


Maybe I should look at that ehow link.

---

### Post by Zzl1xndd on 2010-12-11
This might help:


[https://help.ubuntu.com/community/GoogleCalendarWithEvolution](https://help.ubuntu.com/community/GoogleCalendarWithEvolution)

Check the section under New Google Calendar.

---

### Post by PhilGil on 2010-12-11
> **bradRNstyle said:**
> I like evolution, but when I try to setup synchronization I get this error:

"The GNOME Pilot tools do not appear to be installed on this system."


Maybe I should look at that ehow link.
The eHow link (or the link tweaked just posted) will work. The Google calendar synchronization uses CalDav. The Synchronize menu command is for syncing with a Palm device.

---

### Post by bradRNstyle on 2010-12-11
> **Bitrate said:**
> Evolution should do the job.

[http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html](http://www.ehow.com/how_4488736_sync-evolution-calendar-google-calendar.html)

Step 3 on the ehow site says:

"From the drop-down menu, select "Calendar Type: Google."

--- but google is not an option in my drop down menu. :(

---

### Post by slooksterpsv on 2010-12-11
> **bradRNstyle said:**
> Step 3 on the ehow site says:

"From the drop-down menu, select "Calendar Type: Google."

--- but google is not an option in my drop down menu. :(

I believe you have to have this installed:

libgdata-google1.2-1

---

### Post by laqa18 on 2011-01-03
Sadly, I'm in the same situation. I have Ubuntu 10.10 and Evolution 2.30.3

The only way it seems, is to make the calendar public (for all the world to see) and even then I had some issues. Guess I'll use thunderbird, although Evolution seemed really good.

EDIT:

After making an update with Ubuntu Tweak, the google and CalDav option appeared. :)

---

