---
title: "cut command"
date: 2010-03-09
forum: General Help
---

### Post by ryanf4321 on 2010-03-09
I'm trying to find a way to cut just one line out of the 3 of 4 lines of the "w" commands output. I know you can use this "w | cut -c45-48 | tail -1" to display the last line, or use "head" to display the first line, but to display just one of the middle lines, how can I do that?

Thanks!

---

### Post by lyall on 2010-03-09
> **ryanf4321 said:**
> I'm trying to find a way to cut just one line out of the 3 of 4 lines of the "w" commands output. I know you can use this "w | cut -c45-48 | tail -1" to display the last line, or use "head" to display the first line, but to display just one of the middle lines, how can I do that?

Thanks!

see following link for VI commands
it should how you
[http://ss64.com/bash/vi.html]("http://ss64.com/bash/vi.html")

if it does not do a Google search for **VI commands**

in Vi editor you can use
1dd

good luck and have fun learning

---

### Post by ryanf4321 on 2010-03-09
So i'm kinda new to linux, but do i download vi (or vim) or how do i use it? I really only need to do this for a few scripts or so.

---

### Post by bodhi.zazen on 2010-03-10
You have a number of tools available, grep ?

```
w | grep <search_parameter>
```

Hard to give specific advice, what are you wanting to display exactly ?

> w | grep pts/0
bodhi    pts/0    :0.0             Mon23    0.00s  0.25s  0.01s w

---

### Post by ryanf4321 on 2010-03-10
i am trying to get the idle time from each of the following lines:

22:41:42 up  1:32,  3 users,  load average: 0.02, 0.02, 0.03
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rfinni   tty7     :0               21:10    6:32m  5:35   0.28s gnome-session
rfinni   pts/0    :0.0             22:04    4:38   0.37s  0.00s nano number3.sh
rfinni   pts/1    :0.0             22:05    0.00s  0.33s  0.01s w

i know you can use cut to get just the idle time column, and head or tail to get the first or last line, but how do i get just the middle line?

---

### Post by FreezWay on 2010-03-10
count the spaces and pipe it through awk '{print $(number of spaces)}'

---

### Post by dcstar on 2010-03-10
> **ryanf4321 said:**
> i am trying to get the idle time from each of the following lines:

22:41:42 up  1:32,  3 users,  load average: 0.02, 0.02, 0.03
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
rfinni   tty7     :0               21:10    6:32m  5:35   0.28s gnome-session
rfinni   pts/0    :0.0             22:04    4:38   0.37s  0.00s nano number3.sh
rfinni   pts/1    :0.0             22:05    0.00s  0.33s  0.01s w

i know you can use cut to get just the idle time column, and head or tail to get the first or last line, but how do i get just the middle line?

```
w | tail -n3 | cut -b 44-50
```

---

### Post by gmargo on 2010-03-10
Use **tail -n +3** to skip the first two lines.
```
w | tail -n +3 | awk '{ print $5; }'
```

---

### Post by Grenage on 2010-03-10
> 1dd

I think the 1 is superfluous, you only need dd for a single line.

---

