---
title: "Configure /etc/network/interfaces to log states"
date: 2010-12-18
forum: General Help
---

### Post by dgs012 on 2010-12-18
I'm trying to configure /etc/network/interfaces to log whenever an interfaces goes up or down into a file, using this format:

UP/DOWN [DD-MM-YY/HH:MM:SS]

How exactly do I use commands with the UP and DOWN directives?

---

### Post by gmargo on 2010-12-18
Look at the subdirectories under /etc/networks/.

```

$ ls -l /etc/network                                                                                           
total 20                                                                                                                       
drwxr-xr-x 2 root root 4096 Oct 22 19:24 if-down.d                                                                             
drwxr-xr-x 2 root root 4096 Nov 11 13:50 if-post-down.d                                                                        
drwxr-xr-x 2 root root 4096 Nov 11 13:50 if-pre-up.d                                                                           
drwxr-xr-x 2 root root 4096 Dec  9 12:55 if-up.d                                                                               
-rw-r--r-- 1 root root  268 Oct 22 18:04 interfaces              

```In those "if-up.d/", "if-down.d/", etc directories are scripts that get executed when those events ("interface up" or "interface down" etc) occur.

So all you need do is add your own scripts to those directories.  (What are the arguments? - looking for the docs)

More info in **/usr/share/doc/ifupdown/examples/**.

---

### Post by dgs012 on 2010-12-18
Thanks for the help.

Unfortunately, I'm not allowed to create scripts in those directories.

I must use the /etc/network/interfaces file.

---

### Post by dgs012 on 2010-12-19
Up.

Can anyone help?

---

### Post by gmargo on 2010-12-19
> **dgs012 said:**
> Unfortunately, I'm not allowed to create scripts in those directories.

I must use the /etc/network/interfaces file.

Why that restriction?  Is this homework?

Read the **interfaces(5)** man page.  Everything you need to know is in there.

If this is homework, don't read below this line.

If this is not homework, you can use the following demonstration script and adapt it to your format.

Add these command lines to your **/etc/network/interfaces** file:
```

auto eth0
iface eth0 inet dhcp
        pre-up    /usr/local/bin/iface-changed.sh
        up        /usr/local/bin/iface-changed.sh
        post-up   /usr/local/bin/iface-changed.sh 
        pre-down  /usr/local/bin/iface-changed.sh
        down      /usr/local/bin/iface-changed.sh
        post-down /usr/local/bin/iface-changed.sh

```Put this script into **/usr/local/bin/iface-changed.sh** and make it executable:
```

#!/bin/sh
# Do something for an interface state change.
# Meant to be run from /etc/networks/interfaces file.

# From interfaces(5) man page:
# All  of  these  commands have access to the following environment vari&#8208;
# ables.
#
# IFACE  physical name of the interface being processed
#
# LOGICAL
#        logical name of the interface being processed
#
# ADDRFAM
#        address family of the interface
#
# METHOD method of the interface (e.g., static)
#
# MODE   start if run from ifup, stop if run from ifdown
#
# PHASE  as per MODE, but with finer granularity, distinguishing the pre-
#        up, post-up, pre-down and post-down phases.
#
# VERBOSITY
#        indicates whether --verbose was used; set to 1 if so, 0 if not.
#
# PATH   the   command   search   path:  /usr/local/sbin:/usr/local/bin:&#8208;
#        /usr/sbin:/usr/bin:/sbin:/bin


OUT=/tmp/iface-state.txt

echo "------------------"          >> $OUT
date                               >> $OUT
echo "Physical Interface: $IFACE"  >> $OUT
echo "Logical Interface: $LOGICAL" >> $OUT
echo "Phase: $PHASE"               >> $OUT
echo "Mode: $MODE"                 >> $OUT
echo "------------------"          >> $OUT

exit 0

```Now run "ifdown eth0" and "ifup eth0", then check the output in the /tmp/iface-state.txt file. Now remix into your own format.

---

