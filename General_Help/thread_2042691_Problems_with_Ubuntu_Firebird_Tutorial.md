---
title: "Problems with Ubuntu Firebird Tutorial"
date: 2012-08-15
forum: General Help
---

### Post by p3aul on 2012-08-15
Hi!
I am attempting to set up firebird 2.1 using tutorial from this webpage:
[https://help.ubuntu.com/community/Firebird2.1/On/Ubuntu](https://help.ubuntu.com/community/Firebird2.1/On/Ubuntu)

Everything went great till I come to this point:
>  This will change the current directory to where the file is, decompress the file, change ownership of the file to the user **Firebird**  so that it can access it, and then move the example database to the  Firebird Data folder. To "connect" to the example database fire up the  Terminal once again and run the following command. 
 
 isql-fb SQL> connect "/var/lib/firebird/2.1/data/employee.fdb " user 'SYSDBA' password 'SYSDBApassword';
 Where  "user" is the SYSDBA user and "password" is the password you set for  the SYSDBA Admin in earlier steps. If you connect to the database  successfully you should see the following output in the terminal. 
 
 Database:  "/var/lib/firebird/2.1/data/employee.fdb ", User: SYSDBA SQL> At this point Firebird informs me:
```
Command error: connect "/var/lib/firebird/2.1/data/employee.fdb " user 'SYSDBA' 1432 'SYSDBApassword'
```Well the first thing I did was to check my password. So I naved to the  directory where the password was kept. The password was correct. But  here I noticed something unusual. It also said the user name was sysdba  NOT SYSDBA as the tutorial stated in the connect statement(see above).

It's got me completely bumfuzzled. To come this far...:(
Any help would be greatly appreciated!
Thanks,
Paul

---

