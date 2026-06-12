---
title: "Apt-Get Screwed Up When Terminal Was Closed Durring Install"
date: 2009-07-01
forum: General Help
---

### Post by lightnb on 2009-07-01
I was trying to install package "Bacula" when the terminal was closed partway through install. I can't remove the package, because apt doesn't think it's installed.

But I can't install it again either, because I get a whole bunch of garbage on the terminal about broken dependencies.

How can I manually remove the broken partial install so I can try again?

---

### Post by colau on 2009-07-01
> **lightnb said:**
> I was trying to install package "Bacula" when the terminal was closed partway through install. I can't remove the package, because apt doesn't think it's installed.

But I can't install it again either, because I get a whole bunch of garbage on the terminal about broken dependencies.

How can I manually remove the broken partial install so I can try again?
```

sudo dpkg --configure -a

```

---

### Post by lightnb on 2009-07-01
Doesn't seem to help:

```

me@SwiftFishII:~# sudo dpkg --configure -a
Setting up bacula-common (2.4.2-1ubuntu6) ...
chown: cannot access `/var/run/bacula': No such file or directory
dpkg: error processing bacula-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bacula-console:
 bacula-console depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-console (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-fd:
 bacula-fd depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-fd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-client:
 bacula-client depends on bacula-console (>= 2.4.2-1ubuntu6); however:
  Package bacula-console is not configured yet.
 bacula-client depends on bacula-fd (>= 2.4.2-1ubuntu6); however:
  Package bacula-fd is not configured yet.
dpkg: error processing bacula-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-traymonitor:
 bacula-traymonitor depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-traymonitor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bacula-common
 bacula-console
 bacula-fd
 bacula-client
 bacula-traymonitor

```

---

### Post by colau on 2009-07-01
> **lightnb said:**
> Doesn't seem to help:

```

me@SwiftFishII:~# sudo dpkg --configure -a
Setting up bacula-common (2.4.2-1ubuntu6) ...
chown: cannot access `/var/run/bacula': No such file or directory
dpkg: error processing bacula-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bacula-console:
 bacula-console depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-console (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-fd:
 bacula-fd depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-fd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-client:
 bacula-client depends on bacula-console (>= 2.4.2-1ubuntu6); however:
  Package bacula-console is not configured yet.
 bacula-client depends on bacula-fd (>= 2.4.2-1ubuntu6); however:
  Package bacula-fd is not configured yet.
dpkg: error processing bacula-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula-traymonitor:
 bacula-traymonitor depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.
dpkg: error processing bacula-traymonitor (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bacula-common
 bacula-console
 bacula-fd
 bacula-client
 bacula-traymonitor

```

```

sudo apt-get install bacula

```

---

### Post by lightnb on 2009-07-01
After "Do you want to continue [Y/n]?" and the usuall installation banter, I get:

```

Setting up bacula-common (2.4.2-1ubuntu6) ...
chown: cannot access `/var/run/bacula': No such file or directory
dpkg: error processing bacula-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bacula-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by wojox on 2009-07-01
Try uninstalling it

```
sudo apt-get remove bacula
```

Then reinstall

---

### Post by Soul-Sing on 2009-07-01
Maybe remove it with/using -purge-.

---

### Post by lightnb on 2009-07-01
sudo apt-get remove bacula
sudo apt-get purge bacula

both produce:
```
Package bacula is not installed, so not removed
```


...followed by all of this garbage:
```

Setting up bacula-common (2.4.2-1ubuntu6) ...                                                                                   
chown: cannot access `/var/run/bacula': No such file or directory                                                               
dpkg: error processing bacula-common (--configure):                                                                             
 subprocess post-installation script returned error exit status 1                                                               
dpkg: dependency problems prevent configuration of bacula-console:                                                              
 bacula-console depends on bacula-common (= 2.4.2-1ubuntu6); however:                                                           
  Package bacula-common is not configured yet.                                                                                  
dpkg: error processing bacula-console (--configure):                                                                            
 dependency problems - leaving unconfigured                                                                                     
Setting up gawk (1:3.1.6.dfsg-0ubuntu1) ...                                                                                     
No apport report written because the error message indicates its a followup error from a previous failure.                      

dpkg: dependency problems prevent configuration of bacula-fd:
 bacula-fd depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.                  
dpkg: error processing bacula-fd (--configure):                 
 dependency problems - leaving unconfigured                     
dpkg: dependency problems prevent configuration of bacula-client:
 bacula-client depends on bacula-console (>= 2.4.2-1ubuntu6); however:
  Package bacula-console is not configured yet.                       
 bacula-client depends on bacula-fd (>= 2.4.2-1ubuntu6); however:     
  Package bacula-fd is not configured yet.                            
dpkg: error processing bacula-client (--configure):                   
 dependency problems - leaving unconfigured                           
dpkg: dependency problems prevent configuration of bacula-traymonitor:
 bacula-traymonitor depends on bacula-common (= 2.4.2-1ubuntu6); however:
  Package bacula-common is not configured yet.                           
dpkg: error processing bacula-traymonitor (--configure):                 
 dependency problems - leaving unconfigured                              
Setting up exim4-config (4.69-5ubuntu2) ...                              
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already                                                                                        
                                        No apport report written because MaxReports is reached already                          
                                                                                                      Adding system-user for exim (v4)                                                                                                                          

Setting up exim4-base (4.69-5ubuntu2) ...

Setting up exim4-daemon-light (4.69-5ubuntu2) ...
 * Starting MTA                                                                                                          [ OK ] 

Setting up exim4 (4.69-5ubuntu2) ...

Setting up bsd-mailx (8.1.2-0.20071201cvs-3) ...

Setting up mailx (1:20071201-3) ...
Errors were encountered while processing:
 bacula-common                           
 bacula-console                          
 bacula-fd                               
 bacula-client                           
 bacula-traymonitor                      
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by colau on 2009-07-01
System>Administration>Synaptic Package Manager>Edit>Fix Broken Packages

---

### Post by Soul-Sing on 2009-07-01
```
sudo apt-get purge bacula-common bacula-console bacula-fd bacula-client bacula-traymonitor
```

(sudo apt-get update
sudo apt-get upgrade)

---

### Post by lightnb on 2009-07-01
Thanks, that fixed it.

---

