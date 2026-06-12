---
title: "time not syncing properly"
date: 2010-09-27
forum: General Help
---

### Post by eival on 2010-09-27
the clock on my toolbar is about 10-15 minutes fast, i live in the east coast, i got all the servers selected in that region, Penn State, Delaware, NYU, Virginia, yet its still ahead.

is there anyway to fix this apart from manually setting it?

---

### Post by philinux on 2010-09-27
> **eival said:**
> the clock on my toolbar is about 10-15 minutes fast, i live in the east coast, i got all the servers selected in that region, Penn State, Delaware, NYU, Virginia, yet its still ahead.

is there anyway to fix this apart from manually setting it?

I have no servers selected only the time zone and it works fine.

---

### Post by srs5694 on 2010-09-27
First, type "date" at a command prompt. Is that time ahead? If not, then this sounds like a bug in GNOME (or whatever you're using for a desktop environment). If the time you get from a command prompt is off, then Linux's software clock is off. If that's the case, then you should try to ascertain if the problem is with the hardware clock (from which the software clock is set when you boot) or something else (say, bad software clock drift). You can check your hardware clock by typing "sudo hwclock --show". Alternatively, you can shut down and check the time that the BIOS shows. (That could be off by several hours, though, if your system is configured to use UTC in hardware.)

If the hardware clock is off, then I suggest resetting it and then reloading your system time from the hardware clock. Try this, adjusting the date and time as appropriate:

```

sudo hwclock --set --date "9/27/10 16:45:05"
sudo hwclock --hctosys

```

This might be necessary because of bad drift in the hardware clock. The Network Time Protocol (NTP) program that refers to external servers, depending on its configuration, may refuse to adjust the time if it's too far off what the hardware clock says it should be, which may be why this is happening.

If the hardware clock is set correctly but the software clock isn't, try using the second line above ("sudo hwclock --hctosys"). If that fixes it but the problem recurs, then chances are your software clock is drifting badly. NTP is supposed to fix this, but maybe it can't for some reason, or maybe a bug in NTP is causing the problem. For the moment, though, I'll assume this isn't the problem.

Once you get this fixed, review your NTP configuration. There's no point in using more external NTP servers than necessary. Typically, NTP checks with each server once every few minutes, so if people routinely refer to too many servers, that can put a huge load on them. For a single computer, I'd refer to just one external NTP server, once you find one that works well. You can monitor NTP with the ntpq program, BTW. Type "ntpq -p" to see a list of the NTP servers you're accessing. An asterisk ("*") in the leftmost column indicates the server that your system is using as its primary referent. A plus sign ("+") indicates another good server that can be used if the primary source fails.

---

### Post by oldsoundguy on 2010-09-27
when was the last time you changed out the bios battery (the on board battery?  If you computer gets a lot of use, and it has been a LONG time or NEVER since a  change, you should consider a replacement.

I have my computers on 24/7 .. and change the batteries routinely once a year. (old habit from the days of Dos 3.1)

---

