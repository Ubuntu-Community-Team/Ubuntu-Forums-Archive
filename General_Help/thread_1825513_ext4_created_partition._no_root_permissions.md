---
title: "ext4 created partition. no root permissions"
date: 2011-08-15
forum: General Help
---

### Post by editheraven on 2011-08-15
I just created a new ext4 partition with gparted but i can't write on it. How do i change permissions?

---

### Post by raja.genupula on 2011-08-15
i man honestly i too dont know is this work or not but give a try 

 ** sudo chmod 777 /media/rive_label**

---

### Post by ~!geek!~ on 2011-08-15
> **editheraven said:**
> I just created a new ext4 partition with gparted but i can't write on it. How do i change permissions?

If you only use the machine, I mean only one user is there on the machine, I would suggest you to own the partition and give permissions to read and execute to the others, by doing:
>  sudo chown /media/<name of the partition> -R ; sudo chmod 755 /media/<name of the partition> -R 
If you have more than one user on your machine and you want to share the partition with everyone permitting each one to do read, write and execute on this partition, you may do: > sudo chmod 777 /media/<name of the partition> -R 

---

