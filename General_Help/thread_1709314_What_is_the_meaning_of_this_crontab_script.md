---
title: "What is the meaning of this crontab script?"
date: 2011-03-18
forum: General Help
---

### Post by zcrself on 2011-03-18
```

[SIZE=4]*/30 * * * * /bin/sh /root/shell/rm_xdebug_out.sh[/SIZE]

```
 
[SIZE=4]I don't know what is the [COLOR=Blue]*/30[/COLOR] ?[/SIZE]
[SIZE=4]Can anyone help me?[/SIZE]

---

### Post by WorMzy on 2011-03-18
That specifies that you want the job to run once every 30 minutes.

---

### Post by prshah on 2011-03-18
> **zcrself said:**
>  
what is the [COLOR=Blue]*/30[/COLOR]
```

$ crontab -l
# m h dom mon dow command 
0 * * * * /home/user/telltime.sh
30 * * * * ./telltime.sh 
```

The time columns in the crontab are (in order) minutes, hours, day-of-month, day-of-week.

In the above example, a script to tell the time is run every half an hour.

---

### Post by zcrself on 2011-03-20
> **prshah said:**
> ```

$ crontab -l
# m h dom mon dow command 
0 * * * * /home/user/telltime.sh
30 * * * * ./telltime.sh 
```
 
The time columns in the crontab are (in order) minutes, hours, day-of-month, day-of-week.
 
In the above example, a script to tell the time is run every half an hour.
 Thanks!

---

### Post by zcrself on 2011-03-20
> **WorMzy said:**
> That specifies that you want the job to run once every 30 minutes.
 Thanks !

---

