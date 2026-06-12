---
title: "Install OSSEC HIDS On Ubuntu 11.10 with mysql Support generate Error"
date: 2012-02-26
forum: General Help
---

### Post by bkhezry on 2012-02-26
I work with OSSEC HIDS In Ubuntu 11.10:
[http://www.ossec.net/wiki/Know_How:DatabaseOutput](http://www.ossec.net/wiki/Know_How:DatabaseOutput)

When install with mysql support, it back me this error

[PHP]/tmp/ccuS4FYw.o: In function mysql_osdb_connect': /home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:164: undefined reference tomysql_init'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:178: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:183: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:186: undefined reference to 'mysql_real_connect'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:189: undefined reference to 'mysql_error'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:190: undefined reference to 'mysql_close'

/tmp/ccuS4FYw.o: In function `mysql_osdb_close':

...[/PHP]
I'm Sure That Mysql in install, test it with sample C code and back me data record. I Know Problem is in /src/Config.OS that generat with:

make setdb
CDB not point to the lib of mysql that need to install OSSEC HIDS. but I Don't Know How To Fix It.

Thanks anyone can help me. Thanks alot.

---

### Post by Dangertux on 2012-02-26
> **bkhezry said:**
> I work with OSSEC HIDS In Ubuntu 11.10:
[http://www.ossec.net/wiki/Know_How:DatabaseOutput](http://www.ossec.net/wiki/Know_How:DatabaseOutput)

When install with mysql support, it back me this error

[PHP]/tmp/ccuS4FYw.o: In function mysql_osdb_connect': /home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:164: undefined reference tomysql_init'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:178: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:183: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:186: undefined reference to 'mysql_real_connect'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:189: undefined reference to 'mysql_error'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:190: undefined reference to 'mysql_close'

/tmp/ccuS4FYw.o: In function `mysql_osdb_close':

...[/PHP]I'm Sure That Mysql in install, test it with sample C code and back me data record. I Know Problem is in /src/Config.OS that generat with:

make setdb
CDB not point to the lib of mysql that need to install OSSEC HIDS. but I Don't Know How To Fix It.

Thanks anyone can help me. Thanks alot.

Have you tried symlinking the lib to whatever filename OSSEC is looking for?

That should allow install to continue.

Hope that helps.

---

### Post by ddpbsd on 2012-03-01
> **bkhezry said:**
> I work with OSSEC HIDS In Ubuntu 11.10:
[http://www.ossec.net/wiki/Know_How:DatabaseOutput](http://www.ossec.net/wiki/Know_How:DatabaseOutput)

When install with mysql support, it back me this error

[PHP]/tmp/ccuS4FYw.o: In function mysql_osdb_connect': /home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:164: undefined reference tomysql_init'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:178: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:183: undefined reference to 'mysql_options'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:186: undefined reference to 'mysql_real_connect'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:189: undefined reference to 'mysql_error'

/home/bkhezry/Downloads/ossec-hids-2.6/src/os_dbd/db_op.c:190: undefined reference to 'mysql_close'

/tmp/ccuS4FYw.o: In function `mysql_osdb_close':

...[/PHP]I'm Sure That Mysql in install, test it with sample C code and back me data record. I Know Problem is in /src/Config.OS that generat with:

make setdb
CDB not point to the lib of mysql that need to install OSSEC HIDS. but I Don't Know How To Fix It.

Thanks anyone can help me. Thanks alot.

Perhaps this message on the ossec user mailing list will help: [http://www.mail-archive.com/ossec-list@googlegroups.com/msg12795.html](http://www.mail-archive.com/ossec-list@googlegroups.com/msg12795.html)

It boils down to Ubuntu having a broken MySQL installation.

---

### Post by bkhezry on 2012-03-01
Thanks For Your Replay.
I Before See This Page.
But I Don't Know How Can Change Information In Config.OS
I Found That Ubuntu 11.10 Has Problem With Lib Mysql And Ossec Can't Reference To Lib Of Mysql Correctly. :confused: :(

---

