---
title: "DOSemu in a bash script not closing."
date: 2012-07-16
forum: General Help
---

### Post by hangthedj on 2012-07-16
Hello,

After searching for quite some time, it seems I may have a unique issue.

I finally got a bbs setup using linux and dosemu without having to use a different port for each node using xinet.d.

Everything works fine, unless somebody hangs up.  If they hang up, the script I'm using doesn't finish and eventually I have a ton of dosemu.bin instances still running.

I've tried to kill the pid at the end of the script.  The problem is the script never finishes running if they hang up.

```

#!/bin/bash
export HOME=/home/bbs/
unset DISPLAY
pid=$$
total=6
current_sessions=`ps aux | grep in.telnetd | grep bbs | grep -v grep | wc -l`
if [ $current_sessions -ge $total ]; then
echo "Too many connections, please try again later."
sleep 2
echo "Goodbye."
sleep 1
else
NODE=1
       for i in `seq 1 $total` ; do
                if [ -e "/tmp/bbsnode$i" ] ;
                then
                        DUMMY=1
                else
                        let NODE=$i
                        echo $pid > /tmp/bbsnode$i
                        break
                fi
        done
clear
echo "Please wait ... Loading BBS Node $NODE ..."
sleep 4
/usr/bin/dosemu.bin -n -f /etc/dosemu/dosemu.conf "C:\BBS.bat $NODE"
echo "Goodbye."
rm -rf /tmp/bbsnode$NODE
kill $pid
fi

```

Unfortunately my bash scripting is rusty at best.

Any help is greatly appreciated.

Edit :  ubuntuforums won't let me edit any of my personal information for some reason.  I am not running Jaunty Jackalope, I am running 12.04 x64.

---

