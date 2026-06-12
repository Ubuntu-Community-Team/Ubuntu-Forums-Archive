---
title: "please help"
date: 2011-04-30
forum: General Help
---

### Post by nikola96 on 2011-04-30
I installed wine in the new Ubuntu 11, but when i  right click and go open with wine it says that its not marked as  executable! then i went right click and properties and under the  permissions i clicked "Allow executing file" but it keeps unchecking!   
Please help and thanks! [IMG]http://forum.winehq.org/images/smiles/icon_biggrin.gif[/IMG]

---

### Post by sikander3786 on 2011-04-30
Welcome to the forums :-)

Which files are you trying to execute? Are they on a NTFS partition?

---

### Post by nikola96 on 2011-04-30
they are windows games: .exe!
Im new to ubuntu so i dont know much

---

### Post by nikola96 on 2011-04-30
i want to install windows apps and games so i use ubuntu all the time!

So how do i fix that problem?

---

### Post by sikander3786 on 2011-04-30
The .exe files you are trying to execute, where are they stored at the moment. CD or Hard disk? If Hard disk, are they on a separate partition.

---

### Post by 3Miro on 2011-04-30
It is generally preferable to make a separate installation for the games under Ubuntu, many games will not run without it.

Otherwise, you can copy/paste the files to the Ubuntu partition and then they should work just fine (assuming the game doesn't need a more complex installation).

If this doesn't work, you can setup the windows partition to be mounted manually in fstab. It is a bit more advanced, but here is a good tutorial:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

You want to enable the exec option for the NTFS partition.

---

### Post by nikola96 on 2011-04-30
thanks !

---

### Post by nikola96 on 2011-04-30
i extracted it on the Ubuntu partition and it still is unchecking!

---

### Post by nikola96 on 2011-04-30
the .exe file that im trying to install is on hard drive

---

### Post by 3Miro on 2011-04-30
Where exactly is the file? It should be in /home/your_user_name/something.

Then it should work if you right-click and say "open with wine".

---

### Post by nikola96 on 2011-04-30
it works, thanks!

---

### Post by 3Miro on 2011-04-30
If you have no more questions on this topic, please mark the thread as "solved".

---

