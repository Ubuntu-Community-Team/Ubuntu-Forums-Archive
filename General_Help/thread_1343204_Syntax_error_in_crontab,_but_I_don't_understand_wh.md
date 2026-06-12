---
title: "Syntax error in crontab, but I don't understand why"
date: 2009-12-01
forum: General Help
---

### Post by negativ on 2009-12-01
Trying to execute a script on the last day of every month.

crontab -l

```
0 23 * * * [ `date +%d` -eq `echo \`cal\` | awk '{print $NF}'` ] && /path/to/script.sh
```

That works correctly from the command line, but when called as a cron job results in this:

> /bin/bash: -c: line 0: unexpected EOF while looking for matching ``'
/bin/bash: -c: line 1: syntax error: unexpected end of file

:confused:

I guess I could put the date checking logic in the script itself, but I don't understand why I'm getting this syntax error message.

---

### Post by Aearenda on 2009-12-01
It probably because the command line is being split up. You get a similar (but not identical) error if you type ```
bash -c [ `date +%d` -eq `echo \`cal\` | awk '{print $NF}'` ]
```but not if you type```
bash -c "[ `date +%d` -eq `echo \`cal\` | awk '{print $NF}'` ]"
```

So, I would try this in crontab:
```
0 23 * * * bash -c "[ `date +%d` -eq `echo \`cal\` | awk '{print $NF}'` ] && /path/to/script.sh"
```

EDIT: I've just tried this and it still doesn't work correctly for me.
I reckon you'll waste less time by simply incorporating the last-day-of-the-month check into the script that is run. You could always avoid running it unnecessarily by using the crontab entry ```
0 23 28-31 * * /path/to/script.sh
```

EDIT2: Here's the answer, from "man 5 crontab":
> The ``sixth'' field (the rest of the line) specifies the command to  be
run.   The  entire  command  portion  of the line, up to a newline or %
character, will be executed by /bin/sh or by the shell specified in the
SHELL  variable of the crontab file.  Percent-signs (%) in the command,
unless escaped with backslash (\), will be changed into newline charac&#8208;
ters,  and  all  data  after the first % will be sent to the command as
standard input. There is no way to split a  single  command  line  onto
multiple lines, like the shell's trailing "\".

So the '%' must be escaped!

(Found this at [http://www.linuxquestions.org/questions/debian-26/crontab-and-command-subst-277700/](http://www.linuxquestions.org/questions/debian-26/crontab-and-command-subst-277700/)).

---

