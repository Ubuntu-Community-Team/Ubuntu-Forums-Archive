---
title: "Evolution crashing"
date: 2009-12-21
forum: General Help
---

### Post by sgosnell on 2009-12-21
I've had a problem with Evolution for awhile, and can't fix it.  It crashes whenever I click on the Calendar or Tasks button, immediately, every time, leaving no crash report in /var/crashes.  I'm pretty sure it's related to Google Calendar, but I can't say for sure.  I've read bug reports on Launchpad, threads here and on other forums, and cannot find a fix.  I've disabled all alarms for everything, done multiple remove --purge of Evolution, removed the .evolution folder in my home, and everything else I can think of.  Evolution still remembers my information, including email addresses, former calendars, etc.  I've removed every program with evolution in the name and still it doesn't remove my information.  It still crashes immediately upon clicking on either Tasks or Calendar.  I can live without the email, but the email and contacts are the only things that work.  I need the calendar, but that won't work at all.  

Anyone have any ideas?  I'm just about at the bitter end of my rope.

---

### Post by dcstar on 2009-12-22
> **sgosnell said:**
> I've had a problem with Evolution for awhile, and can't fix it.  It crashes whenever I click on the Calendar or Tasks button, immediately, every time, leaving no crash report in /var/crashes.  I'm pretty sure it's related to Google Calendar, but I can't say for sure.  I've read bug reports on Launchpad, threads here and on other forums, and cannot find a fix.  I've disabled all alarms for everything, done multiple remove --purge of Evolution, removed the .evolution folder in my home, and everything else I can think of.  Evolution still remembers my information, including email addresses, former calendars, etc.  I've removed every program with evolution in the name and still it doesn't remove my information.  It still crashes immediately upon clicking on either Tasks or Calendar.  I can live without the email, but the email and contacts are the only things that work.  I need the calendar, but that won't work at all.  

Anyone have any ideas?  I'm just about at the bitter end of my rope.

Create a new user, log into it and start Evolution.

If it works correctly then you have a configuration problem in your original account, if it does not then there is an underlying problem.

---

### Post by sgosnell on 2009-12-22
I'm almost certain it's a configuration problem, because it keeps the original configuration.  I just can't find the configuration files.  They are not in ~.evolution, because I've completely deleted that folder.  I don't know where evolution keeps its cache and configuration files, other than ~.evolution.

---

### Post by sgosnell on 2010-01-30
Still have the problem.  I've tried creating a new user, and it still crashes the same - it just immediately disappears, with no log in /var/crash.  It's annoying having no calendar.  This also affects the clock applet in the panel, since it uses Evolution to show the calendar, etc.

---

### Post by MoLE on 2011-01-26
I don't know if this will help at all but evolution stores most of it's stuff in

~/.gconf/apps/evolution

and

~/.evolution

So:
```

rm -rf ~/.gconf/apps/evolution
rm -rf ~/.evolution

```
should give you a clean slate and Evo should then reprompt you for all the "new account" information on startup.

Don't forget to shut down all evolution processes with:

```

evolution --force-shutdown

```
prior to deleting these directories.

---

### Post by sgosnell on 2011-01-26
Actually, I solved the problem by removing Ubuntu.  I've been running Debian Testing for some time, and everything works as it should.

---

