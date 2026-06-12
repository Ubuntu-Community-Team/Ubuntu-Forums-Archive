---
title: "Synaptic or apt-get not working..."
date: 2010-02-26
forum: General Help
---

### Post by anup.techonly on 2010-02-26
I installed SAGE unsuccessfully yesterday and after that there are lots os error occurring.. I can not install/remove anything using Synaptic or apt-get.

Please help.

Through synaptic manager it shows..whenever I try to install/remove something..

E: libgmpxx4ldbl: subprocess installed post-installation script returned error exit status 2
E: libgmp3-dev: dependency problems - leaving unconfigured
E: libcdd0: dependency problems - leaving unconfigured
E: gfan: dependency problems - leaving unconfigured
E: lcalc: dependency problems - leaving unconfigured
E: libcdd-test: dependency problems - leaving unconfigured
E: liblinbox0: dependency problems - leaving unconfigured
E: python-excelerator: subprocess installed post-installation script returned error exit status 2
E: python-foolscap: subprocess installed post-installation script returned error exit status 2
E: python-numpy: subprocess installed post-installation script returned error exit status 2
E: python-gnuplot: dependency problems - leaving unconfigured
E: python-gnutls: subprocess installed post-installation script returned error exit status 2
E: python-pyparsing: subprocess installed post-installation script returned error exit status 2


sudo aptitude -f install failed.. 

