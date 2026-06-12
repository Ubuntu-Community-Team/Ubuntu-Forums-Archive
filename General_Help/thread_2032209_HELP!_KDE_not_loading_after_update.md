---
title: "HELP! KDE not loading after update"
date: 2012-07-23
forum: General Help
---

### Post by mogliii on 2012-07-23
I have a Kubuntu 12.04 machine, and after the update today it does not start into KDE anymore. Kernel 3.2.0-27 was installed but when booting with 26 (old version) the same behavior occurs.

GDM (which I am suing) loads as usual and after entering my password the screen turns black, mouse present, but nothing happens. No Error. Harddisk quiet. I tried with different user, same result.

Below is a list of the packages that were upgraded today.

```
2012-07-23 10:39:31 upgrade libqt4-qt3support:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:35 upgrade libqt4-qt3support 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:42 upgrade libqt4-designer 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:46 upgrade libqt4-designer:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:50 upgrade libqt4-script 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:53 upgrade libqt4-script:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:39:57 upgrade libqt4-dbus 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:00 upgrade libqt4-dbus:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:04 upgrade libqt4-xml 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:07 upgrade libqt4-xml:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:10 upgrade libqtcore4 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:17 upgrade libqtcore4:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:34 upgrade libqtgui4 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:38 upgrade libqtgui4:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:42 upgrade libqt4-declarative 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:47 upgrade libqt4-declarative:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:51 upgrade libqt4-network 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:40:54 upgrade libqt4-network:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:03 upgrade libqt4-sql 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:06 upgrade libqt4-sql:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:16 upgrade libqt4-xmlpatterns 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:19 upgrade libqt4-xmlpatterns:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:36 upgrade libqt4-opengl-dev 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:39 upgrade qt4-qmake 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:47 upgrade libqt4-scripttools:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:41:51 upgrade libqt4-scripttools 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:05 upgrade qt4-dev-tools 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:11 upgrade libqt4-help 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:15 upgrade libqt4-opengl 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:18 upgrade libqt4-opengl:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:31 upgrade libqt4-test:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:36 upgrade libqt4-test 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:44 upgrade qdbus:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:47 upgrade qt4-linguist-tools 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:42:50 upgrade libqt4-dbg 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:10 upgrade libqt4-sql-mysql 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:13 upgrade libqt4-svg:i386 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:16 upgrade libqt4-svg 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:27 upgrade libqt4-sql-sqlite 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:29 upgrade libqt4-gui 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:32 upgrade qt4-designer 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:37 upgrade libqt4-core 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:43:42 upgrade libqt4-dev 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
2012-07-23 10:45:01 upgrade handbrake-gtk 4868svnppa1~precise1 4870svnppa1~precise1
2012-07-23 10:45:07 upgrade linux-generic 3.2.0.26.28 3.2.0.27.29
2012-07-23 10:45:09 upgrade linux-image-generic 3.2.0.26.28 3.2.0.27.29
2012-07-23 10:47:20 upgrade linux-headers-generic 3.2.0.26.28 3.2.0.27.29
2012-07-23 10:47:23 upgrade linux-libc-dev 3.2.0-26.41 3.2.0-27.43
2012-07-23 10:47:30 upgrade qt4-doc 4:4.8.1-0ubuntu4.1 4:4.8.1-0ubuntu4.2
```

