---
title: "What is the purpose of the deb mysql-client?"
date: 2010-09-29
forum: General Help
---

### Post by helloworld1215 on 2010-09-29
[http://packages.ubuntu.com/lucid/mysql-client-5.1](http://packages.ubuntu.com/lucid/mysql-client-5.1)

I just removed mysql-client after installing php5-mysql and my php is connecting to my remote server fine. What is the purpose of mysql-client? Is it a direct API for external servers?

[http://packages.ubuntu.com/lucid/i386/mysql-client-core-5.1/filelist](http://packages.ubuntu.com/lucid/i386/mysql-client-core-5.1/filelist)

So it's basically /usr/bin/mysql that allows connection to external servers

---

### Post by DaithiF on 2010-09-30
It provides a command line interface to a mysql server, whether local or remote.  Its not required by php, php has its own library to interact with a mysql server.

---

