---
title: "Need regex help, tutorials don't show what I need!!"
date: 2010-01-28
forum: General Help
---

### Post by chris_l_13 on 2010-01-28
Hi, I need to grab a text string from ifconfig and save it as a string in a shell script.

I can do:
ifconfig | grep HWaddr

and that will return:
eth0      Link encap:Ethernet  HWaddr 12:31:39:00:e4:c7

But all I want is this line:
12:31:39:00:e4:c7

Which tool should I use and how do I do this?  I know there is awk, grep, sed ...
Tutorials that show up on google only show how to search for the line itself and not return only 1 part of the line.

Thanks in advance!

Cheers,
Chris

---

### Post by sisco311 on 2010-01-28
Hi and welcome to the forums!

Use awk:
```
ifconfig | awk '/HWaddr/{print $NF}'
```

---

