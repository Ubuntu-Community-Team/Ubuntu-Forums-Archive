---
title: "How to do usermaping with Active Directory using pam_pkcs11"
date: 2012-03-06
forum: General Help
---

### Post by newbbuntu on 2012-03-06
We have a PKI environment in Active Directory where we can use smartcard from Windows clients to login.
 
I've also setup ubuntu 11.10 with samba/winbind and I'm able to login using Active Directory credentials to ubuntu 11.10.
 
Now, I'm trying to get the smartcard authentication to work on ubuntu 11.10 and have been using the 
[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard) as a reference.
 
 
I tried adding an Active Directory username ex)jsmith that is mapped to the smartcard in /etc/pam_pkcs11/subject_mapping as ex)
 
/C=US/O=U.S. Government/OU=DoD/OU=PKI/OU=CONTRACTOR/CN=RA... -> jsmith
 
Has anyone been able to do the usermapping with Active Directory using pkcs11?
 
 
OS: Ubuntu 11.10 oneiric
libpam-pkcs11 0.6.6-2build1 (also tried pam_pkcs11 -0.6.7)

---

