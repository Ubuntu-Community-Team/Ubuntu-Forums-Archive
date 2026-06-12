---
title: "sabayon /w openldap?"
date: 2010-09-26
forum: General Help
---

### Post by jeight on 2010-09-26
I have an LTSP standalone server up and running. I have openldap + SAMBA  so I can log into Windows with my user credientials. My problem comes  when trying to intergrate sabayon with my ldap users. I made a profile  called "Student Profile" and then put the following into   /etc/sabayon/users.xml

<?xml version="1.0" encoding="UTF-8"?>
<profiles>
  <ldap uri="ldap://[192.168.2.3]("http://192.168.2.3/")">
    <profilemap search_base="ou=Users,dc=sparky,dc=local" 
                scope="one" query_filter="(uid=%u)" 
                result_attribute="Student Profile"/>
  </ldap>
  <default profile=""/>
</profiles>


If this is completely wrong please let me know. I know that I'm on the right track, but so far it's a no go.

---

