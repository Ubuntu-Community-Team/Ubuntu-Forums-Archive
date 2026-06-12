---
title: "jdbc - what driver do i use???"
date: 2010-12-26
forum: General Help
---

### Post by rhythmiccycle on 2010-12-26
i'm trying to get started with jdbc.

i have mysql setup and running fine.

i want to use jdbc so i can write java that can add row to a table, and get info from a database.

the database is already set up
(I made user called "guest" password "123" that has access to the database "emotherearth")

```

grant all privileges on emotherearth.* to guest@localhost identified by "123";

```



right now i'm just trying to make a connection
(next i want to read a table)


Of all the websites I looked at, the following code is the best I can find (and make sense of)

```

//  Establish a connection to an Interbase database using JDBC and ODBC. 
import java.sql.*; 

class JdbcTest1
{
  public static void main (String[] args)
  { 
    try
    { 
      // Step 1: Load the JDBC ODBC driver. 
      Class.forName("sun.jdbc.odbc.JdbcOdbcDriver"); 
      // Step 2: Establish the connection to the database. 
      String url = "jdbc:odbc:localhost"; 
      Connection conn = DriverManager.getConnection(url,"guest","123");  
    }
    catch (Exception e)
    { 
      System.err.println("Got an exception! "); 
      System.err.println(e.getMessage()); 
    } 
  } 
}

```


when i run that I get the out put:
```

$ java JdbcTest1 
Got an exception! 
sun.jdbc.odbc.JdbcOdbcDriver

```

this output make me think that I'm using the wrong driver.
I have no idea what to do next,

please help

---

### Post by burton247 on 2010-12-26
Probably better to post in the programming section!

I use mysql-connector-java it comes as a jar file that you'll have to link.

I then use this to load it up, different to what you have:

Class.forName("com.mysql.jdbc.Driver").newInstance();

---

### Post by rhythmiccycle on 2010-12-26
> **burton247 said:**
> Probably better to post in the programming section!

I use mysql-connector-java it comes as a jar file that you'll have to link.

I then use this to load it up, different to what you have:

Class.forName("com.mysql.jdbc.Driver").newInstance();

Thanks for the reply,
I post here b/c I don't get replies in the other sections.

Where do I get the jar file? Is there a website?

---

### Post by burton247 on 2010-12-26
[http://dev.mysql.com/downloads/connector/j/](http://dev.mysql.com/downloads/connector/j/)

That should do it. I assumed the programming section would answer a programming question but if you say you get a better response here.

---

### Post by rhythmiccycle on 2010-12-28
I got it to work:

The key step was running this in the terminal

```

sudo apt-get install libmysql-java

```

i also had to change the url,

the following is the code that compiled and ran without errors

```

//  Establish a connection to an Interbase database using JDBC and ODBC. 
import java.sql.*; 

class JdbcTest1
{
  public static void main (String[] args)
  { 
    try
    { 
      // Step 1: Load the JDBC ODBC driver. 
     Class.forName("com.mysql.jdbc.Driver").newInstance();
      // Step 2: Establish the connection to the database. 
      String url = "jdbc:mysql://localhost:3306/mysql"; 
      Connection conn = DriverManager.getConnection(url,"root","password");  
    }
    catch (Exception e)
    { 
      System.err.println("Got an exception! "); 
      System.err.println(e.getMessage()); 
    } 
  } 
}


```

---

