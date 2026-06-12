---
title: "Cron + Bash script variables issues"
date: 2010-04-03
forum: General Help
---

### Post by Berduchwal on 2010-04-03
Hi
I am trying to write as bash script in order to have backup done by cron on the webhosting server. I want all backup runs to have incremental number in front of them.

I came up with an idea to store incremental number of a backup in txt file on a server so when next one runs is can check the number in the file.

However I am having terrible issues. 

My script:
```
#!/bin/bash
TME=$(date +"%d-%m-%Y %T")
MSG='Script started: '
echo $MSG$TME

declare -i no1
TME=$(date +"%d-%m-%Y %T")
MSG='Declaration made: '
echo $MSG$TME

. /home/marcin/test/seq.txt
MSG='Backup sequential number: '
echo $MSG$no1

FN=/home/marcin/test/$no1-$(date +%T)-backup.tar
tar -cvpzf $FN /home/marcin/zw1
MSG=$'Backup save as: '
echo $MSG$FN

$((no1++))
echo $no1
echo 'no1='$no1 > /home/marcin/test/seq.txt
```

/home/marcin/test/seq.txt file before script runs
```
no1=12
```

terminal output
```
Script started: 03-04-2010 11:20:00
cron-JustHose backup-delete.sh: 7: declare: not found
Declaration made: 03-04-2010 11:20:00
Backup sequential number: 12
tar: Removing leading `/' from member names
/home/marcin/zw1/
$Backup save as: /home/marcin/test/12-11:20:00-backup.tar
backup-delete.sh: 23: arithmetic expression: expecting primary: "no1++"

```

Google helped me a lot but now I am totally stuck. Can you please advise what I am doing incorrectly.


bash --version
> GNU bash, version 4.0.33(1)-release (x86_64-pc-linux-gnu)

---

### Post by prodigy_ on 2010-04-03
Syntax error. It's ```
((no1++))
``` without the $ character.

---

### Post by Berduchwal on 2010-04-03
Thank you!

Modified to:
```

((no1++))
echo $no1
echo 'no1='$no1 > /home/marcin/test/seq.txt
```

Got:
```
backup-delete.sh: 23: no1++: not found
12

```

Any clues about:
```
backup-delete.sh: 7: declare: not found

```

---

### Post by prodigy_ on 2010-04-03
This all sounds awfully like if dash (/bin/sh) is being called to run your script, not bash.

---

### Post by Berduchwal on 2010-04-03
So sh is not bash?
I used:
```
sh backup-delete.sh
```

I should used:
```
bash backup-delete.sh
```


Thank you very much!

---

### Post by prodigy_ on 2010-04-03
Well, ages ago (pre 6.10) /bin/sh was indeed a link to /bin/bash. If you're interested, you'll find more info [here](https://wiki.ubuntu.com/DashAsBinSh).

---

### Post by wilmatan on 2011-05-14
is bash script same as java script?

[IMG]http://imagicon.info/cat/25/1.gif[/IMG]

---

### Post by Thewhistlingwind on 2011-05-14
> **wilmatan said:**
> is bash script same as java script?

[IMG]http://imagicon.info/cat/25/1.gif[/IMG]

No, not the same thing. Not even close. Bash is a scripting language for automating system tasks.

Javascript is a language used for building web-apps. (Having it enabled is also a security risk.)

---

