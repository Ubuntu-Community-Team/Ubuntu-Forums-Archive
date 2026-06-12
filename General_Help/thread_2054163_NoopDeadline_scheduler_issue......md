---
title: "Noop/Deadline scheduler issue....."
date: 2012-09-06
forum: General Help
---

### Post by xillius200 on 2012-09-06
I got myself an SSD a while back and want to use it's full potential on linux. However whenever I try to use noop/deadline rather than CFQ the system actually runs slower and gradually over an hour of use starts to lag really bad.....however with CFQ i have 0 issues but I want to use noop/deadline. Has anyone else had thi problem or can help me solve this issue?? :/

---

### Post by Bobhuber on 2012-09-06
> **xillius200 said:**
> I got myself an SSD a while back and want to use it's full potential on linux. However whenever I try to use noop/deadline rather than CFQ the system actually runs slower and gradually over an hour of use starts to lag really bad.....however with CFQ i have 0 issues but I want to use noop/deadline. Has anyone else had thi problem or can help me solve this issue?? :/
Use noop . Where did you put the command ?  Put the following command at the end of /etc/rc.local before the exit 0 command. I assume you left the file system as ext4 and still have a swap partition.
echo noop > /sys/block/sda/queue/scheduler

---

### Post by xillius200 on 2012-09-07
> **Bobhuber said:**
> Use noop . Where did you put the command ?  Put the following command at the end of /etc/rc.local before the exit 0 command. I assume you left the file system as ext4 and still have a swap partition.
echo noop > /sys/block/sda/queue/scheduler

I think you have either not bothered to read my post fully or you have misunderstood.....

---

### Post by Bobhuber on 2012-09-07
> **xillius200 said:**
> I think you have either not bothered to read my post fully or you have misunderstood.....
I read your post and fully understand what you are saying. There is a reason the system is slowing after an hour of use and my guess is that it has nothing to do with the scheduler.
However if you feel that you don't need or want help by supplying a bit more information that is your prerogative.
Have a nice day.

---

### Post by xillius200 on 2012-09-07
> **Bobhuber said:**
> I read your post and fully understand what you are saying. There is a reason the system is slowing after an hour of use and my guess is that it has nothing to do with the scheduler.
However if you feel that you don't need or want help by supplying a bit more information that is your prerogative.
Have a nice day.

I have already tested the system over a long period of time and the system only slows when I change scheduler of which if I leave it on CFQ I get 0 issues. Maybe it is something else however what you were telling me was how to enable noop of which I already know....so how exactly was that an answer which helps me, when it will just begin to slow down my system and cause issues again?? I just came to the conclusion thats its the scheduler when testing in many different cases with a brand new or old installation of ubuntu of any variant runs perfect until I choose noop or deadline scheduler of which the system begins to slow after an hour of use. However when using CFQ I can use the computer with no issues of slowing after an hour and no issues of anything. I tested this on a clean installation with and without updates along with 4 different kernel versions and it only happens when I use noop or deadline scheduler. If I go and use another scheduler. As you say something else could be at play however what you told me to do was irrelevant and wouldn't help at all!! 

Seems deadline was just a kernel issue with the one which came installed updated kernel thats fixed. However noop is still have the same issue like with all other kernels and all other variants I have tried.

Cba anymore just gonna stick thread as solved and be done and over with it.

---

