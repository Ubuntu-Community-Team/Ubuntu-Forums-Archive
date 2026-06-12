---
title: "grep only filename from log file?"
date: 2011-08-22
forum: General Help
---

### Post by Jungleboss on 2011-08-22
I need some help. I'm trying to grep only the filename (incl. path) from a log. 

**ORA-00060: Deadlock detected. More info in file /oracle/admin/ARNDB/udump/arndb_ora_11957.trc.**

or the line:
[B]ORA-00060: Deadlock detected. More info in file /oracle/admin/ARNDB/udump/arndb_ora_1157.trc.
[/B]

And the result should be:
**/oracle/admin/ARNDB/udump/arndb_ora_11957.trc**

or 

**/oracle/admin/ARNDB/udump/arndb_ora_1157.trc**
?

---

### Post by Wayne_V on 2011-08-22
if the input is consistent, try:

cat <log file> | grep ORA-00060 | awk '{print $8}'

---

### Post by sisco311 on 2011-08-22
You can use grep's -o option to print only the matched parts, something like:
```
grep -o -e '/.*[^.]' filename
```
You might need to use another grep to filter out some lines:
```
grep -e '^ORA-00060:' file | grep -o -e '/.*[^.]'
```

In awk you can try something like:
```
awk '/^ORA-00060:/{print $NF}' filename
```
or to get rid of the extra period from the end of the filename:
```
awk '/^ORA-00060:/{print substr($NF, 0, length($NF)-1)}' filename
```

---

### Post by bodhi.zazen on 2011-08-22
> **Wayne_V said:**
> if the input is consistent, try:

cat <log file> | grep ORA-00060 | awk '{print $8}'

tisk tisk, no need to cat file | grep pattern

Just grep

grep pattern file ;)

Worse , no need to grep with awk :twisted:

I was going to suggest awk is a better tool for this, but now I see sisco311 has stole my thunder.

---

### Post by Jungleboss on 2011-08-23
Thank you!

My current command is like this:

```
tail -n 500 /oracle/admin/ARNDB/bdump/alert_ARNDB.log |awk '/^ORA-00060:/{print substr($NF, 0, length($NF)-1)}'
```

Suggested grep command also works fine.

Now I just need to cat the returned filename. If I use:

```
cat `tail -n 500 /oracle/admin/ARNDB/bdump/alert_ARNDB.log |awk '/^ORA-00060:/{print substr($NF, 0, length($NF)-1)}'`
```

It works fine if there is a ORA-00060 line in the alert log. But if not the command just hangs.

How can this be solved?

---

### Post by Wayne_V on 2011-08-23
an easy way would be to just assign the file name to a variable and then check it exists before trying to cat it:

FILE=`tail -n .....`

if [ -f $FILE ]
then
   cat $FILE
else
  echo "no ORA-00060"
fi

---

### Post by sisco311 on 2011-08-23
```
while read-r filename
do
    cat "$file"
done< <(tail -n 500 logfile | awk ...)
```

---

### Post by incognus on 2011-08-23
> **Jungleboss said:**
> I need some help. I'm trying to grep only the filename (incl. path) from a log. 

**ORA-00060: Deadlock detected. More info in file /oracle/admin/ARNDB/udump/arndb_ora_11957.trc.**

or the line:
[B]ORA-00060: Deadlock detected. More info in file /oracle/admin/ARNDB/udump/arndb_ora_1157.trc.
[/B]

And the result should be:
**/oracle/admin/ARNDB/udump/arndb_ora_11957.trc**

or 

**/oracle/admin/ARNDB/udump/arndb_ora_1157.trc**
?
grep -o '/.*' /path/to/file
should work or
grep -o '/.*.trc' /path/to/file
if you want only the paths leading to .trc files

---
Cheers!

---

