---
title: "temporarily fail to use ssh with &quot;connection refused&quot; error returned"
date: 2012-03-30
forum: General Help
---

### Post by bijune on 2012-03-30
Hi, people

Days ago, I can use ssh quite normally. But recently (I am not sure from when on or from which operation), I temporarily get "connection refused" message by calling ssh. 

Several hours ago, I connect to another computer in the local area network by ssh, but now ssh terminal stops to respond, and I cannot ssh the computer with "ssh: connect to host **** port 22: Connection refused" message. Meanwhile I can successfully ping the computer.
After a period (like one hour), I can connect the computer with ssh again.

This problem occurs recently frequently, I am wondering what should be the possible reasons?

Thanks a lot!

June

---

### Post by Krazi3 on 2012-03-30
I think maybe some other app. or software is using your port 22.

Try shutting down extra software using the internet or intranet and then try again.

---

### Post by bijune on 2012-03-30
thanks, Krazi3.

at the same time another application using port 8890 also cannot be accessed. it appears that applications using different ports fails at the same time I tend not to think it is a port occupation problem~

---

