---
title: "OpenLDAP slapadd: slap_init no backend"
date: 2009-07-18
forum: General Help
---

### Post by ericg_ on 2009-07-18
I am running Ubuntu 8.10 with the OpenLDAP Server that comes with it.

I ran the following command:

[B]slapadd -l init.ldif -b dc=example,dc=com
[/B]
and received the following error:

[COLOR=Red]**slapadd: slap_init no backend for "dc=example,dc=com"**[/COLOR]

I have been searching all over the Web for the fix to this issue.  I believe I have checked all of the appropriate conf files for errors (see the attached conf files; slapd.conf, ldap.conf, and init.ldif).

In the slapd.conf file I specify the backend as hdb.  I feel like I am missing something so simple.

This is my first time working with LDAP.  I understand the framework but I not following all of the multiple indepencies very well.  


Follow-on Question:
Are there any VERY GOOD (and free)  administration tools?

Thanx,
EricG :confused:

---

### Post by ericg_ on 2009-07-18
I have decided to retrieve the sample ldap.conf, slapd.conf, and init.ldif files from the orignal tar-file.  We will see if I can grasp this server environment.

Thanx for viwing this thread.

If anyone has some well commented, but not complicated, conf file a beginner can utilize, please send them my way.

Again, thanx...

---

