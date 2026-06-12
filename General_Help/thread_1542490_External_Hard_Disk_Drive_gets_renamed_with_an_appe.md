---
title: "External Hard Disk Drive gets renamed with an appended underscore"
date: 2010-07-30
forum: General Help
---

### Post by skylime on 2010-07-30
Almost every time I use my external Hdd the drive gets named with an appended underscore. this is the list from my /media folder.


/media$ ls
1CF44533F4451106  F Drive  G Drive_   G Drive___   G Drive_____
E Drive           G Drive  G Drive__  G Drive____  G Drive______

i have tried to remove the directories in terminal by using sudo rmdir but this is the error i get:


sudo rmdir /media/g\ drive
rmdir: failed to remove `/media/g drive': No such file or directory

now each file in the /media folder has a white x on them and i don't not know what that means. but i attached a screen grab of the folder. 

I would just like how to know how to delete all the underscored folders.

---

### Post by prodigy_ on 2010-07-30
> ```
sudo rmdir /media/g\ drive
```
is wrong because Linux file system is case-sensitive.

---

### Post by Stefanie on 2010-07-30
Are you running Lucid? Last time I came across this issue was under Hardy. The problem occurs when your HD is not properly unmounted (eg when hibernating), so it has to be remounted under a new location (hence the underscore). Make sure you always unmount your external hard drive before you unplug it.

For me, running  ```
 sudo umount -a 
``` and then plugging the device in again usually solved the problem.

---

### Post by skylime on 2010-07-30
yes i have lucid. and i do unmount before disconneting the drive and it still happens.

---

### Post by skylime on 2010-07-30
> **prodigy_ said:**
> is wrong because Linux file system is case-sensitive.

wow i feel like the biggest ***. thank you so much. it worked. THANK YOU
:KS

---

### Post by prodigy_ on 2010-07-30
NP. :-) You can manually mount this drive wherever you want. Use ```
man mount
``` command to get more info.

---

