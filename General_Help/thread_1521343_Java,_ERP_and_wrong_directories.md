---
title: "Java, ERP and wrong directories"
date: 2010-06-30
forum: General Help
---

### Post by amdefeo on 2010-06-30
Hi everyone, 

This may be the simplest problem ever but its driving me crazy, hopefully someone can help me. 

I am trying to install Adempiere the open source ERP database on Ubuntu 10.04. The issue I am having is with Java. I have Java-6 jre & jdk installed, but the database is looking for java in the following location 
/usr/lib/jvm/java-6-openjdk -and finally is looking for- lib/tools.jar

Right now java lives in the etc directory, and I do not have the jvm and lib folder and I dont have the tools.jar file. 
The strange part is on both of my other laptops running 10.04 have the proper java folders in the proper locations, for the database to run, but not on my home computer. 
I am using oracle 10g, and I do have that installed and running. 
Can anyone give me advice on what I may be missing or how to get the jvm folder and the tools.jar file in the /usr directory. 

Thanks.

---

