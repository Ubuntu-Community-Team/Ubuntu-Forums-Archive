---
title: "limiting READ folder options"
date: 2011-11-03
forum: General Help
---

### Post by Fdisk101 on 2011-11-03
Hi all, hoping someone can give me a solution to the following.

I have created a file server so files can be automaticaly copied into a network share, however.. i dont want that user to have the right to read or copy from that share, like a blind send function as these documents are confidential.
Is it possible with linux to configure a server this way? Im new to linux and learning as fast as i can but the above problem needs a solution and im out of ideas.
Enlighten me please, will be most greatful if can be done

ta
Newbie

---

### Post by 11jmb on 2011-11-03
```
chmod -R 700 <directory>
```

will give read/write/execute privileges only to the owner of all the files in the directory.

---

### Post by 11jmb on 2011-11-03
I should point out that encrypting may be a better option.

---

### Post by Fdisk101 on 2011-11-03
thanks for info, was reading general file permisions and wondered if this would do it

2     -w-     010     Write access is allowed only
encryption would  just confuse things given setup, i just need to be able to copy files from a other location but then not be able to read the directory

would that be chmod 620 ? wont be able to play till morning..

---

### Post by Fdisk101 on 2011-11-04
didnt work... needs read to respond.. help

---

