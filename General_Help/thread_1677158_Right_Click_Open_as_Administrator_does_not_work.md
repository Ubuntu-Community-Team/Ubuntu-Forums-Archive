---
title: "Right Click Open as Administrator does not work"
date: 2011-01-28
forum: General Help
---

### Post by wah fun on 2011-01-28
Strange. After a recent update, I can no longer right click on a folder and open it as Administrator. I get this error message: 

Unable to determine the program to run.

The item you selected cannot be open with administrator powers because the correct application cannot be determined.

I don't quite get this but why is it looking for a program to run? I only want to open a folder, not run a program.  Anyway, I have done an uninstall and re-install of nautilus-gksu but that did not solve the problem. I have googled but no answers I could use.

Again, all I want to do is open a folder as Administrator so I can perform other operations that require root permission on files in that folder.

using: 10.04 LTS fully updated

thx

---

### Post by Cjaster on 2011-01-28
I don't even get a Open As Administration option. I just do:
sudo -i
enter the password
preform operations from the terminal

---

### Post by Joeb454 on 2011-01-28
If you need to perform root actions in a folder through nautilus, you could run the following from either a terminal, or Alt+F2 prompt

```
gksu nautilus /path/to/folder
```

---

### Post by drs305 on 2011-02-24
I stumbled upon this thread while looking for any reports of nautilus-gksu failure. I am experiencing the same issue. 

I've gone into an older Maverick VM, installed all the updates and nautilus-gksu still works. My VM is relatively bare-bones, so there must be a conflict with something I've added or altered on my production system.

If I can isolate the cause I'll report back here and file a bug report.

---

### Post by chaoticist on 2011-05-08
I am also now experiencing this problem. I can not right click to open as administrator, nor can I use gksu nautilus /path/to/folder. The error message I get is: "No protocol specifiedCould not parse arguments: Cannot open display:"

I discovered this problem when I was trying to install a new truetype font.

---

