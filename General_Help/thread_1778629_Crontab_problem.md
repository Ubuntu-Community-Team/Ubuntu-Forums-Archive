---
title: "Crontab problem"
date: 2011-06-09
forum: General Help
---

### Post by Krauser Joestar on 2011-06-09
Hey there everyone


So, what am i doing wrong here?


> # m h  dom mon dow   command
  */1 *  *    *   *     ls -l /home/username
Just wanted to do a simple ls action on my home directory every single minute. I've done with just * and still nothing.


Thanks in advance.

---

### Post by ExileAmongYou on 2011-06-09
What are you expecting to happen? What are you trying to achieve with this command?

---

### Post by Krauser Joestar on 2011-06-09
> **ExileAmongYou said:**
> What are you expecting to happen? What are you trying to achieve with this command?

Isn't it obvious that i'm trying to list all the directories of my home folder? Or am i missing something here?


I'll put here the steps


> $ crontab -e
then i add the line that is shown on the first post, and i save it. Just this.


I wonder if i have to do this on the /etc/crontab file. I've tried and it doesn't work too but i'm most likely doing something wrong.

---

### Post by Dave_L on 2011-06-09
You need to save the output somewhere:

```
*/1 * * * * ls -l /home/username >>/home/username/crontest.log
```

---

### Post by Krauser Joestar on 2011-06-09
> **Dave_L said:**
> You need to save the output somewhere:

```
*/1 * * * * ls -l /home/username >>/home/username/crontest.log
```


I was doing that right now actually and it worked.

Thank you guys.


Also, while we're on it, what's the difference between a new crontab file and the /etc/crontab one? Of course, i mean aside the descriptions of each column.

---

### Post by ExileAmongYou on 2011-06-09
> **Krauser Joestar said:**
> Isn't it obvious that i'm trying to list all the directories of my home folder? Or am i missing something here?

Yeah sorry, I did understand what the command was doing, I just wasn't sure where you were expecting the output to turn up. Glad you figured it out!

---

