---
title: "Insane CPU usage for enabling a Network Printer!?!?"
date: 2009-10-21
forum: General Help
---

### Post by Lauxmonster on 2009-10-21
This is more of a comment rather than a question, but if anyone knows the answer, I would appreciate it.

----

Today, I saw going through my "Network" that my network printer which I was having trouble connecting showed up as a Samba device. So, I took the SMB:// address and went to the "Printing" menu and setup my printer. Well, it works...and it prints fine.

But almost immediately after I did this, my CPU fan starting whirring up...and it started reaching higher and higher RPMs...to the point where I got worried. So, I checked System Monitor and sure enough, there was the good old Pentium 4 2.4GHz at a whopping 98% CPU utilization.

So, I went to the processes list, and I saw nothing that exceed more than 5% CPU utilzation yet, the resources tab showed that the System was hogging the entire CPU. 

I ran in Terminal:

```
top
```

The user "lp" was using a tremendous amount of resources with a process called cifmp520. I know cifs is a network protocol thing, and mp520 is a name of a canon printer. So, I just killed the printer under the "Printing" menu and the CPU dropped to around 20%. 

I have no idea why this did this. Is this common, or did I mess up something. Any ideas. Thanks.

---

