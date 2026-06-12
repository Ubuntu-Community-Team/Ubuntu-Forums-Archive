---
title: "Sort command not working"
date: 2009-10-07
forum: General Help
---

### Post by rwttaber on 2009-10-07
I am trying to sort and delete repeated words from a wordlist I have made.

I use this command

sort   -u   /home/rwt/Wordlist.txt   -o   /home/rwt/NewWordlist.txt

It should sort, unique (delete repeated words) and then out put the sorted and unique words into a new wordlist. It works fine for small files.

What am I doing wrong? What are some more commands I could try to sort and delete repeated words inside a text file?

Thanks 
rwttaber

---

### Post by wojox on 2009-10-07
Instead of sort -u try:

```
sort myfile.txt | uniq -u
```

---

