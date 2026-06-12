---
title: "Which logs?"
date: 2011-05-09
forum: General Help
---

### Post by norm.h on 2011-05-09
"Which logs should I read to try to establish the cause of a crash?"

---

### Post by howefield on 2011-05-09
What type of crash ?

Depending on your version of Ubuntu, you probably have System > Administration > Log File Viewer available, an easy way of accessing and reading your logs. You could start with dmesg.

---

### Post by norm.h on 2011-05-09
> **howefield said:**
> What type of crash ?

Depending on your version of Ubuntu, you probably have System > Administration > Log File Viewer available, an easy way of accessing and reading your logs. You could start with dmesg.

Complete lock-up, requiring reboot from reset button.
Running Ubuntu 10.10, and have found Log File Viewer.
Will check later. Many thanks.

---

### Post by drazoro on 2011-05-09
> **norm.h said:**
> "Which logs should I read to try to establish the cause of a crash?"

If you would prepare an interactive log view I will recommend you try the following :
$sudo tail -f /var/log/syslog  
[OR]
$sudo tail -f | dmesg 

I am assuming that you are using 11.04.

---

### Post by norm.h on 2011-05-09
> **drazoro said:**
> If you would prepare an interactive log view I will recommend you try the following :
$sudo tail -f /var/log/syslog  OR]   $sudo tail -f | dmesg 
I am assuming that you are using 11.04.

Not sure what you mean by an "interactive log view".
I'm running 10.10.
The crash happened on May 7th, so I don't know how to run your suggested commands for that date.

When I booted today, the machine failed to get further than a completely black / blank screen.
Rebooting via the reset button worked fine.

---

