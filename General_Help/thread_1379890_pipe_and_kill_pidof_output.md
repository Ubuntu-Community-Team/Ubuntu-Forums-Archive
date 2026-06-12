---
title: "pipe and kill pidof output"
date: 2010-01-13
forum: General Help
---

### Post by zeezam on 2010-01-13
I want to kill a specific program with the kill -9 pid in a hole command.

How do I pipe and kill the output from this command?

pidof transmission | 
?

---

### Post by Locutus_of_Borg on 2010-01-13
kill -9 `pidof *app*`

note that those are backticks, not apostrophes/single-quotes

note the backtick is usually on the same key as ~ on standard american 104 key keyboards

---

### Post by zeezam on 2010-01-13
> **Locutus_of_Borg said:**
> kill -9 `pidof *app*`

note that those are backticks, not apostrophes/single-quotes

note the backtick is usually on the same key as ~ on standard american 104 key keyboards

Works fine but when i put it in a script it fails.

./killxbmc 
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

killxbmc
```
  GNU nano 2.0.9                                                File: killxbmc                                                                                                      

#!/bin/bash
kill -9 `pidof xbmc.bin` && rm ~/xbmc_crashlog*

```

---

### Post by Locutus_of_Borg on 2010-01-14
```

#!/bin/bash
app=`pidof xbmc.bin`
kill -9 $app && rm ~/xbmc_crashlog*

```

---

### Post by zeezam on 2010-01-14
> **Locutus_of_Borg said:**
> ```

#!/bin/bash
app=`pidof xbmc.bin`
kill -9 $app && rm ~/xbmc_crashlog*

```

Still got this;

~$ ./killxbmc
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

---

### Post by Locutus_of_Borg on 2010-01-15
odd, i tested it before i posted to make sure it worked, and it did on my system

is there a particular reason you dont want to use ```
killall -9 xbmc.bin
```

---

### Post by zeezam on 2010-01-15
> **Locutus_of_Borg said:**
> odd, i tested it before i posted to make sure it worked, and it did on my system

is there a particular reason you dont want to use ```
killall -9 xbmc.bin
```

Maybe it doesn't mather...

---

### Post by rnerwein on 2010-01-15
hi 
i think the only matter of the printed out the usage of the kill command is that no pid is given.
that means your application is not running. try ps -ef | grep xbmc.bin (and check out the owner of this proceses
ciao

---

### Post by k64 on 2010-01-15
> **zeezam said:**
> Works fine but when i put it in a script it fails.

./killxbmc 
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

killxbmc
```
  GNU nano 2.0.9                                                File: killxbmc                                                                                                      

#!/bin/bash
kill -9 `pidof xbmc.bin` && rm ~/xbmc_crashlog*

```

Try using killall instead of kill. It certainly will help.

---

### Post by zeezam on 2010-01-17
> **rnerwein said:**
> hi 
i think the only matter of the printed out the usage of the kill command is that no pid is given.
that means your application is not running. try ps -ef | grep xbmc.bin (and check out the owner of this proceses
ciao

$ ps -ef | grep xbmc.bin
xbmc      6628  6620 21 03:40 ?        01:54:08 /usr/share/xbmc/xbmc.bin
xbmc      8349  8321  0 12:21 pts/0    00:00:00 grep --color=auto xbmc.bin

---

### Post by Locutus_of_Borg on 2010-01-17
just use

killall -9 xbmc.bin 

in the script

---

### Post by zeezam on 2010-01-19
> **Locutus_of_Borg said:**
> just use

killall -9 xbmc.bin 

in the script

Works fine.

---

