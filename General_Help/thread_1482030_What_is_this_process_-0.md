---
title: "What is this process: -:0"
date: 2010-05-13
forum: General Help
---

### Post by burneverything on 2010-05-13
Hello,

just saw this in htop, in the command column it only says:
-:0
and it belongs to root, what is it?

Running 8.04 minimal install + lxde desktop

Thanks for reading

---

### Post by Rubi1200 on 2010-05-13
If possible, take a screenshot and post it to the forum; would help us figure it out.
Thanks.

---

### Post by burneverything on 2010-05-13
> **Rubi1200 said:**
> If possible, take a screenshot and post it to the forum; would help us figure it out.
Thanks.

Here is one attached

---

### Post by Rubi1200 on 2010-05-13
Ok, so you might want to start by running this command:

lsof -u root

to see what files are associated with this.

Also ps aux # may provide some info.

pstree will show if there are other processes associated with this one.

Hope this helps.

---

### Post by scorp123 on 2010-05-13
> **burneverything said:**
> Hello,

just saw this in htop, in the command column it only says:
-:0
and it belongs to root, what is it?

":0" usually stands for the X11 server (the stuff that ultimately makes up the GUI). You should enable "Tree" listing in 'htop' so you can see what process spawned which other process. This gives way better output.

Or what you can also do: ```
ps -efH
```
... and then check what that output says about the same process ID and who spawned it.

---

### Post by burneverything on 2010-05-13
Ok I used the tree view and it is indeed to do with X, it was spawned by Xdm.
I'd just never noticed it before and searches returned absolutely no results.

Thanks

---

### Post by scorp123 on 2010-05-13
> **burneverything said:**
> it was spawned by Xdm. And now for some background info: You see, there is no limit why there should be only one XDM / GDM / KDM login screen and only one GUI environment running at the same time. Yes, usually and especially with desktop users there will indeed be one and only one at the same time. But in theory you could be running several desktop sessions at once ... so the first one would be ":0" (counting starts at 0), then there could be a ":1", a ":2" and so on. That's where those numbers come from. .... just in case you wondered :)

---

### Post by burneverything on 2010-05-14
Thanks for the background info.
Guess I'll have to read the fine manual to actually work out how to get more than one session of X to run concurrently as when I've tried to do this flying blind "computer says no.."

---

