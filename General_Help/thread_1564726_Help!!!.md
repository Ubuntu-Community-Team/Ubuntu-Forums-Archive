---
title: "Help!!!"
date: 2010-08-30
forum: General Help
---

### Post by pokethesmot on 2010-08-30
i tried to make a backup file and it was 2 large and now i wanna delete it but it wont let me its called backup.tar.bz2 and ive tried everything i know it says i dont have permission i have ubuntu by the way can some one plesae tell me how to delete it

---

### Post by wojox on 2010-08-30
Where is it in the file system? Outside your home directory? Try

```
sudo rm -rf /path/to/backup.tar.bz2
```

---

### Post by andrewthomas on 2010-08-30
> **pokethesmot said:**
> i tried to make a backup file and it was 2 large and now i wanna delete it but it wont let me its called backup.tar.bz2 and ive tried everything i know it says i dont have permission i have ubuntu by the way can some one plesae tell me how to delete it
```
rm /path/to/file
or 
sudo rm /path/to/file
```By the way,  **Help!!!** is not a very descriptive title

---

### Post by pokethesmot on 2010-08-31
> **andrewthomas said:**
> ```
rm /path/to/file
or 
sudo rm /path/to/file
```By the way,  **Help!!!** is not a very descriptive title
thanks everyone for the help Linux rocks and im sorry about the tittle

---

### Post by v1ad on 2010-08-31
if you can mark it solved please :D thread tools -> solved

---

