---
title: "grep doesn't work in a simple cron job"
date: 2011-01-22
forum: General Help
---

### Post by cerist on 2011-01-22
Hello,

I have a problem with grep in my cron job: 
a simple command like this doesn't work
```

#!/bin/bash

source /home/cerist/.profile
ifconfig wlan0 | grep "inet adr" > /home/cerist/Documents/p.txt

```

Of corse I have tried with full path like this
```

#!/bin/bash

source /home/cerist/.profile
/sbin/ifconfig wlan0 | /bin/grep "inet adr" > /home/cerist/Documents/p.txt

```

Both of this scripts work fine when started from my shell. Unfortunately they don't work when executed from cron job, and I get an empty p.txt file.

Here is my crontab file:
```
*/1 * * * * bash /home/cerist/Documents/test.sh
```

Have any one of you faced this kind of problem before ?

Thank you in advance.

---

### Post by dcottingham on 2011-01-22
I suspect "inet adr" is a typo, and "inet addr" would work better.

---

### Post by dcstar on 2011-01-22
> **cerist said:**
> 
..........
Here is my crontab file:
```
*/1 * * * * **bash** /home/cerist/Documents/test.sh
```


Why is that there?

---

### Post by Cheesehead on 2011-01-23
Works great when I tried it:
```
#Crontab test line
* * * * * /sbin/ifconfig wlan0 | /bin/grep "inet addr" > /tmp/test.txt

# Result
$ cat /tmp/test.txt
          inet addr:192.168.12.190  Bcast:192.168.12.237  Mask:255.255.255.0

```

- You don't need to export your .profile if you are doing simple text and file manipulations. But it doesn't hurt in this case either.
- There is nothing wrong with your basic commands or syntax. But you might have a simple misspelling somewhere.

- Do you have other cron jobs? Do test cron jobs or other cron jobs work?
- Are you using the 'crontab -e' command to edit your crontab?

---