Which log could I find more information in? :(
Gnome is not installed, so cannot try alternative window manager.

Tried also with kdm (did first sudo stop gdm and then sudo start kdm) but no difference. This time the kdm background image remains.

Below is the relevant syslog part for such a login trial
```
Jul 23 16:36:22 Desktop gdm-session-worker[2979]: pam_ecryptfs: pam_sm_authenticate: /home/user is already mounted
Jul 23 16:44:34 Desktop kernel: [ 1625.429405] [fglrx] IRQ 45 Disabled
Jul 23 16:44:44 Desktop acpid: client 2932[0:0] has disconnected
Jul 23 16:44:44 Desktop acpid: client connected from 3879[0:0]
Jul 23 16:44:44 Desktop acpid: 1 client rule loaded
Jul 23 16:44:44 Desktop kernel: [ 1635.776218] fglrx_pci 0000:01:00.0: irq 45 for MSI/MSI-X
Jul 23 16:44:44 Desktop kernel: [ 1635.777228] [fglrx] Firegl kernel thread PID: 3883
Jul 23 16:44:44 Desktop kernel: [ 1635.777400] [fglrx] Firegl kernel thread PID: 3884
Jul 23 16:44:44 Desktop kernel: [ 1635.777509] [fglrx] Firegl kernel thread PID: 3885
Jul 23 16:44:44 Desktop kernel: [ 1635.777695] [fglrx] IRQ 45 Enabled
Jul 23 16:44:45 Desktop kernel: [ 1635.930949] [fglrx] Gart USWC size:1280 M.
Jul 23 16:44:45 Desktop kernel: [ 1635.930953] [fglrx] Gart cacheable size:508 M.
Jul 23 16:44:45 Desktop kernel: [ 1635.930960] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jul 23 16:44:45 Desktop kernel: [ 1635.930962] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Jul 23 16:44:45 Desktop kernel: [ 1635.930965] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Jul 23 16:44:49 Desktop kdm_greet[3887]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory
Jul 23 16:45:05 Desktop kdm: :0[3886]: pam_ecryptfs: pam_sm_authenticate: /home/user is already mounted

```
I cannot recognize any problem

---

### Post by mogliii on 2012-07-23
Ok, I could solve it by myself. Somehow.

I cannot reproduce what it was exactly.

What I did was:
1) Uninstall fglrx (Ati driver), didnt change anything
2) Stopped dbus and tried to start -> No help
3) Installed xfce4, could start xfce
4) within xfce I run plasma-desktop, which started
5) I restarted and installed kubuntu-desktop (all dependencies were installed, but the actual package not) -> could login and start KDE
6) Reinstalled fglrx

Very strange. Anyway closing this thread.

---

### Post by fsando on 2012-07-23
Thanks for posting. I'm always wary of kernel updates - using fglrx too, this post is useful to me. I'm now better prepared to fight possible issues.

---

### Post by sirfaber on 2012-07-24
Same problem here... RESOLVED too... I just did
[INDENT]1. reinstall fglrx
2. install kubuntu-desktop[/INDENT]
These kind of problem shouldn't happen...

---

### Post by osofamoso on 2012-07-26
thank you very much for the hint. 
I had the same problem today and I wouldn't have been able to solve it without your post. 
btw I am using an nvidia card, so I skipped the fglrx stuff. 
All I had to do was install kubuntu-desktop wich was simply missing. 
how did you find out that? I wasn't aware a package like this exists. 


thx again!

:guitar:

oso

---

### Post by mastablasta on 2012-07-26
> **sirfaber said:**
> These kind of problem shouldn't happen...
 
this should be reported as bug on launch pag. 
 
you are right they shouldn't happen. kernel should be tested before update is pushed to users. especiallly on LTS.

---

### Post by janstap on 2012-08-01
Hi,

The install kubuntu-desktop did it for me too; sirfaber and osofamoso thanks! Before googling, I looked around a bit, starting with /var/log/kdm.log, which already showed a bounce at a nonexisting item:

[...]
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  1 19:26:35 2012
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/2075418470/.config/ibus/bus
 ddxSigGiveUp: Closing log
Server terminated successfully (0). Closing log file.

An strace on the kdm process, while logging in at the kdm interface did not give much:

root@xpsm1330:~# ps aux|fgrep kdm
root      1561  0.0  0.0  26840  1176 ?        Ss   21:13   0:00 kdm
root      3966  0.0  0.0   9360   744 pts/2    S+   21:29   0:00 fgrep --color=auto kdm
root@xpsm1330:~# strace -f -p 1561
1530  select(12, [4 6 7 9 11], NULL, NULL, NULL) = 1 (in [9])
1530  rt_sigprocmask(SIG_BLOCK, NULL, [], 8) = 0
1530  read(9, "\1\0\0\0", 4)            = 4
1530  read(9, "\350\3\0\0", 4)          = 4
1530  read(9, "\4\0\0\0", 4)            = 4
1530  read(9, "jan\0", 4)               = 4
1530  read(9, "\10\0\0\0", 4)           = 4
1530  read(9, "default\0", 8)           = 8
1530  select(12, [4 6 7 9 11], NULL, NULL, NULL

As far as KDM was concerned, it had done its job and was just waiting for a new user to log in (and fail, as I have only kubuntu-desktop installed).

---

