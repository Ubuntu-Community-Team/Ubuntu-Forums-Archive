---
title: "Deleting Ubuntu"
date: 2012-02-07
forum: General Help
---

### Post by AFoolInTheRain on 2012-02-07
Is this article accurate and complete, or is there anything else I should know. Do any of you know a better/easier way?

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by oldos2er on 2012-02-07
Yes, restore Windows' boot loader first before deleting anything. Once you've done this, you can safely delete and/or format any Linux partitions.

---

### Post by AFoolInTheRain on 2012-02-07
To clarify, Are you suggesting something different than the article? 

Your suggested plan is to:

[LIST]
[*]Run the Windows recovery disk to reinstall the Windows boot loader.
[*]Then restart and boot into windows.
[*]Then delete the linux partitions from Windows.
[/LIST]
Thats it?

---

### Post by oldos2er on 2012-02-07
Yes.

---

### Post by AFoolInTheRain on 2012-02-08
Did some more research and am finding two problems.

1st: I do not have a Win 7 install disc, only recovery media created form the old recovery partition.

2nd: I have a 64-bit machine, and I have seen some things about the fixmbr command not being supported by 64bit machines.

Thoughts?

---

### Post by Mark Phelps on 2012-02-08
Read through the info below.  You may be able to use Boot-Repair to restore the Windows MBR:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

