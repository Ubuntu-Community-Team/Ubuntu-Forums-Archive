---
title: "unmounting"
date: 2006-06-26
forum: General Help
---

### Post by notoriouslou1022 on 2006-06-26
I want to put up a windows 10gb partition on my lap top for gaming. I have Ubuntu installed already and got gpart to resize. The only problem is when I try to unmount my harddrive its says its busy (with makes sense). May someone please help me.





Lou

---

### Post by taurus on 2006-06-26
Are you trying to unmount your Linux filesystem or the Windows?

---

### Post by notoriouslou1022 on 2006-06-26
linux

---

### Post by RAOF on 2006-06-26
You'll have to use a LiveCD.  As you've seen, you can't unmount your system (root) drive (wierd stuff would happen ;)).  Also, trying to resize (or, at least, make smaller) a mounted partition would be a **very** risky business - that's why nothing (I know of) will let you do it.

The Ubuntu install CD just happens to be a LiveCD.  You can use that.

---

### Post by notoriouslou1022 on 2006-06-26
its says its busyyyyy

---

### Post by professor_chaos on 2006-06-27
[QUOTE=notoriouslou1022]its says its busyyyyy[/QUOTE]

Its busy because its in use. You cannot "normally/safely" unmount a inuse filesystem. listen to RAOF, and boot using the livecd and partition from there.

---

### Post by RAOF on 2006-06-27
[QUOTE=notoriouslou1022]its says its busyyyyy[/QUOTE]
If you're using a live cd and its **still** saying this, then maybe the livecd is automatically mounting the partitions on your harddrive.  You should be able to unmount those, then you can mess around with the partitions to your heart's content.

---

