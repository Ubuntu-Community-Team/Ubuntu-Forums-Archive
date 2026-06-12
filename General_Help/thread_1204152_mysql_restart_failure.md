---
title: "mysql restart failure"
date: 2009-07-04
forum: General Help
---

### Post by babbar.ankit on 2009-07-04
I am trying to restart mysql but it fails 
sudo apt-get install mysql-server

---

### Post by mbeach on 2009-07-04
the command you are giving is to install the server.

to restart you are probably looking for something like:
```
sudo /etc/init.d/mysql restart
```

it would be helpful if you posted the exact error you are getting.

---

### Post by babbar.ankit on 2009-07-04
done myself!

---

### Post by mbeach on 2009-07-05
great job. 

Could you post your solution so that others may learn from it as well.

---

