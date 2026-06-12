---
title: "backup a file and keep every version of the backup"
date: 2011-01-19
forum: General Help
---

### Post by COKEDUDE on 2011-01-19
I am trying to backup my .bash_history and I want to keep every version of the backup. I am thinking to put one of these in my crontab.

```
0 0 * * 0,3 cat .bash_history > boo
0 0 * * 0,3 cp .bash_history boo
```

I would like the backups to be called boo1, boo2, boo3, etc. I would like to keep every version of the backup. So how would I go about changing this?

---

### Post by geirha on 2011-01-19
Easiest way is to use the date instead, e.g. 
```
cp ~/.bash_history ~/backup/"$(date +%Y-%m-%d_bash_history)"
```

Now a small "gotcha" there is that % is special to cron, so you either need to put that in a script, or escape the %-symbols from cron.
```
0 0 * * 0,3 cp ~/.bash_history ~/backup/"$(date +\%Y-\%m-\%d_bash_history)"
```

---

### Post by COKEDUDE on 2011-01-19
> **geirha said:**
> Easiest way is to use the date instead, e.g. 
```
cp ~/.bash_history ~/backup/"$(date +%Y-%m-%d_bash_history)"
```

Now a small "gotcha" there is that % is special to cron, so you either need to put that in a script, or escape the %-symbols from cron.
```
0 0 * * 0,3 cp ~/.bash_history ~/backup/"$(date +\%Y-\%m-\%d_bash_history)"
```

What do the **+** and **-** in front of **+%Y-%m-%d** do? 

What happens if you don't add escape character in front of % in cron? The man pages say it adds a newline character. What would that actually do? 

Could you also explain how to do that as boo1, boo2, boo3, etc?

---

### Post by geirha on 2011-01-19
> **COKEDUDE said:**
> What do the **+** and **-** in front of **+%Y-%m-%d** do? 

From the man-page
```

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

```

+ just says this is the format argument. - is nothing special, it'll be output as is.

> **COKEDUDE said:**
> 
What happens if you don't add escape character in front of % in cron? The man pages say it adds a newline character. What would that actually do? 


If the cron-line had said this instead
```
0 0 * * 0,3 cp ~/.bash_history ~/backup/"$(date +%Y-%m-%d_bash_history)"
```
cron would've replaced the percents with newlines, then run the first line with sh and use the rest as stdin. So you'd be running something similar to:
```
echo 'Y-
m-
d_bash_history)"' | sh -c 'cp ~/.bash_history ~/backup/"$(date +'

```


> **COKEDUDE said:**
> 
Could you also explain how to do that as boo1, boo2, boo3, etc?
That's very cumbersome. You either have to store the current number in a separate file, or you have to iterate the files until you find an available number to use.
```
[ -f ~/backup/number ] && read number < ~/backup/number || number=0; number=$((number+1)); cp ~/.bash_history ~/"backup/boo$number" && echo "$number" > ~/backup/number
```

---

