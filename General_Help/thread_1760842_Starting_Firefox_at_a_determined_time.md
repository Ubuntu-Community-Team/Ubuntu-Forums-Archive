---
title: "Starting Firefox at a determined time"
date: 2011-05-17
forum: General Help
---

### Post by ChuckVanT on 2011-05-17
I want to launch Firefox at a different time every day, and send it to a landmarked page, not my home page.

Is there a relatively simple way to automate this?



Thanks in advance,
Chuck

---

### Post by WorMzy on 2011-05-17
crontab is your friend here.

```
man crontab
```

```
              # MIN HOUR DAY MONTH DAYOFWEEK  COMMAND
              # run `date` at 6:10 am every day
              10 6 * * * date

```

As for launching a specific page, you just need to pass the address to firefox like so:

```
firefox www.website.com
```

---

### Post by hwttdz on 2011-05-17
Also you might have to put an "export DISPLAY=:0.0" before you put your firefox command in there.  

i.e.
0 7 * * * export DISPLAY=:0.0 && firefox ubuntuforums.org

---

