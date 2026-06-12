---
title: "Evolution LDAP Bug?"
date: 2011-06-28
forum: General Help
---

### Post by ocwo92 on 2011-06-28
I'm trying to add an LDAP directory to Evolution, but Evolution doesn't honor my searches.

The directory is searchable from the command line, e.g.:

```
ldapsearch -x -h crtdir.certifikat.dk -b "c=DK" "mail=email@addre.ss"
```

will return the result of the search. Similarly, I can search the directory in Thunderbird.

I'm using Evolution 2.32.2 on Natty. The "Server" field contains "crtdir.certifikat.dk", and the port is 389. I've specified an insecure connectoin and anonymous login. The login field is left empty. In the details tab, the search base is "c=DK", and the search tree is specified as subtree. The search filter is left empty.

I suspect Evolution is having problems with the fact that the LDAP directory requires a simple connection ("-x" in the command line), which doesn't seem to be an option in Evolution's LDAP settings.

Can anyone help me out? How can I troubleshoot Evolution's connection?

---

### Post by ocwo92 on 2011-06-29
> **ocwo92 said:**
> Can anyone help me out? How can I troubleshoot Evolution's connection?
I decided to set up my own LDAP server, and with full debug logging, it looks like Evolution doesn't even connect to the server. I've filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/803331") report on it.

---

### Post by dcstar on 2011-06-30
> **ocwo92 said:**
> I decided to set up my own LDAP server, and with full debug logging, it looks like Evolution doesn't even connect to the server. I've filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/803331") report on it.

I have used Evolution to connect via LDAP to Microsoft servers, it is pretty tricky to get going and certain things do not work as expected.

---

