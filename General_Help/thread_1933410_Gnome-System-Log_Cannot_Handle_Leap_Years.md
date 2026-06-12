---
title: "Gnome-System-Log Cannot Handle Leap Years"
date: 2012-02-29
forum: General Help
---

### Post by Karlchen on 2012-02-29
Hello, folks.

As the title states, I suspect that the Gnome system logfile viewer **gnome-system-log** cannot handle leap years. I.e. it will stumble on every single logfile under /var/log which holds today's date: 29-Feb-2012.

Affected system environment:
+ Ubuntu 10.04.4 Desktop, 32-bit
+ Gnome desktop
+ gnome-utils 2.30.0-0ubuntu1.1
+ gnome-system-log 2.30.0

Whenever **gnome-system-log **is opened it tries to read the file /var/log/messages. Of course, /var/log/messages holds entries having today's date, i.e. 29-Feb-2012.
gnome-system-log will cause 100% CPU load on one CPU and never display /var/log/messages.
If I try to open /var/log/syslog, too, - there are timestamps referencing 29-Feb-2012 in it as well - **gnome-system-log** will cause 100% CPU load on the second CPU and never display /var/log/syslog.
Only by closing **gnome-system-log** the CPU load will return to a normal level.
(Note: viewing logfiles not mentioning 29-Feb-2012 will work normally and not cause any heavy CPU load)

If you launch **gnome-system-log** from a terminal you will learn what the source of the problem seems to be: > (gnome-system-log:3296): GLib-CRITICAL **: g_date_new_dmy: assertion `g_date_valid_dmy (day, m, y)' failed This message will be repeated almost endlessly.

This looks a lot as if either **gnome-system-log** itself or a module which it uses is unaware of leap years. Yes, 2012 is a leap year, and 29-Feb-2012 is a valid date, whatever the function g_date_valid_dmy() may think about it. 

Does anyone know whether a bugfix is available for gnome-system-log or for the module causing the problem?
[SIZE=1]*(No need to tell me other ways of viewing my logfiles without launching gnome-system-log. I am aware of one or two workarounds.)*[/SIZE]

Kind regards,
Karl
--
P.S.:
I'm all curious to find out whether the same problem will raise its head on Lisa Mint, uhm, Oneiric Ocelot plus Mint clothes, as well ...

---

### Post by Karlchen on 2012-02-29
Answering my own question from the initial report:

gnome-system-log v3.2.1 on Linux Mint 12 32-bit (based on Ubuntu 11.10) exhibits the same misbehaviour. Minor improvement: it manages to display the current syslog file, though it will never manage to built up the categories "Tuesday, Feb 28" and "Wednesday, Feb 29" as it should, because the current syslog covers these two days.

Launched from a terminal session the already known error messages quickly fill the screen. > (gnome-system-log:3770): GLib-CRITICAL **: g_date_new_dmy: assertion `g_date_valid_dmy (day, m, y)' failed And the CPUs jump up to 100% load and will return to normal operation only after gnome-system-log has been closed.

Yet, telling from the numerous replies this problem does not seem to affect anybody but myself. Either no-one ever bothers to check the logfiles which Ubuntu generates. Or the two other persons in the world that do never use gnome-system-log for this purpose. :wink:

Karl

---

### Post by winh8r on 2012-02-29
I can confirm that this problem is occuring on 10.04 today, but as you obviously did, I worked out a way round it by viewing the logs by navigating to them using the GUI.

I agree that the problem is probably caused by the leap year, and suspect that the reason it goes largely unnoticed is the fact that it can only be replicated once every four years so a fix is probably more bother than it is worth!!

But well spotted though, it shows that you are paying attention!!!!

Good Luck

---

### Post by imachavel on 2012-02-29
Wow sounds w2kish

Cool thread

P.s. that gnome system log seems to look nothing like the event viewer in windows 7
In terminal if I type:
Gnome-system-log

It opens a log viewer GUI screen, it seems to open s log I need to go to file, then open. Still good read

---

### Post by Karlchen on 2012-03-01
Hello, winh8r.
> [...] suspect that the reason it goes largely unnoticed is the fact that it can only be replicated once every four years so a fix is probably more bother than it is worth!! I agree that we users will only notice (and complain) once every 4 years.
I do not agree that it is not worth fixing. Correct date/time interpretation is vital in a lot of places of the OS and of various software products, without us users even noticing that it happens,  because date/time functions simply work correctly.
Identifying leap years correctly was one of the first and pretty trivial things which we were taught in our Cobol programming training at the end of the previous century.
Therefore from my point of view, it is kind of embarrassing if the gnome utils hold a programme or a shared library which cannot perform this trivial trick. The more so as gnome-system-log does not simply fail to recognize "Feb 29" as a valid date of the year 2012 (oh, I see, the logfiles are missing the year in their date representation, hm), but the more so as it seems to get into some kind of endless loop and eats up the available CPU resources.

Yet, it seems that no-one touched the source code since 2008 according to the copyright note, the previous leap year. So, I doubt the bug will be fixed in 2016. It ain't high priority, but 4 years should be long enough to fix low priority glitches as well.

Kind regards,
Karl

---

### Post by Karlchen on 2012-03-02
Ok, final update for now on "gnome-system-log and leap years":

Today is March 2nd. The machine had not run on Linux on March 1st.
The current messages logfile holds entries for the days February 26th through to March 2nd.

The interesting thing is what gnome-system-log does when launched:

It reads the messages file just fine. If there should have been a CPU spike then it must have disappeared from gnome-system-monitor before there was a chance of spotting it.

In the left column gnome-system-log presents the messages file like this: ```
- messages
... Sunday, Feb 26
... Monday, Feb 27
... Tuesday, Feb 28
... Friday, Mar  2
``` Wednesday, Feb 29 is missing from the list. Only if you click on the "messages" entry in the left column and not on one of the weekdays you will see the entries for the February 29th as well.

OK, let's end the story here for the moment or for the next 4 years ...

Karl

---