anup@anup-laptop:/var/lib/dpkg/info$ sudo aptitude -f install
[sudo] password for anup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following partially installed packages will be configured:
  gfan lcalc libcdd-test libcdd0 libgmp3-dev libgmpxx4ldbl liblinbox0 
  python-excelerator python-foolscap python-gnuplot python-gnutls 
  python-numpy python-pyparsing 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up libgmpxx4ldbl (2:4.3.1+dfsg-1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgmpxx4ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libgmp3-dev:
 libgmp3-dev depends on libgmpxx4ldbl (= 2:4.3.1+dfsg-1ubuntu3); however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing libgmp3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd0:
 libcdd0 depends on libgmp3-dev; however:
  Package libgmp3-dev is not configured yet.
dpkg: error processing libcdd0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gfan:
 gfan depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing gfan (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               lcalc:
 lcalc depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing lcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd-test:
 libcdd-test depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing libcdd-test (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblinbox0:
 liblinbox0 depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing liblinbox0 (--configure):
 dependency problems - leaving unconfigured
Setting up python-excelerator (0.6.3a-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-excelerator (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-foolscap (0.4.2+dfsg-1) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-foolscap (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-gnuplot:
 python-gnuplot depends on python-numpy; however:
  Package python-numpy is not configured yet.
dpkg: error processing python-gnuplot (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnutls (1.1.8-1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gnutls (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-pyparsing (1.5.2-1ubuntu1) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libgmpxx4ldbl
 libgmp3-dev
 libcdd0
 gfan
 lcalc
 libcdd-test
 liblinbox0
 python-excelerator
 python-foolscap
 python-numpy
 python-gnuplot
 python-gnutls
 python-pyparsing
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgmpxx4ldbl (2:4.3.1+dfsg-1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgmpxx4ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-foolscap (0.4.2+dfsg-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-foolscap (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-pyparsing (1.5.2-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of liblinbox0:
 liblinbox0 depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing liblinbox0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgmp3-dev:
 libgmp3-dev depends on libgmpxx4ldbl (= 2:4.3.1+dfsg-1ubuntu3); however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing libgmp3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd0:
 libcdd0 depends on libgmp3-dev; however:
  Package libgmp3-dev is not configured yet.
dpkg: error processing libcdd0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd-test:
 libcdd-test depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing libcdd-test (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnutls (1.1.8-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gnutls (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-excelerator (0.6.3a-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-excelerator (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lcalc:
 lcalc depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing lcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gfan:
 gfan depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing gfan (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnuplot:
 python-gnuplot depends on python-numpy; however:
  Package python-numpy is not configured yet.
dpkg: error processing python-gnuplot (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgmpxx4ldbl
 python-foolscap
 python-pyparsing
 liblinbox0
 libgmp3-dev
 libcdd0
 libcdd-test
 python-gnutls
 python-numpy
 python-excelerator
 lcalc
 gfan
 python-gnuplot
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

regards,

Anup.

---

### Post by darolu on 2010-02-26
what do you get with "apt-get check" and "apt-config"?

---

### Post by anup.techonly on 2010-02-26
Hope this helps you to understand...

anup@anup-laptop:/var/lib/dpkg/info$ sudo apt-get check
[sudo] password for anup: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

anup@anup-laptop:/var/lib/dpkg/info$ sudo apt-config
apt 0.7.23.1ubuntu2 for amd64 compiled on Oct 15 2009 19:26:36
Usage: apt-config [options] command

apt-config is a simple tool to read the APT config file

Commands:
   shell - Shell mode
   dump - Show the configuration

Options:
  -h   This help text.
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp

---

### Post by darolu on 2010-02-26
Use the option "dump" when using apt-config: "sudo apt-config dump" (this will show you the apt configurations, hopefully we'll catch the error with this info).
In theory apt-get cache fixes dependency trees, hopefully it will help you.

---

### Post by anup.techonly on 2010-02-26
Here is what I get through 'sudo apt-config dump'

anup@anup-laptop:/var/lib/dpkg/info$ sudo apt-config dump
APT "";
APT::Architecture "amd64";
APT::Build-Essential "";
APT::Build-Essential:: "build-essential";
APT::Install-Recommends "1";
APT::Install-Suggests "0";
APT::Acquire "";
APT::Acquire::Translation "environment";
APT::Authentication "";
APT::Authentication::TrustCDROM "true";
APT::NeverAutoRemove "";
APT::NeverAutoRemove:: "^linux-firmware$";
APT::NeverAutoRemove:: "^linux-image.*";
APT::NeverAutoRemove:: "^linux-restricted-modules.*";
APT::NeverAutoRemove:: "^linux-ubuntu-modules-.*";
APT::Never-MarkAuto-Sections "";
APT::Never-MarkAuto-Sections:: "metapackages";
APT::Never-MarkAuto-Sections:: "restricted/metapackages";
APT::Never-MarkAuto-Sections:: "universe/metapackages";
APT::Never-MarkAuto-Sections:: "multiverse/metapackages";
APT Periodic "";
APT Periodic::Update-Package-Lists "1";
APT Periodic download-Upgradeable-Packages "0";
APT Periodic::AutocleanInterval "0";
APT::Update "";
APT::Update Post-Invoke-Success "";
APT::Update Post-Invoke-Success:: "touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true";
APT::Update Post-Invoke-Success:: "[ ! -S /var/run/dbus/system_bus_socket ] || /usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged";
APT::Archives "";
APT::Archives::MaxAge "30";
APT::Archives::MinAge "2";
APT::Archives::MaxSize "500";
Dir "/";
Dir::State "var/lib/apt/";
Dir::State::lists "lists/";
Dir::State::cdroms "cdroms.list";
Dir::State::mirrors "mirrors/";
Dir::State::userstatus "status.user";
Dir::State::status "/var/lib/dpkg/status";
Dir::Cache "var/cache/apt/";
Dir::Cache::archives "archives/";
Dir::Cache::srcpkgcache "srcpkgcache.bin";
Dir::Cache pkgcache "pkgcache.bin";
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc parts "apt.conf.d";
Dir::Etc preferences "preferences";
Dir::Etc preferencesparts "preferences.d";
Dir::Bin "";
Dir::Bin::methods "/usr/lib/apt/methods";
Dir::Bin::dpkg "/usr/bin/dpkg";
Dir::Log "var/log/apt";
Dir::Log::Terminal "term.log";
aptitude "";
aptitude::Keep-Unused-Pattern "^linux-image.*$ | ^linux-restricted-modules.*$ | ^linux-ubuntu-modules.*$";
aptitude::Get-Root-Command "sudo:/usr/bin/sudo";
Unattended-Upgrade "";
Unattended-Upgrade::Allowed-Origins "";
Unattended-Upgrade::Allowed-Origins:: "Ubuntu karmic-security";
DPkg "";
DPkg pre-Install-Pkgs "";
DPkg pre-Install-Pkgs:: "/usr/sbin/dpkg-preconfigure --apt || true";
DPkg post-Invoke "";
DPkg post-Invoke:: "if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi ";
anup@anup-laptop:/var/lib/dpkg/info$

---

### Post by Kevbert on 2010-02-26
Please try this in terminal:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update

```
It may be that your package status file has been corrupted.

Also please post the output of
```
df -h
```
This will show the disk useage for various commands.

Another command to try is
```
sudo dpkg --configure -a
```
to repair any incomplete/interrupted installs.

---

### Post by anup.techonly on 2010-02-26
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update

Done..


anup@anup-laptop:/var/lib/dpkg$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              28G  5.9G   21G  23% /
udev                  2.0G  316K  2.0G   1% /dev
none                  2.0G  200K  2.0G   1% /dev/shm
none                  2.0G   96K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda1             128G   51G   71G  43% /media/Data1
/dev/sda2              12G  4.1G  6.5G  39% /media/Data2
/dev/sda7              60G   17G   40G  30% /home

anup@anup-laptop:/var/lib/dpkg$ sudo dpkg --configure -a
Setting up libgmpxx4ldbl (2:4.3.1+dfsg-1ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libgmpxx4ldbl (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-foolscap (0.4.2+dfsg-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-foolscap (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-pyparsing (1.5.2-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-pyparsing (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of liblinbox0:
 liblinbox0 depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing liblinbox0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgmp3-dev:
 libgmp3-dev depends on libgmpxx4ldbl (= 2:4.3.1+dfsg-1ubuntu3); however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing libgmp3-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd0:
 libcdd0 depends on libgmp3-dev; however:
  Package libgmp3-dev is not configured yet.
dpkg: error processing libcdd0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcdd-test:
 libcdd-test depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing libcdd-test (--configure):
 dependency problems - leaving unconfigured
Setting up python-gnutls (1.1.8-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-gnutls (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-numpy (1:1.3.0-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-numpy (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-excelerator (0.6.3a-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-excelerator (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lcalc:
 lcalc depends on libgmpxx4ldbl; however:
  Package libgmpxx4ldbl is not configured yet.
dpkg: error processing lcalc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gfan:
 gfan depends on libcdd0; however:
  Package libcdd0 is not configured yet.
dpkg: error processing gfan (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnuplot:
 python-gnuplot depends on python-numpy; however:
  Package python-numpy is not configured yet.
dpkg: error processing python-gnuplot (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgmpxx4ldbl
 python-foolscap
 python-pyparsing
 liblinbox0
 libgmp3-dev
 libcdd0
 libcdd-test
 python-gnutls
 python-numpy
 python-excelerator
 lcalc
 gfan
 python-gnuplot

---

### Post by Kevbert on 2010-02-26
Please take a look at [[COLOR="Red"]this.[/COLOR]]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/") The /var/lib/dpkg/status file will point to where things started to go wrong and you could also try looking at the dpkg.log via System-Admin-Log File Viewer (and the previous dpkg.log.1 file).

---

### Post by anup.techonly on 2010-02-26
Actually I checked that page earlier. But, I have so many 'subprocess pre-removal script returned error exit status 2' errors.

I started doing what he advised, but the problem was not solved, when I try to reinstall it, the problem resurfaces.

---

### Post by Kevbert on 2010-02-26
It looks like a bug and has been reported [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096").

---

