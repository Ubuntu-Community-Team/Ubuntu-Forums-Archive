---
title: "ldap reading applied reading"
date: 2011-03-28
forum: General Help
---

### Post by siuchi on 2011-03-28
I moved from Centos ldap to ubuntu not long ago.
There's some big different fro me is that setting are no longer in a configuration file, and you need to input the setting into the ldap itself using ldapadd command.

I used something like the following command to input some replication setting and deleted the ldif file. Problem is how can i read/display those applied setting .

Many Thanks.

sudo ldapadd -c -Y EXTERNAL -H ldapi:/// -f consumer_sync.ldif

---

