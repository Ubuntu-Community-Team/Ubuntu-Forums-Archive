---
title: "Master Boot Record"
date: 2009-07-09
forum: General Help
---

### Post by NewWithoutClue on 2009-07-09
Hi. I was wondering if anyone could help me fix my master boot record. I happened to attempt to reinstall ubuntu, and the CD that I was using happened to be scratched so the install wouldn't finish and grub doesnt want to work for me. I was hoping there was a way to restore the former bootloader that windows provided whilist on linux in live mode (because i can still use the CD, but it wont install to disk). can anyone help me?


p01n7

---

### Post by vikkikanhaua on 2009-07-09
if u want to restore windows booting without installing linux then put in the windows bootable disk, go to the the repair mode & now i exactly don't remember but there is a command "/fix MBR" or like this.
u can find it by typing 'help'.
this will write windows boot record to the MBR

---

### Post by ajgreeny on 2009-07-09
If you do not have a full windows install disk, for example you may have a restore disk from your manufacturer instead, you can also restore the windows MBR with [supergrub]("http://www.supergrubdisk.org/")

---

