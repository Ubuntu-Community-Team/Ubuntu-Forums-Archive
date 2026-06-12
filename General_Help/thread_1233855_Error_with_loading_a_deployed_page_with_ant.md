---
title: "Error with loading a deployed page with ant"
date: 2009-08-07
forum: General Help
---

### Post by DesignerX on 2009-08-07
I used 'ant deploy' command for deploying a web page (exactly as stated at the sun tutorial for hello1 at "http://java.sun.com/javaee/5/docs/tutorial/doc/bnadx.html#bnaen")

Everything goes well but when I try to load the page in the browser I get the following error :

HTTP Status 500 -

type Exception report

message

descriptionThe server encountered an internal error () that prevented it from fulfilling this request.

exception

org.apache.jasper.JasperException: PWC6033: Unable to compile class for JSP

root cause

java.lang.NullPointerException


I installed java 6 jdk and still has this problem.

Do I need to configure ant or asadmin in some way ??

thx.

---

### Post by furuno on 2009-08-07
Well, it is quite a hassle (for me) to deploy application that way, altough might soudn irrelevant, but, why don't you just deploy your application in your IDE (NetBeans / Eclipse)? It's much easier, for example, F6 is all you need to deploy in NetBeans...

---

### Post by DesignerX on 2009-08-07
I need to deploy it with ant for a certain task.

At the web root directory I run : 'ant deploy' which deploys the files and creates the .WAR file successfully.

The problem is accessing the web page through the browser. I get the same error when using the asadmin verifier tool.

---

### Post by DesignerX on 2009-08-07
Solved it. It seems that I didn't startup the web server properly. 
Anyway now it works :)

---

