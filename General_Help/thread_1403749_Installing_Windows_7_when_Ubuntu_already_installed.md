---
title: "Installing Windows 7 when Ubuntu already installed"
date: 2010-02-10
forum: General Help
---

### Post by TheNessus on 2010-02-10
ok, I got an extra space for another OS, and I need win7 for it. 

Will it delete Grub2? how do I get it back, and what else should I expect to go wrong? thanks

---

### Post by mavmic on 2010-02-10
i want to get rid of windows from my laptop and leave only ubuntu . how can i do it safely ?

---

### Post by FearfulJesuit on 2010-02-10
@ Mavmic

Use GParted and delete the partition with Windows on it.

@TheNessus
um...if you don't create another partition, it will get rid of Grub and your ubuntu OS. Create a FAT partition and install Win7. Should not be a problem. Look at GParted to create a partition.

---

### Post by colobix on 2010-02-10
you gonna have to use the ubuntu live cd after the win7 installation to edit the grub menu.

---

### Post by HotForLinux on 2010-02-10
> **TheNessus said:**
> ok, I got an extra space for another OS, and I need win7 for it. 

Will it delete Grub2? how do I get it back, and what else should I expect to go wrong? thanks

I have never done that but if you install Win7, when Ubuntu is already installed, that might change the MBR. So you just have to rewrite the MBR. Ther'es plenty of places that explain how to do this easy operation.

---

### Post by TheNessus on 2010-02-10
> **FearfulJesuit said:**
> @ Mavmic

Use GParted and delete the partition with Windows on it.

@TheNessus
um...if you don't create another partition, it will get rid of Grub and your ubuntu OS. Create a FAT partition and install Win7. Should not be a problem. Look at GParted to create a partition.

That is quite obvious. I have a spare partition. :)

Anyway thanks peeps, i'll look into it.

---

