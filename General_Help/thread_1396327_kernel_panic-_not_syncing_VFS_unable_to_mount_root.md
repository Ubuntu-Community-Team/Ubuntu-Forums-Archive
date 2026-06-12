---
title: "kernel panic- not syncing VFS: unable to mount root fs on unknown block (8,1)"
date: 2010-02-01
forum: General Help
---

### Post by mdg83 on 2010-02-01
I'm very much a newbie... I'm using Ubuntu 9.10 through Windows 7 and got this message today...

kernel panic- not syncing VFS: unable to mount root fs on unknown block (8,1) 

Is there a way to fix this? (and I'm going to need really simple instructions here)

Also I tried to uninstall ubuntu in windows 7 and then reinstall but it will not let me. it says that an error has occurred: The system cannot find the file specified stdout=


can someone help in as simple language as possible? thank you

---

### Post by macsdev on 2010-02-01
I understand you have installed wubi on Windows. Did Ubuntu do a Kernel Upgrade recently? I'm pretty sure it did. I had the same problem. Check this link and follow the instructions in the post : [http://ubuntuforums.org/showpost.php?p=8639088&postcount=79](http://ubuntuforums.org/showpost.php?p=8639088&postcount=79)

---

### Post by mdg83 on 2010-02-02
Thank you, this is very helpful except but it says to "copy it over C:\wubildr" and I don't know how to do that? Im sure its very simple I just don't know how to do this. could someone walk me through step by step in windows 7

---

### Post by macsdev on 2010-02-02
> **hhh81 said:**
> 

"For a patch/workaround:

A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding

New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated."

**Download the file from the given link and Paste it in your C: drive. There should be a file by the name wubildr already. Just Overwrite it.**

---

### Post by GromEx on 2010-02-06
Thank you! The advice was really very helpful! I was able to restore Ubuntu with the help of new [wubildr]("https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90").

I'm running Ubuntu 9.10 with wubi on Windows XP SP3.

---

