---
title: "Odd cron problem"
date: 2010-02-17
forum: General Help
---

### Post by SiHa on 2010-02-17
I'm trying to run an hourly cronjob. My crontab```
# m h  dom mon dow   command
00 23  *   *   *     /usr/share/mythtv/mythconverg_backup.pl
43 *   *   *   *     /usr/local/bin/mythrename.pl --link --underscores --format "%T %H-%i %d-$n"

```
The problem is the mythrename.pl line, checking my syslog reveals:```
Feb 17 06:43:01 mythbox-desktop CRON[11309]: (mythbox) CMD (/usr/local/bin/mythrename.pl --link --underscores --format ")

```

I need the quotes, otherwise all the formatting options aren't parsed. If I remove them, and remove all the whitespace in between:```
43 *   *   *   *     /usr/local/bin/mythrename.pl --link --underscores --format %T_%H-%i_%d-$n
```

I get:```
Feb 17 06:43:01 mythbox-desktop CRON[11309]: (mythbox) CMD (/usr/local/bin/mythrename.pl --link --underscores --format )

``` instead

Now from what I've read, the length limit for a crontab line is 512 characters, so I'm confused. Can anyone shed any light on why this isn't working? The line will work just fine when pasted into a terminal.

TIA,

Simon

---

### Post by Satoru-san on 2010-02-17
you cannot run a python script like you can an init.d script. Just like you cannot run a shell script like that.

In shell you have to either put bash script or sh script.sh.

[s]You need to start the script off with python2.6 or just plain python. That will run your py script.[/s]

[s]EDIT:
Just realized its perl and not python
Stand by[/s]

for me it works when I run perl5.8.8 script.pl
it is then linked symbolicly to perl.

cheers.

---

### Post by dcstar on 2010-02-17
> **SiHa said:**
> I'm trying to run an hourly cronjob. My crontab```
# m h  dom mon dow   command
00 23  *   *   *     /usr/share/mythtv/mythconverg_backup.pl
43 *   *   *   *     /usr/local/bin/mythrename.pl --link --underscores --format "%T %H-%i %d-$n"

```
The problem is the mythrename.pl line, checking my syslog reveals:```
Feb 17 06:43:01 mythbox-desktop CRON[11309]: (mythbox) CMD (/usr/local/bin/mythrename.pl --link --underscores --format ")

```

I need the quotes, otherwise all the formatting options aren't parsed.
.....

Quotes are usually not the only delimiters allowed.

---

### Post by SiHa on 2010-02-18
> **Satoru-san said:**
> you cannot run a python script like you can an init.d script. Just like you cannot run a shell script like that.

In shell you have to either put bash script or sh script.sh.

[s]You need to start the script off with python2.6 or just plain python. That will run your py script.[/s]

[s]EDIT:
Just realized its perl and not python
Stand by[/s]

for me it works when I run perl5.8.8 script.pl
it is then linked symbolicly to perl.

cheers.

Thanks, but that's not it. The script has the requisite path to the perl interpreter at the beginning, and the full path to the script is declared. If you  notice the prvious entry is also a perl script and that runs just fine. In fact the problem entry also runs, just everything after '--format' doesn't make it to the commandline that is run by cron.

[QUOTE=dcstar]Quotes are usually not the only delimiters allowed. [/QUOTE]
OK...
.
.
So you're suggesting I try others?

OK, I will, but as stated in my OP, even without quotes, the extra parameters still don't get passed.

In the absence of anything else, I'll just make a one-liner script that has the correct command in it, and point cron to that. A bit of a kludge, but it should work.

---

