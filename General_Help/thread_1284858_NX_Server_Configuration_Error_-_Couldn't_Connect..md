---
title: "NX: Server Configuration Error - Couldn't Connect."
date: 2009-10-07
forum: General Help
---

### Post by n0an on 2009-10-07
Hello,

I am stuck with a host who is ready to re-install the image, but not solve the problem. My nx was running fine last night. Today, when I try to connect I go a connection error. So I re-installed the latest .deb package using a guide, but it won't work.

```
NX> 148 Server capacity: not reached for user: admin
NX> 105 Start session with: --link="isdn" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="Ubuntu" --type="unix-gnome" --geometry="1200x800" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1200x800x32+render"
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: EE23059F. To get detailed information about
NX> 595 ERROR: the error search for the string EE23059F in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15
```> admin@ks201192:~$ nxclient
-bash: nxclient: command not found
admin@ks201192:~$ sudo /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.
admin@ks2011> admin@ks201192:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.
Help will be greatly appreciated.

Thanks

---

### Post by all4nothing on 2009-11-14
I discovered that you get this error when the hostname of the server is wrong - so for example, if you change the hostname from localhost.localdomain to Intranet, you will receive this error - may be worth checking you have a valid hostname - and if you changed it between the time it worked, and the time it didn't, changing it back

---

