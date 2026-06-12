---
title: "How to see &quot;My Documents&quot; folder of Windows 7 in Ubuntu"
date: 2010-02-26
forum: General Help
---

### Post by Electricalkhukuma on 2010-02-26
I have installed Ubuntu 9.04 under my Windows 7 but now my Windows is not opening up because of Hard disk crash. I am still able to see all my windows files from '\home' folder in Ubuntu. How can i be able to see my Document files present in My Document folder of Windows 7??

---

### Post by PoHandle on 2010-02-26
Mount your Windows partition, and browse to
```
/media/*[windows-partition-uuid]*/Users/*[your-username]*/My Documents
```
where *[windows-partition-uuid]* will be the UUID of your Windows partition (automatically selected) and *[your-username]* is the username you use for Windows.

---

### Post by Electricalkhukuma on 2010-02-26
How can I mount Windows partition ? Ubuntu is installed on the same partition as the windows.

---

### Post by blur xc on 2010-02-26
Did you do a wubi install?

BM

---

### Post by Electricalkhukuma on 2010-02-26
yes, i did a wubi install.

---

### Post by zachHH on 2010-02-26
You should probably be able to find your documents by going to File System -> host/Users/YourUsername/Documents

---

### Post by Electricalkhukuma on 2010-02-26
@ zachHH & all
thanks! It just solved the problem.

---

