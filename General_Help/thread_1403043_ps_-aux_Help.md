---
title: "ps -aux Help"
date: 2010-02-09
forum: General Help
---

### Post by skeeterxb on 2010-02-09
Question for anyone who might know a way of doing this. I am looking for help in usin a command which will allow me to evaluate the performance. What i would also like to do is compare the performance over 30 minute intervals. I am thinking i can use the ps -aux command but not sure on how i would specify the time intervals. Is there another way? I really want to see the CPU, disk usuage and memory. Thanks in advance to anyone who can offer guidance. 
 
-Tim

---

### Post by jamesisin on 2010-02-09
You could pipe the output from ps into a file and run that script periodically using cron.

---

### Post by skeeterxb on 2010-02-09
Hmm interesting.  Which command/script would you recommend to return the CPU/Memory and disk usage.  New to this as you can probably tell.

---

### Post by jamesisin on 2010-02-09
Well df is good for disc usage:

```
df -h
```

You can trim the information coming from that output by using another command called awk and of course grep.

(The -h option gives usage in human readable numbers.)

For example compare the output from the above to this one:

```
df -h | grep '/dev/sd' | awk '{print $3}'
```

---

### Post by x33a on 2010-02-09
try the following commands
```
uptime
free
df -h
```

---

### Post by skeeterxb on 2010-02-09
Thank you the info on the df command was useful.  Just seems like there has to be one command to get all this data (disk usage, cpu and memory).  What about vmstat, i believe i read something where you can specify a time for the command to run, do you have any experience with this?   Getting the data is one goal with the other being to run the command in 30 minute increments to produce a 6 to 12 hour report on all the data to compare the detail.  Thanks in advance, as i am very new at this any detailed explaination is well recieved.

---

### Post by jamesisin on 2010-02-09
Take a look.  You can run vmstat and see the output.  No danger there.

If there is something in it you find useful, you can follow my instructions above (with some modifications) to parse out the bits that interest you most.

Same goes for ps (I use ps -waxf usually).

Finally, you can put all of these into a single script (run periodically with cron) to get a nice report.

---

### Post by jamesisin on 2010-02-09
You can also take a look at this conversation I had concerning how to best use cron:

[http://ubuntuforums.org/showthread.php?t=1366759](http://ubuntuforums.org/showthread.php?t=1366759)

---

### Post by skeeterxb on 2010-02-10
Is there anyway i could get you to help me with such a script, i am new to these.

---

### Post by x33a on 2010-02-10
first decide which command you want to use. Then we'll help you make your script.

---

