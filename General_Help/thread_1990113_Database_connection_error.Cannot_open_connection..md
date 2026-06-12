---
title: "Database connection error.Cannot open connection."
date: 2012-05-29
forum: General Help
---

### Post by Renjith Jithu on 2012-05-29
Hi,

      We installed OSCAR 12.1.4RC2 in a Ubuntu server machine.
We followed the instructions in the manual at:

[http://www.oscarmanual.org/oscar_emr_12/developers/installation/deb](http://www.oscarmanual.org/oscar_emr_12/developers/installation/deb)

  Everything goes fine. Installation was success. We can see the OSCAR login page by typing

[http://serverip:8080/Oscar12](http://serverip:8080/Oscar12)

        Once we enter the login credentials and click Sign-In, it comes with
an error message saying :

Database connection error.Cannot open connection.
Please correct and try again.

   Looks like the Mysql connection parameters were not set properly.
We did some google search. Whats mentioned is that the connection parameters are
in one oscar.properties file. But what see is an oscar_mcmaster.properties file.
It's still pointing to the old oscar_mcmaster database and a wrong password.

Whats happening..? Any idea ...?
How do we fix this ..?
We tried manually changing the parameters in this file and even re-started Tomcat6.
Still it doesn't solve the problem.

With Regards
Renjith

---

### Post by dino99 on 2012-05-29
i've looked at that manual url but there is no details installation guide or changelog. So its hard to know how this prog is running.

To help you:
- glance at errors/warnings logged
- launch this prog in a terminal to know about errors

- send message to OSCAR team.

---

