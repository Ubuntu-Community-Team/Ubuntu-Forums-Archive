---
title: "Exiftool problem"
date: 2012-08-29
forum: General Help
---

### Post by vikler on 2012-08-29
So I have a directory with a lot of sub-directories, each has .jpg files inside. I need to recursively find filles according to a seach pattern. This is how I do it:
```

exiftool -if '$Caption-Abstract =~ /mykeywordhere/i' * / -p '$filename' -q -f -r > temp.txt

```
However the -r key makes the recursion too deep, going inside some system directories, so the search never ends. I start getting several error messages like:
```

...
Error opening directory /etc/cups/ssl
Error opening directory /etc/ssl/private
Error opening directory /etc/ppp/peers
Error opening directory /etc/chatscripts
...

```
Btw the names of .jpg files are actually found according to my search criteria, before the whole "too deep into system sub-directories" thing happens. So I need your help in how to fix the code. Thanks so much to anyone who answers, I've been googling for a few days with no luck yet:(

---

### Post by vikler on 2012-08-29
bump

---

### Post by raja.genupula on 2012-08-29
Hi dont BUMP your post so early . Minimum BUMP time is 24 Hrs. 

while coming to your answer , are you trying as root ? because you need to be a root to access filesystem .

---

