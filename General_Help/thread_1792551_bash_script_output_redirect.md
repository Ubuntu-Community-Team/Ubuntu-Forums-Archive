---
title: "bash script output redirect"
date: 2011-06-28
forum: General Help
---

### Post by maclenin on 2011-06-28
Hello!

I have a single "backup.sh" script containing multiple rsync commands:

```
#!/bin/bash

echo $(date)

#data
rsync -avrP ~/data/ /backup/data/

#media
rsync -avrP ~/media/ /backup/media/

#email
rsync -avrP ~/email/ /backup/email/

read

exit
```

What I am trying to do, specifically, is place a command **INSIDE** the script, itself, to direct the (sequential) output of all 3 rsync commands (as well as echo $(date)) to BOTH the terminal and a (date-stamped) log file - something akin to:
```
tee backup_log_`date +"%m%d%Y_%H%M"`
```
...which (when incorporated - in various ways - into the script - without "|") directs output to the terminal **BUT** generates an **EMPTY** date-stamped log file.

**or**

```
> backup_log_`date +"%m%d%Y_%H%M"`
```
...which (when incorporated - in various ways - into the script) closes the terminal and generates an **EMPTY** date-stamped log file.

I have toyed with adding "> backup_log" (and ">> backup_log")  or "tee backup_log" etc after each command - however, this struck me as inefficient.

I have constructed this line...
```
$ ./backup.sh | tee backup_log_`date +"%m%d%Y_%H%M"`
```
...in the terminal - and within a desktop launcher (though I could not get the date stamp to work from the launcher, using **sh -c**), to yield what I am trying to yield (i.e. output to **BOTH** terminal and (dated) log). However, I'd rather have this functionality incorporated into the script, itself - if feasible....

It seems I need some kind of "collect / consolidate / redirect the output of multiple commands from within a bash script" insight! Perhaps there is a bash "function" into which I could gather the commands and from which I could collect the output (sort of javascript-esque)?

Thanks for any guidance!

---

### Post by eric3_14159 on 2011-07-24
You are, in fact, correct. There is a way to "collect / consolidate / redirect the output of multiple commands from within a bash script".

Putting () around any bash commands will consolidate all of their output. You can easily test this out on the terminal, if you try running
```
(date; echo hello, world) > output
```
You will see that both the output of date and "hello, world" are in the file output.

You can put "(" on the first line of the shell script and ") > [your output stuff]", and it should do what you want.

I hope this helps, and that this response isn't too late to be useful!

---

### Post by maclenin on 2011-07-25
Thanks, **eric3_14159**, for the insight! New knowledge is never late, it arrives precisely when it means to!  I had a couple of threads running - relatedly and simultaneously - and went, ultimately, with a start-up log_script, which launched the backup.sh | tee'd to the log + date "("to capture any and all output from the backup.sh") > see [here]("http://ubuntuforums.org/showthread.php?t=1793228")".

---

