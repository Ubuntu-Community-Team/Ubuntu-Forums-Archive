---
title: "&quot;overlay dynlist&quot; with LDAP server using slapd.d (not slap.conf) :Ubuntu9.10?"
date: 2010-04-01
forum: General Help
---

### Post by shams_i on 2010-04-01
Hi
The desired implementation is to control user logins on different lab machines based on the project groups. 
Scenario: Bob is part of project group 'mars' & John is part of 'venus' then I have added lab machines x1-x3 to group 'mars' & y1-y3 to group venus. Now I want John to only access machines allocated for project 'mars' i.e x1 to x3 & John to access machines allocated for 'venus' i.e y1 to y3

I went through this link __[http://www.hurricanelabs.com/september2009_login_security_using_openldap_and_pam ]("http://www.hurricanelabs.com/september2009_login_security_using_openldap_and_pam")learned that it can be achieved using "overlay dynlist". Please correct me if I've got it wrong.
However my lab LDAP server is running on Ubuntu 9.10 (karmic koala) and it is using slapd.d (not slapd.conf)
So now if I want to attempt to use "overlay dynlist" how should I go about it? Has anyone done this before? Any help will be appreciated.

---

