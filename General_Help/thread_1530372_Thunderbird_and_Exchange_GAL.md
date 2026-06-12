---
title: "Thunderbird and Exchange GAL"
date: 2010-07-13
forum: General Help
---

### Post by wallywojo on 2010-07-13
If you want to get Thunderbird working just like outlook for looking up email addresses of people in the organization, follow these steps. I just wanted to post here because I have seen many differing posts about how to configure and I am sure this is version dependent of the exchange server, but this is what for certain works for me.

1) Select Address Book in toolbar.
2) Select File--> New --> LDAP Directory
3) On the General tab populate these values:
[LIST]
[*]Name: general name to refer to this address book
[*]Hostname: the name of the global address server
[*]Base DN: if above was dd1.mycompany.com this entry should read DC=mycompany,DC=com
[*]Port number: based on SSL setting default
[*]Bind DN: use format of <username>@<domain> so wallywojo@mycompany
[*]Use secure connection (SSL) - uncheck this option
[/LIST]

For getting the hostname, I found it easiest on an Office XP Outlook client by selecting the To button on a message, from there right click in the upper right the words 'Global Address List' and select properties. The current server is the value needed for Hostname property in LDAP directory.

All other settings I left as default. Good Luck.

---

