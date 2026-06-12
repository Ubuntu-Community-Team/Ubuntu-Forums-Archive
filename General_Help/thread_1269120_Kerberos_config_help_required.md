---
title: "Kerberos config help required"
date: 2009-09-17
forum: General Help
---

### Post by Vantrax on 2009-09-17
Im looking for a rather knowledgeable person that has experience with configuring client side Kerberos config files (krb5.conf) to handle multiple realms with capath settings to allow auth queries to two domains.

I have two domains, a staff domain and a student domain. The student domain has a trust relationship (Hierarchical) set up with the staff domain so that on Windows systems staff can log into student environments with their own account.

That trust relationship does not appear to map automatically into the MIT Kerberos/PAM configurations (as far as I can tell) so you have to configure both realms in the krb5.conf file and have a relationship set up with capaths that effectively tries the student, then the staff domain for auth validation.

The problem is I have no idea how to pull that off. 

Here is the file that i have managed so far:

cat /etc/krb5.conf

```
[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmin.log

[libdefaults]
 default_realm = STUDENT-TEST.AD.EXAMPLE.EDU
 dns_lookup_realm = true
 dns_lookup_kdc = true
 ticket_lifetime = 4h
 forwardable = yes

[realms]
 STUDENT-TEST.AD.EXAMPLE.EDU = {
  kdc = student-test.adexample.edu:88
  admin_server = student-test.ad.example.edu:749
  default_domain = student-test.ad.example.edu
 }

 STAFF-TEST.AD.EXAMPLE.EDU = {
  kdc = staff-test.ad.example.edu:88
  admin_server = staff-test.ad.example.edu:749
  default_domain = staff-test.ad.example.edu
 }

[domain_realm]
 .student-test.ad.example.edu = STUDENT-TEST.AD.EXAMPLE.EDU
 student-test.ad.example.edu = STUDENT-TEST.AD.EXAMPLE.EDU
 .staff-test.ad.example.edu = STAFF-TEST.AD.EXAMPLE.EDU
 staff-test.ad.example.edu = STAFF-TEST.AD.EXAMPLE.EDU

[capath]
 STUDENT-TEST.AD.EXAMPLE.EDU = {
	STAFF-TEST.AD.EXAMPLE.EDU = .
 }

[appdefaults]
 pam = {
   debug = false
   ticket_lifetime = 36000
   renew_lifetime = 36000
   forwardable = true
   krb4_convert = false
 }
```


Any ideas? Hints? Advice?

---

