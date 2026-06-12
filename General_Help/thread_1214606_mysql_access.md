---
title: "mysql access"
date: 2009-07-16
forum: General Help
---

### Post by benh13 on 2009-07-16
how do i access mysql and use it? i have just installed it but i don't know where to go to begin making databases. i think i have phpmyadmin installed too. i have tried typing mysql root-u password=my password into terminal, but i don't know where to go from here.
can anybody help?
thanks

---

### Post by kaustubh.bansal on 2009-07-16
If you've properly installed it, just write the following in your terminal
```

mysql -u <user_name> -p

```
and hit return, you'll be prompted for password..

---

### Post by knappers on 2009-07-16
If you installed it using synaptic then it should be available in Applications->programming
 
Should be MYSQL Administrator and MYSQL Query Browser
 
 
to create a db open mysql administrator click on catalogs and in the left pane, where you see mysql and test below  the Schemata right click -> create new schema
and away you go (well there's a bit more to it than that but just have a play, you can always right click on the schema you have created and -> drop schema but don't drop the mysql schema.

---

### Post by benh13 on 2009-07-16
> **kaustubh.bansal said:**
> If you've properly installed it, just write the following in your terminal
```

mysql -u <user_name> -p

```and hit return, you'll be prompted for password..

cheers works now.

---

