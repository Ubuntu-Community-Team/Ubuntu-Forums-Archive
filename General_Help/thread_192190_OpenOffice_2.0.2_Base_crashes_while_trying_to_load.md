---
title: "OpenOffice 2.0.2 Base crashes while trying to load JDBC driver"
date: 2006-06-08
forum: General Help
---

### Post by ashok_kumar on 2006-06-08
I was very happy with the previous release of Ubuntu 5.10 except for one problem. I regularly connect to MySQL database hosted on another server and also on *localhost* thorugh JDBC connector which was shipping with Ubuntu 5.10. I tried initially to configure ODBC connector to connect to MySQL server, but failed miserably. Then one day I tried JDBC with *com.mysql.jdbc.Driver* and I was successful. I was using it regularly. It had one problem though that OpenOffice Date type of fields were not working. But it was perhaps a problem related with OpenOffice 2.0.1 as same problem was noticed by me in Windows version also and it was sloved with upgrade to OpenOffice 2.0.2.

When I came to know that Ubuntu 6.06 will be shipping with OpenOffice 2.0.2, I was eagerly waiting for the day of launch. I did a clean install with dual boot (Windows XP Pro). But when I tried to connect to MySQL server, and tried to load JDBC driver *com.mysql.jdbc.Driver* which is internally provided, OpenOffice Base just crashed with the following message and went for recovery: -

[FONT="Courier New"]Due to an unexpected error, OpenOffice.org crashed. All the files you are working on will be saved now. The next time OpenOffice.org is launched, your files will be recovered automatically.[/FONT]

Thereafter, OpenOffice recovered my files and again restarted. This happens every time I try to load the JDBC driver. This was working without any problem in OpenOffice 1.1.129/ Ubuntu 5.10.

Can anybody help. Step by step approach would be welcome as I have only average familiarity with Linux. I shall be greatful.

Ashok Kumar

---

### Post by driverkt on 2006-06-08
Go to this site: [http://dev.mysql.com/downloads/connector/j/3.1.html](http://dev.mysql.com/downloads/connector/j/3.1.html)

Download the JDBC driver, put it in your java classpath, and it will help you connect to MySQL databases.  If you want to connect to another kind, you'll need to find the appropriate driver elsewhere.  

Hope that helps.

---

### Post by driverkt on 2006-06-08
Basically, Dapper doesn't ship with this driver by default, so you'll need to install it just like you did with 5.10.

---

### Post by ashok_kumar on 2006-06-10
I did what was suggested. But I had requested for a step-by-step approach as my Linux knowledge is limited.

I created a directory /home/ashok/.openoffice2/user/java/ and put the file mysql-connector-java-3.1.13-bin.jar therein. Thereafter went to tools->option->java and added the jar file in the classpath. The java driver loaded successfully.

However, when I tried to access MySQL database, it gave a long list of exceptions for which the ***screenshot*** is attached.

Thereafter, I tried to locate where all .jar files of OpenOffice are placed. It was /usr/share/java/OpenOffice. I tried to add the folder. The driver could not be loaded. I then included it in the classpath. The driver was loaded successfully, but then it gave same error while trying to connect.

I also tried changing owner and group of the jarfile, and use encoding system in place of UTF-8, which is normally what I use. It was of no use. Help!!!!!!!!!!!!.

And by the way, I did not load any driver in case of Ubuntu 5.10, it just worked out of the box. I did not even have to specify the classpath.

Ashok Kumar

---

### Post by ashok_kumar on 2006-08-24
The sulution to the problem is available at [https://launchpad.net](https://launchpad.net) in response to bug no.50063.

Best of luck!!!

---

