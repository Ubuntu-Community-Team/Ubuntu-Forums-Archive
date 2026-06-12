---
title: "Script to check monthly usage-help?"
date: 2010-08-21
forum: General Help
---

### Post by ExileAmongYou on 2010-08-21
Disclaimer: This is not really a tech support type question, it's a "help a terminal n00b learn how to write a completely ad hoc script" type thing. Only put time into this if you've got it to spare.

So I'm trying to find a way to monitor my internet usage per month. I've installed vnstat, and altered its config file so that the month starts on the 4th (my ISP rollover date). Now I'm trying to find a good, shiny way to get at the data. Obviously I can run

```
vnstat -m
```

in a terminal, but that's not particularly pretty. Ideally I'd like to have either a button I could click on the panel, or a cron job, that would send my download total for the month to notify-osd.

The next thing i tried was

```
vnstati -m -o /home/exile/Desktop/innernet
```

which puts a little .png table of my usage on the desktop. Still fairly ugly, and it requires a fair few clicks to get at. I only know some pretty basic terminal commands, so all I've been able to come up with is

```
vnstat --dumpdb | grep -w -m 1 m;
```

which gives

```
m;0;1282391482;350;87;839;649;1
```

The third section (ie. the downloads) is what I want to get at. Any ideas on how to grab that part, convert it to megabytes, and send it to notify-osd?

Thanks in advance to anyone with the patience to help me out.

---

