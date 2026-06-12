---
title: "openLDAP server problem to add my .ldif"
date: 2011-12-12
forum: General Help
---

### Post by xMusic on 2011-12-12
Hi,

I'm on a virtual machine, using Ubuntu 10.04

I followed many tutorials and I always have problems at the same step.

This is one of the tutorial that is pretty simple and clear to use imo:

[http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/openldap-server.html)

I install the packets with no problem
I add the differents schemes with no problems
I write and add the "backend.example.com.ldif" without any problem

BUT, for the "frontend.example.com.ldif i am asked for a "Enter LDAP password" :

[http://i221.photobucket.com/albums/dd161/hieijr/LDAPbug.jpg](http://i221.photobucket.com/albums/dd161/hieijr/LDAPbug.jpg)

impossible to get through this step, no matter what password i try and even after i change the pass manually with the "slappasswd"

in every single tutorial I follow when I am asked for a LDAP password I can't get past it...

please help me

---

### Post by luvshines on 2011-12-14
Well from the tutorial, the password 'secret' should work fine if you have copied the exact same frontend ldif, I guess.

Did u change it in the ldif file ?

---

