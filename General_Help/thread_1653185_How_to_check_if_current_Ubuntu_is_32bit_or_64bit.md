---
title: "How to check if current Ubuntu is 32bit or 64bit?"
date: 2010-12-26
forum: General Help
---

### Post by pstein on 2010-12-26
I have got an Notebook whose CPU is 64bit.
The Notebook has an Ubuntu installation. Now I want to find out if this Ubuntu is 32bit or 64bit.
 
How can I check this?
 
uname -a
 
gives something with ....i686...."
 
What does that mean?
 
Does that refer to the hardware or the Ubuntu OS?
 
Keep in mind: An 32bit Ubuntu can be installed on a 64bit hardware!!!
I am interested in the OS capability not of the hardware!
 
Peter

---

### Post by karthick87 on 2010-12-26
Type the following in your terminal,
```
uname -m
```

if it returns i686 then it is 32bit..

---

