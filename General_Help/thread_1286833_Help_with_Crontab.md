---
title: "Help with Crontab"
date: 2009-10-09
forum: General Help
---

### Post by CharlesA on 2009-10-09
I read the howto [here]("https://help.ubuntu.com/community/CronHowto") and [here]("http://ubuntuforums.org/There%20is%20also%20an%20operator%20which%20some%20extended%20versions%20of%20cron%20support,%20the%20slash%20%28%27/%27%29%20operator,%20which%20can%20be%20used%20to%20skip%20a%20given%20number%20of%20values.%20For%20example,%20%22*/3%22%20in%20the%20hour%20time%20field%20is%20equivalent%20to%20%220,3,6,9,12,15,18,21%22;%20%22*%22%20specifies%20%27every%20hour%27%20but%20the%20%22/3%22%20means%20that%20only%20the%20first,%20fourth,%20seventh...and%20such%20values%20given%20by%20%22*%22%20are%20used.").

I'm trying to get a scripts set to run at 1 hour intervals using cron.

my crontab file:
* */1 * * * ~/rsync

I'm obviously doing something wrong, since the rsync script runs every minute and I am not sure how to fix it so that it runs every hour.

Any assistance is welcome, my google-fu is failing to give me anything other then howtos (and none of them show how to set it up as an hourly task) :(

---

### Post by hwttdz on 2009-10-09
[http://en.wikipedia.org/wiki/Cron#crontab_syntax](http://en.wikipedia.org/wiki/Cron#crontab_syntax)

If you want to run every hour it makes most sense to pick a minute (such as the zeroth minute) and do
0 * * * (whatever)

What's happening for yours is that it evaluates that the hour is divisible by 1, and then it runs it every minute during an hour when the hour is divisible by one (which is every hour, so it runs it every minute of every hour).

---

### Post by CharlesA on 2009-10-09
> **hwttdz said:**
> [http://en.wikipedia.org/wiki/Cron#crontab_syntax](http://en.wikipedia.org/wiki/Cron#crontab_syntax)

If you want to run every hour it makes most sense to pick a minute (such as the zeroth minute) and do
0 * * * (whatever)

What's happening for yours is that it evaluates that the hour is divisible by 1, and then it runs it every minute during an hour when the hour is divisible by one (which is every hour, so it runs it every minute of every hour).

Thanks. I'm curious if it's possible to set it up to send every 3 hours by using:
0 */3 * * * (whatnever)

---

### Post by hwttdz on 2009-10-09
I suppose so, I had never seen this step (/) functionality before.  The other alternative is to list times, 0,3,6,9,12,15,18,21, but I guess the step is more elegant and easier to change if you want to switch from every 3 to every 4.

---

### Post by CharlesA on 2009-10-09
Thanks for the info. I'll try it out. :)

EDIT: Yup, it worked.

---

