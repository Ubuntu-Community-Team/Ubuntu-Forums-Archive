---
title: "Directory watching / File watching"
date: 2010-12-17
forum: General Help
---

### Post by Rigoletto on 2010-12-17
Hello,

it is possible to start a script if a file is putted into a directory?
Is there a service that can do that?

Or must i script a "filewatcher" via a timer/sleeper?

I want it for example to automaticly convert pictures that putted in there to a specific resolution and similar things.

greets
Rigoletto

---

### Post by anglican on 2010-12-17
> **Rigoletto said:**
> Hello,

it is possible to start a script if a file is putted into a directory?
Is there a service that can do that?

Or must i script a "filewatcher" via a timer/sleeper?

I want it for example to automaticly convert pictures that putted in there to a specific resolution and similar things.

greets
RigolettoA quick and easy way to do this sort of thing is with cron and find. e.g. make a crontab entry:

```
15 * * * * find /some/directory -maxdepth 1 -mmin 60 -type f -exec /conversion/program {} \;
```
which would check /some/directory every hour (at 15 minutes past the hour) for files whose data has been modified in the last hour and run /conversion/program on them. It would not run /conversion/program on sub-directories or files within sub-directories. Remove the "-maxdepth 1" option if you also want to run /conversion/program on files in sub-directories within /some/directory.

H

---

### Post by tredegar on 2010-12-17
You should also take a look at [incron]("http://freshmeat.net/projects/incron/") (a **cron** for **inotify**).

It is in the repositories.

---

