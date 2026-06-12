---
title: "I can login but I am not listed in users and groups"
date: 2009-12-12
forum: General Help
---

### Post by tcchris on 2009-12-12
I am the primary login , I can login but my name is not listed in the gdm screen . I have to click other . When I went to "Users and Groups " to add a user for children to use , I noticed that I am not listed , only root and the new child login . I wanted to adjust my user to be in the child group but I am not there . Help !

---

### Post by nothingspecial on 2009-12-12
If you type 
```
cat /etc/passwd | cut -d":" -f1
```

are you listed?

---

### Post by tcchris on 2009-12-12
Yes I am listed that way , also uid and gid are 500
other user is 1000

---

### Post by nothingspecial on 2009-12-12
That`s weird. AFAIK you should be 1000. But I`m far from an expert in this. You could add yourself to the child group from the shell.

---

### Post by Leppie on 2009-12-12
yes, primary user in ubuntu is 1000 by default (after installation).
was this a clean install?

---

### Post by tcchris on 2009-12-12
yes clean install , should I try changing UID to 1001

---

### Post by tcchris on 2009-12-12
Update , 
1. Change "boo" child account from user and group 1000 to 1001 
2. I had to give "boo" the child account admin privileges temporarily
3. Login as boo , change "chris" my account from 500 to 1000 
4. Reset "boo" privileges 
Now everything works fine 
Thank you so much for the advice
I am not sure how this happened , but it is all good now

---

