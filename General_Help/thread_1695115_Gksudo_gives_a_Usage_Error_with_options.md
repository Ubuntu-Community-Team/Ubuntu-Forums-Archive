---
title: "Gksudo gives a Usage Error with options"
date: 2011-02-25
forum: General Help
---

### Post by DocWho27 on 2011-02-25
I'm trying to have my system shutdown at specified times.  To do this I would use a crontab and gksudo, but there's a problem.  I want to halt my system after the fact so I've been trying this:
```
gksudo -S shutdown -h now
```

The problem is with the -h option, since it works without it.

Thanks for the help!


Ubuntu x64
Intel Core 2 Duo @ 2.3 Ghz

---

### Post by DanneStrat on 2011-02-25
> **DocWho27 said:**
> I'm trying to have my system shutdown at specified times.  To do this I would use a crontab and gksudo, but there's a problem.  I want to halt my system after the fact so I've been trying this:
```
gksudo -S shutdown -h now
```

The problem is with the -h option, since it works without it.

Thanks for the help!


Ubuntu x64
Intel Core 2 Duo @ 2.3 Ghz
I noticed that you use "gksudo" for your

command which should only be used for graphical applications.

Since you're trying to run a "non gui" terminal application,

use "sudo".

Do this instead:

```
sudo shutdown -h now
```

Do you know that you can schedule a shutdown

at a specific time(without using cron) by doing for example:

```
sudo shutdown -h 12:00
```

Then the computer would shutdown at 12:00am.

---

### Post by lisati on 2011-02-25
I noticed you'd used gksudo too. Please have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by DocWho27 on 2011-02-25
I do know that I can schedule a single shutdown at any specified time, but I want to have my system shut down every every night on it's own (more or less).

There is a good chance that I won't have a terminal open open at the time specified, so I chose to use gksudo.

I guess  any app that runs advanced power management (such as hibernate & shutdown at specified times) would be another answer to what I'm looking for.

---

### Post by DanneStrat on 2011-02-26
> **DocWho27 said:**
> I do know that I can schedule a single shutdown at any specified time, but I want to have my system shut down every every night on it's own (more or less).

There is a good chance that I won't have a terminal open open at the time specified, so I chose to use gksudo.

I guess  any app that runs advanced power management (such as hibernate & shutdown at specified times) would be another answer to what I'm looking for.

You can do the following:

Install "gnome-schedule" from the repositories.

You want to make a scheduled task

to shut down your computer.

The "shutdown" command requires

elevated privilegies so you have to start

gnome-schedule with "gksudo". 

Open a terminal and run:

```
gksudo gnome-schedule
```Make a new scheduled task to run every

day and set the time you want.

In the "command" box type the following:

```
/sbin/shutdown -h now
```Now go ahead and apply the new task.

Let me know if it works.

---

### Post by DocWho27 on 2011-02-26
Thanks! That helped a bunch!

I ran into a slight snag with trying to save unsaved documents, but I found gnome-session-save --logout and that should do the trick.  Just need to write a script that runs session-save and then shutdown.

Thanks again!

---

### Post by DanneStrat on 2011-02-26
> **DocWho27 said:**
> Thanks! That helped a bunch!

I ran into a slight snag with trying to save unsaved documents, but I found gnome-session-save --logout and that should do the trick.  Just need to write a script that runs session-save and then shutdown.

Thanks again!

Alright!

Good luck!

---

