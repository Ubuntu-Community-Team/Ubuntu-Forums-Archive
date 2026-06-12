---
title: "no messages in var/log"
date: 2011-10-31
forum: General Help
---

### Post by nagileon on 2011-10-31
Hi there,
Why is there no messages file in the /var/log directory please ?
How to change it or trace the system messages in this case ?
Best regards,
Peter

---

### Post by Paddy Landau on 2011-10-31
To see the system messages, use the command dmesg.

Open a terminal and type dmesg.

If you need to scroll the output, use
```
dmesg | less
```You can scroll using the up- and down-page or arrows, and quit by pressing *q*.

If you just need to see the last few lines, use
```
dmesg | tail
```I hope I've understood your requirements correctly.

---

### Post by philinux on 2011-10-31
> **nagileon said:**
> Hi there,
Why is there no messages file in the /var/log directory please ?
How to change it or trace the system messages in this case ?
Best regards,
Peter

It was changed syslog has the same info. You can use the app log file viewer.

---

### Post by redmk2 on 2011-10-31
> **philinux said:**
> It was changed syslog has the same info. You can use the app log file viewer.

Not all the info is the same.  The cure is simple though.  If you want messages back see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1728570").

---

### Post by philinux on 2011-11-01
> **redmk2 said:**
> Not all the info is the same.  The cure is simple though.  If you want messages back see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1728570").

Yes I see that.

[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8)

I guess the devs are not listening on this one if you follow the trail to the other bug.

---

### Post by redmk2 on 2011-11-01
> **philinux said:**
> Yes I see that.

[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/762505/comments/8)

I guess the devs are not listening on this one if you follow the trail to the other bug.

It's this kind of dumbing down that will kill Ubuntu for the real Linux user.  I can understand training wheels for newbies, but altering so many fundamental concepts makes me leery of future developments.  Thanks to Debian itself, we have a way out of the mess.

---

### Post by Paddy Landau on 2011-11-01
> **redmk2 said:**
> It's this kind of dumbing down that will kill Ubuntu for the real Linux user.
Well, Ubuntu is not meant for the "real Linux user" (by "real", I presume you mean the hardcore stereotype who likes to dig into the innards).

Ubuntu is meant for the "typical" computer user -- the businessman, the teacher, the gamer (well, OK, not yet for the gamer), and so forth -- rather than for the technically proficient.

As an analogy, I am not a car engineer and so I want my car to "just work" without having to fiddle with the engine. Ubuntu is intended for that type of person. A car engineer, on the other hand, may love to fiddle with his engine. As I understand it, something like Arch Linux is better for that type of person.

---

### Post by redmk2 on 2011-11-01
> **Paddy Landau said:**
> Well, Ubuntu is not meant for the "real Linux user" (by "real", I presume you mean the hardcore stereotype who likes to dig into the innards).
I would not presume anything.  To disable a notification system because it might be redundant, only to find that it is not and then not repair your error is arbitrary and wrong.  > 

Ubuntu is meant for the "typical" computer user -- the businessman, the teacher, the gamer (well, OK, not yet for the gamer), and so forth -- rather than for the technically proficient.
Regardless of what the talent lever of the operator is, there will come a time when someone (maybe from this forum) will have to diagnose a failure.  Error logs are important.> 

As an analogy, I am not a car engineer and so I want my car to "just work" without having to fiddle with the engine. Ubuntu is intended for that type of person.  A car engineer, on the other hand, may love to fiddle with his engine. As I understand it, something like Arch Linux is better for that type of person.
I say bunk to that idea.  There is room for both casual and expert users.  Besides, it would be nice if you mechanic (eh, technician) could fiddle with the engine using pertinent data; don't you think?  The diagnostic data port on any modern car is for the technician not the driver.

After 20+ years in IT, I expect onward progress.  I do not expect disabling a useful tool that is standard on all other Linux distros.  Especially if it has been done for miss-guided reasons.

I like Ubuntu because I don't have to chase down CODECS.  I'm not a religious re: binary blobs or proprietary software modules.

I don't like Ubuntu when they make changes without describing these changes and allowing for some discussion.  For my desktop,  I don't want to 'roll my own", but I would like to be able to see *dmesg *occasionally.

---

