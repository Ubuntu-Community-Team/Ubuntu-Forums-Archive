---
title: "Fix Broken Pakage"
date: 2011-06-02
forum: General Help
---

### Post by gypsumwolf on 2011-06-02
I can not install using apt or gdebi or dpkg.

I used gdebi to install xplico and killed it (oops) while it was installing.

I tried all of these.

apt-get clean
apt-get autoclean
apt-get autoremove
apt-get -f install
dpkg --configure -a
also tried recovery mode and the dpkg fix broken option.

It Didn't fix it.

The error when I try to install something like synaptic (via apt-get install synaptic):

```
Removing xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg: error processing xplico (--remove):
 subprocess installed post-removal script returned error exit status 100
Errors were encountered while processing:
 xplico
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by iclestu on 2011-06-02
> **gypsumwolf said:**
> I can not install using apt or gdebi or dpkg.

I used gdebi to install xplico and killed it (oops) while it was installing.

I tried all of these.

apt-get clean
apt-get autoclean
apt-get autoremove
apt-get -f install
dpkg --configure -a
also tried recovery mode and the dpkg fix broken option.

It Didn't fix it.

The error when I try to install something like synaptic (via apt-get install synaptic):

```
Removing xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg: error processing xplico (--remove):
 subprocess installed post-removal script returned error exit status 100
Errors were encountered while processing:
 xplico
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

what about 

```
apt-get purge xplico
```

as xplico seems to be causing the trouble then the rest (of course, be aware that this deletes config files for xplico  as well as the app but im guessing its not operational anyway?)

then you can clean up etc then re-install?

worth a blast?

---

### Post by gypsumwolf on 2011-06-02
It gives me a similar error:

```
apt-get purge xplico
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xplico
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 41.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124967 files and directories currently installed.)
Removing xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg: error processing xplico (--remove):
 subprocess installed post-removal script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xplico
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

That would suck it I have to reinstall Kubuntu and set everything back up. But I will if I have to.

---

### Post by iclestu on 2011-06-02
im sure that wont be necesary.

someone will know how to fix it....

The thought occured (now i am COMPLTELY stabbing in the dark)..... why not try to INSTALL xplico then remove it if there is a xplico related script missing???

---

### Post by gypsumwolf on 2011-06-02
When I try to install it again it works fine EXCEPT it fails again.

```
(Reading database ... 124967 files and directories currently installed.)
Removing xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg: error processing xplico (--remove):
 subprocess installed post-removal script returned error exit status 100
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xplico
Error during install: 'installArchives() failed'root@box:~/Downloads# 

```

---

### Post by iclestu on 2011-06-02
i got no more ideas but im sure someone who actually knows what they are doing will be along shortly ;)

---

### Post by gypsumwolf on 2011-06-02
Thanks for trying. If I don't get an answer probably within an hour or so  I may just reinstall since I need a working system for my job.

---

