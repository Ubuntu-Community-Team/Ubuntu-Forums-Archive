---
title: "Logging program"
date: 2010-01-28
forum: General Help
---

### Post by aparigraha on 2010-01-28
I run a few small public, school and research libraries with 2-3 public computers at each library. They are all running Win XP at the moment. But I'm all into Linux when I'm not at work so I really want all libraries to go 100% open source. The head IT department is not really a department, just one useless individual who use external help for everything... and she is way beyond retirement. 

Well here is my only issue to get it all going. Every year I need to send some statistics upwards through the system, and that includes statistics covering public computer usage (hours and minutes per day, how many different users per day and week and so on).

I don't intend to manage the public machines remotely, if I don't have to. And I don't want to manually check /var/log. I'm more interested in a logging program/script that summarizes everything and sends me the stats over e-mail. All machines are by the way hooked up to the same internal network (172.20.....)

Soooo, I'm very greatful for any good suggestions?

---

### Post by aparigraha on 2010-01-29
Come on.
There has to be someone here who's paranoid enough to know everything about logging :)

---

### Post by rnerwein on 2010-01-29
hi

may be will solve your problem: [COLOR=#000099][B]apt-get install acct

create a script to parse the output of dump-acct (or find it on the net).
tell cron to run the script(s) perodicaly.
ciao
[/B][/COLOR]

---

