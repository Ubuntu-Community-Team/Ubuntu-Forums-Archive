---
title: "Openldap and Active Directory hybrid"
date: 2012-02-13
forum: General Help
---

### Post by 13th Victim on 2012-02-13
I'm making a project in which I have to set an Openldap directory that work as a primary server together with an Active Directory server. For these servers I'm using Ubuntu 10.04 LTS and Windows 2K3 SP3.

I have done some research about how to merge them and found that using PAM is the most ideal way. Then there is NIS - which I'm not sure how it really works and Kerberos 5 - which is over and above my capabilities. 

Now I know how to make the basic services work like DHCP3, Bind9, OpenLDAP to work on their own - do these services need a special kind of configuration to work with AD? Do these services need to be somehow merged with PAM and/or NIS? Is Samba server needed for such a hybrid system? And what must be done on the AD side?

I know its a bit of a handful but any kind of help will be appreciated.
Thank you

---

### Post by 13th Victim on 2012-02-20
anyone?
if i posted something wrong just tell me

---

### Post by Khayyam on 2012-02-20
> **13th Victim said:**
> I'm making a project in which I have to set an Openldap directory that work as a primary server together with an Active Directory server.

I don't understand exactly what your trying to do. If the OpenLDAP is the "primary" then it needs to be setup to provide AD services, and that makes AD somewhat redundent. OpenLDAP can act as a replacement for AD, or the two can be united with authentication/user data replicated. Services provided by AD don't need to be provided by OpenLDAP if AD is available, unless your network is such that a 'fallover' is required, but this wouldn't make the OpenLDAP server "primary".

AD is simply a form of LDAP, but unlike OpenLDAP it comes defined to provide services for Windows networks. OpenLDAP is more of a 'blank slate', there is nothing predefined, every aspect of the schema must be written from scratch. This makes OpenLDAP alot more flexable than AD, but it also requires alot more skill to impliment. So, OpenLDAP can replace AD, or AD and OpenLDAP work in conjunction, each providing for certain needs, though replicating authentication and user data.  

> **13th Victim said:**
> I have done some research about how to merge them and found that using PAM is the most ideal way. Then there is NIS - which I'm not sure how it really works and Kerberos 5 - which is over and above my capabilities.

Merge what ... Authentication?

PAM is Linux's standard authentication mechanism, but authentication can be provided elsewhere (eg, OpenLDAP). Anything using PAM can be made to authenticate via LDAP by using pam_ldap.

NIS is a "directory protocol" providing information (email addresses, hostnames, usernames, NFS mounts, etc) LDAP has come to replace it in many respects.

Kerberos is an authentication protocol, it is often used as a method of client-server authentication, and as a means of authenticating LDAP quiries and data exchanges (replication).

> **13th Victim said:**
> Now I know how to make the basic services work like DHCP3, Bind9, OpenLDAP to work on their own - do these services need a special kind of configuration to work with AD? Do these services need to be somehow merged with PAM and/or NIS? Is Samba server needed for such a hybrid system? And what must be done on the AD side?

I don't think you do "know", remember OpenLDAP is a blank slate, it does nothing unless you define a schema for it, and like a database you need to add data to it via some method (either by querying another LDAP server and replicating the data, or writting .ldif's). Your schema must be setup in such a way that it matches to domain and data. This side of things can be alot of work, which is why OpenLDAP is primarily used in networks where the cost of centralisation is offset by the number of clients/services.

There are various how-to's out there covering replication, AD intergration (authentication), AD replacement, schema construction, etc. There are also some fairly good OpenLDAP books (ORA's for instance). It took me something like six months to get a grip on the subject, and after making alot of silly mistakes, and OpenLDAP dropping an "objectclass" that was being used to set a group value, had something fit for purpose. So, its somewhat of a steep curve to get from slapd running to serving data.

You should get use to alot of the following:

```
for i in $(find . -name *.ldif) ; do
    sed -i.bak s/// ${i}
    ldapmodify -D "cn=root,dc=domain,dc=tld " -w "$1" -x -v -f ${i} ;
done
```

Anyhow, I don't mean to be unhelpful, its just that having a clear idea of what is needed and how best to approach it will save you alot of time. If you haven't already read the [OpenLDAP Quick Start Guide]("http://www.openldap.org/doc/admin/quickstart.html") I'd suggest you do so. If you search for "OpenLDAP Active Directory syncronization" you'll find various how-to's on how to keep authentication data synconized between the two.

HTH ... khay

---

