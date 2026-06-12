---
title: "How to change permission of other partition?"
date: 2012-03-05
forum: General Help
---

### Post by farukdgn on 2012-03-05
How can I change permission of a file that isn't in system partition of HDD? I only need to change "Allow executing file as program" permission. Thanks.

---

### Post by An Sanct on 2012-03-05
I guess, that you have access to that file...

Run Nautilus or any other file browser as sudo
```
sudo nautilus
``` 
or graphical
```
gksu nautilus
``` 
browse to the specific file and change the property.

---

### Post by farukdgn on 2012-03-06
Didn't work. When I click Allow executing file as program, it goes back in  1 second.

---

### Post by Morbius1 on 2012-03-06
Is the file sitting on an NTFS or FAT32 partition and is it internal or external?

As a side question, are you doing this because of wine or java? If so there's another way to circumvent that error message you are getting. Wine and Java themselves don't care if it's executable.

---

