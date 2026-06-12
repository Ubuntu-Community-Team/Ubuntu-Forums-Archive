---
title: "How To Install FreeRadius using Mysql (Ubuntu 10.04)"
date: 2011-01-29
forum: General Help
---

### Post by Mellow Heart on 2011-01-29
[CENTER]**[SIZE=3]please help me To complete install freeradius[/SIZE]**[/CENTER]
 
[CENTER]**[SIZE=3]see this link[/SIZE]**
[**[SIZE=3]http://ubuntuforums.org/showthread.php?t=1169178[/SIZE]**]("http://ubuntuforums.org/showthread.php?t=1169178")[/CENTER]
 
[CENTER]**[SIZE=3]when i need to execute fr2-mysql-daloradius-and-freeradius.sql in mysql qeury browser :[/SIZE]**[/CENTER]
 
[CENTER]**[SIZE=3]this error show to me :[/SIZE]**[/CENTER]
```

[CENTER]**[SIZE=3]Error while executing query: CREATE TABLE radacct (radacctid bigint(21) NOT NULL auto_increment,acctsessionid varchar(32) NOT NULL default '',acctuniqueid varchar(32) NOT NULL default '',username varchar(64) NOT NULL default '',groupname varchar(64) NOT NULL default '',realm varchar(64) default '',nasipaddress varchar(15) NOT NULL default '',nasportid varchar(15) default NULL,nasporttype varchar(32) default NULL,acctstarttime datetime NULL default NULL,acctstoptime datetime NULL default NULL,acctsessiontime int(12) default NULL,acctauthentic varchar(32) default NULL,connectinfo_start varchar(50) default NULL,connectinfo_stop varchar(50) default NULL,acctinputoctets bigint(20) default NULL,acctoutputoctets bigint(20) default NULL,calledstationid varchar(50) NOT NULL default '',callingstationid varchar(50) NOT NULL default '',acctterminatecause varchar(32) NOT NULL default '',servicetype varchar(32) default NULL,framedprotocol varchar(32) default NULL,framedipaddress varchar(15) NOT NULL default '',acctstartdelay int(12) default NULL,acctstopdelay int(12) default NULL,xascendsessionsvrkey varchar(10) default NULL,PRIMARY KEY (radacctid),KEY username (username),KEY framedipaddress (framedipaddress),KEY acctsessionid (acctsessionid),KEY acctsessiontime (acctsessiontime),KEY acctuniqueid (acctuniqueid),KEY acctstarttime (acctstarttime),KEY acctstoptime (acctstoptime),KEY nasipaddress (nasipaddress)) :No database selected (errno: 1046)Click 'Ignore' if you'd like to have this error ignored until the end of the script[/SIZE]**[/CENTER]
 
 
 

```
 
[CENTER]**[SIZE=3]and in this step :[/SIZE]**[/CENTER]

**[SIZE=3]```
sudo vi /etc/freeradius/radius.conf
```[/SIZE]**
```

 

[CENTER]**[SIZE=3]There will be a section in there reguarding instantiate for authorize. Just search for sql1 above that create a line with sql. Save and exit[/SIZE]**[/CENTER]

```
 

[CENTER]**[SIZE=3]In this step what you want me to write in this file ???[/SIZE]**
 
[CENTER]**[SIZE=3]thank you[/SIZE]**[/CENTER]
 
 
 
 
 
 
 
 
 
[/CENTER]

---

### Post by TeoBigusGeekus on 2011-01-29
The error message you get, is because you haven't selected a database.
As the tutorial says, you should create a database named radius
```
CREATE DATABASE radius;
```
and then select it
```
USE radius;
```

As for your second question, open the /etc/freeradius/radius.conf file (although I think it should be radiusd.conf) and search for the Instantiation section. Add a line in that section, before the closing bracket of instantiate{}, with the text sql.

---

### Post by Mellow Heart on 2011-01-30
thank you for your answer

I will try it 

But now I'm having another problem
When you try me for the graphical interface stop working when you type the user name
But keep writing works index
And letters in the keyboard and mouse are not working
I tried writing it from terminal

```

sudo dpkg-reconfigure -phigh -a
```

But back to me this error

```
invoke-rc.d: initscript atd, action "start" failed
```

and i trying to access to recovery menu

xfix try to auto repair graphic problems

but whiout any solution
I am working on gnome

---

### Post by Mellow Heart on 2011-01-31
up .......?????/

---

### Post by Mellow Heart on 2011-02-01
**any body help me**

---

