---
title: "bacula and database creation"
date: 2010-10-27
forum: General Help
---

### Post by pmatos on 2010-10-27
Hi,

I have installed bacula which by default installed the mysql backend. Asked me for the root password of mysql but since I couldn't remember I cancelled the configuration. I checked it out afterwards and now I know it but I can't find my way back to the bacula database setup screen once again. I have read that there should be a create_bacula_database script somewhere but I can't find it. Any tips on how to set this up?

Cheers,

Paulo Matos

---

### Post by TeoBigusGeekus on 2010-10-28
Check if bacula has a settings folder in your home partition and delete it (you'll of course lose any customization you've made to it). Then try to run it again.

Else:
```
find / -name create_bacula_database 2>/dev/null
```

---

### Post by pmatos on 2010-10-28
> **TeoBigusGeekus said:**
> Check if bacula has a settings folder in your home partition and delete it (you'll of course lose any customization you've made to it). Then try to run it again.

Else:
```
find / -name create_bacula_database 2>/dev/null
```

That's the problem. I don't really know how to run it again. create_bacula_database doesn't seem to be shipped by ubuntu.

---

### Post by TeoBigusGeekus on 2010-10-28
How did you run it in the first place?

---

### Post by pmatos on 2010-10-28
> **TeoBigusGeekus said:**
> How did you run it in the first place?

It was ran automatically with sudo apt-get install bacula.

I guess it's an automatic ubuntu configure script of some sort. I can't find a way to rerun it!

---

### Post by TeoBigusGeekus on 2010-10-28
Try
```
sudo apt-get purge bacula
```
delete any specs folder in your home partition
and then
```
sudo apt-get install bacula
```

---

### Post by pmatos on 2010-10-28
> **TeoBigusGeekus said:**
> Try
```
sudo apt-get purge bacula
```
delete any specs folder in your home partition
and then
```
sudo apt-get install bacula
```

Unfortunately it didn't work. Actually now I get an error from debconf:

```
pmatos@mietzekatze:~$ sudo apt-get install bacula
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavahi-qt3-1 liblualib50 kdelibs5-data liblua50
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bacula-client bacula-common-mysql bacula-console bacula-director-common
  bacula-director-mysql bacula-fd bacula-sd bacula-sd-mysql bacula-server
  bsd-mailx dbconfig-common mtx
Suggested packages:
  bacula-doc dds2tar scsitools mt-st
Recommended packages:
  bacula-sd-tools
The following NEW packages will be installed
  bacula bacula-client bacula-common-mysql bacula-console
  bacula-director-common bacula-director-mysql bacula-fd bacula-sd
  bacula-sd-mysql bacula-server bsd-mailx dbconfig-common mtx
0 upgraded, 13 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/2,400kB of archives.
After this operation, 6,783kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
debconf: Unknown template field '_description', in stanza #9 of /tmp/bacula-director-mysql.template.109132

Selecting previously deselected package bacula-common-mysql.
(Reading database ... 329323 files and directories currently installed.)
Unpacking bacula-common-mysql (from .../bacula-common-mysql_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package bacula-console.
Unpacking bacula-console (from .../bacula-console_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package bsd-mailx.
Unpacking bsd-mailx (from .../bsd-mailx_8.1.2-0.20100314cvs-1_amd64.deb) ...
Selecting previously deselected package bacula-director-common.
Unpacking bacula-director-common (from .../bacula-director-common_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package dbconfig-common.
Unpacking dbconfig-common (from .../dbconfig-common_1.8.46_all.deb) ...
Selecting previously deselected package bacula-director-mysql.
Unpacking bacula-director-mysql (from .../bacula-director-mysql_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package mtx.
Unpacking mtx (from .../mtx_1.3.12-3ubuntu1_amd64.deb) ...
Selecting previously deselected package bacula-sd.
Unpacking bacula-sd (from .../bacula-sd_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package bacula-sd-mysql.
Unpacking bacula-sd-mysql (from .../bacula-sd-mysql_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package bacula-server.
Unpacking bacula-server (from .../bacula-server_5.0.2-1ubuntu1_all.deb) ...
Selecting previously deselected package bacula-fd.
Unpacking bacula-fd (from .../bacula-fd_5.0.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package bacula-client.
Unpacking bacula-client (from .../bacula-client_5.0.2-1ubuntu1_all.deb) ...
Selecting previously deselected package bacula.
Unpacking bacula (from .../bacula_5.0.2-1ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for ureadahead ...
Setting up bacula-common-mysql (5.0.2-1ubuntu1) ...
Setting up bacula-console (5.0.2-1ubuntu1) ...
Setting up bsd-mailx (8.1.2-0.20100314cvs-1) ...
update-alternatives: using /usr/bin/bsd-mailx to provide /usr/bin/mailx (mailx) in auto mode.
Setting up bacula-director-common (5.0.2-1ubuntu1) ...
Setting up dbconfig-common (1.8.46) ...
Setting up bacula-director-mysql (5.0.2-1ubuntu1) ...
debconf: Unknown template field '_description', in stanza #9 of /var/lib/dpkg/info/bacula-director-mysql.templates

dbconfig-common: writing config to /etc/dbconfig-common/bacula-director-mysql.conf
 * Stopping Bacula Director...                                           [ OK ] 
Processing configuration...Ok.
 * Starting Bacula Director...                                           [ OK ] 
Setting up mtx (1.3.12-3ubuntu1) ...
Setting up bacula-sd (5.0.2-1ubuntu1) ...
 * Starting Bacula Storage daemon...                                     [ OK ] 
Setting up bacula-sd-mysql (5.0.2-1ubuntu1) ...
Setting up bacula-server (5.0.2-1ubuntu1) ...
Setting up bacula-fd (5.0.2-1ubuntu1) ...
 * Starting Bacula File daemon...                                        [ OK ]
Setting up bacula-client (5.0.2-1ubuntu1) ...
Setting up bacula (5.0.2-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
```

And when I actually try to start it:
```
pmatos@mietzekatze:~$ sudo bconsole
[sudo] password for pmatos: 
Connecting to Director localhost:9101
pmatos@mietzekatze:~$
```

So, basically nothing happens.

---

