---
title: "schedule tasks for the 3rd friday of every month"
date: 2010-07-19
forum: General Help
---

### Post by projkt4 on 2010-07-19
I'm trying to run some jobs on the 3rd friday of every month. Unfortunately cron by itself will not allow me to dictate relative times for scheduled tasks. I found quartz with it's crontrigger cron expressions, allowing me to run something like this; "0 15 10 ? * 6#3"	to allow me to fire off @ 10.15am on the 3rd friday of every month. I've installed libquartz onto my test machine but I have no idea how to activate it. Any help?






source:
[http://docs.netkernel.org/book/view/book:mod:cron/doc:mod:cron:cronexpression](http://docs.netkernel.org/book/view/book:mod:cron/doc:mod:cron:cronexpression)

[http://www.quartz-scheduler.org/docs/tutorials/crontrigger.html](http://www.quartz-scheduler.org/docs/tutorials/crontrigger.html)

---

### Post by rubylaser on 2010-07-19
Cron can do exactly what you want, you just need to feed it input from date.  This is should work just fine and give you the third Friday of every month.

```
# m h  dom mon dow   command
15 10 * * * [ `date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1 | cut -d ' ' -f 6` ] && jobs.sh
```

No need to use anything other than built in commands :)

Hope that helps

---

### Post by projkt4 on 2010-07-19
Thank you! Can you explain some of this context? i get the first standard part of the cron job, but could you explain the part in the brackets? I'll be needing to replicate this bur for other times like the 2nd Tuesday, etc.

> **rubylaser said:**
> Cron can do exactly what you want, you just need to feed it input from date.  This is should work just fine and give you the third Friday of every month.

```
# m h  dom mon dow   command
15 10 * * * [ `date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1 | cut -d ' ' -f 6` ] && jobs.sh
```

No need to use anything other than built in commands :)

Hope that helps

---

### Post by rubylaser on 2010-07-19
Sure, this looks really complicated, but is really doing nothing fancy (I just realized that I had a typo). Here's the fixed version...

```
# m h  dom mon dow   command
15 10 * * *[ `date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1 | cut -d ' ' -f 6` ] && jobs.sh
```

The first part of the cron job is just the time minutes followed by hours, so 10:15 in this case.
Then the last part, meaning this *[ `date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1 | cut -d ' ' -f 6` ] basically will result in *<number of the third Friday>.  This just takes the date command, turns it into a calendar for the month, selects the correct line, then selects the 6th item (Friday) and outputs the number. (If you want to see how it works, just run these commands individually.)

Here's a sample.
```
&#10140;  Desktop  date
Mon Jul 19 15:27:51 EDT 2010
&#10140;  Desktop  date '+%m %y'
07 10
&#10140;  Desktop  date '+%m %y' | cal
     July 2010
Su Mo Tu We Th Fr Sa
             1  2  3
 4  5  6  7  8  9 10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30 31

&#10140;  Desktop  date '+%m %y' | cal | egrep '([0-9]+ +){1}'
             1  2  3
 4  5  6  7  8  9 10
11 12 13 14 15 16 17
18 19 20 21 22 23 24
25 26 27 28 29 30 31
&#10140;  Desktop   date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1
11 12 13 14 15 16 17
&#10140;  Desktop  date '+%m %y' | cal | egrep '([0-9]+ +){1}' | head -n 3 | tail -n 1 | cut -d ' ' -f 6
16
```

Finally, it will run your jobs.sh command.  Hopefully, that helps you understand how it works.

---

### Post by projkt4 on 2010-07-19
ok, cool. That makes a lot of sense. What happens though if I'm looking for say the 2nd monday of the month and the month starts on a Tuesday. By the logic of your script, wouldn't it actually select the first Monday of the month because the first Monday would be on the second line of the month? Or am I missing something? I really appreciate you explaining the rest of your script to me.

---

### Post by rubylaser on 2010-07-19
Well, I was just trying to find a quick example to solve your problem, that will fall apart without more work for different scenarios, so why don't you just do something like this instead?

```
15 10 * * 1 [ `date +\%e` -gt 8 -a `date +\%e` -lt 14 ] && jobs.sh
```

You'll need to calculate the viable date range for the specific day, and week of the month, but this will run every 2nd Monday at 10:15.  Hope that helps.

---

### Post by nitrogoldfish on 2010-07-19
rubylaser: your condition will return false if the 2nd Tuesday happens to be the 8th or 14th. Use ge and le instead to return true if the parameters are equal. Also, I would recommend referring to the day of week by name instead of number. This is easier to read, and you never have to try to remember which day 0 refers to.

I believe it would be a lot simpler to solve this problem by specifying a range of days to cron. 10:15AM on the 2nd Tuesday of each month would look like this:
```

#minute, hour, day of month, month, day of week, command
15       10    8-14          *      tue          jobs.sh

```

Similarly, the 3rd Friday of the month would look like this:
```

#minute, hour, day of month, month, day of week, command
15       10    15-21         *      fri          jobs.sh

```

Hope this helps

---

### Post by rubylaser on 2010-07-20
Now, that's a good answer, and easy to read.  Thanks for posting that.

---

### Post by projkt4 on 2010-07-20
Nirtofish, rubylaser; thank you both. I now have a solution i can replicate, but more importantly I know how it works. The ubuntu community is lucky to have you both.

---

