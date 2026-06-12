---
title: "Question about CPU affinity..."
date: 2009-12-18
forum: General Help
---

### Post by Falkor on 2009-12-18
Hi, I have a question about using taskset.

For my Ubuntu 9.04 x86_64, I am using Core 2 Quad box. I set the default affinity to CPU 0, by doing the following:

Edit:         [COLOR=RoyalBlue]/etc/rc.d/rc.sysinit[/COLOR]
Addline:    [COLOR=RoyalBlue]/bin/taskset -p 1 0[/COLOR]

(By the way, 0 for CPU 0, correct? I checked via htop and seemed to be correct)

That has been working fine for me, but from searching the web, I found some suggestion about adding an additional line:

                [COLOR=RoyalBlue]/bin/taskset -p 1 $$[/COLOR]

What does that line do?

I checked the man page of taskset and some references for regular expression, and I couldn't find the explanation about the $ character.


Any pointer would be appreciated. :KS

---

### Post by pbrane on 2009-12-18
I don't understand why you are setting the process with PID 1 to use only one core. The *-p* option tells taskset to operate on the process with that PID. You can run **man taskset** in a terminal to see the options. The $$ is probably used in a script.

 What are you trying to do?

---

### Post by dcstar on 2009-12-18
I thought that OS kernel designers deliberately tried to spread any CPU workload across all available cores for a lot of very good reasons - one being balancing any thermal stress as evenly as possible across a CPU die.

I don't see a lot of advantage to forcing one small part of a CPU to possibly run hotter or colder than it is supposed to, it can't do much good to the chip.

---

### Post by pbrane on 2009-12-18
dcstar:
Most apps aren't SMP aware and don't utilize multiple cores. However because of "core hopping" it can be beneficial to "lock" a task on one core. For instance I play bzflag and core hopping will cause timing issues.

---

### Post by Falkor on 2009-12-18
Hi pbrane & dcstar,

Thanks for your replies.

For my home server (CentOS 5.4 x86_64) and my web server (Ubuntu 9.04 x86_64), I don't need that.

I am doing this for my game server, which is for hosting Counter-Strike: Source.

The game doesn't use multi-core. Before I set the CPU affinity, the instance of game server would just jump from one core to another, but didn't use more than one, and I did experience an occasional lag.

As this box doesn't run anything else, I tried setting CPU affinity as the following, and I am getting a better real-life performance.

I currently have them as:

< game server #1 > core 1
< game server #2 > core 2
< game server #3 > core 3

and I would like to set init (PID 1), to use core 0 as default.

---

### Post by Falkor on 2009-12-18
Most suggestions I have read disagree about using taskset to lock the process to a fixed core, and yet from my own experience, for Counter-Strike: Source (or any app that doesn't use multi-core), setting CPU affinity does help.

> **pbrane said:**
> dcstar:
... core hopping will cause timing issues.

So is that the reason of the improvement that I am getting? :KS

---

### Post by pbrane on 2009-12-20
Falkor:
Sorry for not getting back to you sooner, but yes I think thats the reason. I understand that each core has it's own timing registers ( TSC ) and they aren't necessarily sync'd so switching back and forth seems to cause issues on most networked games, most of which rely on some sort of constant sync'd timing source.

---

### Post by Falkor on 2009-12-21
pbrane,

No problem, and thanks for coming back to my question. :P

Regarding the $$, instead of for some custom script, according to the man page of bash that I read, it is some process ID.

([3.7.3 Command Execution Environment]("http://www.gnu.org/software/bash/manual/bashref.html"))

([3.4.2 Special Parameters]("http://www.faqs.org/docs/bashman/bashref_25.html#SEC25"))

I don't know what it does exactly, but I will post it once I have found out.

---

### Post by pbrane on 2009-12-22
if I run **echo $$** in a terminal it returns the current shell ( bash ) PID.

```

~$ echo $$
**3502**
~$ ps u 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
me        **3502**  2.5  0.2  22264  5020 pts/0    Ss   14:58   0:00 /bin/bash -l

```

---

### Post by Falkor on 2009-12-22
pbrane,

From your result, I double-checked the Bash reference manual again, and according to this:

> **5.2 Bash Variables** ([link]("http://www.gnu.org/software/bash/manual/bashref.html#Bash-Variables"))

BASH
- The full pathname used to execute the current instance of Bash.

BASHPID
-  Expands to the process id of the current Bash process. This differs from $$ under certain circumstances, such as subshells that do not require Bash to be re-initialized.
Thus $$ is referring to the Bash shell.


Thank you very much for your help. I think I got all my questions answered. :guitar:

---

