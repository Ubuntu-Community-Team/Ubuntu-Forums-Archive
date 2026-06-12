---
title: "Hibernate connection failing  ..org.hibernate.exception.JDBCConnectionException:"
date: 2009-12-12
forum: General Help
---

### Post by vimodchandra on 2009-12-12
Hi,
  I developed a small Spring application which uses hibernate for database connection.It is deployed in Tomcat 6.0.20 and was working perfectly in my Windows machine.When I deployed my Tomcat server in my Ubuntu Server(8.04 LTS) system,this exception is coming when spring tries to connect to Database.Should I modify anything before migrating my spring+hibernate+tomcat application to Ubuntu from my Windows platform...? Please help...

---

### Post by vimodchandra on 2009-12-13
Yes..it got corrected.The problem was,I dint comment the line
             #bind-address = localhost
in my /etc/mysql/my.cnf file.

---

### Post by abani-1 on 2011-09-27
Hi,
Please verify that the version of the database used in ubuntu and in your window are same other wise change the corresponding jar file for the driver.

---

### Post by lisati on 2011-09-27
Back to sleep for this thread.

---

