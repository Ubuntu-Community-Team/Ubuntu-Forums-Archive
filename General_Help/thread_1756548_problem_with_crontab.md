---
title: "problem with crontab"
date: 2011-05-12
forum: General Help
---

### Post by tapi0n on 2011-05-12
Good afternoon,

I'm currently working on a project for school. One of the requirements is to run some commands using crontab.

I've tried adding my script via *crontab -e *as well as adding it to the system wide crontab in */etc/crontab*.

here's the script:

[I]#!/bin/sh
grep -w 'check_backup' crontest/input.txt | grep -w 'test1 testserver' >> crontest/test1.txt

[/I]So bassicly the script is going to check for 'check_backup' in input.txt, then it's going to check if the lines matching also match 'test1 testserver'. Then, if both requirements are met he's going to append it to test1.txt.

I tried adding the absolute path to the grep command (*/bin/grep) *doesn't work either.

*/var/log/syslog *returns  **CMD (   sh crontest/grep.sh) **and that's about the only place I'm able to debug.

I'm stared myself crazy at forum posts without finding an answer. I hope someone is able to help me out.

Greetings,


EDIT:

Ok so got it working, in my cronjob forgot to put a *'*/' at the start of my path. So I guess it was pointing to a non-existing path. Anyway, just wanted to share this for anyone who might come up with the same problem in the future. Make sure to check your paths! :-)

---

### Post by perdan on 2011-05-12
Just a shot in the dark here, but have you tried giving the full paths to the files that grep should read from?

---

### Post by tapi0n on 2011-05-13
Sorry for the late response, but yes I have. Thing is, even when schedueling a cronjob for a simple *echo *it doesn't work either.

---

