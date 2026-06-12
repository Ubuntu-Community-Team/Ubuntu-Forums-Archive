---
title: "Problems with kipi-plugins since Digikam upgrade to 2.2"
date: 2011-10-11
forum: General Help
---

### Post by Usksider on 2011-10-11
Hi all,

Although I've been using Ubuntu for a while now I'm a complete novice at the way the system works, so I tend to leave well alone. Stupidly I tried to upgrade Digikam following Phillip's guide (on Digikam web).

The upgrade didn't work and I've had to strip Digikam 2.2 out and revert to an older (supported) version which (mostly) works. 

I've run in to a side issue though. It was recommended for me to re-install libgl1-mesa-glx but can't because the installation fails:

E: libgl1-mesa-glx: subprocess installed post-installation script returned error exit status 2
E: libglu1-mesa: dependency problems - leaving unconfigured
E: unity: dependency problems - leaving unconfigured

In detail:

Preconfiguring packages ...
Selecting previously deselected package libglide3.
(Reading database ... 254658 files and directories currently installed.)
Unpacking libglide3 (from .../libglide3_2002.04.10ds1-5_i386.deb) ...
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2.1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing libgl1-mesa-glx (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
 unity depends on libglu1-mesa | libglu1; however:
  Package libglu1-mesa is not configured yet.
  Package libglu1 is not installed.
  Package libglu1-mesa which provides libglu1 is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
Setting up libglide3 (2002.04.10ds1-5) ...
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libgl1-mesa-glx
 libglu1-mesa
 unity
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2.1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing libgl1-mesa-glx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx
 unity
 libglu1-mesa


The same sort of problem applies to kipi-plugins, which I was also advised to re-install. 


E: libgl1-mesa-glx: subprocess installed post-installation script returned error exit status 2
E: libglu1-mesa: dependency problems - leaving unconfigured
E: unity: dependency problems - leaving unconfigured
E: kipi-plugins: dependency problems - leaving unconfigured

In Detail:

(Reading database ... 254669 files and directories currently installed.)
Preparing to replace kipi-plugins 1.9.0-1ubuntu2 (using .../kipi-plugins_1.9.0-1ubuntu2_i386.deb) ...
Unpacking replacement kipi-plugins ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2.1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing libgl1-mesa-glx (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
 unity depends on libglu1-mesa | libglu1; however:
  Package libglu1-mesa is not configured yet.
  Package libglu1 is not installed.
  Package libglu1-mesa which provides libglu1 is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        dpkg: dependency problems prevent configuration of kipi-plugins:
 kipi-plugins depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
 kipi-plugins depends on libglu1-mesa | libglu1; however:
  Package libglu1-mesa is not configured yet.
  Package libglu1 is not installed.
  Package libglu1-mesa which provides libglu1 is not configured yet.
dpkg: error processing kipi-plugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 libgl1-mesa-glx
 libglu1-mesa
 unity
 kipi-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2.1) ...
update-alternatives: error: alternative link /usr/lib/xorg/extra-modules is already managed by i386-linux-gnu_gl_conf.
dpkg: error processing libgl1-mesa-glx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kipi-plugins:
 kipi-plugins depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing kipi-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity:
 unity depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libglu1-mesa:
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx which provides libgl1 is not configured yet.
dpkg: error processing libglu1-mesa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-glx
 kipi-plugins
 unity
 libglu1-mesa



Given my extremely low level of knowledge when it comes to hacking the O/S can anyone suggest what I ought to do now to rectify these errors?

Thanks in advance.

---

### Post by ghostborg on 2011-11-16
I have this exact same problem. PIA.

Update:
For me, it turned out Nvidia Current was pulling it's update from the PPA Philip5 that I added to install Handbrake.
I discovered this by clicking on details while attempting one of the failed updates.
I just disabled the repo and un-installed nvidia-current and immediately installed it again.

---

### Post by Usksider on 2011-11-18
I stripped out v2.2 and reinstalled v2.1.1 which works fine. Couldn't find a way to make v2.2 work for me at all :(

---

