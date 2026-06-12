---
title: "PHP + Oracle Instant Client 11g R2 problems"
date: 2012-01-28
forum: General Help
---

### Post by PascalGR on 2012-01-28
Dear all,

I'm trying to install PECL's oci8 module for PHP and I have stacked to the error below.

What I've done so far is:

[LIST=1]
[*]Downloaded Oracle Instant Client 11g R2 (11.2.0.3.0-2) RPM packages (basic, sqlplus, odbc, jdbc, devel (SDK), tools)
[*]Converted the RPM versions of the packages to deb files
[*]Successfully installed the generated debian packages
[/LIST]
Now I want to be able to connect to Oracle databases through PHP. To do so, I try to install the OCI8 package through PECL, but make fails with the following error:

```
checking Oracle Instant Client SDK header directory... configure: error: Oracle Instant Client SDK header files not found
ERROR: `/tmp/pear/temp/oci8/configure --with-oci8=instantclient,/usr/lib/oracle/11.2/client' failed

```I have build-essential, libaio1, php5-dev packages installed (if not I wouldn't get there), and I don't know what the problem is. ORACLE_HOME is installed at "/usr/lib/oracle/11.2/client", with the includes directory (symbolic link) correctly points to /usr/include/oracle/11.2/client'.

Any help would be greatly appreciated.

System Info:
Ubuntu 11.10 32-bit
PHP 5.3.x
Oracle Instant Client 11g R2

Thanks in advance,
Pascal

---

### Post by PascalGR on 2012-01-28
I've figured out, I was missing the lib/ directory of the pecl prompt for the ORACLE_HOME directory. The correct command was:
# pecl install oci8

at the prompt, I've given:
instantclient,/usr/lib/oracle/11.2/client**/lib**

---

### Post by BlinkinCat on 2012-01-28
Hi, You should mark thread as "solved" using the thread tools at top of page.
This will benefit others - :)

---

