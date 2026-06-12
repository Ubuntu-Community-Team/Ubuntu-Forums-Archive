---
title: "running parallel jobs on a single machine"
date: 2010-11-19
forum: General Help
---

### Post by vivien_yan on 2010-11-19
Hi, I have a ubuntu 9.10 on a Dell Precision Workstation. Since I have 8 cores (dual quad), I'm wondering how I can run parallel jobs on the machine without opening multiple terminals manually. 

For example, I have job1.bat, job2. bat, ..., job7.bat, I want to run them on 7 of the 8 cores. Because I have to run these jobs (with a little bit different settings) for multiple times, I don't want to open 7 different terminals and run the jobs manually. 

Does anyone know of any ways to solve this problem? Thanks!

---

### Post by JohnElway on 2010-11-19
I'm not entirely sure I understand your question but I'll offer up some info anyway. Are you interested in running these scripts in the background? You can just use '&' for that.

Example: job1.bat & job2.bat & job3.bat ...etc

This will cause all the scripts to run simultaneously as opposed to running one after the other finishes. Or are you just interested in running multiple bash sessions within one terminal window? For that you can use 'screen' which is popular with users who like terminals. Info on that here: [http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-](http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-)

Apologies if this isn't the info you're looking for.

---

### Post by sohlinux on 2010-11-19
do you mean you want to assign a single processor core to a specific task? if so then you can use taskset

if you don't already have it you can get it - sudo apt-get install schedutils

---

### Post by vivien_yan on 2010-11-19
I think running in the background is exactly what I'm looking for. 

I am currently using screen. But I'm tired of switching to different screens to check whether the jobs are done.

Thank you very much! 

> **JohnElway said:**
> I'm not entirely sure I understand your question but I'll offer up some info anyway. Are you interested in running these scripts in the background? You can just use '&' for that.

Example: job1.bat & job2.bat & job3.bat ...etc

This will cause all the scripts to run simultaneously as opposed to running one after the other finishes. Or are you just interested in running multiple bash sessions within one terminal window? For that you can use 'screen' which is popular with users who like terminals. Info on that here: [http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-](http://www.linux.com/learn/tutorials/285795-taking-command-of-the-terminal-with-gnu-screen-)

Apologies if this isn't the info you're looking for.

---

### Post by vivien_yan on 2010-11-19
I'll check on that too.

Thank you! 

> **sohlinux said:**
> do you mean you want to assign a single processor core to a specific task? if so then you can use taskset

if you don't already have it you can get it - sudo apt-get install schedutils

---

### Post by pietjanjaap on 2010-12-06
GNU parallel

---

