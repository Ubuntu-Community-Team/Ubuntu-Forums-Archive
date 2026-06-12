---
title: "Landscape-sysinfo, update-motd, and 12.04.1 LTS - No System Info on login"
date: 2012-08-29
forum: General Help
---

### Post by xdracco on 2012-08-29
Aloha forums,

I recently updated my production server from 10.04.1 LTS to 12.04.1 LTS and while the upgrade was simple and painless, now landscape-sysinfo no longer displays system information when I log in.

When I log in, this is what I now see:

```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic-pae i686)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun Aug 26 16:25:24 MST 2012

Last login: Tue Aug 28 16:29:09 2012 from 55.56.57.58
```So, I poked around and found a couple of things but still no solution. At first glance, the file /etc/update-motd.d/50-landscape-sysinfo that is shipped with 12.04.1 is incorrect:

```
#!/bin/sh
cores=$(grep -c ^processor /proc/cpuinfo 2>/dev/null)
[ "$cores" -eq "0" ] && cores=1
threshold="${cores:-1}.0"
if [ $(echo "`cut -f1 -d ' ' /proc/loadavg` < $threshold" | bc) -eq 1 ]; then
    echo
    echo -n "  System information as of "
    exec /bin/date
    echo
    exec /usr/bin/landscape-sysinfo
else
    echo
    echo " System information disabled due to load higher than $threshold"
fi
```In the current script, the script exits after the comand "exec /bin/date", for obvious reasons (see man exec).

So, what I did is simply remove the 2 'exec' statements (leaving the command) but that still doesn't work. Actually, it works from command line, just not when I log in.

Running '/etc/update-motd.d/50-landscape-sysinfo' produces the desired output but only when I run the command:

```
[non-root-user@ubuntusv:/etc/update-motd.d] #/etc/update-motd.d/50-landscape-sysinfo

  System information as of Wed Aug 29 08:44:31 MST 2012

  System load:  0.01               Users logged in:       1
  Usage of /:   3.2% of 291.44GB   IP address for eth0:   10.0.0.1
  Memory usage: 12%                IP address for eth0:0: 10.0.0.2
  Swap usage:   0%                 IP address for eth0:1: 10.0.0.3
  Processes:    99                 IP address for eth0:2: 10.0.0.4

  Graph this data and manage this system at https://landscape.canonical.com/
```As you can see, what I see when I log in missing a good piece of information.

Any ideas?

Thanks!

---

### Post by xdracco on 2012-08-29
oh geez.. so it's the shell...

this script requires bash in order to be able to execute landscape-sysinfo...

did anyone have this issue?

---

### Post by xdracco on 2012-08-29
for anyone else that runs into this issue, just use this patch:

```
--- landscape-sysinfo.wrapper.orig    2012-08-27 17:22:18.000000000 -0700
+++ landscape-sysinfo.wrapper.mod    2012-08-29 15:30:45.000000000 -0700
@@ -1,13 +1,13 @@
-#!/bin/sh
+#!/bin/bash
 cores=$(grep -c ^processor /proc/cpuinfo 2>/dev/null)
 [ "$cores" -eq "0" ] && cores=1
 threshold="${cores:-1}.0"
 if [ $(echo "`cut -f1 -d ' ' /proc/loadavg` < $threshold" | bc) -eq 1 ]; then
     echo
     echo -n "  System information as of "
-    exec /bin/date
+    /bin/date
     echo
-    exec /usr/bin/landscape-sysinfo
+    /usr/bin/landscape-sysinfo
 else
     echo
     echo " System information disabled due to load higher than $threshold"
```Save to file.. landscape-sysinfo.wrapper.patch....

then do:
$ patch -u /usr/share/landscape/landscape-sysinfo.wrapper /path/to/landscape-sysinfo.wrapper.patch

-- OR --

Figure it out from the patch code. =)

Enjoy...

---

