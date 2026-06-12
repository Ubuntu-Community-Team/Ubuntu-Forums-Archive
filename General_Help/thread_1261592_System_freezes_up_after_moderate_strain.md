---
title: "System freezes up after moderate strain"
date: 2009-09-08
forum: General Help
---

### Post by fiddler616 on 2009-09-08
Hello,

I used to run Hardy (and now Intrepid) on my old laptop, and then I got a "new" (second-hand) one that I put Jaunty on. It has 512 MB RAM and a 1.79 Ghz processor. Most of the time it's quite fast--faster than my old laptop, but under certain situations--using Firefox for a long time; having 10ish tabs in Firefox; installing something in a terminal while typing a document...it freezes up. Sometimes (after many minutes), it recovers, and running uptime gives numbers in the six range (processor had six times as much work as it could handle). Sometimes there's nothing for it and I just hard boot.

Do I have a sketchy installation? I thought it might be the hardware--Windows sometimes freezes--but Windows doesn't freeze nearly as much. Or should I just forget GNOME and use Crunchbang?

Thanks.

---

### Post by P4man on 2009-09-09
> **fiddler616 said:**
> , and running uptime gives numbers in the six range (processor had six times as much work as it could handle). 

Hu? What do you mean? What does uptime have to do with cpu load?

Anyway, if both windows and ubuntu are freezing up, you may well be looking at a hardware problem. Still, have you seen anything in the logs that might give a clue? System > adminstration > logfile viewer

---

### Post by fiddler616 on 2009-09-09
> **P4man said:**
> Hu? What do you mean? What does uptime have to do with cpu load?
I read an article on Digg a few months ago that said that the last three numbers in uptime:
```
$ uptime
 07:16:46 up 31 min,  2 users,  load average: 0.03, 0.25, 0.30 

```
were the "load average" over the past 5, 10 and 15 minutes. 1.0 means you have just as much as you can handle, 2.0 means two times as much, etc.
> 
Anyway, if both windows and ubuntu are freezing up, you may well be looking at a hardware problem. Still, have you seen anything in the logs that might give a clue? System > adminstration > logfile viewer
The thing is, even though Windows freezes, it's not nearly as often--I'm allowed to browse the web or type a document in peace.

This is my first experience with log files. [s]Attached[/s](too big to attach: [link]("http://tsmacdonald.com/messages.log.txt")) is everything that was under the "messages" menu option--if you want something else let me know.

Lines like this
```
Scanning 2 areas for low memory corruption
```
are a bit worrying--but I don't know exactly what it means.

Thank you!

---

