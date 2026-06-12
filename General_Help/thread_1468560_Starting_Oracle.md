---
title: "Starting Oracle"
date: 2010-05-01
forum: General Help
---

### Post by Adrienk on 2010-05-01
I installed oracle using the terminal but I don't know how to run it, in windows there is a exe called SQL run or run SQL to which you type all the commands into....where is that in linux? or how do i started oracle XE in linux?

Version: oracle 10g
Version of ubuntu: 10.4

---

### Post by Adrienk on 2010-05-01
bump need help people

---

### Post by Adrienk on 2010-05-01
Bump

---

### Post by Waappu on 2010-05-03
Hi,

You can strat database by command
```

sudo /etc/init.d/oracle-xe start

```
Stop database
```

sudo /etc/init.d/oracle-xe stop

```

Oracle XE comes with is SQLplus.
Start it type in terminal
```

sqlplus

```

You need set enviroment variables correctly
This might help with that
[http://ubuntuforums.org/showpost.php?p=7838671&postcount=4](http://ubuntuforums.org/showpost.php?p=7838671&postcount=4)

Oracle XE comes also with Application Expres (Apex), that is web interface to develope applications and run commands.
Xe preinstalled Apex version is 2.1.
You can upgarde it 
[http://www.oracle.com/technology/products/database/application_express/html/3.2_and_xe.html](http://www.oracle.com/technology/products/database/application_express/html/3.2_and_xe.html)

And see documentation about it
[http://www.oracle.com/technology/products/database/application_express/html/doc.html](http://www.oracle.com/technology/products/database/application_express/html/doc.html)

Also SQL Developer is nice tool to work with Oracle database
[http://www.oracle.com/technology/products/database/sql_developer/index.html](http://www.oracle.com/technology/products/database/sql_developer/index.html)


Might also help
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)
[http://www.oracle.com/technology/tec...n-kubuntu.html](http://www.oracle.com/technology/tec...n-kubuntu.html)

[http://www.oracle.com/pls/xe102/homepage](http://www.oracle.com/pls/xe102/homepage)

And Oracle XE do not come with any support.
You can try get support from Oracle Database 10g Express Edition forum
[http://forums.oracle.com/forums/forum.jspa?forumID=251](http://forums.oracle.com/forums/forum.jspa?forumID=251)

---

