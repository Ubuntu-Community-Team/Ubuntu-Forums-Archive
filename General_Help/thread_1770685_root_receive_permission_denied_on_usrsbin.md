---
title: "root receive permission denied on /usr/sbin"
date: 2011-05-29
forum: General Help
---

### Post by doekia on 2011-05-29
Hi every one,

I have a pretty old system (Gutsy 7.10) that runs like a charm except I cannot add packages and certainly connat perform the upgrade to 8.04 -> 10.04). But the point is not there.

I pointed the problem to occur while acessing the** /usr/sbin** in write mode. The root user get a permission denied error... (example: touch /usr/sbin/testfile.txt).

I'm getting totally confused, I have triple check those to no avail:
[PHP]
  - disk space:
             Filesystem           1K-blocks      Used Available Use% Mounted on
             /dev/sda1            147983380  14208464 126257704  11% /
             varrun                 1014976       196   1014780   1% /var/run
             varlock                1014976         0   1014976   0% /var/lock
             udev                   1014976        72   1014904   1% /dev
             devshm                 1014976         0   1014976   0% /dev/shm
             lrm                    1014976     34696    980280   4% /lib/modules/2.6.22-14-
generic/volatile
[/PHP] - disk sanity (fsck)
 - free inodes
 - rebooted, stopped all services (samba, cupsys, apache, mysql)

I am totally illiterate regarding apparmor, but while I tried to add /usr/bin/dpkg to complain it apparently did nothing... 
[PHP]
/etc/init.d/apparmor status
    apparmor module is loaded.
2 profiles are loaded.
2 profiles are in enforce mode.
   /usr/sbin/cupsd
   /usr/lib/cups/backend/cups-pdf
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode :
   /usr/sbin/cupsd (4586) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

aa-complain /usr/bin/dpkg

/etc/init.d/apparmor status
    apparmor module is loaded.
2 profiles are loaded.
2 profiles are in enforce mode.
   /usr/sbin/cupsd
   /usr/lib/cups/backend/cups-pdf
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode :
   /usr/sbin/cupsd (4586) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

[/PHP]Does my problem relates to apparmor? any other "voodo-yet-to-be-aware-of" component? or another stupidity of mine?

PS: The initial intent was to install java-common to install sun-java6-jdk for a java-application 

Thanks for your support

---

