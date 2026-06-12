---
title: "kernel: [ 1201.791965] possible SYN flooding on port 6882. Sending cookies."
date: 2009-07-04
forum: General Help
---

### Post by dcbaba on 2009-07-04
Hi,

I am new to ubuntu. I am using torrent to download files. All of a sudden I have started getting messages in the log :
<<
kernel: [ 1201.791965] possible SYN flooding on port 6882. Sending cookies.
>>

Every minute the message gets updated  in the kern.log, messages, syslog files. The files get flooded with the same message over and over again. I shut off ubuntu and torrent. Then again restarted. But that did not help.

What could be the reason? and how to resolve this problem?

Any help would be greatly appreciated.

---

### Post by clarknova on 2009-08-19
Your machine thinks it's under attack because of the high rate of incoming connections. SYN cookies are there to try to maintain a usable network connection despite such an attack.

You can dial down the settings on your bittorrent client to make the messages go away or you can disable syn cookies.

Past versions of Ubuntu have had syn cookies disabled by default. I suppose it's safer to leave them enabled, but I have turned mine off. If you really do get DOSsed,then I guess turn them back on.

Disabling syn cookies immediately (won't survive a reboot):
```

sudo su
(enter your password if prompted)
echo 0 > /proc/sys/net/ipv4/tcp_syncookies

```
Disabling syn cookies at boot:
```

sudo sed -i s/#net.ipv4.tcp_syncookies=1/net.ipv4.tcp_syncookies=0/ /etc/sysctl.conf

```

---

### Post by zemon_ on 2009-11-13
After disabling SYN cookies, they are enabled again after reboot.

Should I add this line to the /etc/rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 0 > /proc/sys/net/ipv4/tcp_syncookies

exit 0

```

---

### Post by Giblet5 on 2009-11-13
> **clarknova said:**
> your machine thinks it's under attack because of the high rate of incoming connections. Syn cookies are there to try to maintain a usable network connection despite such an attack.

You can dial down the settings on your bittorrent client to make the messages go away or you can disable syn cookies.

Past versions of ubuntu have had syn cookies disabled by default. I suppose it's safer to leave them enabled, but i have turned mine off. If you really do get dossed,then i guess turn them back on.

Disabling syn cookies immediately (won't survive a reboot):
```

sudo su
(enter your password if prompted)
echo 0 > /proc/sys/net/ipv4/tcp_syncookies

```
**disabling syn cookies at boot**:
```

**[color="darkred"]sudo sed -i s/#net.ipv4.tcp_syncookies=1/net.ipv4.tcp_syncookies=0/ /etc/sysctl.conf[/color]**

```

+1 ftw

---

### Post by zemon_ on 2009-11-13
```
sudo sed -i s/#net.ipv4.tcp_syncookies=1/net.ipv4.tcp_syncookies=0/ /etc/sysctl.conf
```

This command does not work for disabling syn cookies after reboot.
I need this config file to stay at zero after reboot to disable SYN cookies.

```
nano /proc/sys/net/ipv4/tcp_syncookies
```

---

### Post by hugslasht on 2009-11-13
> **clarknova said:**
> Your machine thinks it's under attack because of the high rate of incoming connections. SYN cookies are there to try to maintain a usable network connection despite such an attack.

You can dial down the settings on your bittorrent client to make the messages go away or you can disable syn cookies.

Past versions of Ubuntu have had syn cookies disabled by default. I suppose it's safer to leave them enabled, but I have turned mine off. If you really do get DOSsed,then I guess turn them back on.

Disabling syn cookies immediately (won't survive a reboot):
```

sudo su
(enter your password if prompted)
echo 0 > /proc/sys/net/ipv4/tcp_syncookies

```Disabling syn cookies at boot:
```

sudo sed -i s/#net.ipv4.tcp_syncookies=1/net.ipv4.tcp_syncookies=0/ /etc/sysctl.conf

```
This command does not work for disabling syn cookies after reboot.
I need this config file to stay at zero after reboot to disable SYN cookies.

---

### Post by zemon_ on 2009-11-13
This command changes the value to zero in the tcp_syncookies config,which disables SYN cookies.

```
echo 0 > /proc/sys/net/ipv4/tcp_syncookies
```

This command disables SYN cookies in the /etc/sysctl.conf

```
sudo sed -i s/#net.ipv4.tcp_syncookies=1/net.ipv4.tcp_syncookies=0/ /etc/sysctl.conf
```

After reboot the tcp_syncookies config value located in the ipv4 folder returns to one, which means SYN cookies are enabled again.

---

