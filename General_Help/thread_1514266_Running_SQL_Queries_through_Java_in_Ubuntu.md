---
title: "Running SQL Queries through Java in Ubuntu"
date: 2010-06-20
forum: General Help
---

### Post by Frikkie[RSA] on 2010-06-20
Hi. I would like some help to run sql queries in Ubuntu. For a school IT project, we must write a Java program that runs queries. Seeing that I'm going away on holiday and will be away from my Win7 desktop, I will have to work on my Ubuntu laptop.

When I run my program, I get these two sql exceptions:

```
sun.jdbc.odbc.JdbcOdbcDriver
No suitable driver found for jdbc:odbc:ITPAT2010
```Note: it is not my program that is causing the problem, since it works fine on Win7. But here's my code anyway:

```
void OpenDB()
   {
        System.out.println("INTO BRIDGE");
        String url = "jdbc:odbc:ITPAT2010";  //JOU BRUG SE NAAM
        try
        {
            Class.forName ("sun.jdbc.odbc.JdbcOdbcDriver");
        }
        catch (java.lang.ClassNotFoundException e)
        {
            //JOptionPane.showMessageDialog (null,"ClassNotFoundException: "+e.getMessage ());
            System.out.println(e.getMessage ());
        }
        try
        {
            con = DriverManager.getConnection (url, "Admin", "awe");
        }
        catch (SQLException ex)
        {
            //JOptionPane.showMessageDialog (null,"SQLException: " + ex.getMessage ());
            System.out.println(ex.getMessage ());
        }

        System.out.println("BRIDGE OPEND");
   }
```I believe the drivers that handles the connection to the database aren't installed. The format of my database is: *.accdb (was created on Win7 using Office 2010). I can't open this file, probably because I have no database programs installed?

Anyway, help would really be appreciated, else I will be forced to go back to XP on my laptop in order to get my project done.

Thanks

Oh, I should probably add that I'm using Ubuntu 9.10 - the Karmic Koala.

---

### Post by Mic[RSA] on 2010-06-29
I would also like to know the solution to this problem. I have been told to download SQLite, yet still I need to set up a bridige for the queries to run. How do you set up a bridge in Ubuntu?

---

