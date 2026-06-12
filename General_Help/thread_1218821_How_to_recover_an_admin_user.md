---
title: "How to recover an admin user"
date: 2009-07-21
forum: General Help
---

### Post by coituslegends on 2009-07-21
Hi guys,

i have accidentally deleted the first user i have created when i installed ubuntu 9.04, it has admin privileges. i can't log in using that username but i can still see it on the home folder. i deleted it on system>administration>user and groups. Now i added a new user but it does not have admin or sudo privileges. 

Can i still recover that username? How can i create a user with admin privileges or give privileges to users using the terminal?

Please give me some advice.

---

### Post by nothingspecial on 2009-07-21
```
sudo adduser dave
```

Follow the prompts and you will have a new user called dave.

```
sudo adduser dave admin
```

Now dave can sudo.

When you remove a user it doesn`t delete his/her home directory. You have to delete that manually using sudo. Be careful deleting things with root privaleges.

---

### Post by CatKiller on 2009-07-21
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by coituslegends on 2009-07-23
heY NOTHINGSPECIAL , thanks for that. it did solved my problem.

---

