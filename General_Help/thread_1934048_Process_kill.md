---
title: "Process kill"
date: 2012-03-01
forum: General Help
---

### Post by Diametric on 2012-03-01
Hi,

I cannot for the life of me remember the command that lists process such that you can enter in a number to kill it while the list updates.

Anyone?

Thanks!

---

### Post by imachavel on 2012-03-01
ps aux | less

[http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/](http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/)

mine shows:


USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   3324  1912 ?        Ss   11:58   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    11:58   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    11:58   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    11:58   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    11:58   0:00 [migration/1]
root         9  0.0  0.0      0     0 ?        S    11:58   0:00 [ksoftirqd/1]
root        10  0.0  0.0      0     0 ?        S    11:58   0:00 [kworker/0:1]
root        11  0.0  0.0      0     0 ?        S<   11:58   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S<   11:58   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S<   11:58   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    11:58   0:00 [kworker/u:1]
root        15  0.0  0.0      0     0 ?        S    11:58   0:00 [sync_supers]
root        16  0.0  0.0      0     0 ?        S    11:58   0:00 [bdi-default]
root        17  0.0  0.0      0     0 ?        S<   11:58   0:00 [kintegrityd]
root        18  0.0  0.0      0     0 ?        S<   11:58   0:00 [kblockd]
root        19  0.0  0.0      0     0 ?        S<   11:58   0:00 [ata_sff]
root        20  0.0  0.0      0     0 ?        S    11:58   0:00 [khubd]
root        21  0.0  0.0      0     0 ?        S<   11:58   0:00 [md]
root        22  0.0  0.0      0     0 ?        S    11:58   0:00 [kworker/1:1]
root        23  0.0  0.0      0     0 ?        S    11:58   0:00 [khungtaskd]
root        24  0.2  0.0      0     0 ?        S    11:58   0:02 [kswapd0]
root        25  0.0  0.0      0     0 ?        SN   11:58   0:00 [ksmd]

---

### Post by howefield on 2012-03-01
pidof processname

---

### Post by Dave_L on 2012-03-01
> I cannot for the life of me remember the command that lists process such that you can enter in a number to kill it while the list updates.

You may be thinking of "top". When "top" is running, if you type "k", you'll be prompted with "PID to kill:".

"htop" is similar, but might not be installed by default.

---

### Post by Diametric on 2012-03-01
Thanks for both of the replies, but the command I'm looking for is an interactive one.  When the command is entered an updating list of processes is listed and there is an option to type in a process ID to kill a given process.  Kind of like a 

```
tail -f /var/log/logfile
```

But is interactive like I described.  

Does that make sense?

Cheers.

---

### Post by Diametric on 2012-03-01
> **Dave_L said:**
> You may be thinking of "top". When "top" is running, if you type "k", you'll be prompted with "PID to kill:".

"htop" is similar, but might not be installed by default.

That is exactly it!  Thank you so much - that was killing me.

Cheers!

---

### Post by Khayyam on 2012-03-01
... zsh can complete on 'kill'

```
% zstyle ':completion:*:*:kill:*:processes' list-colors '=(#b) #([0-9]#)*=0=01;31'
% kill <tab>
---- process ID
 [COLOR=DarkRed]9038[/COLOR] pts/2    0:00.40 -zsh
 [COLOR=DarkRed]9144[/COLOR] pts/2    0:00.11 vim notes.txt
 [COLOR=DarkRed]9166[/COLOR] pts/2    0:01.23 -zsh                         
 [COLOR=DarkRed]9394[/COLOR] pts/2    0:00.07 ssh host.domain.tld                                           
 [COLOR=DarkRed]9475[/COLOR] pts/2    0:00.00 -zsh
[COLOR=DarkRed] 9501[/COLOR] pts/2    0:00.05 mutt
```best ... khay

---

