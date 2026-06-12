---
title: "Getting FTP messages from a script"
date: 2009-08-18
forum: General Help
---

### Post by danylo13 on 2009-08-18
Hi,

I'm trying to do download/upload tests through FTP. I want to write the results of the ftp transfer to a file but nothing seems to be writing to the file. Here is my script:

```

$HOST=xxx
$USER=yyy
$PASSWD=zzz

ftp -n $HOST >>output.log 2>>output.err <<END_SCRIPT 
quote USER $USER
quote PASS $PASSWD
get $FILE
quit
END_SCRIPT

exit 0


```output.log and output.err are always empty though. Anyone have any ideas why?
Thanks.

DAN

---

### Post by DaithiF on 2009-08-18
Hi,
for starters these:
```
$HOST=xxx
$USER=yyy
$PASSWD=zzz

```

should be:
```
HOST=xxx
USER=yyy
PASSWD=zzz

```

---

### Post by Slim Odds on 2009-08-18
I would also look into a program called expect.

It's really good for stuff like this.

---

