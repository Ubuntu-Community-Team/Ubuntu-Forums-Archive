---
title: "no root file system is defined"
date: 2011-01-21
forum: General Help
---

### Post by beowulfk on 2011-01-21
I'm trying to install ubuntu on d partition i deleted, which now is "free space" but its giving me that error

so im guessing i have to click on add, what do what i click on? primary? beginning? end? ext 4 im guesing and which mount point?

im installing it on d portition which i deleted and is now free space, i have windows 7 on c, \

im so confused:(

---

### Post by beowulfk on 2011-01-21
=( I give up, i guess i'll just stick to windows 7, im too stupid to do this

---

### Post by mikewhatever on 2011-01-21
Not stupid, just a bit uninformed.
primary/logical - choose logical
Beginning/end - choose beginning
file system - ext4
mount point - / (that is forward slash)

---

### Post by beowulfk on 2011-01-21
> **mikewhatever said:**
> Not stupid, just a bit uninformed.
primary/logical - choose logical
Beginning/end - choose beginning
file system - ext4
mount point - / (that is forward slash)

thanks a lot :p

---

### Post by beowulfk on 2011-01-21
one last question what is boot loader? which one do i choose?

/dev/sda5 (one i just created or one of the 1-3 which is vista/7/7

there's also a dev/sda ata (500.1gb)
it also says you have no selected any partitions for use as a swap space

---

### Post by mikewhatever on 2011-01-21
Boot loader is something that boots or loads the OS. In case you only have one hdd, leave the default option, /dev/sda.
The swap partition functions as extended RAM (same as page file in Windows). You can get away without it, if you have a lot of RAM, 2GB or more.

---

### Post by beowulfk on 2011-01-22
> **mikewhatever said:**
> Boot loader is something that boot the OS. In case you only have one hdd, leave the default, /dev/sda.
The swap partition functions as extended RAM (same as page file in Windows). You can get away without it, if you have a lot of RAM, 2GB or more.

Thank you very much, may you live a long and prosperous life.

---

### Post by mikewhatever on 2011-01-22
I'll try, and you are welcome.:p

---

### Post by woodeye3 on 2011-01-22
Mikewhatever
 I've been reading your discussion.
I'm also trying to load ubuntu alongside win7 on a 10g partition
I got past the previous problem, thanks to you, now I'm stuck at the next stage assigning a swap partition.
I do have 4g ram
HD still has 140g left
After I've got ubuntu up and running I'd like to install mythbuntu and start playing with it

---

### Post by mikewhatever on 2011-01-22
To create a swap partition, click 'New' and select 'swap' in the file system menu.

---

