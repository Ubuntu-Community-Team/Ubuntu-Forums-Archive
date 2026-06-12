---
title: "strange wget behavior bash script"
date: 2010-09-04
forum: General Help
---

### Post by _Robertico_ on 2010-09-04
I created a script to download some iso files.

This is the script:

```
#!/bin/bash
lynx -dump http://www.mydownloadsite.com/Downloads.htm | egrep -o http://www.mydownloadsite.com/images/iso_.*[A-Z].iso | xargs -n1 wget -d -P ~/Downloads/ISO/ -U¨
```Everytime i run this script wget starts downloading the first iso but hangs after downloading about 2% (not everytime the same amount of bytes).

When is use the same wget commandline directly, everything goes fine. Checked the download in different ways, but server sided everything seems ok.

When running script as root, same behavior.

---

### Post by _Robertico_ on 2010-09-05
Fixed.

---

### Post by limestone on 2010-09-05
It would be super if you posted your answer for others with same issue.
And mark the thread as solved.

---

