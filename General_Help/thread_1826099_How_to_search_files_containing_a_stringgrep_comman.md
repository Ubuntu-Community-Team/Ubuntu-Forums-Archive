---
title: "How to search files containing a string/grep command"
date: 2011-08-16
forum: General Help
---

### Post by rizwanmumtaz on 2011-08-16
Hello folks, 

I am kinda new to Ubuntu. Can anybody tell me how to search for those files which contain word "AM_COLLECTION=22". I need to know all the files with this string. ( I know the grep command can do it but either I am making some stupid mistake while using it or there is some other weird problem) 

Thanks, 
Riz

---

### Post by smurphy_it on 2011-08-16
grep -i "AM_COLLECTION=22" /directory-to-search

---

### Post by Vaphell on 2011-08-16
are we talking about plain text files?
if you need to search recursively
```
grep -r 'AM_COLLECTION=22' .
``` should do

---

### Post by g58g on 2011-08-19
i need help to find this  -  4500*2  - in a text file on my hard drive on notepad. I have not been able to use grep to find this string. can grep be use for this problem?  thank you for a response

---

### Post by Doug S on 2011-08-19
(If I understand the question from g58g) If I know part of the file name, but not where it is, and I don't want to search every file on the drive, I would use this command to find the file: ```
find . -type f -name "*.txt" -exec grep -H '4500\*2' {} \;
```

---

