---
title: "openldap setup - can't add cn=config file"
date: 2010-06-18
forum: General Help
---

### Post by Daimonan on 2010-06-18
For the past couple days I've been working on setting up an openLDAP server, and its been a bit of a trying experience.  I haven't had much luck finding tutorials or documents which take a straightforward, step-by step approach to explaining the setup and how everything works.

But, I digress.  Right now, I'm working on configuring the server.  As I understand it, the slapd.config file is not the 'preferred' way of configuring the server anymore - instead, you're supposed to create a config.ldif file and upload it, where the settings are all stored in their own small directory structure.

I've installed bdb, I've got openLDAP up and can run the slapd daemon.  I'm having trouble uploading the config.ldif file, however.  Here's what I'm doing:

slapadd -F /usr/local/etc/openldap/slapd.d/ -n 0 -l config.ldif

I get the following error:

slapadd: could not add entry dn="cn=config" (line=1): 
_#                      8.78% eta   none elapsed            none spd  41.5 k/s 
Closing DB...


My config.ldif file is almost exactly the same as the one outlined here: [http://www.openldap.org/doc/admin24/slapdconf2.html](http://www.openldap.org/doc/admin24/slapdconf2.html).  

Do I need to do some other type of setup?  Maybe get the database running, etc?  Let me know if any of you guys have any ideas.

---

