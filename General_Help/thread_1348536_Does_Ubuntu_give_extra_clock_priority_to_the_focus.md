---
title: "Does Ubuntu give extra clock priority to the focused application?"
date: 2009-12-07
forum: General Help
---

### Post by Tryfon on 2009-12-07
I was just wondering if the Ubuntu is configured to give some extra priority in processing time to the application which is focused by the user at the time. If not, wouldn't such a feature be a good idea?

---

### Post by Slim Odds on 2009-12-07
> **Tryfon said:**
> I was just wondering if the Ubuntu is configured to give some extra priority in processing time to the application which is focused by the user at the time. If not, wouldn't such a feature be a good idea?

I don't think it's needed. Is there something that you think is actually wrong? If you're an administrator of the machine, you can always change the priority of any application that you like (just be careful).

---

### Post by Tryfon on 2009-12-07
I know that you can do it manually. The question is if it is done automatically. Many times, for example, I am working on firefox and suddenly some other application starts doing something in the background (like extracting for example) and firefox freezes and becomes gray. In this case, and I can think of many more others, I would like the system to act smartly and give some extra processing priority to the application with the focused GUI so that it doesn't freeze.
Does this exist? Would it be a good idea? Is it technically feasible?

---

### Post by Slim Odds on 2009-12-07
> **Tryfon said:**
> I know that you can do it manually. The question is if it is done automatically. Many times, for example, I am working on firefox and suddenly some other application starts doing something in the background (like extracting for example) and firefox freezes and becomes gray. In this case, and I can think of many more others, I would like the system to act smartly and give some extra processing priority to the application with the focused GUI so that it doesn't freeze.
Does this exist? Would it be a good idea? Is it technically feasible?

There is no reason why firefox should be affected that way by another application unless there are other problems (like a bottle neck at the disk I/O). If the problem is disk I/O, extra processing time (changing the CPU priority) on firefox won't get you anywhere.

At some point, all applications are really sharing all the resources on the machine. You might want to take a look at all the resource usage when this problem shows itself to narrow down what the problem really is.

---

