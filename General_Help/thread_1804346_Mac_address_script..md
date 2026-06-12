---
title: "Mac address script."
date: 2011-07-14
forum: General Help
---

### Post by fredrik444 on 2011-07-14
Hi! I'm new around here and didn't really know where to post this, but anyways here it goes.

I need help on making a script that changes the MAC-address on my network card when i download or upload X-amount of GB. I have been searching  around on the web, but I haven't been able to find anything that does that.

Anyone have some ideas on how to do it?

---

### Post by mikejonesey on 2011-07-14
check current download amount;
```
ifconfig wlan0 | grep "RX bytes" | sed 's/.*(//' | sed 's/).*//'
```change mac;
[FONT=monospace]```
ifconfig eth0 down
ifconfig eth0 hw ether 00:00:00:00:00:00
ifconfig eth0 up
ifconfig eth0 |grep HWaddr
```ps create a cron, you will need to do a lil math for the new macs, i can't be botherd to do that... :)

pss your current mac:
```
ifconfig -a wlan0 | grep HWaddr | sed 's/.*HWaddr //'
```

psss your mac always goes back to the one set on the network card at boot (the orig), i think, it did a couple a years back neways...
[/FONT]

---

### Post by fredrik444 on 2011-07-14
Thanks, that's all i need. :) <3

---

### Post by mikejonesey on 2011-07-14
i got boared; should any one else want this;
```
#!/bin/bash
interface="wlan0"
#mac will switch afer 100MB
maxDownload=100

curDownload=$(ifconfig wlan0 | grep "RX bytes" | sed 's/.*(//; s/ MiB.*//')
if [ "$curDownload" -gt "$maxDownload" ]; then
    newMac=$(date | md5sum | sed 's/../&:/g' | cut -b 1-17)
    ifconfig $interface down
    ifconfig $interface hw ether $newMac
    ifconfig $interface up
    ifconfig $interface |grep HWaddr
fi
```
i would prob sticky it to run as root... (SUID)

---

