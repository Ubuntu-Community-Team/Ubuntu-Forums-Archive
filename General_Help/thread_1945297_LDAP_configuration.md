---
title: "LDAP configuration"
date: 2012-03-22
forum: General Help
---

### Post by abasel on 2012-03-22
I have installed LDAP as per [http://www.youtube.com/watch?v=DM_UQVVVtoY]("http://www.youtube.com/watch?v=DM_UQVVVtoY") and all went well except for the following:

When I visit the phpldapadmin page, the user credentials default to cn=admin,dc=example,dc=com. I overwrite these with the correct ones and log in only to be told the following:

> 
Logged in as: 
	
	dc=example,dc=com
This base entry does not exist.Create it?


I have edited ldap.conf correctly so I have no idea where it is pulling dc=example,dc=com from.

---

### Post by abasel on 2012-03-25
Came right 

[https://help.ubuntu.com/community/InstallingphpLDAPadmin](https://help.ubuntu.com/community/InstallingphpLDAPadmin)

:-)

---

