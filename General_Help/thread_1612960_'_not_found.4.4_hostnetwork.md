---
title: "' not found.4.4: host/network"
date: 2010-11-03
forum: General Help
---

### Post by Hovercat on 2010-11-03
I recently installed a new Ubuntu PC that runs iptables and PSAD.

I had the same script on another Ubuntu PC, but when I copied the script onto the new PC, I got this error. I don't remember where I found the tutorial for this, all I know is that this is the script (Edited for my usage):

```
#!/bin/bash
# Script to check important ports on remote webserver
# Copyright (c) 2009 blogama.org
# This script is licensed under GNU GPL version 2.0 or above
# ---------------------------------------------------------------------
 
WORKDIR="/var/ddosprotect/"
INTERVAL="5"
HITCOUNT="10"
SAFEIPFILE="safe.txt"
 
cd $WORKDIR
 
iptables -F
if [ -f $SAFEIPFILE ]; then
  IPS=$(grep -Ev "^#" $SAFEIPFILE)
  for i in $IPS
  do
        iptables -A INPUT -s $i -j ACCEPT
  done
fi
 
iptables-restore /var/ddosprotect/iptables
iptables -A INPUT -m state --state NEW -m recent --set
iptables -A INPUT -m state --state NEW -m recent --update --seconds $INTERVAL --hitcount $HITCOUNT -j LOG
```

Safe.txt contains:

```
127.0.0.1
192.168.1.8
192.168.1.1
98.200.58.73
192.168.0.1

```

And the error message generated is:

```
root@NETWORK-SERVER:/var/ddosprotect# ./ipblock.sh
' not found.4.4: host/network `127.0.0.1
Try `iptables -h' or 'iptables --help' for more information.
' not found.4.4: host/network `192.168.1.8
Try `iptables -h' or 'iptables --help' for more information.
' not found.4.4: host/network `192.168.1.1
Try `iptables -h' or 'iptables --help' for more information.
' not found.4.4: host/network `98.200.58.73
Try `iptables -h' or 'iptables --help' for more information.
' not found.4.4: host/network `192.168.0.1
Try `iptables -h' or 'iptables --help' for more information.

```

If anyone can find the URL to the tutorial containing a script extremely similar to this, it would be greatly appreciated.

---

### Post by Hovercat on 2010-11-04
Can someone please help?

---

### Post by Hovercat on 2010-11-05
Can someone help me please?

---

### Post by Hovercat on 2010-11-06
Someone help....

---

### Post by fredvanl on 2012-01-16
This is probably caused by an invisible (DOS/Windows) carriage return character in the file that contains the safe IP-addresses. Open it in in vi to check. If a ^M shows up at the end of each line, you know the cause....

---

