---
title: "search in a log file via command line"
date: 2011-06-03
forum: General Help
---

### Post by luke0927 on 2011-06-03
I have some large log files that I would like to search for a specific text via command line in the file.  I know I can open the file in GUI but is there command that I can run against the file path then make it search in the file in command line?

Thanks!

---

### Post by TeoBigusGeekus on 2011-06-03
Look at grep command.

---

### Post by linkageless on 2011-06-03
grep is the main tool, but sometimes you might use awk, sed or even perl.

For example:
grep 'find me' big.log |more

for really large files, in conjunction with grep I might use tail and/or head, for example:

tail -10000 /var/log/reallybig.log |head -1000|grep -A 2 -i 'search text'|more

This would consider the first 1000 (head -1000) lines from the last 10000 lines (tail -10000) and case insensitively filter these looking for 'search text', and also display the two lines after any match.

---

### Post by Habitual on 2011-06-04
oops

---

### Post by collisionystm on 2011-06-04
> **luke0927 said:**
> I have some large log files that I would like to search for a specific text via command line in the file.  I know I can open the file in GUI but is there command that I can run against the file path then make it search in the file in command line?

Thanks!

Yup, easy. Use nano.

Open terminal

nano logfile

Use ctrl+w to open the search box. Type what u want and hit enter to search the log.

Be sure to mark this solved!

---

### Post by linkageless on 2011-06-07
> **collisionystm said:**
> Yup, easy. Use nano.


I *love* nano, but depending on how large the files are, searching could be heavy duty. Off the cuff and from past experience, I'd say if the file is larger than your free ram, you're better off using grep unless you're prepared to wait a long while.

---

### Post by seawolf167 on 2011-06-07
> **TeoBigusGeekus said:**
> Look at grep command.

+1 An example:

```
cat /var/log/cron.log | grep -i *search_string*
```

---

### Post by nothingspecial on 2011-06-07
But you might not be wanting to edit your log files

type

```
less /path/to/log 
```

which will display the log file in less

to search, press / then enter your search term

press N to go to the next occurence or Shift-N to go back

(hint of the day, man pages are opened with less by default - you can search them like this also ;) )

---

### Post by Habitual on 2012-05-14
> **seawolf167 said:**
> +1 An example:

```
cat /var/log/cron.log | grep -i *search_string*
```

cat not necessary at all.
```
 grep -i /var/log/cron.log
```

---

