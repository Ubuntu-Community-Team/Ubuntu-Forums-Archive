---
title: "deleted partition, need help to restore"
date: 2010-02-02
forum: General Help
---

### Post by dlworth on 2010-02-02
I have read several answers to this question, but none seem to fit quite right. I am a NOOB and do not quite know my way with all of the commands or lingo for that matter, so I do request that any answers be directed to an 80 year old with minimal exp. 

I had installed a dual boot (vista/karmic) on my machine all was well until I was dealing with an external disk and wiped the partitions on my internal. Trying to boot, I get a grub loading error : no such partition. I have a working cd/dvd and a live cd. Could someone please explain the steps to replace the grub to the MBR without loosing the data on my drive. The "ls" command gives the response (hd0).

Thank you in advance, I'll start begging next, that is not a pretty picture.

---

### Post by bakegoodz on 2010-02-02
The easiest way to fix Grub is with the Super Grub bootdisk
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

They have some good documentation and examples that may help
[http://www.supergrubdisk.org/wiki/Boot_Problems#README_FIRST](http://www.supergrubdisk.org/wiki/Boot_Problems#README_FIRST)

---

### Post by audiomick on 2010-02-02
I think that more than Grub is gone.

Look here.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by dlworth on 2010-02-03
Ok, I will not have to beg!!! I created a bootable disc of SystemRescue and ran Testdisk. The program found my missing partitions and gave me the location of each. Sadly, the program was not able to restore all of my partitions, but was able to return the NTFS boot partition. 

Attempting to boot the computer, I received an error message saying windows was not able to load due to a corrupt boot system. I simply placed my Vista repair disk in and in no time I had Vista up and running with no loss of data. 

I am still working on getting the dual boot back, but since I already had all my Ubuntu data backed up that will be as simple as a reinstall.

Thank you audiomick, even though your reply had me worried about my data, you put me in a direction that I had not looked. Thank you.

---

