---
title: "BASH Script: Odd output near IF statement"
date: 2010-05-31
forum: General Help
---

### Post by Darkness Des on 2010-05-31
For some reason, I get said block of errors when I run my script without  arguments:

```

/home/mark/bin/backup: line 34: [: =: unary operator expected
/home/mark/bin/backup: line 37: [: =: unary operator expected
/home/mark/bin/backup: line 40: [: =: unary operator expected
/home/mark/bin/backup: line 43: [: =: unary operator expected
/home/mark/bin/backup: line 46: [: =: unary operator expected
/home/mark/bin/backup: line 49: [: =: unary operator expected
/home/mark/bin/backup: line 52: [: =: unary operator expected
/home/mark/bin/backup: line 55: [: =: unary operator expected
/home/mark/bin/backup: line 58: [: =: unary operator expected

```

With arguments, it's made to exit with status 0 instead of displaying  the menu. Attached is the script where I last left it. Please help.

---

### Post by Darkness Des on 2010-05-31
Please disregard the backup.sh file above, here's the new one:

---

### Post by kaibob on 2010-05-31
I believe you have to double quote $1 after the test command or, as an alternative, use the newer test command. Thus, for example, use either:

[ "$1" = sys ]

or

[[ $1 = sys ]]

For a little background on the test commands see:

[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

---

### Post by iMisspell on 2010-05-31
try placing the $1 in double quotes "$1" and see if it helps.

---

### Post by Darkness Des on 2010-05-31
Thanks to both of you, kaibob and iMisspell, that worked perfectly. I now know what to do from now on in my scripts.

---

### Post by iMisspell on 2010-05-31
Your welcome

A suggestions.
Toss that select in a function, then do a check to see if your script has had command has been sent to it, if no command, display select options like you have, if a command has been sent (like from a CronJob) then run the command.

That just popped into my head.
About half an hour before you posted this thread, i was working on two scripts for back-ups, one MySQL and the other SVN which both will be working under CronJob. 

I thought the suggestion to have your script multi-purpose, CronJob and how you have it, might bee some food for thought, if you have not already considered it.

Good luck.

---

