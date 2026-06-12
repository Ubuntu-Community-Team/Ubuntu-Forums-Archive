---
title: "sudo: no valid sudoers sources found, quitting"
date: 2010-02-16
forum: General Help
---

### Post by SagnaB on 2010-02-16
Ok I think I my have just screwed things up...
I wanted the CPU frequency scaling monitor (2.28.0) to not ask for password every single time i changed it from 600MHz to 1.70 GHz. So I googled a bit and found a site that said adding to the sudoers file:
```

$ sudo cpufreq-set -g Performance

```would fix this.

So, I opened a terminal and entered:
```

sudo visudo

```to open the sudoers file. This was successful as it displayed the sudoers files contents in the terminal.
I then proceeded to enter ```
$ sudo cpufreq-set -g Performance
```then i typed exit and it prompted me to save the file as sudoers.tmp. I did not save it as that as I believed that would not work. I saved over the existing sudoers file by saving it just as ´sudoers´. Hit return, and it exited.

I then wanted to check to see if the changes did indeed happen and reopened the sudoers file with
```
sudo visudo
```And now it says:
```

>>> /etc/sudoers: syntax error near line 26 <<<
sudo: parse error in /etc/sudoers near line 26
sudo: no valid sudoers sources found, quitting

```If i reboot, will this cause me the gigantic problem I am anticipating? What on Earth can I do now?

---

### Post by SagnaB on 2010-02-16
I now realize that I cannot use sudo at all. I have seriously messed this up. I don´t have to do a full reinstall do i? For I fear that a mere reboot will show the effects in full
ie: inability to login.

May I have some help with this? I&#7743; sorry to seem naggy. This is my college laptop, that I only really use for word processing, but I need it this week for all year.

Sincerest thanks in advance.

---

### Post by MinimalBin on 2010-02-16
Boot into *recovery mode* and reconfigure / reinstall *sudo*.

---

### Post by anaconda on 2010-02-16
yep.
Edit the sudoesr file from 
recovery mode or liveCD, whichever you prefer.

---

### Post by SagnaB on 2010-02-18
Ahh cool. Thanks heaps guys :) A very simple solution indeed. 

I find it puzzling that there is so much help, support and advice for Linux, particularly Ubuntu and it is free. Where as I would fork out several hundred dollars for, say, Windows, and there doesn´t seem to be the same level of assistance. One would assume that the ´paid for´ operating system would offer greater assistance at the end user level.
Curious.

---

### Post by rnerwein on 2010-02-18
> **SagnaB said:**
> Ahh cool. Thanks heaps guys :) A very simple solution indeed. 

I find it puzzling that there is so much help, support and advice for Linux, particularly Ubuntu and it is free. Where as I would fork out several hundred dollars for, say, Windows, and there doesn´t seem to be the same level of assistance. One would assume that the ´paid for´ operating system would offer greater assistance at the end user level.
Curious.

hi
you can use sudoers for your behavior in the following matter.
insert at the last !!! line ( it must be the last line or it is overwritten by the 
admin rule).

your_user_name ALL=NOPASSWD: your_command

in my sudoers i get:
my_user_name ALL=NOPASSWD: /bin/bash,/usr/sbin/accton

it works as designed.
ciao

---

### Post by malocchius on 2010-05-06
I had the same problem, but I solved it by running:
```
su
```then running:
```
export EDITOR=gedit && sudo visudo

```After making the necessary changes I ran
```
export EDITOR=gedit && sudo visudo -c

```To check that the file parsed OK.

I hope this helps anyone else who might have been playing Russian roulette with the /etc/sudoers.d folder too...

---

### Post by demvin on 2011-07-24
I have also a problem with this...I created a file in the sudoers.d directory but due to an error in the file, it won't parse.  Now I can't sudo and the server is at the other end of the world, so a bit harder to boot into recovery mode...

I wish sudo would ignore files in sudoers.d with parse error...

---

