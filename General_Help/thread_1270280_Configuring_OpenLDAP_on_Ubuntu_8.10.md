---
title: "Configuring OpenLDAP on Ubuntu 8.10"
date: 2009-09-19
forum: General Help
---

### Post by paragkalra on 2009-09-19
Hello Folks,

I just installed 'slapd-2.4.11' and 'ldap-utils' on my Ubuntu 8.10 using Synaptic Manager.

I have following queries related to configuring LDAP on Ubuntu. First & Foremost I am completely new to LDAP so please don't mind if my questions are really funny :)

1. After installation the file '/etc/ldap/ldap.conf' doesn't seem to contain the parameters like 'rootpw' & 'rootdn'. Am I seeing the wrong file or is there any other ldap configuration file on Ubuntu?

2. What is my default root node address and how to change it?

3. My machine doesn't have any FQDN. Its name is  - 'station3' and I don't intend to give it a FQDN. Now my question can I have my root node address set to 'dc=station3,dc=home'? If yes, then I guess it has to be through 'ldapmodify' but can someone please share the exact syntax?

Thanks in Advance....

---

### Post by paragkalra on 2009-09-19
One more question:

4. Is there an LDAP browser available on Ubuntu?

---

