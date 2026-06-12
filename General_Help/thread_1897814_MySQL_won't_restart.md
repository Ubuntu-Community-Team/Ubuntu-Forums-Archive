---
title: "MySQL won't restart??"
date: 2011-12-19
forum: General Help
---

### Post by adamantasaurus on 2011-12-19
I'm following this tutorial.....

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p4)

I'm at this part here.......
```

We want MySQL to listen on all interfaces, not just localhost, therefore we edit /etc/mysql/my.cnf and comment out the line bind-address = 127.0.0.1:

vi /etc/mysql/my.cnf

[...]
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 127.0.0.1
[...]
Then we restart MySQL:

/etc/init.d/mysql restart

```

When I enter.....
```
 
/etc/init.d/mysql restart 

```
it gives me this error........ 

```

bash: /etc/init.d/mysql: No such file or directory

```

I'm using Ubuntu Server 10.04 (no gui)

Any advice would be greatly appreciated.

Thank You

Adamantasaurus

---

### Post by adamantasaurus on 2011-12-20
Anyone??

---

### Post by Dangertux on 2011-12-20
Depending on how you install MySQL it may be slightly different. Try the following commands

```

sudo /etc/init.d/mysql restart

``````

sudo service mysql restart

``````

sudo /etc/init.d/mysqld restart

``````

sudo service mysqld restart

```Hope this helps.

---

### Post by adamantasaurus on 2011-12-20
> **Dangertux said:**
> Depending on how you install MySQL it may be slightly different. Try the following commands

```

sudo /etc/init.d/mysql restart

``````

sudo service mysql restart

``````

sudo /etc/init.d/mysqld restart

``````

sudo service mysqld restart

```Hope this helps.

Thanks for the help but I tried all of those, and none of them work. Do you have any other suggestions?

---

### Post by Dangertux on 2011-12-21
It's possible that there is neither a startup script or upstart job for mysql. What method did you use to install it?

---

### Post by adamantasaurus on 2011-12-21
> **Dangertux said:**
> It's possible that there is neither a startup script or upstart job for mysql. What method did you use to install it?

I just followed that tutorial word for word, should I try installing it again?

---

### Post by Dangertux on 2011-12-21
Yeah o would go ahead and try this

```

sudo apt-get install mysql-server mysql-client

```

See if that fixes the issue. Note if it does you will have to re edit your my.cnf file

---

### Post by adamantasaurus on 2011-12-21
> **Dangertux said:**
> Yeah o would go ahead and try this

```

sudo apt-get install mysql-server mysql-client

```

See if that fixes the issue. Note if it does you will have to re edit your my.cnf file

I tried the install command and it told me 0 upgraded 0 newly installed 0 to remove and 0 not upgraded. 

Does that mean it worked? or should I remove it first and then reinstall.

Note:

After I reinstalled it I tried to restart it and it still didn't work.

---

