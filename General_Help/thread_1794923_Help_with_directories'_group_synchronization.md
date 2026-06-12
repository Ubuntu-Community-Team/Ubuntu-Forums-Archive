---
title: "Help with directories' group synchronization"
date: 2011-07-01
forum: General Help
---

### Post by kyselejsyrecek on 2011-07-01
Hello,

I have just changed by mistake the group of all files and directories matching the pattern /* and /*/* to 'root'.

I am not able now to log in after the screensaver locks my screen (logging in at system startup works fine) and I assume that this is not the only bad thing that happened by this horrible mistake that I've made.

I have another computer running the same Ubuntu version (11.04) and I tried to synchronize the group permissions of those directories using unison, however, it has fairly difficult interface and I'm not able to tell it that I do not want to synchronize subdirectories, just the previous two levels (/* and /*/*).. the command that I have used was:

sudo unison -group -ignore "Path */*" / ssh://root@192.168.1.2/../

Could anyone please help me synchronizing group permissions of /* and /*/* files back?

Thank you very much!

---

