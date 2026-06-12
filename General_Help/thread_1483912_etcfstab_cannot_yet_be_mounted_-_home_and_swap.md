---
title: "/etc/fstab cannot yet be mounted - /home and swap"
date: 2010-05-15
forum: General Help
---

### Post by Distriker on 2010-05-15
Hello, I have a big problem with my Ubuntu Karmic Koala.

When I try enter in the OS, in the loader screen say this:

> One or more of the mounts listed in:
  /etc/fstab cannot yet be mounted:
   /home: waiting for UUID = 34a9582f-cc14-4dc8-98f7-f982f79f094
   swap: waiting for UUID = 62a791d8-3876-4ce2-a9e7-0480e657a9b4

Press ESC to enter a recovery shell

I don't know that I must do it. I enter in the recovery shell, but nothing, I don't know.

It's important that I enter in Ubuntu. If you can help me, help, please.

Thanks.

Greetings.

---

### Post by mali2297 on 2010-05-15
You probably need to edit the file /etc/fstab and update the UUIDs. Can you reach a terminal prompt in recovery mode? If so, you can edit fstab from there (type *sudo nano -Bw /etc/fstab*). Otherwise, I suggest using a LiveCD.

Instructions on how to edit fstab can be found at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by Distriker on 2010-05-15
But, what I must change in the /etc/fstab?

Must I write the dates of last message?

Greetings.

---

### Post by ajgreeny on 2010-05-15
Run the live CD then in terminal let's see the output of ```
sudo fdisk -l
``` and then ```
sudo blkid
```  That will tell us the current partition setup and the UUIDs of the hard disks.

Still in the live CD mount your installed version of ubuntu from Places menu by double clicking on the appropriate icon, which should be pretty obvious from its size, navigate to /etc/fstab and copy the contents of that back here as well, all of which you can do while in the live CD.

That should allow someone to tell you what is wrong with your fstab file and what to edit to put it right.

---

### Post by Distriker on 2010-05-15
Thanks, I try this then and tell you.

Greetings

---

