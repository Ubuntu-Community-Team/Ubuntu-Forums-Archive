---
title: "unable to run build command"
date: 2011-01-16
forum: General Help
---

### Post by alphaforce125 on 2011-01-16
I'm trying to complete the install of GLOBUS but I'm having a post-install config problem.

running: perl gt-server-ca.pl -y
returns: setup-simple-ca failure. See gt server log for details.
Log contains: ERROR:  could not run build command: /sandbox/globus/globus-5.0.2/sbin/gpt-build -force /home/sebastian/.globus/simpleCA//globus_simple_ca_783e00f0_setup-0.20.tar.gz 

So I attempted running: sudo perl gt-server-ca.pl -y
returns: Please set GLOBUS_LOCATION to your install dir

Problem is GLOBUS_LOCATION is setup. confirmed by 
running set | grep GLOBUS_LOCATION
returns: GLOBUS_LOCATION=/sandbox/globus/globus-5.0.2
which is correct.

I'm really lost why it's unable to properly complete, any help would be greatly appreciated.

Following instructions as set here: [http://globus.org/toolkit/docs/5.0/5.0.2/admin/quickstart/](http://globus.org/toolkit/docs/5.0/5.0.2/admin/quickstart/)

Specifically under "1.3. Setting up security on your first machine"

Thanks in advance.

---

### Post by alphaforce125 on 2011-01-19
bump

---

