---
title: "Windows XP problem after powered off during defrag"
date: 2009-12-22
forum: General Help
---

### Post by welshmike on 2009-12-22
Firstly my wife's laptop can still boot and run Ubuntu 9.10 OK.
It has dual boot Ubuntu 9.10 and Windows XP.
XP was running slowly and I set XP to defrag the Windows partition.
My wife turned the laptop off during defrag and now XP insists on doing a Chkdsk as start up. Chkdsk looks like it is continually "Inserting an index entry into index £0 of file 25" and is not completing. I can only get control by turning off the laptop. On reboot of XP I can escape Chkdsk but when XP comes up and I try to defrag the XP partition it refuses and insists that a Chkdsk must be done.

Is there a way I can use Ubuntu to fix the XP problem please?
I'm reluctant to have to reinstall XP as it will probably screw the MBR and I won't then be able to boot Ubuntu.

As additional tools I have an Ubuntu 9.10 install CD and also a USB pen drive from which I can run Ubuntu 9.10 netbook remix live.

---

### Post by synapsys on 2009-12-22
I would try booting into the XP recovery console from the XP cd.

Then type 

```
chkdsk /r
```See what happens....

PS: might take awhile....grab a coffee.....

---

### Post by welshmike on 2009-12-22
Thanks very much synapsys.
I should have known that but am trying to forget about Microsoft and learn about Ubuntu. I'm currently watching chkdsk /r running on the Recovery Console - it paused at to 25% complete for a while now pausing at 52% complete. So I'm hoping it will be 100% complete soon.

Typed on my own PC & not my wife's PC (of course).

Mike

---

