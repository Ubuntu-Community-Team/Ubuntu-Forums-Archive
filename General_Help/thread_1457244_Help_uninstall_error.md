---
title: "Help uninstall error"
date: 2010-04-18
forum: General Help
---

### Post by mogey5101 on 2010-04-18
I keep on receiving this error when i uninstall Ubuntu, [URL="http://mogeyq.co.cc/other/wubi-9.10ubuntu1-rev160log.txt"]log file is linked.
[/URL]

---

### Post by Kai Summers on 2010-04-18
OK from what I can see in the log there is a file that the task list is expecting that does not exsist anymore. The easiest fix for this would be to place the bcdedit.exe file back in C:\Windows\sysnative\. Try that, hopefully that will work as a quick fix. If it is just trying to delete the file and not call any commands from it then a blank text file renamed to bcdedit.exe should work to fool the task list into thinking that it has deleted the file.

---

### Post by mogey5101 on 2010-04-18
Thanks it has been solved.

---

### Post by mogey5101 on 2010-04-18
Actually that fix didn't work either.

---

