---
title: "Time problem"
date: 2012-02-25
forum: General Help
---

### Post by Krupski on 2012-02-25
Hi all,

I am running Ubuntu 11.10 64 bit server with XFCE desktop installed on top. I've been running this way for several years now (that is, XFCE on top of server).

I dual boot between Windows XP and Ubuntu.

My problem now is after upgrading to 11.10, my computer time messes up. If I boot Windows, the time is wrong. If I reset the time in Windows, then boot Linux the time is wrong.

This never happened before... and yes I do have the timezones properly set on both OS's.

Anyone run into this problem and/or have a solution?

Thanks...

-- Roger

---

### Post by liege102273 on 2012-02-25
I am having the same problem.  It seems to reset to GMT, or +8 hours for my time zone when I go back to Windows.  I dual boot between Win 7 and Ubuntu using two separate hard drives.

---

### Post by efflandt on 2012-02-25
In a terminal see **man hwclock** and [B]apropos time
[/B]
Windows assumes that the CMOS clock/calendar is local time, and it sounds like your Linux thinks it is UTC (common for *nix only systems).  So you need to use **sudo hwclock** to tell Linux that CMOS it relies on during boot is **--localtime**.

---

### Post by Krupski on 2012-02-26
> **efflandt said:**
> In a terminal see **man hwclock** and [B]apropos time
[/B]
Windows assumes that the CMOS clock/calendar is local time, and it sounds like your Linux thinks it is UTC (common for *nix only systems).  So you need to use **sudo hwclock** to tell Linux that CMOS it relies on during boot is **--localtime**.

Thank you. I found Windows sets the clock to local time, so using:

```
[FONT=Lucida Console][COLOR=DarkGreen]**hwclock --hctosys**[/COLOR][/FONT]
```

...set my Linux clock to read correctly.

I think instead I will probably fudge Windows to use UTC so I don't have to fudge Linux.

Thanks for the help!

-- Roger

---

