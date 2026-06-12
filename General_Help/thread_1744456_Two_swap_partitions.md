---
title: "Two swap partitions"
date: 2011-04-30
forum: General Help
---

### Post by sant on 2011-04-30
I have replaced Lucid by Natty using this option during installation:  erase only previous Ubuntu Lucid installation and put Natty instead.
The installation resulted into two swap partitions. The installer ignored my swap partition and created a new one shrinking my root partition.
Has anyone had the same problem ?. I have found [this bug report in Launchpad]("https://bugs.launchpad.net/installation-report/+bug/763783") .

---

### Post by rfry11 on 2011-04-30
The installer really isn't perfect, and its automated tasks seem to lean more heavily on the most basic cases, such as people who ONLY have Ubuntu installed. 

What you should do is just format it all yourself in the installation instead of having Ubuntu do it for you, so that you can make sure it's not touching your Windows partition and adequately deleting and restoring partitions. 

Also, I remember reading somewhere that it's best to delete and redo the swap partition every time you install a new Linux OS, but I really don't know why. Just something I read.

---

### Post by MrRichard on 2011-04-30
I manually created Natty's partition, so I didn't have this problem. 

Do you need help fixing this problem?

---

### Post by sant on 2011-04-30
Thank you for your answers and for your help, the problem is fixed.
I have deleted "old" swap partition and I have made */home*[I] partition bigger
[/I]

---

