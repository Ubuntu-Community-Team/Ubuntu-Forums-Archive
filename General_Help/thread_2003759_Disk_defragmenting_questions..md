---
title: "Disk defragmenting questions."
date: 2012-06-14
forum: General Help
---

### Post by Hirobian on 2012-06-14
Greetings fellow linux users! I dual-boot with Windows and Ubuntu 12.04. I use a Dell Inspiron 1546.

Recently I have noticed that I no longer have enough disk space for ubuntu so I want to take some free space from the windows partition and put it over to Ubuntu. But first, before doing so, I wish to defragment my hard drive to avoid breaking Windows.

**Will defragmenting my disk _in windows_ accidentally break ubuntu? Or will the defragmenter just defragment the Windows partition in itself?** :confused:

Maybe I just don't understand the process well enough, please explain to me if you know how this works in detail so that I may understand.

---

### Post by kanikilu on 2012-06-14
> **Hirobian said:**
> Greetings fellow linux users! I dual-boot with Windows and Ubuntu 12.04. I use a Dell Inspiron 1546.

Recently I have noticed that I no longer have enough disk space for ubuntu so I want to take some free space from the windows partition and put it over to Ubuntu. But first, before doing so, I wish to defragment my hard drive to avoid breaking Windows.

**Will defragmenting my disk _in windows_ accidentally break ubuntu? Or will the defragmenter just defragment the Windows partition in itself?** :confused:

Maybe I just don't understand the process well enough, please explain to me if you know how this works in detail so that I may understand. There should be no problem defragmenting the Windows partition, in fact, it's recommended to do so before resizing:

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by sgage on 2012-06-14
> **Hirobian said:**
> **Will defragmenting my disk _in windows_ accidentally break ubuntu? Or will the defragmenter just defragment the Windows partition in itself?**.

Nothing to worry about - you will only defragment the Windows partition. Your Ubuntu installation will be unaffected. There's a good chance that you've been defragmenting your Windows partition on a weekly basis, since it is one of the standard "sceduled tasks" in Windows 7.

---

### Post by Hirobian on 2012-06-14
Thank you so much! C: I'm marking this thread as solved. ):P

---

### Post by 3Miro on 2012-06-14
Defrag Windows, boot from a live CD, resize the partitions.

BEFORE YOU MESS WITH YOUR HDD, BACKUP EVERYTHING IMPORTANT. 

You never know what can go wrong and mess up you work.

---

### Post by Hirobian on 2012-06-14
Always. ^^

---

