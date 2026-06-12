---
title: "java &amp; SQL"
date: 2010-02-27
forum: General Help
---

### Post by nischalinn on 2010-02-27
I want to learn Java programing language and MySQL in linux.What packages do I've to install?Are there any sites providing basic tutorials of java and MySQL?

---

### Post by johngreth on 2010-02-27
This is a good place to start for java: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

And here for mysql: [http://dev.mysql.com/doc/refman/5.5/en/tutorial.html](http://dev.mysql.com/doc/refman/5.5/en/tutorial.html)

Also, you'll need to install Java. There are many different options. GCJ is installed by default, but it is lacking some important features. See:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

For developing in java I suggest using Eclipse, which can be found in the Software Center.

For mysql you'll need to install "mysql-server".

If you're interested in creating JSP (Java Server Pages), you'll need to install tomcat server. The easiest way to do this is to run ```
sudo tasksel
```Just move down to tomcat, press the space bar to select it, and press enter to install it. I'm somewhat unfamiliar with this, but you may also need to install LAMP Server to make tomcat and mysql talk to each other. If you choose to do this, just be aware that people on the Internet may have access to the programs you write and test because installing LAMP and Tomcat will effectively turn your computer into a basic server.

I don't know anything about using java and mysql together, but this looks like a good place to start: [http://dev.mysql.com/usingmysql/java/](http://dev.mysql.com/usingmysql/java/)

---

