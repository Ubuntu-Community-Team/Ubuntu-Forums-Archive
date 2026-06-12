---
title: "how to restore my poor partitions"
date: 2010-07-30
forum: General Help
---

### Post by sysabod on 2010-07-30
dear all:
 
my hard drive has 6 partitions, c for windows xp, d for windows 7, e for ubuntu10.04
 
f is a empty partition which is the origin of my disaster, so, please be patient to hear 
 
out my story.
 
i wanna install mac os x in my partition f,so i open the disk management in windows xp, and inadvertently deleted all the logical drives after parition f ,i,e, from partition f to partition h are all deleted due to my stupid mis-operation.
 
now,each time i power on the computer, it goes to a command line with "grub-rescue>", i had followed the steps provided by other people after google this,but none of them works,the error is either "no such parititon" or "unknown filesystem".
 
...., i am really upset and anxious now,can you guys give me some tips or solutions ?
 
Thanks in advance !

---

### Post by sysabod on 2010-07-30
well,it seems nobody even posted,but i get good news for you. I have solved it by my 
 
self. I just use some stuff like disk doctor in the dos mode and reconstruct my partition 
 
table,which restored my whole data ,finally i reinstalled the grub-loader to my 
 
MBR,successfully returned to my familiar booting screen.
 
Hope this is helpful!:D

---

### Post by dino99 on 2010-07-30
as everybody knows, the biggest bug is somewhere between chair and keyboard ](*,)

---

### Post by terry2001 on 2010-07-30
The command line program "Testdisk" or "system rescue cd " would have helped you.

---

