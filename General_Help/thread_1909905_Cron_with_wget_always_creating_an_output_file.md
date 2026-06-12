---
title: "Cron with wget always creating an output file?"
date: 2012-01-16
forum: General Help
---

### Post by alexlittle on 2012-01-16
Hi all,

I'm trying to write a cron task to regularly call wget on a url. The cron runs fine, but every time it runs it creates a cron.php.X file in my home directory. I've tried to turn off output using the --quiet option and with > /dev/null 2>&1 but it's still outputting a new file with every run of the command.

The command in crontab that I'm running is:

```
*/5 * * * * wget --quiet http://localhost/scorecard/admin/cron.php > /dev/null 2>&1
```

If I run the command 

```
wget --quiet http://localhost/scorecard/admin/cron.php
```

or

```
wget --quiet http://localhost/scorecard/admin/cron.php > /dev/null 2>&1
```

directly on the command line then it also outputs cron.php.X file in my home dir. I thought the wget --quiet option was meant to stop any output? And also that > /dev/null 2>&1 should trash any output?

For info, the content of the created cron.php.X is the html of the page I'm calling (no error messages or similar).

Can anyone point out where I may be going wrong with this? I'm sure I've missed something obvious.

Any help much appreciated,
Thanks,
Alex

---

### Post by alexlittle on 2012-01-17
Got this fixed now...

The line in cron needs to be:

```
*/5 * * * * wget --quiet -O /dev/null http://localhost/scorecard/admin/cron.php
``` 

Though not sure why "-O /dev/null" works but "> /dev/null" doesn't. Guess it's something to do with how wget works.

---

### Post by gsgleason on 2012-01-17
You could also use curl instead which outputs to std out instead of a file, and redirect the std out to /dev/null.

I generally prefer curl for scripting.

---

