---
title: "ecpg not found"
date: 2006-03-21
forum: General Help
---

### Post by Vince@ on 2006-03-21
I installed PostgreSQL 8.1 and would like to use the precompiler ECPG to do embedded SQL in C. It should apparently be installed when postgresql is installed but when I try to use it, it doesn't exist and I get:

```
bash: ecpg: command not found
```

Do I use it the wrong way, did I forget to install some packages,....
Thanks for your help

---

### Post by seishi on 2007-03-15
You need install libecpg-dev

```
sudo apt-get install libecpg-dev
```


about a year since you asked
i hope you already got the solution, :lolflag:

---

