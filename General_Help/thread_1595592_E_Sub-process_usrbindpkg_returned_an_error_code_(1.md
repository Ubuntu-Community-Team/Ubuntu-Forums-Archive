---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-10-13
forum: General Help
---

### Post by JaredFactley on 2010-10-13
Openvpn has been giving me error messages for a while now when using package managers and I can't seem to figure out what to do about it. I don't use it any more, so removing it would not be a problem if that were possible. But I can't figure out how to do it. I get this error message every time I try.

```
jared@jared-laptop:~$ sudo apt-get remove openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libofx4 kdelibs4c2a python-beagle libosp5 libgwenhywfar47 mint-translations
  kdelibs-data libaqbanking29-plugins libaqofxconnect5 openssl-blacklist
  liblualib50 libqbanking8 pidgin-data libktoblzcheck1c2a libamrnb3
  libaqbanking29 libaqbanking-plugins-libgwenhywfar47 libamrwb3 libavahi-qt3-1
  libaqhbci17 aqbanking-tools libpkcs11-helper1 mint-common libqt3-mt
  libaqbanking29-plugins-qt liblua50 libaqbanking-data openvpn-blacklist
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  openvpn
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 1,225kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174450 files and directories currently installed.)
Removing openvpn ...
/etc/default/openvpn: 11: Syntax error: Unterminated quoted string
invoke-rc.d: initscript openvpn, action "stop" failed.
dpkg: error processing openvpn (--remove):
 subprocess installed pre-removal script returned error exit status 2
/etc/default/openvpn: 11: Syntax error: Unterminated quoted string
invoke-rc.d: initscript openvpn, action "cond-restart" failed.
/etc/default/openvpn: 11: Syntax error: Unterminated quoted string
invoke-rc.d: initscript openvpn, action "restart" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 openvpn
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Have found others with the same problem with other applications, but none of the solutions have worked for me so far.

---

### Post by happyhamster on 2010-10-13
> **JaredFactley said:**
> /etc/default/openvpn: 11: Syntax error: Unterminated quoted string
Could you show the content of that file here? Just run:
```

cat /etc/default/openvpn

```
or open the file in a text-editor. Thanks.

---

### Post by JaredFactley on 2010-10-13
It returned...

```
# This is the configuration file for /etc/init.d/openvpn

#
# Start only these VPNs automatically via init script.
# Allowed values are "all", "none" or space separated list of
# names of the VPNs. If empty, "all" is assumed.
#
#AUTOSTART="all"
#AUTOSTART="none"
#AUTOSTART="home office"
AUTOSTART="openvpn
#
# Refresh interval (in seconds) of default status files
# located in /var/run/openvpn.$NAME.status
# Defaults to 10, 0 disables status file generation
#
#STATUSREFRESH=10
#STATUSREFRESH=0
# Optional arguments to openvpn's command line
OPTARGS=""

```

---

### Post by happyhamster on 2010-10-13
This line is missing the closing " character:
```
AUTOSTART="openvpn
```
It should look like:
```
AUTOSTART="openvpn"
```

---

### Post by JaredFactley on 2010-10-13
Too simple if you know what to look for.

Thanks a lot, worked perfectly.

---

