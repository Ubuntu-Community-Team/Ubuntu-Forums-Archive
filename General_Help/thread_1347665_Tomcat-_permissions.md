---
title: "Tomcat- permissions"
date: 2009-12-06
forum: General Help
---

### Post by karthi_slm on 2009-12-06
Hai

I set the following in the tomcat-users.xml file
<role rolename="manager"/>
<user username="tomcat" password="karthik" roles="manager"/>
<role rolename="admin"/>
<user username="tomcat" password="karthik" roles="admin"/>
but it repeatedly asking me for the password.
I checked my password is correct
is there any thing wrong in this

Looking for the help..........

---

### Post by karthi_slm on 2009-12-14
Hai Guys,

                  I fixed my problem. Now I am able to see the tomcat web application manager page.
What I did is I changed the folder and file permission of tomcat6 and tomcat-users.xml file.
Then I enroll the login user,save it . It works.....

Thanks team.

---

