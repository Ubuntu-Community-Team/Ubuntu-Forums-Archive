---
title: "KDE 4.7 freezing up my system"
date: 2011-08-11
forum: General Help
---

### Post by linuxuser12345 on 2011-08-11
I installed KDE 4.7 (minimal desktop install) on my desktop computer, running Ubuntu 11.04, and every time I go to log in with the KDE Plasm Workspace, my computer all of a sudden freezes up after about a minute of working fine. My mouse slows down incredibly and eventually comes unresponsive to keyboard, power button, and mouse click input. The mouse can move, but it's movement isn't fluid, and it can only move a little bit. 

Can anyone help me? I have also had problems with KDE 4.7 on other computers as well, but this desktop I am using is almost brand new. :/

---

### Post by linuxuser12345 on 2011-08-11
Has anyone had this problem? Is anyone able to help me?? :/

---

### Post by linuxuser12345 on 2011-08-11
Maybe if I completely remove everything KDE from my home folder, completely uninstall, and re-install KDE? Maybe that will work?

---

### Post by linuxuser12345 on 2011-08-11
And it did it again :(
I *was* able to retrieve the System Log files, though! Here they are from around the time I logged into KDE until the computer crashed and I had to force a reboot:
```
Aug 11 23:27:20 Kitchen-PC gdm-session-worker[1531]: pam_sm_authenticate: Called
Aug 11 23:27:20 Kitchen-PC gdm-session-worker[1531]: pam_sm_authenticate: username = [jeb]
Aug 11 23:27:20 Kitchen-PC gdm-session-worker[1626]: Passphrase file wrapped
Aug 11 23:27:21 Kitchen-PC kernel: [   37.389194] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
Aug 11 23:27:21 Kitchen-PC kernel: [   37.524493] Intel AES-NI instructions are not detected.
Aug 11 23:27:21 Kitchen-PC kernel: [   37.584434] padlock_aes: VIA PadLock not detected.
Aug 11 23:27:23 Kitchen-PC kernel: [   39.012552] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:67:9e:89:87:00:18:01:08:ab:8e:08:00 SRC=91.189.89.76 DST=192.168.1.5 LEN=126 TOS=0x00 PREC=0x00 TTL=250 ID=56526 DF PROTO=TCP SPT=443 DPT=51984 WINDOW=79 RES=0x00 ACK PSH URGP=0 
Aug 11 23:27:28 Kitchen-PC kernel: [   44.934982] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:67:9e:89:87:00:18:01:08:ab:8e:08:00 SRC=91.189.89.76 DST=192.168.1.5 LEN=126 TOS=0x00 PREC=0x00 TTL=250 ID=56527 DF PROTO=TCP SPT=443 DPT=51984 WINDOW=79 RES=0x00 ACK PSH URGP=0 
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Successfully made thread 1840 of process 1840 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Supervising 5 threads of 2 processes of 2 users.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Successfully made thread 1842 of process 1840 (n/a) owned by '1000' RT at priority 5.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Supervising 6 threads of 2 processes of 2 users.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Successfully made thread 1844 of process 1840 (n/a) owned by '1000' RT at priority 5.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Supervising 7 threads of 2 processes of 2 users.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Successfully made thread 1845 of process 1840 (n/a) owned by '1000' RT at priority 5.
Aug 11 23:27:36 Kitchen-PC rtkit-daemon[1594]: Supervising 8 threads of 2 processes of 2 users.
Aug 11 23:27:37 Kitchen-PC rtkit-daemon[1594]: Successfully made thread 1855 of process 1855 (n/a) owned by '1000' high priority at nice level -11.
Aug 11 23:27:37 Kitchen-PC rtkit-daemon[1594]: Supervising 9 threads of 3 processes of 2 users.
Aug 11 23:27:37 Kitchen-PC pulseaudio[1855]: pid.c: Daemon already running.
Aug 11 23:27:40 Kitchen-PC kernel: [   56.614260] Valid eCryptfs headers not found in file header region or xattr region
Aug 11 23:27:40 Kitchen-PC kernel: [   56.614264] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Aug 11 23:27:40 Kitchen-PC kernel: [   56.781217] [UFW BLOCK] IN=eth0 OUT= MAC=00:30:67:9e:89:87:00:18:01:08:ab:8e:08:00 SRC=91.189.89.76 DST=192.168.1.5 LEN=126 TOS=0x00 PREC=0x00 TTL=250 ID=56528 DF PROTO=TCP SPT=443 DPT=51984 WINDOW=79 RES=0x00 ACK PSH URGP=0 
Aug 11 23:27:41 Kitchen-PC hp-systray: hp-systray[1817]: error: Unable to open /home/jeb/.hplip/hp-systray.lock lock file.

```

---

### Post by linuxuser12345 on 2011-08-12
Any ideas? Is there a way I can completely remove everything KDE from my system and re-install them? Maybe that will work?

---

### Post by linuxuser12345 on 2011-08-12
I just fixed broken packages, reinstalled KDE, upgraded to the newest version of 4.7, and installed the Kubuntu-Desktop package, and I still keep getting these errors. :(
I think the time my system goes to crash that is the same time I start using something that takes a lot of desktop effects. Then my CPU usage goes through the roof and stays that way, like it's locked. Then I have to restart.

---

### Post by toallpointswest on 2011-12-22
I'm having the same problem with KDE 4.7, it runs for a few minutes then hard locks the system. Ever enabling Ctrl-Alt-Backspace doesn't help, I'll have to pull my logs in a bit

---

### Post by linuxuser12345 on 2011-12-23
Reinstalling Ubuntu helped me out tons.

---

### Post by toallpointswest on 2011-12-26
Found the problem, Akondi was consuming nearly 100% of my CPU after startup. So I disabled it and no more problems since.  I used the following to do it from a remote terminal: 

```

akonadictl stop

```

```

StartServer=true to StartServer=False
in
~/.config/akonadi/akonadiserverrc

```

---

### Post by timswait on 2012-01-27
I'm getting a similar problem :( My computer was working fine yesterday, but now everytime I turn it on it functions normally for a minute or two and then becomes almost completely unresponsive! In the minute or two that I'm able to use it I've opened a terminal typed "akonadictl stop", but I get the reply "Akondi not running" I don't have time to edit files before it freezes up, so I can't edit that file :(

---

### Post by timswait on 2012-01-27
That has worked this time, I needed to catch it at just the right time to stop it running akondi! Too early entering the command and it hadn't started yet so couldn't be stopped, too late and the computer was frozen so couldn't do anything!

---

