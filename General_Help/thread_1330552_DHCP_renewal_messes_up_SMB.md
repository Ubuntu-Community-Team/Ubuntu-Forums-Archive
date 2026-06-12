---
title: "DHCP renewal messes up SMB"
date: 2009-11-18
forum: General Help
---

### Post by e633 on 2009-11-18
... or at least that's my suspicion. #-o
System is Ubuntu 9.10 RC, all packages up to date. 
Detailed system specs here: [http://de.pastebin.ca/1676792](http://de.pastebin.ca/1676792)
smb.conf here: [http://de.pastebin.ca/1676804](http://de.pastebin.ca/1676804)

I use to mount this share from a shortcut on my desktop:
nautilus smb://192.168.1.101/d$/my_files
login is taken care of by "Encryption Key Manager seahorse 2.28.1".
After a while (there seems to be no regularity), (nautilus?) hangs and the share becomes unaccessible and unmountable. System log reports nothing.
This morning for example i was enjoying some music with Banshee when all of a sudden it just stopped. I double clicked on the song and Banshee simply hanged. I forced quit and Banshee remained in zombie state until reboot, spamming the system log with this:
```
Nov 18 13:39:59 mypc kernel: [ 8880.540187] INFO: task banshee-1:5218 blocked for more than 120 seconds.
Nov 18 13:39:59 mypc kernel: [ 8880.540194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 18 13:39:59 mypc kernel: [ 8880.540199] banshee-1     D c08145c0     0  5218   3020 0x00000004
Nov 18 13:39:59 mypc kernel: [ 8880.540209]  f5ab5da8 00200046 f0b00000 c08145c0 f0b88f28 c08145c0 d82ef98b 00000745
Nov 18 13:39:59 mypc kernel: [ 8880.540224]  c08145c0 c08145c0 f0b88f28 c08145c0 00000001 00000745 c08145c0 f1ca7500
Nov 18 13:39:59 mypc kernel: [ 8880.540237]  f0b88c90 f5ab5db4 eac43a90 eac43b2c f5ab5ddc c02b0705 f64a6400 00000000
Nov 18 13:39:59 mypc kernel: [ 8880.540250] Call Trace:
Nov 18 13:39:59 mypc kernel: [ 8880.540265]  [<c02b0705>] request_wait_answer+0x65/0x1e0
Nov 18 13:39:59 mypc kernel: [ 8880.540274]  [<c015c280>] ? autoremove_wake_function+0x0/0x40
Nov 18 13:39:59 mypc kernel: [ 8880.540282]  [<c02b08de>] fuse_request_send+0x5e/0x70
Nov 18 13:39:59 mypc kernel: [ 8880.540288]  [<c02b55ab>] fuse_flush+0xdb/0x110
Nov 18 13:39:59 mypc kernel: [ 8880.540296]  [<c01e53bc>] filp_close+0x2c/0x70
Nov 18 13:39:59 mypc kernel: [ 8880.540303]  [<c0146c93>] put_files_struct+0x63/0xb0
Nov 18 13:39:59 mypc kernel: [ 8880.540309]  [<c0146d23>] exit_files+0x43/0x60
Nov 18 13:39:59 mypc kernel: [ 8880.540315]  [<c0147dff>] do_exit+0x11f/0x2e0
Nov 18 13:39:59 mypc kernel: [ 8880.540322]  [<c01527dd>] ? dequeue_signal+0x2d/0x170
Nov 18 13:39:59 mypc kernel: [ 8880.540328]  [<c0147ffa>] do_group_exit+0x3a/0xb0
Nov 18 13:39:59 mypc kernel: [ 8880.540335]  [<c015403f>] get_signal_to_deliver+0x18f/0x300
Nov 18 13:39:59 mypc kernel: [ 8880.540342]  [<c010304b>] do_signal+0x6b/0x160
Nov 18 13:39:59 mypc kernel: [ 8880.540350]  [<c05708b8>] ? _spin_lock+0x8/0x10
Nov 18 13:39:59 mypc kernel: [ 8880.540357]  [<c016bf8c>] ? futex_wake+0xec/0x110
Nov 18 13:39:59 mypc kernel: [ 8880.540365]  [<c0165316>] ? getnstimeofday+0x56/0x110
Nov 18 13:39:59 mypc kernel: [ 8880.540373]  [<c048e832>] ? sys_socketcall+0xa2/0x270
Nov 18 13:39:59 mypc kernel: [ 8880.540379]  [<c010318d>] do_notify_resume+0x4d/0x60
Nov 18 13:39:59 mypc kernel: [ 8880.540386]  [<c0103448>] work_notifysig+0x13/0x1b
```I tried to open the shortcut on my desktop again, this is the result: Could not display "smb://192.168.1.101/d$/". The file is of an unknown type.
Then i tried to unmount (from the same shortcut) and i got this:
Unable to unmount d$ on 192.168.1.101
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. Please select another viewer and try again.
Problem is, "remote application" is fine (Windows Server 2003 R2 x64) and the network is fine (wired LAN with a crappy TP-Link router in the middle).

Same thing happens while viewing some video with VLC, just different messages in log and the freezing *sometimes* seems to solve much more quickly.
```

Nov 18 18:17:11 mypc kernel: [  163.493054] CE: hpet increasing min_delta_ns to 15000 nsec

```just after starting the video, then

```

Nov 18 18:14:50 mypc pulseaudio[1818]: core-util.c: Home directory /etc/timidity not ours.
Nov 18 18:14:50 mypc pulseaudio[1818]: lock-autospawn.c: Cannot access autospawn lock.
Nov 18 18:14:50 mypc pulseaudio[1818]: main.c: Failed to acquire autospawn lock
Nov 18 18:14:50 mypc console-kit-daemon[1099]: WARNING: Couldn't read /proc/1061/environ: Failed to open file '/proc/1061/environ': No such file or directory
Nov 18 18:14:51 mypc anacron[1880]: Anacron 2.3 started on 2009-11-18
Nov 18 18:14:51 mypc anacron[1880]: Normal exit (0 jobs run)
Nov 18 18:14:53 mypc kernel: [   26.068020] eth0: no IPv6 routers present
Nov 18 18:15:04 mypc gdm-session-worker[1897]: pam_sm_authenticate: Called
Nov 18 18:15:04 mypc gdm-session-worker[1897]: pam_sm_authenticate: username = [steve]
Nov 18 18:15:06 mypc kernel: [   39.358377] padlock: VIA PadLock not detected.
Nov 18 18:17:01 mypc CRON[2318]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 18 18:17:11 mypc kernel: [  163.493054] CE: hpet increasing min_delta_ns to 15000 nsec
Nov 18 18:17:50 mypc pulseaudio[2002]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 18 18:17:50 mypc pulseaudio[2002]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 18 18:17:50 mypc pulseaudio[2002]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 18 18:25:42 mypc sudo: pam_sm_authenticate: Called
Nov 18 18:25:42 mypc sudo: pam_sm_authenticate: username = [steve]

```but then...
```

Nov 18 19:06:23 mypc dhclient: DHCPREQUEST of 192.168.1.103 on eth0 to 192.168.1.1 port 67
Nov 18 19:06:23 mypc dhclient: DHCPACK of 192.168.1.103 from 192.168.1.1
Nov 18 19:06:23 mypc dhclient: bound to 192.168.1.103 -- renewal in 3062 seconds.
Nov 18 19:06:23 mypc NetworkManager: <info>  DHCP: device eth0 state changed bound -> renew
Nov 18 19:06:23 mypc NetworkManager: <info>    address 192.168.1.103
Nov 18 19:06:23 mypc NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 18 19:06:23 mypc NetworkManager: <info>    gateway 192.168.1.1
Nov 18 19:06:23 mypc NetworkManager: <info>    nameserver 'intentionally omitted'
Nov 18 19:06:23 mypc NetworkManager: <info>    nameserver 'intentionally omitted'

```and VLC freezes too and "Could not display "smb://192.168.1.101/d$/". The file is of an unknown type." after trying to access the shortcut on my Desktop.
Then i tried to stop the video, close VNC but to no avail. System monitor freezes too if i click on the "processes" tab! sudo killall vlc is useless too.

I tried to be as verbose as possible, waiting for you more experienced users to help me better troubleshoot this annoyance.

---

### Post by e633 on 2009-11-18
UPDATE: it happened just now while transferring a 1.1GB file, at exactly 571.2MB.
Still nothing in the system log.

EDIT: ooooops, that's embarrassing but... this has been my fault! No more free space on target device :D
shame on me! First post is still valid though.

---

### Post by dcstar on 2009-11-18
> **e633 said:**
> UPDATE: it happened just now while transferring a 1.1GB file, at exactly 571.2MB.
Still nothing in the system log.

EDIT: ooooops, that's embarrassing but... this has been my fault! No more free space on target device :D
shame on me! First post is still valid though.

Very simple solutions:[LIST=1]
[*]Use a decent DHCP Lease time (more than 51 minutes...)
[*]Use a Static IP address
[/LIST]

---

### Post by doas777 on 2009-11-18
agreed. lease time could be measured in days, not minutes.
also some samba errors are logged on the server, not the client.
if you look in /var/log/samba you should find a file called somthing like 'log.<clienthostname>', and will contain events pertaining to that client.

good luck

---

### Post by capscrew on 2009-11-18
> **doas777 said:**
> agreed. lease time could be measured in days, not minutes.
also some samba errors are logged on the server, not the client.
if you look in /var/log/samba you should find a file called somthing like 'log.<clienthostname>', and will contain events pertaining to that client.

good luck

Whenever a DHCP lease is renewed the Samba daemon (smbd) reloads.  Static lease or no, if there is a renew then smbd reloads (and breaks the connection).  This is normal behavior.  To truly eliminate the problem, the OP should configure the static address manually.    

See [_**[COLOR="DarkRed"]here [/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1140094")for all the gory details.

Edit:  Just a little rant on the difference between static IP and *reserved *IP addressing.

[COLOR="Green"]Static [/COLOR]IP = manually configured IP address (no DHCP involved)
[COLOR="Red"]Reserved [/COLOR]IP = DHCP configured IP address that is always the same

These two scenarios are very different *execept * for the consistent IP address.

---

### Post by e633 on 2009-11-19
> **dcstar said:**
> Very simple solutions:
[LIST=1]
[*]Use a decent DHCP Lease time (more than 51 minutes...)
[*]Use a Static IP address
[/LIST]


1. Done
2. Server always had a static IP.

> **doas777 said:**
> samba errors are logged on the server, not the client.
if you look in /var/log/samba you should find a file called somthing like 'log.<clienthostname>', and will contain events pertaining to that client.

As i said in my first post, server is Windows Server 2003 R2 x64. No such log files!
I am currently making a test run with a DHCP lease time of 1200 minutes.

EDIT: damn... just as i clicked "submit new post" it happened again.  ](*,)
Logs clean. Any ideas?

---

### Post by BFG on 2009-11-19
Are other items on the LAN configured with a static IP? If so you could check for clashes.

What does ifconfig report your IP address as before and after event?

---

### Post by e633 on 2009-11-19
I can confirm there are no clashes as i have full control of all machines here.
My IP remains the same.
I'd like to stress the fact that other applications freeze too (look in my first post) and that nautilus gives an "unknown file type" error whenever i try to access a smb:// URI.

---

### Post by BFG on 2009-11-19
If your IP remains the same it's unlikely to be DHCP.  Could be something weird with permissions.

For testing, can you use the /etc/fstab file to mount, so you can set parameters?

---

### Post by e633 on 2009-11-19
Sure, tell me what you have in mind, i'm ready!
FYI i have two accounts on this server: one is member of the "Users" group (with restriced permissions, basically read only), the other one is member of "Administrators" and has full control. 
In fact i usually login with the latter to access hidden shares such as d$ or c$.

---

### Post by e633 on 2009-11-20
Happened again, this time while transferring a 2.3GB file. I was using the least privileged account this time.
Changing ethernet cable now and making another test run, still waiting for your ideas!
:rolleyes:

---

