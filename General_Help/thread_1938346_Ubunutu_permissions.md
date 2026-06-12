---
title: "Ubunutu permissions"
date: 2012-03-09
forum: General Help
---

### Post by bender1 on 2012-03-09
I have bought a dedicated server that has ubuntu 10.04 on it ,and i plan on making a MMO server on it.I am connected using putty.Can you tell me how can i change the permission on one file using the putty terminal? i want it to be read and write on all and checked allow execute as a program.

---

### Post by codemaniac on 2012-03-09
From ternminal you can change a persmission of a file easily.If you want to place read + write for all , you can do like below .

```
chmod a+rw filename
```

---

### Post by idoitprone on 2012-03-09
you want everyone? or a group 

everone excute

```
chmod o+rx filename
```grou execute
```
chmod g+rx filename
```
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
[http://www.ahinc.com/linux101/permission.htm](http://www.ahinc.com/linux101/permission.htm)

---

### Post by bender1 on 2012-03-09
I want only 1 file in a folder

---

### Post by codemaniac on 2012-03-09
> **bender1 said:**
> I want only 1 file in a folder

Please clear up your query ,else no one can help you out .

---

### Post by bender1 on 2012-03-09
in a folder i have a couple of config files and a file i want to make it read +write  and to execute as a program.

---

### Post by codemaniac on 2012-03-09
You still didn't mention if you want to give permissions to all or users or group or others .

Please go through the filesystem permissions on unix .
The below will give you a short tutorial .
[http://www.dartmouth.edu/~rc/help/faq/permissions.html]("http://www.dartmouth.edu/~rc/help/faq/permissions.html")

---

### Post by bender1 on 2012-03-09
owner and group

---

### Post by codemaniac on 2012-03-09
```
chmod ug+rwx file_name
```
would set read , write and execute permissions to the owner and group for the file named file_name.

---

### Post by bender1 on 2012-03-09
Thank you:D

---

