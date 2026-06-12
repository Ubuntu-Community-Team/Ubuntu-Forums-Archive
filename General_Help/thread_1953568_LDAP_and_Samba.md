---
title: "LDAP and Samba"
date: 2012-04-06
forum: General Help
---

### Post by taustin on 2012-04-06
I am trying to set up a Windows domain using Samba 3 (I don't need anything that would require Active Directory). I have gotten Sambe to do what I need it to do as a PDC, but I suspect I'll need backup domain servers in remote locations for things to work acceptable. This, from what I can tell, is done with LDAP, to replicate domain records automatically.
 
I cannot figure out how to get LDAP to work. I have found a number of howtos, and every one gets me to a point where something fails. The most relevant one seems to be [https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html) (which is for the version of Ubuntu I'm working with). But, it says "During the install you were prompted to define administrative credentials." This did not happen, and when I get to "**ldapsearch -x -LLL -H ldap:/// -b dc=example,dc=com dn"**, I get "no such record."
 
What am I missing?

---

### Post by wyliecoyoteuk on 2012-04-06
Not sure that this is related, but on Unix, LDAP stuff is often case sensitive.
Simlar to Samba, where domain, workgroup and NetBIOS computer names need to be in uppercase to work.
Not an LDAP guru, but this has caught me out several times in the past.

If you have a windows PC,Softerra's free LDAP browser is a good tool for troubleshooting these problems.

---

### Post by taustin on 2012-04-06
I've been bitten by case sensitivity many times (being mostly a Windows victim), but in thise case, that's not it. The instructions seem to imply when I go the apt-get install, it should be asking for some information to establish the administrative credentials, and it's not doing that. Other versions of the same instrctions (the ones for 11.04, in particular) have some additonal steps that (I think) do that manually, but I don't really understand what's going on so I'm not sure.

---

