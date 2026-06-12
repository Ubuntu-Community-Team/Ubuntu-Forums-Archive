---
title: "Daily General Maintanance"
date: 2009-10-15
forum: General Help
---

### Post by CD27 on 2009-10-15
I am writing this thread because I'm curious, but I also think others would benefit from such information as well. It is almost 1 am here, so my apologies if this has already been submitted (just link the others here as well, maybe we can expound on them in addition).

Basically, what I'm looking for is a list of terminal commands to run that act as your basic daily maintenance. For example, checking for updates and upgrades. I know sometimes the update manager won't show if there's an update for a specific thing if it's small, but if you run:

```

sudo apt-get update

```

Sometimes it'll download some updates that you didn't see before.

```

sudo apt-get upgrade

```

Kind of does the same thing to me, so running this command helps me get new packages that have been released as fixes to bugs (I know I've got like 12 bugs in my OS right now that I have no idea how to fix or submit for troubleshooting...actually, if anyone is willing to help on that please contact me on msn messenger at [email]psinetic@gmail.com[/email]).


Simply put, I'm looking for a script that I can put together with a bunch of terminal commands that work good to keep your system up to date and in working order that i can set a chron-job for.


If at all possible, I'd like as many inputs as possible, this would be helpful in several ways, not just in having something to keep all the newbies up to date, but also to help us (yes, I would be more than happy to put myself into the newbie category) understand the commandline alot better and be able to do alot of this on our own. Thanks in advance!!!

-Eric :guitar:

---

### Post by oldos2er on 2009-10-15
How to report bugs in Ubuntu: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by cariboo on 2009-10-15
If you have questions, post them here, they have probably already been answered, so it shouldn't be to hard to help you solve them.

As far as daily maintenance goes, the only thing I do is back up my home directory daily using a script I created. I'm running Karmic, so I usually update 2-3 times a day, on my Jaunty install I only update when I get a notification from update manager.

```
rsync -av --delete /home/<me> <me>@server:restore/
```

is what I use to back up my home directory.

---

