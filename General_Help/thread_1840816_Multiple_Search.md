---
title: "Multiple Search"
date: 2011-09-08
forum: General Help
---

### Post by hepyack on 2011-09-08
hello;
I have about 555 line list one name and surname per line. and I have second list which is include just 20-25 surnames.  My aim is to search surnames from second list via linux code but I need whole line (name - surname) if it finds. Is that possible?

---

### Post by Bodsda on 2011-09-08
> **hepyack said:**
> hello;
I have about 555 line list one name and surname per line. and I have second list which is include just 20-25 surnames. My aim is to search surnames from second list via linux code but I need whole line (name - surname) if it finds. Is that possible?
 
Of course, very possible. I'm not going to write the code for you, that would defeat the whole purpose. What code do you currently have, what problems are you running into?
 
Bodsda

---

### Post by hepyack on 2011-09-08
> **Bodsda said:**
> Of course, very possible. I'm not going to write the code for you, that would defeat the whole purpose. What code do you currently have, what problems are you running into?
 
Bodsda
I have 
cat /home/etc/file.txt | sort -u > /home/etc/file1
grep -w 'word|word1|word2' /home/etc/file

but i couldn t succeed

---

