---
title: "It doesn't show or block stuff in MoBlock on my live USB"
date: 2011-01-12
forum: General Help
---

### Post by anti-other on 2011-01-12
Hey, what's up. After some difficulty I got MoBlock and Mobloquer installed on my Ubuntu 10.10 live USB. Lists all updated perfectly, and I made sure that HTTP and FTP traffic are _not_ allowed. All's going well, still it shows **nothing** under the "Logs" tab, and under the "Manage" tab, "Number of blocked connections: " is still 0. MoBlock is "up and running". Now I did some browsing as a test, cuz I'm pretty used to Peer Guardian on Windows, and I know that by now it should have blocked quite a lot of stuff.    :confused: Should I have "No time stamping" checked, cuz in the "Blockcontrol log", whilst struggling to get it working, it said that "notimestamp" was a depreciated feature.. or some thing like that anyway. It still shows nothing under the "Logs" tab, and it shows "no blocked connections under the "Manage" tab still.
Some help would be super appreciated!! Thank you!!  ^_^

---

### Post by jre on 2011-01-14
... seems you solved your problem already, anyway: using the "notimestamp" option is just a no-op now. It neither harms nore helps.
For a test just issue the command
```
blockcontrol test
```

---

