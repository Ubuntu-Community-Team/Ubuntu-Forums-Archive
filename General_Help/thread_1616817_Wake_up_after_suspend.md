---
title: "Wake up after suspend"
date: 2010-11-08
forum: General Help
---

### Post by Adnanius on 2010-11-08
I'm trying to create a launcher which should set the wakealarm  date & time for system to wake up from suspend. I would like to use it as an alarm, waking the system the next day at fixed time (7 am). 

I've found the following script, which works flawlessly:
 
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date -d @1289258154` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
```

ONLY problem left, is the date specification, 
the "date -d @1289258154" fixes the date & time in the Epoch format. 

MY QUESTION: how can I specify "next date" & "7 am" with the date command so that I don't have to edit the script everyday!???

Many thanks,

---

### Post by rampageoberon on 2010-11-08
Hi there, would this work for you?

```
sudo sh -c "echo `date --date="$(date -d tomorrow +%D) 07:00"` > /sys/class/rtc/rtc0/wakealarm
```

---

### Post by rampageoberon on 2010-11-08
> **Adnanius said:**
> I'm trying to create a launcher which should set the wakealarm  date & time for system to wake up from suspend. I would like to use it as an alarm, waking the system the next day at fixed time (7 am). 

I've found the following script, which works flawlessly:
 
```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date -d @1289258154` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
```

ONLY problem left, is the date specification, 
the "date -d @1289258154" fixes the date & time in the Epoch format. 

MY QUESTION: how can I specify "next date" & "7 am" with the date command so that I don't have to edit the script everyday!???

Many thanks,

Hmm thinking about it even the following could work:

```
sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
sudo sh -c "echo `date -d "tomorrow 07:00:00"` > /sys/class/rtc/rtc0/wakealarm"
cat /sys/class/rtc/rtc0/wakealarm
```

---

### Post by Adnanius on 2010-11-09
It's awesome!! works like a charm now, many thanks!! 
I'll be using the rythmbox plugin to start the alarm, and now with this script I can schedule the wake up, happy to be an ubuntu user!!

---

