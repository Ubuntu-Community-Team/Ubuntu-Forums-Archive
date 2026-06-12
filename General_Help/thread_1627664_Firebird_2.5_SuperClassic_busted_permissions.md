---
title: "Firebird 2.5 SuperClassic busted permissions"
date: 2010-11-21
forum: General Help
---

### Post by yyyc186 on 2010-11-21
Fresh clean install of Firebird 2.5 SuperClassic.
Install the examples package.

Ran following shell to unbundle the examples.

sudo  install -o firebird -g firebird -m 0660 \
    /usr/share/doc/firebird2.5-examples/examples/empbuild/employee.fdb.gz \
    /var/lib/firebird/2.5/data/
sudo  gunzip /var/lib/firebird/2.5/data/employee.fdb.gz

Now if I try the tried and true example:

roland@roland-Generic-Desktop1:~$ isql-fb
Use CONNECT or CREATE DATABASE to specify a database
SQL> connect "/var/lib/firebird/2.5/data/employee.fdb " user 'SYSDBA' password '*****';
Statement failed, SQLSTATE = HY000
Can't access lock files' directory /tmp/firebird
SQL> exit
CON> ;


but, if I use sudo

roland@roland-Generic-Desktop1:~$ sudo isql-fb
Use CONNECT or CREATE DATABASE to specify a database
SQL> connect "/var/lib/firebird/2.5/data/employee.fdb " user 'SYSDBA' password '*****';
Database:  "/var/lib/firebird/2.5/data/employee.fdb ", User: SYSDBA
SQL> show tables
CON> ;
       COUNTRY                                CUSTOMER                       
       DEPARTMENT                             EMPLOYEE                       
       EMPLOYEE_PROJECT                       JOB                            
       PROJECT                                PROJ_DEPT_BUDGET               
       SALARY_HISTORY                         SALES                          

SQL> exit
CON> exit
CON> ;

roland@roland-Generic-Desktop1:~$ lsb_release -rd
Description:    Ubuntu 10.10
Release:        10.10
roland@roland-Generic-Desktop1:~$ 

Exact same problem when trying to create a database

roland@roland-Generic-Desktop1:~$ isql-fb
Use CONNECT or CREATE DATABASE to specify a database
SQL> create database '/home/roland/test.fdb' user 'SYSDBA' password '*****';
Statement failed, SQLSTATE = HY000
Can't access lock files' directory /tmp/firebird
SQL> exit
CON> ;

roland@roland-Generic-Desktop1:~$ sudo isql-fb
Use CONNECT or CREATE DATABASE to specify a database
SQL> create database '/home/roland/test.fdb' user 'SYSDBA' password '*****';
SQL> exit;
roland@roland-Generic-Desktop1:~$ 

package was installed via synaptic.

Is there a work around?

---

