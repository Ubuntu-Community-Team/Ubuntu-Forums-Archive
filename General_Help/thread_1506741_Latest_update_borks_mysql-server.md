---
title: "Latest update borks mysql-server"
date: 2010-06-10
forum: General Help
---

### Post by GuiGuy on 2010-06-10
I (stupidly) allowed an update to run (Lucid), knowing full well that something will break, as it always does <sigh>;

Anyway, I get this

> 
dpkg: error processing mysql-server-5.1 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.1
 mysql-server


The problem now is that it won't let me uninstall it, purge it, configure it etc. Whatever I attempt in relation to mysql-server the system seems to hang. 

The apt history log tells me 
> 
Start-Date: 2010-06-11  06:56:45
Upgrade: mysql-server-5.1 (5.1.41-3ubuntu12.1, 5.1.41-3ubuntu12.3)



This is the mysql error log
> 00611  7:01:40 [Note] Plugin 'FEDERATED' is disabled.
100611  7:01:41  InnoDB: Started; log sequence number 0 201192
100611  7:01:41 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
100611  7:01:41 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100611  7:01:41 [ERROR] Aborting

100611  7:01:41  InnoDB: Starting shutdown...
100611  7:01:42  InnoDB: Shutdown completed; log sequence number 0 201192
100611  7:01:42 [Note] /usr/sbin/mysqld: Shutdown complete


syslog isn't telling me much either

> 
Jun 11 07:01:42 FF01VB init: mysql main process (1156) terminated with status 1
Jun 11 07:01:42 FF01VB init: mysql main process ended, respawning



I then tried remove and purge through synaptic. I hung everytime, with something obviously running in the background.

I manually stopped mysql-server and synaptic continued with an error. 

So, it seems I cannot remove, install, purge or run mysql-server now.


I really need some help here. TIA

---

### Post by drdos2006 on 2010-06-10
Same happened on my 9.10 64 bit MYSQL client installation.
I did this.

Open Synaptic (System/Administration "Synpatic Package Manager")
Click on "Edit" from the top menu.
Click on "Fix Broken Packages"
Click on "Apply Marked Changes"
Confirm and click "Apply"
Waited for completion. took about 5 minutes.
Fixed..

regards

---

