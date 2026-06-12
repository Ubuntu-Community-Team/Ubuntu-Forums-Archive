---
title: "Shutdown in progress query"
date: 2012-05-10
forum: General Help
---

### Post by rhdinah on 2012-05-10
Is there anyway from the CLI to query whether a shutdown is in progress or not? Or possibly more information as to how much time is left before shutdown occurs? Thanks!

[other than the possible periodic message to users that shutdown is imminent]

---

### Post by sudodus on 2012-05-10
> **rhdinah said:**
> Is there anyway from the CLI to query whether a shutdown is in progress or not? Or possibly more information as to how much time is left before shutdown occurs? Thanks!

[other than the possible periodic message to users that shutdown is imminent]
Why do you want this information? If there is a shutdown command issued, which is waiting a number of minutes or until a certain wall-clock time, it can be cancelled using
```
sudo shutdown -c
```

---

### Post by sudodus on 2012-05-10
I got curious and issued
```
sudo shutdown 23:00
```
which can be found with this command
```
ps -AF|grep shutdown
``` which in my case printed
```
root      3055  3001  0   937   984   0 18:34 pts/1    00:00:00 shutdown 23:00
``` (and another line for grep shutdown)

Hence I can see that shutdown is scheduled to happen at 11 pm. Is this what you want?

---

### Post by rhdinah on 2012-05-10
> **sudodus said:**
> I got curious and issued
```
sudo shutdown 23:00
```
which can be found with this command
```
ps -AF|grep shutdown
``` which in my case printed
```
root      3055  3001  0   937   984   0 18:34 pts/1    00:00:00 shutdown 23:00
``` (and another line for grep shutdown)

Hence I can see that shutdown is scheduled to happen at 11 pm. Is this what you want?

Your grep idea is good ... from my unix days I typically use ps -ef :)

Why would I want to use it? I have a control application that can schedule a machine shutdown automatically ... and I need to see what shutdown time it has determined.

Thanks!

---

