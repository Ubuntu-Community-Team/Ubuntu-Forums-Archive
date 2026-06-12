---
title: "udev script runs more than once .."
date: 2010-09-14
forum: General Help
---

### Post by lonegroover on 2010-09-14
Hi folks,

Strange problem.

I set up a small script to run a backup to a USB stick on plugin, using the following udev rule:

```
SUBSYSTEMS=="usb", ATTRS{serial}=="03B1617140F1F949", KERNEL=="sd*", SYMLINK="disgo%n", RUN+="/usr/local/sbin/disgo"
```The script just does an rsync of my home directory to the USB stick. For reference, here it is:

```
#!/bin/bash
echo running at $(date) >> /tmp/disgo.log 
sleep 12

typeset -i attempts=0

while [[ ! $MOUNTED ]] && (($attempts < 5)); do
   sleep 3
   attempts=$((attempts+1))
   mount /mnt/disgo && MOUNTED=1
done

if $(df |grep -w disgo >/dev/null); then
   echo mounted on $attempts attempts >> /tmp/disgo.log
   rsync --delete --delete-excluded -av --exclude-from=/home/jg/.excludes /home/jg /mnt/disgo >> /tmp/disgo.log
   umount /mnt/disgo
else
   echo unable to mount /mnt/disgo after 5 attempts at $(date) >> /tmp/disgo.log
fi
exit 0

```

The trouble is, the script runs at least TWICE each time the stick is plugged in. Furthermore, on the first run, although the /dev/disgo symlink turns up, the /dev/disgo1 symlink is nowhere to be seen, and so the script gives up after 5 attempts to mount the stick.

But as soon as the script exits, the /dev/disgo1 appears, and udev runs the script again! This time it's able to mount the device and perform the backup.

However, ideally I'd just like the /dev/disgo1 symlink to appear when the stick is plugged in, and the script to run just once ..

Any ideas? I'm running Ubuntu 10.4

```
davros:~> uname -a
Linux davros 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux
```Here's the logfile from the last time the stick was plugged in. The logfile was deleted before I pushed the stick into the socket.

As you can see, on this occasion it ran **three times** .. :confused:

```

running at Tue Sep 14 13:57:51 BST 2010
unable to mount /mnt/disgo after 5 attempts at Tue Sep 14 13:58:18 BST 2010
running at Tue Sep 14 13:58:18 BST 2010
mounted on 1 attempts
sending incremental file list
jg/.bash_history
jg/.mozilla/firefox/09kqidrc.default/
jg/.mozilla/firefox/09kqidrc.default/XUL.mfasl
jg/.mozilla/firefox/09kqidrc.default/cert8.db
jg/.mozilla/firefox/09kqidrc.default/cookies.sqlite
jg/.mozilla/firefox/09kqidrc.default/cookies.sqlite-journal
jg/.mozilla/firefox/09kqidrc.default/formhistory.sqlite
jg/.mozilla/firefox/09kqidrc.default/localstore.rdf
jg/.mozilla/firefox/09kqidrc.default/places.sqlite
jg/.mozilla/firefox/09kqidrc.default/places.sqlite-journal
jg/.mozilla/firefox/09kqidrc.default/sessionstore.js
jg/.ssh/known_hosts
jg/.sylpheed-2.0/
jg/.sylpheed-2.0/folderlist.xml
jg/.sylpheed-2.0/folderlist.xml.bak
jg/.sylpheed-2.0/folderlist.xml.bak.1
jg/.sylpheed-2.0/folderlist.xml.bak.2
jg/.sylpheed-2.0/folderlist.xml.bak.3
jg/.sylpheed-2.0/folderlist.xml.bak.4

sent 2397827 bytes  received 535 bytes  1598908.00 bytes/sec
total size is 546466954  speedup is 227.85
running at Tue Sep 14 13:58:37 BST 2010
lrwxrwxrwx 1 root root 3 Sep 14 13:58 /dev/disgo -> sdf
lrwxrwxrwx 1 root root 4 Sep 14 13:58 /dev/disgo1 -> sdf1
mounted on 1 attempts
sending incremental file list

sent 199571 bytes  received 206 bytes  133184.67 bytes/sec
total size is 546466954  speedup is 2735.38

```

---

### Post by ronakin on 2010-11-28
hey,

I've the same problem, I've saved the following rule in a file under /etc/udev/rules.d/85-myrule.rules

KERNEL=="ttyUSB[0-9]*", ACTION=="add", RUN+="/root/my_script.py --device=%k"

when it identify a /dev/ttyUSB it runs the script. however, the minute the script is done, it runs it again
I've checked the script and it's completly ok, I've also run it on several devices to deny a problem with the device

I'm using ubuntu 10.04

I will appreciate any help, I'm kinda lost

---

