---
title: "gparted advice"
date: 2010-02-28
forum: General Help
---

### Post by harryliddic on 2010-02-28
I recently wanted to put all my linux on my 80G drive and with dual boot put my Winxp on a 40G drive. The linux device is sda and the winxp is sdb
I successfully mounted the 9.10 on the sda but when I went to re-install the winxp on sdb. It said it had to have a partition on sda. I resized the linux partition for  4GB of unallocted space the changed the space to ntfs. When I clicked to apply an error message can up about saving details and to my chagrin gparted froze. I need winxp for a program called Final Draft that I use in my playwriting. And I need a lot of space in linux for video editing. Is there a way to put winxp on my sdb.  
.

---

### Post by drpjkurian on 2010-02-28
Hi
I advise you to go the other way around, ie 
1. Boot from Live CD of Ubuntu and make a Partition of 40 GB in the file format of NTFS
2.Keep the rest of 40 GB as unallocated space
3.Install Windows XP in 40 GB NTFS partition
4.Install Ubuntu by using  the option "Install in continious free space". It will be automatically installed in the unallocated space.

---

### Post by harryliddic on 2010-02-28
Hi. Thanks for the reponse

so in other words Half of sba will be spit between 9.10 and winxp and sdb will be all linux. will the Live cd put in the swap space?

---

### Post by drpjkurian on 2010-02-28
> **harryliddic said:**
> Hi. Thanks for the reponse

so in other words Half of sba will be spit between 9.10 and winxp and sdb will be all linux. will the Live cd put in the swap space?

Hi
Yes the HD will be divided into two or can be partionrd according to your choice.
When you install Ubuntu in the continuous free space, It formats that unallocated space to ext3 and also installs the swap partition too. No need to break your head

---

### Post by harryliddic on 2010-02-28
Hi
One more question will large video files of up to 15G sit on both drives? Turn the corner so to speak?

---

### Post by drpjkurian on 2010-02-28
> **harryliddic said:**
> Hi
One more question will large video files of up to 15G sit on both drives? Turn the corner so to speak?

Nope

---

