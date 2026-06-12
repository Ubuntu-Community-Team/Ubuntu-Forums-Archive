---
title: "restarting from windows into ubuntu always detects unclean shutdown"
date: 2009-12-14
forum: General Help
---

### Post by morganpatrick on 2009-12-14
hi,

when i boot into windows and then reboot and go to linux, it always says the shutdown was unclean and checks the drives.

I have my linux /home partition mapped in windows and am accessing it from there.

---

### Post by zeroseven0183 on 2009-12-15
I assume this is a Windows issue and not Linux. Anyway, you should run 
fsutil dirty query <drive>
chkntfs /x <drive>
chkdsk /f /r <drive>

Hope that helps. If not, better search forums about Windows.

---

