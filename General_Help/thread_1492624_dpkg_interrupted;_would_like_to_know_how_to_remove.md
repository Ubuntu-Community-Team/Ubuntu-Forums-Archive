---
title: "dpkg interrupted; would like to know how to remove unneeded installs"
date: 2010-05-24
forum: General Help
---

### Post by orchidfire on 2010-05-24
Hi all,

I attempted to install gnucash just now to test it out, but, in the middle of the installation (which I was doing through Terminal), something happened and dpkg was interrupted.  I'm unable to provide the Terminal output because (a) for some reason, prior to the error messages about a segment fault, the terminal shows a number of blank lines and does not show me what happened before the segfault, and (b) after the segfault, when I tried starting up gedit or make a screen capture, the prompt windows were blank, so I was unable to save the terminal output to either.

When I restarted Ubuntu, it told me that /tmp was not ready; I waited for it to mount, and, apparently, it did, as Ubuntu restarted fine.

I tried updating my software, as the icon in my panel was telling me I needed updates.  However, it told me that dpkg had been interrupted and that I needed to troubleshoot it with [FONT="Courier New"]sudo apt-get install -f[/FONT], which then told me to run [FONT="Courier New"]sudo dpkg --configure -a[/FONT], which I did, receiving the following output:

```
sqlu@thalamus:~$ sudo apt-get install -f
[sudo] password for sqlu: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
sqlu@thalamus:~$ sudo dpkg --configure -a
Setting up libktoblzcheck1c2a (1.24-2) ...

Processing triggers for man-db ...
Setting up slib (3b1-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing slib (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for install-info ...
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt3-mt (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libgwenhywfar47 (3.11.3-1) ...

Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up libyaml-syck-perl (1.07-1build1) ...
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
Setting up libaqbanking-data (4.2.3-1) ...

Setting up libguile-ltdl-1 (1.6.8-10) ...

dpkg: dependency problems prevent configuration of libaqbanking29-plugins-qt:
 libaqbanking29-plugins-qt depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libaqbanking29-plugins-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqbanking8:
 libqbanking8 depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libqbanking8 (--configure):
 dependency problems - leaving unconfigured
Setting up libaqbanking29 (4.2.3-1) ...

Setting up guile-1.6-libs (1.6.8-10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing guile-1.6-libs (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libaqhbci17 (4.2.3-1) ...

Setting up libaqofxconnect5 (4.2.3-1) ...

Setting up libaqbanking-plugins-libgwenhywfar47 (4.2.3-1) ...
dpkg: dependency problems prevent configuration of guile-1.6:
 guile-1.6 depends on guile-1.6-libs; however:
  Package guile-1.6-libs is not configured yet.
dpkg: error processing guile-1.6 (--configure):
 dependency problems - leaving unconfigured
Setting up libaqbanking29-plugins (4.2.3-1) ...
Setting up aqbanking-tools (4.2.3-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 slib
 libqt3-mt
 guile-1.6-slib
 libaqbanking29-plugins-qt
 libqbanking8
 guile-1.6-libs
 guile-1.6
sqlu@thalamus:~$ 

```

It looks like there were errors with a number of packages, and I'm guessing something else might have also broken.  Since I'm already using homebank and don't really need to use gnucash, I was wondering if there was a way for me to check what was installed by gnucash and remove those packages, since they're cluttering my system, and I'm concerned that they might interfere with other packages if they're broken or something.

I've been using Ubuntu for about two years now and have some knowledge of the command line and such, but I'd say my skills are still pretty basic, so I would really appreciate explanations of what happened or the commands that I would need to do to fix this.  I'm running 64-bit 10.04.

Thanks so much!

---

### Post by bumanie on 2010-05-24
In terminal > sudo aptitude purge gnucash

---

### Post by orchidfire on 2010-05-25
> **bumanie said:**
> In terminal

I tried running the command, and it looks like it's encountering the same errors:

```
sqlu@thalamus:~$ sudo aptitude purge gnucash
[sudo] password for sqlu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  guile-1.6 guile-1.6-libs guile-1.6-slib libaqbanking29-plugins-qt libqbanking8 libqt3-mt slib 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up guile-1.6-libs (1.6.8-10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing guile-1.6-libs (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6:
 guile-1.6 depends on guile-1.6-libs; however:
  Package guile-1.6-libs is not configured yet.
dpkg: error processing guile-1.6 (--configure):
 dependency problems - leaving unconfigured
Setting up slib (3b1-3ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing slib (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on guile-1.6; however:
  Package guile-1.6 is not configured yet.
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt3-mt (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libqbanking8:
 libqbanking8 depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libqbanking8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libaqbanking29-plugins-qt:
 libaqbanking29-plugins-qt depends on libqbanking8; however:
  Package libqbanking8 is not configured yet.
 libaqbanking29-plugins-qt depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libaqbanking29-plugins-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                             Errors were encountered while processing:
 guile-1.6-libs
 guile-1.6
 slib
 guile-1.6-slib
 libqt3-mt
 libqbanking8
 libaqbanking29-plugins-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up slib (3b1-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing slib (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt3-mt (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
Setting up guile-1.6-libs (1.6.8-10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing guile-1.6-libs (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libaqbanking29-plugins-qt:
 libaqbanking29-plugins-qt depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libaqbanking29-plugins-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqbanking8:
 libqbanking8 depends on libqt3-mt (>= 3:3.3.8-b); however:
  Package libqt3-mt is not configured yet.
dpkg: error processing libqbanking8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of guile-1.6:
 guile-1.6 depends on guile-1.6-libs; however:
  Package guile-1.6-libs is not configured yet.
dpkg: error processing guile-1.6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 slib
 libqt3-mt
 guile-1.6-slib
 guile-1.6-libs
 libaqbanking29-plugins-qt
 libqbanking8
 guile-1.6
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

sqlu@thalamus:~$ 

```

Also, gnucash was never installed on my system (typing "gnucash" into the run dialogue brings up nothing).  Does that affect this?

---

