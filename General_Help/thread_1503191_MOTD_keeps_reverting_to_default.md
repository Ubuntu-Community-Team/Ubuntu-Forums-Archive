---
title: "MOTD keeps reverting to default"
date: 2010-06-06
forum: General Help
---

### Post by JockVSJock on 2010-06-06
Greetings, I am setting a customized MOTD, however after 24 hrs, it reverts back to the default MOTD. 

I noticed that it is a softlink 

```

cmmiller@ladytron:/etc$ ls -al | grep motd
lrwxrwxrwx   1 root root         13 2009-07-05 10:47 motd -> /var/run/motd
cmmiller@ladytron:/etc$

```

And I'm making the change to /var/run/motd, however it keeps changing. 

Not sure what is going on here.

---

### Post by sdennie on 2010-06-06
You probably want to change /etc/motd.tail or /etc/motd.  On my debian server, /etc/motd.tail was the file that gave me the results I wanted.

---

### Post by JockVSJock on 2010-06-06
BTW, I forgot to include that I'm running Ubuntu 8.04.  

I don't have a /etc/motd.tail and I've also tried to change /etc/motd and it continues to get overwritten.

---

