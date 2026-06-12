---
title: "Lucid Problems"
date: 2010-05-02
forum: General Help
---

### Post by cmcanulty on 2010-05-02
Since I upgraded I have no sound on anything and I get this error message on every install I need some advice to fix this, thanks I tried rebooting with no result
```
cmcanulty@Gateway:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cmcanulty@Gateway:~$ 

```

---

### Post by mk1w86 on 2010-05-02
You need to put sudo in front of the command like this:

```
sudo apt-get -f install
```

to give it root privileges. ;)

How does this command relate to your sound problems?

---

### Post by cmcanulty on 2010-05-02
That still gives the error at the end
```
cmcanulty@Gateway:~$ sudo apt-get -f install
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libmarble4 (4:4.4.2-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmarble4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmikmod2 (3.1.11-a-6.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmikmod2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqalculate4 (0.9.6-4ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqalculate4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt3-mt (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsmpeg0 (0.4.5+cvs20030824-2.2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsmpeg0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libsdl-mixer1.2:
 libsdl-mixer1.2 depends on libmikmod2 (>= 3.1.10); however:
  Package libmikmod2 is not configured yet.
 libsdl-mixer1.2 depends on libsmpeg0; however:
  Package libsmpeg0 is not configured yet.
dpkg: error processing libsdl-mixer1.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of marble:
 marble depends on libmarble4 (= 4:4.4.2-0ubuntu2); however:
  Package libmarble4 is not configured yet.
dpkg: error processing marble (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pdfedit:
 pdfedit depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error procesNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          sing pdfedit (--configure):
 dependency problems - leaving unconfigured
Setting up python-lxml (2.2.4-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lxml (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libmarble4
 libmikmod2
 libqalculate4
 libqt3-mt
 libsmpeg0
 libsdl-mixer1.2
 marble
 pdfedit
 python-lxml
E: Sub-process /usr/bin/dpkg returned an error code (1)
cmcanulty@Gateway:~$ 

```

---

