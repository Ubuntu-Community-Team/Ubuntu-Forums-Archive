---
title: "Just updated to 10.04, wtf is this &amp; how do i get rid of it?"
date: 2010-06-10
forum: General Help
---

### Post by Radamand on 2010-06-10
[SIZE="5"]Its some kind of 'search' box, but it wont go away!  its right in the center of my screen and i cant seem to get rid of it.[/SIZE]


[IMG]http://img39.imageshack.us/img39/2568/thingks.jpg[/IMG]

---

### Post by ThesaurusRex on 2010-06-10
I've never seen that grotesque magnifying glass in my life. Did you try typing something to make it go away? Or, maybe do something like:

```
ps
```

Try to find that search box, then:

```
kill [pid]
```

Where [pid] is the pid of the search box.

---

### Post by grindboy on 2010-06-10
That is GnomeDO. You can stop it from popping up by clicking the dropdown arrow then settings and finally unticking the option to have it run at startup/login.

---

### Post by BoneKracker on 2010-06-10
That's _bloatware_, that's what that is.

---

### Post by Radamand on 2010-06-10
> **grindboy said:**
> That is GnomeDO. You can stop it from popping up by clicking the dropdown arrow then settings and finally unticking the option to have it run at startup/login.

Normally I would agree with you, but i've tried that, clicking the dropdown thingy does nothing...

i've seen this thing before (before i updated to 10.04), but i never had it stick on the screen before. i'll try to find the process and kill it, hopefully i can find it in the startup sequence...

UPDATE: Thanks Grindboy, now that I know what the stupid thing is called I was able to kill the process and remove it from the startup sequence!

---

### Post by grindboy on 2010-06-10
Glad I could help

---

