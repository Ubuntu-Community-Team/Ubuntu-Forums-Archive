---
title: "crontab question"
date: 2010-07-14
forum: General Help
---

### Post by Cyked on 2010-07-14
If I use the following for crontab -e what does it do?

```

# m h  dom mon dow   command
* 15 * * 3 /etc/scripts/rename.sh

```

I assumed, and thought it was, running the sh file every Wednesday at 3.

Does it continue to run the whole 15:00 through 15:59 how ever often cron is actually going off?

I feel like I'm seeing different behavior from this.  Am I just crazy?

---

### Post by tgm4883 on 2010-07-14
It runs it every minute from 3:00 to 3:59 on every wednesday

You probably want
```
# m h  dom mon dow   command
0 15 * * 3 /etc/scripts/rename.sh
```

---

### Post by Cyked on 2010-07-14
> **tgm4883 said:**
> It runs it every minute from 3:00 to 3:59 on every wednesday

You probably want
```
# m h  dom mon dow   command
0 15 * * 3 /etc/scripts/rename.sh
```


[Yeah.]("http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/")

lol.  Thanks.  Sorry... I have an 8 week old.  Comprehension is a blessing at this point.:D

---

### Post by sgosnell on 2010-07-14
That says to run it every minute, which is what the asterisk calls for.  Use a zero instead.  At least that's my understanding of it.

Too late.  Slow connection.

---

