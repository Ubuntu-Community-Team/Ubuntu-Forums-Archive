---
title: "TTY is autologged as root?"
date: 2012-03-03
forum: General Help
---

### Post by Kdar on 2012-03-03
How can I disable tty being autologged as root?

On one system, whenever I go to tty (ALT+F1.. etc) it comes up right away as root@system#..... It never asks me for username or password.

How can I disable this? Do you think it somewhere in bashrc?
I want it to ask me for username and password like it usually does.

---

### Post by raja.genupula on 2012-03-03
this is a positive guide 
[http://linux.koolsolutions.com/2009/04/30/autologin-linux-console-mode/](http://linux.koolsolutions.com/2009/04/30/autologin-linux-console-mode/)

read it you gonna know what you have to do reversely ,
but take care while doing . 

all the best .

---

### Post by Diametric on 2012-03-04
How the hell does that happen?  Did you change any config files...that makes me worried.

---

### Post by duncan12 on 2012-03-04
You can't really follow a guide in reverse when that guide says to install a package and configure it... if you never installed any packages to replace your TTY in the first place.

I don't know the answer, but that is SO random. Wouldn't the password have to be stored somewhere in plain text for this to be theoretically possible though? Perhaps search your filesystem for your root password:

I think ```
grep "password" *
``````
(grep PATTERN FILE, * meaning all files)
``` does that job.

However I could be wrong about both those things, I'm no expert.


EDIT: I think that grep command only does your home folder - maybe ```
cd /
``` then the command will work.

---

### Post by Diametric on 2012-03-04
I wish I could contribute more to this issue - but the grep command doesn't yield anything...and I'm not sure it would despite the OP's problem.  


Hmmm...gonna search on this...see what I can find.

---

### Post by Kdar on 2012-03-05
Sorry, to clarify its not exactly a vanilla ubuntu, but a linaro ubuntu built for Pandaboard platform (arm).

I was able to solve autologging as root, but I have another problem. 

On every tty, there are constantly a stream of kernel messages and also, tty1 is not responding, I can't quarry a prompt or logging request. 

I tried fix constant streak of kernel messages by changing /proc/sys/kernel/prink from "15 1 1 7" to "4 1 1 7", but it goes back on reboot.

---

### Post by matt_symes on 2012-03-05
Hi

> **Kdar said:**
> Sorry, to clarify its not exactly a vanilla ubuntu, but a linaro ubuntu built for Pandaboard platform (arm).

I was able to solve autologging as root, but I have another problem. 

Spill the beans ;) How did you fix it ?

> On every tty, there are constantly a stream of kernel messages and also, tty1 is not responding, I can't quarry a prompt or logging request. 

I tried fix constant streak of kernel messages by changing /proc/sys/kernel/prink from "15 1 1 7" to "14 1 1 7", but it goes back on reboot.

Take a look at

```
sysctl
```

and its configuration files.

```
matthew@matthew-Aspire-7540:~$ sysctl -a 2> /dev/null | grep printk 
kernel.printk = 4       4       1       7
kernel.printk_ratelimit = 5
kernel.printk_ratelimit_burst = 10
kernel.printk_delay = 0
matthew@matthew-Aspire-7540:~$ 
```

Kind regards

---

### Post by Kdar on 2012-03-06
There some some script file in /etc/init/auto-serial-console.conf
I don't why they put it there. It was calling another script to log-in as root, I believe it was something to do with getty. I will check later when I will be right next to the system.

@matt_symes
Thanks, I will try this tonight.

---

### Post by matt_symes on 2012-03-06
Hi

> @matt_symes
Thanks, I will try this tonight.

Read through the man pages for sysctl and look at the file ```
/etc/sysctl.conf
```

Kind regards

---

### Post by Kdar on 2012-03-06
Correction to my last post, I was trying to change /proc/sys/kernel/prink from "15 1 1 7" to "4 1 1 7"

Today, I changed sysctl.conf with printk settings (4 1 1 7).
However, it never keeps them on reboot. I have to do sysctl -p to activate them.

I was reading somewhere that sysctl.conf is called before some of those settings can be applied. I am wondering how could I run it again second time to apply printk changes?

---

