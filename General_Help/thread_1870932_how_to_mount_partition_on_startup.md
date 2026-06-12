---
title: "how to mount partition on startup"
date: 2011-10-28
forum: General Help
---

### Post by chinmay3 on 2011-10-28
Hello there !
I have dual boot with ubuntu 10.04 & 11.04 with two partition both of ext4 type. I have stored all my music files in home folder of ubuntu 11.04. when i open these music files in clementine or rhythmbox in ubuntu 10.04 they don't play unless i open that partion on desktop. I wan't some method that mount 11.04 partition automatically when i startup 10.04. I tried editing /etc/fstab & crashed system once. & further attempt have no success. 
will anybody know how to do this job as easily as possible. 
Thanks in advance!!!

---

### Post by gsmanners on 2011-10-28
The simplest explanation I can find is: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

It's not altogether easy, but it isn't that terribly hard.

---

### Post by Lars Noodén on 2011-10-28
When the partition is properly mounted, run the mount command and look at the output.  Use the values for that for /etc/fstab.  

You can test /etc/fstab by mounting the partition by referring only to its mount point.  e.g.

```

sudo mount /home/me/Music

```

Keep a backup copy of /etc/fstab so that you can revert more easily if you give up before it is working.  As you noticed, it can be unforgiving with errors.

---

