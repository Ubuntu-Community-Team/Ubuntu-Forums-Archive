---
title: "Problems Running Cups from Command Line"
date: 2010-12-23
forum: General Help
---

### Post by syedr on 2010-12-23
I need some help desperately, and would appreciate a quick response.

To begin, here's the output from 'uname -a' for the machine I'm using:

Linux ubuntu 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64 GNU/Linux

Now, when I start my computer, cupsd is running:

$ ps aux | grep "cups"
root       879  0.1  0.9  76908  4588 ?        Ss   14:42   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf

I then stop cups server:
$ sudo initctl stop cups
cups stop/waiting

I can now confirm cups is not running:

$ ps aux | grep "cups"
syed      1933  0.0  0.1  11332   876 pts/0    S+   14:49   0:00 grep --color=auto cups

Now, if I try to run cupsd from the command line:
$ sudo /usr/sbin/cupsd -C /etc/cups/cupsd.conf

Then, the terminal window is shut down immediately (same thing happens with screen).

However, when I open up a new terminal and query for whether cups is running, I see that it is indeed running:
$ ps aux | grep "cups"
root      1941  0.0  0.9  81960  4544 ?        S    14:50   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf

Now, I know cups can be started via initctl but I need to run it from the command line, without the process crashing. I'm doing this because I want to dynamically instrument cups using Pin.

I would really appreciate any help!

---

### Post by AlphaLexman on 2010-12-23
From the man page:
```
If  no  options  are
       specified  on  the  command-line  then  the  default configuration file
       /etc/cups/cupsd.conf will be used.
```
> **syedr said:**
> Now, if I try to run cupsd from the command line:
$ sudo /usr/sbin/cupsd [COLOR="Red"]-C[/COLOR] /etc/cups/cupsd.conf

should be:
```
$ sudo /usr/sbin/cupsd [COLOR="Red"]-c[/COLOR] /etc/cups/cupsd.conf
```

---

### Post by syedr on 2010-12-23
Thanks that fixed it.
 
Also, I needed the "-f" flag so that the service keeps running in the foreground -- this way, I can instrument it as it runs.

---

