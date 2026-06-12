---
title: "Nice to be nice??? O.o"
date: 2011-05-22
forum: General Help
---

### Post by cayphed on 2011-05-22
I'm still a bit "fresh" to all this but just recently my 10.04 install has been lagging terribly, so I took a quick look and it appear sthat cpu load is at nice 100% and occasionally the user gets a touch of load but this "nice" stuff is drinking up the rest...
It is very frustrating to say the least...

Any pointers on how to find the probblem to start with will be great....

---

### Post by Nerotriple6 on 2011-05-22
The nice value determines the priority of a thread (process). The higher the nice value the lower the priority (a lower priority process is nicer to the rest of them).

If you didn't change the nice values yourself you shouldn't have lag.. So here are some questions I hope you can answer in order for us to understand what is causing the lag.

What processor unit (CPU) do you have?
Have you updated 10.04 via the Update Manager?
What processes are having these high CPU loads you are describing?

If you don't know how to determine which processes that are having these CPU loads, can you open a Terminal window and type the following inside it?
```
top
```
Then press enter and it will list a bunch of information such as the top processes. With that window open can you then press *Print Screen* to take a screenshot of it and upload that to put in a post in this thread?
That way we can see the processes, **but preferably just list the most resource hungry processes.**

To stop monitoring press "q" in the terminal window or just close it.

---

### Post by cayphed on 2011-05-22
I only ever update via the update manager, cause I'm to scared to break something, lolz,
As I went back into Ubuntu (dual-boot) I also noticed my HDD light is solid on now when previously it 
would occasionly flicker.
See attached screenshot.
Ty for your help on this, it's slowly getting more frustrating to use ubuntu at the moment
due to the lag....
And yes it did just take nearly an hour to boot up run those two tasks in screen shot and shut-down,
previously did all this in seconds not minutes....

---

### Post by hawthornso23 on 2011-05-22
0.0%id - that means zero percent idle! You've got a problem alright. SOMETHING is chewing up your cpu. Damned if I can see what it is though. And rebooting doesn't fix it?

---

### Post by cayphed on 2011-05-22
Nah, rebooting fixes sqwat.... I just don't know where to look.... :'(

---

### Post by zarquod on 2011-05-22
> **cayphed said:**
> As I went back into Ubuntu (dual-boot) I also noticed my HDD light is solid on now when previously it would occasionly flicker.

That sounds as if your HDD bus is having trouble. Check the cables, something may have come loose.

And remember to make backups. That might as well be a sign of a more serious hardware issue.

---

### Post by cayphed on 2011-05-22
> **zarquod said:**
> That sounds as if your HDD bus is having trouble. Check the cables, something may have come loose.

And remember to make backups. That might as well be a sign of a more serious hardware issue.
 
But it's in a "snap-in" laptop and windows doesn't have the issue, ubuntu didn't either till nearly a week ago....

---

