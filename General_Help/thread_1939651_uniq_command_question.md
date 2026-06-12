---
title: "uniq command question"
date: 2012-03-12
forum: General Help
---

### Post by dheerajkabra on 2012-03-12
Hi,
I ma running uniq command on a file called "test.txt" with below content:

```
cron_schedule = 0 * * * *
cron_schedule = 0 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */15 * * * *
cron_schedule = */15 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */15 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = */30 * * * *
cron_schedule = 0 1 * * *
cron_schedule = 0 1 * * *
cron_schedule = 0 1 * * *
cron_schedule = 0 1 * * *
cron_schedule = 0 1 * * *
```


so i run below:

```
cat test | uniq -c
      2 cron_schedule = 0 * * * *
      3 cron_schedule = */30 * * * *
      2 cron_schedule = */15 * * * *
      5 cron_schedule = */30 * * * *
      1 cron_schedule = */15 * * * *
     12 cron_schedule = */30 * * * *
      5 cron_schedule = 0 1 * * *
```


So, my question is, why is showing multiple entries for lines with "*/15" and "*/30". I mean, that's the whole purpose I am using uniq to tell the number of times a particular line repeats.

Please let me know is there something that I am missing here?

thanks.

---

### Post by sudodus on 2012-03-12
Maybe there is some whitespace that is different (trailing blanks, tab instead of blanks etc)

But in this case I think it merges only adjacent lines that are the same. If you sort the lines and then use uniq, it should work

```
cat test | sort | uniq -c
```

---

### Post by dheerajkabra on 2012-03-13
true. It worked for me. Thanks sudodus.

---

### Post by sudodus on 2012-03-13
> **dheerajkabra said:**
> true. It worked for me. Thanks sudodus.
You are welcome :KS
Please click [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and select 'Mark the this thread as SOLVED'

---

