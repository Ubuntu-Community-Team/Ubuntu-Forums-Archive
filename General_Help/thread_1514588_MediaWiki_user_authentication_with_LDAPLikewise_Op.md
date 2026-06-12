---
title: "MediaWiki user authentication with LDAP/Likewise Open"
date: 2010-06-21
forum: General Help
---

### Post by getdanonit on 2010-06-21
Hi all,

I've been trying to get this working for a while now to no avail. If someone could just point me in the right direction would be a great help.

I am running Ubuntu Server 10.04 with Mediawiki 1.15.14 installed. I am trying to setup Active Directory authentication for my mediawiki. 

Ideally I would like to be using the already working likewise-open AD authentication on my ubuntu server. Has anyone else had success in configuring mediawiki to use the likewise authentication? 

If not, maybe you could help with this guide 

[http://ryandlane.com/blog/2009/03/23/using-the-ldap-authentication-plugin-for-mediawiki-the-basics-part-1/]("http://ryandlane.com/blog/2009/03/23/using-the-ldap-authentication-plugin-for-mediawiki-the-basics-part-1/")

I need to complete the SSL part. Everything else is in place and I believe this is all that is left to do to get this working. My DC's are self certifying and I can get the information about the CA certificate by running this command

```
openssl s_client -connect adserver.test.example.com:636
```

I just don't know which packages (if any) are required and where to put the CA certificate in the ubuntu system so mediawiki uses it. 

Also if I get this option working will this impact on my current likewise setup? Basically if I go installing ldap packages will these screw with likewise?

Ideally using likewise would make life easier but I realise that could be my week accounted for.

Thoughts anyone?

Thank you.

---

### Post by getdanonit on 2010-06-25
Anyone? Anything? Yes I'm a noob....

---

