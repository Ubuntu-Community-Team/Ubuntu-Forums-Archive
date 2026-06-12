---
title: "Lucid Grub problems"
date: 2010-07-27
forum: General Help
---

### Post by deviant01 on 2010-07-27
Okay previously I had Ubuntu installed then i installed backtrack which wrecked the ubuntu partition and im too stupid to fix it properly so I opted for a full reinstall.

After the re-install I'd get the "Error: out of disk"... but after a few seconds the system would boot into Lucid anyway... so I'm thinking theres still an MBR or another partition in there somewhere...
now however, after an update this morning i get to the grub

I can get into my system by typing 
linux /boot/vmlinuz...%latest kernel variable%
boot

system continues to boot then i can get in... how can i edit grub for it to do this automatically?

---

### Post by VH-BIL on 2010-07-27
Install gparted, you can check out your partitions in that.

---

### Post by deviant01 on 2010-07-27
okay i get
unallocated (1MiB)
/dev/sda1 ext4 (143.31GB)
/dev/sda2 extended (5.74)
       /dev/sda5 swap (5.74)

Im taking it i dont need the unallocated partition
If so will i need to change anything the Grub does?

---

### Post by VH-BIL on 2010-07-27
They are just the partitions for sda, you can use the drop down at the top right to see other physical drives.

---

### Post by VH-BIL on 2010-07-27
It may be a problem with a boot partition.

---

### Post by deviant01 on 2010-07-27
Nope no other drives or partitions...


I can get into the system but i have to tell the grub what to do.
If I reboot my system i get to grub
is there something i can edit once the system is up

---

### Post by VH-BIL on 2010-07-27
you can make changes to grub using the startupmanager package in synaptic

---

### Post by wojox on 2010-07-27
Try installing from a [LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") first.

---

### Post by deviant01 on 2010-07-27
Sweet thanks Bill...

Back to what it used to be

I still get "Error: out of disk" what's up with that... but at least my system boots now

---

### Post by dino99 on 2010-07-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by VH-BIL on 2010-07-27
> **deviant01 said:**
> Sweet thanks Bill...

Back to what it used to be

I still get "Error: out of disk" what's up with that... but at least my system boots now

Try this page:
[https://lists.ubuntu.com/archives/ubuntu-in/2010-May/007915.html](https://lists.ubuntu.com/archives/ubuntu-in/2010-May/007915.html)

---

### Post by MorleyPotter on 2010-07-27
have you tried sudo update-grub, it should automatically find all the bootable partitions.

You could also edit the file manually, by entering sudo gedit /boot/grub/grub.cfg [but it's not recommended]

---

