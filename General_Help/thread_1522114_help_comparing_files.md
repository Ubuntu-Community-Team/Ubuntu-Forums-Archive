---
title: "help comparing files"
date: 2010-07-01
forum: General Help
---

### Post by blackhawx on 2010-07-01
hello everyone,
I have 2 files filled with email addresses. both are over 100 lines long and not in the same order when compared.  Is there a terminal command that checks to see if there is either...

the same email address in both files

or 

unique email addresses only found in one file


My ultimate goal is to take the 2 list and combine them without having to manually go through each line to see if there is a duplicate email address when I combine both files.

thanks a bunch!

---

### Post by gzarkadas on 2010-07-01
Use:
```

cat list1 list2 | sort -s -u > final-list

```list1 list2 : the paths to your two initial lists
final-list : the path to the merged and stripped from duplicates final list.

---

