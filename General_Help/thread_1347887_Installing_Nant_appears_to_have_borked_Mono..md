---
title: "Installing Nant appears to have borked Mono."
date: 2009-12-06
forum: General Help
---

### Post by afrodeity on 2009-12-06
I installed Nant, not realising its a mono-dev tool, while trying to install opensim and ran it. I now get weird messages from dpkg.

This is what it looks like trying to uninstall. You can see a process at the bottom that is stuck.

```

afrodeity@afrodeity-desktop:~$ sudo apt-get remove nant
[sudo] password for afrodeity: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-i18n-west1.0-cil libmono-getoptions2.0-cil libmono-security1.0-cil
  liblog4net1.2-cil libmono0 libmono-system-web1.0-cil libmono-peapi2.0-cil
  libmono-corlib1.0-cil libmono-system1.0-cil libmono-data-tds1.0-cil
  libmono-system-data1.0-cil libnunit2.4-cil libmono-cecil-private-cil
  mono-csharp-shell libmono-dev libmono-system-runtime1.0-cil
  libmono-relaxng1.0-cil mono-devel libmono-management2.0-cil mono-2.0-devel
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nant
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 5,083kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 242735 files and directories currently installed.)
Removing nant ...
Processing triggers for man-db ...
Setting up liblog4net1.2-cil (1.2.10+dfsg-3) ...
* Installing 1 assembly from liblog4net1.2-cil into Mono

** (/usr/lib/mono/2.0/gacutil.exe:9250): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
E: installing Assembly /usr/lib/cli/log4net-1.2/log4net.dll failed
E: Installation of liblog4net1.2-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing liblog4net1.2-cil (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up libnunit2.4-cil (2.4.7+dfsg-4) ...
* Installing 6 assemblies from libnunit2.4-cil into Mono

** (/usr/lib/mono/2.0/gacutil.exe:9264): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
E: installing Assembly /usr/lib/cli/nunit-2.4/nunit.core.dll failed
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed
dpkg: error processing libnunit2.4-cil (--configure):
 subprocess installed post-installation script returned error exit status 9
Errors were encountered while processing:
 liblog4net1.2-cil
 libnunit2.4-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
afrodeity@afrodeity-desktop:~$ 

```

How do I resolve this? It comes up whenever I try to install or uninstall anything.

---

### Post by afrodeity on 2009-12-06
[https://bugs.launchpad.net/ubuntu/+source/mono/+bug/483363?comments=all](https://bugs.launchpad.net/ubuntu/+source/mono/+bug/483363?comments=all)

---

### Post by afrodeity on 2009-12-07
Well don't all rush to help.

---

### Post by afrodeity on 2009-12-08
[http://ubuntuforums.org/showthread.php?t=1348866](http://ubuntuforums.org/showthread.php?t=1348866)

---

