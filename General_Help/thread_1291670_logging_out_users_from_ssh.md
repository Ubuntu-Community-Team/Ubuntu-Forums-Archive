---
title: "logging out users from ssh"
date: 2009-10-15
forum: General Help
---

### Post by Neezer on 2009-10-15
So here's the situation,

I am out of town for work and just got my ubuntu 9.04 system up and running back home. I get ssh set up which I think is very cool. 

My laptop has vista on it so I am using putty to connect and use the comand line on the ubuntu box back home. I turned the box on back home, but didn't log into it. So it should still be on the login screen...no way to check because I don't have to monitor plugged into it...just the box plugged into the router.

my putty seems to be running very slowly and I'm wondering if it could be because there are multiple instances of nate (my username) running on the machine....how can I find out? can I just log all users "nate" out then relog back in? How would I go about logging all of the "nate"s out?

EDIT: I tried doing a few things from my ssh terminal....I did the ps command and ended up with:

```

nate@server:~$ ps
  PID TTY          TIME CMD
26404 pts/0    00:00:00 bash
26775 pts/0    00:00:00 less
27458 pts/0    00:00:00 ps

```

I have used ps before, and don't remember seeing PID's that high before. I tried kill 26775, but it didn't do anything. Upon doing ps again, I got the same result with the less still running.

I tried logout....

```

nate@server:~$ logout
There are stopped jobs.

```

---

### Post by sirtrent on 2009-10-15
Hmmmm, interesting. I know that whenever I use ssh, I usually use 'logout' to close up my command line, but I have a feeling that even if you just close the window ssh will likely automatically log you out (Someone can correct me if I'm wrong).

Anyway, the command 'users' should tell you who's currently logged in. Note that you'll see a username for each terminal open, be it ssh, gnome-terminal window etc.

I don't know how to force a logout, though...except by 'sudo reboot'.

---

### Post by Neezer on 2009-10-15
> **sirtrent said:**
> Hmmmm, interesting. I know that whenever I use ssh, I usually use 'logout' to close up my command line, but I have a feeling that even if you just close the window ssh will likely automatically log you out (Someone can correct me if I'm wrong).

Anyway, the command 'users' should tell you who's currently logged in. Note that you'll see a username for each terminal open, be it ssh, gnome-terminal window etc.

I don't know how to force a logout, though...except by 'sudo reboot'.

```

nate@server:~$ users
nate nate

```

will sudo reboot start the machine back up as well? ie. reboot the whole computer? I want to be able to continue to work on my server issues while I'm out of town...probably 3 weeks or so. 

I know the server flavor would have been better, but I just didn't feel like I was ready to go without a GUI at the moment. I actually tried to start out with server edition and I was VERY intimidated so I just reinstalled with the 9.04 desktop version.


EDIT:

Upon more browsing I found a thread with this command in it, and man did I get a lot of stuff returned!!! 


```

nate@server:~$ ps -elf --forest | less
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD
5 S root         2     0  0  75  -5 -     0 kthrea Oct13 ?        00:00:00 [kthreadd]
1 S root         3     2  0 -40   - -     0 migrat Oct13 ?        00:00:00  \_ [migration/0]
1 S root         4     2  0  75  -5 -     0 ksofti Oct13 ?        00:00:00  \_ [ksoftirqd/0]
5 S root         5     2  0 -40   - -     0 watchd Oct13 ?        00:00:00  \_ [watchdog/0]
1 S root         6     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [events/0]
1 S root         7     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [khelper]
1 S root         8     2  0 -40   - -     0 worker Oct13 ?        00:00:00  \_ [kstop/0]
1 S root         9     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kintegrityd/0]
1 S root        10     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kblockd/0]
1 S root        11     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kacpid]
1 S root        12     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kacpi_notify]
1 S root        13     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [cqueue]
1 S root        14     2  0  75  -5 -     0 worker Oct13 ?        00:00:02  \_ [ata/0]
1 S root        15     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [ata_aux]
1 S root        16     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [ksuspend_usbd]
1 S root        17     2  0  75  -5 -     0 hub_th Oct13 ?        00:00:00  \_ [khubd]
1 S root        18     2  0  75  -5 -     0 serio_ Oct13 ?        00:00:00  \_ [kseriod]
1 S root        19     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kmmcd]
1 S root        20     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [btaddconn]
1 S root        21     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [btdelconn]
1 S root        22     2  0  80   0 -     0 pdflus Oct13 ?        00:00:00  \_ [pdflush]
1 S root        23     2  0  80   0 -     0 pdflus Oct13 ?        00:00:00  \_ [pdflush]
1 S root        24     2  0  75  -5 -     0 kswapd Oct13 ?        00:00:00  \_ [kswapd0]
1 S root        25     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [aio/0]
1 S root        26     2  0  75  -5 -     0 ecrypt Oct13 ?        00:00:00  \_ [ecryptfs-kthrea]
1 S root        29     2  0  75  -5 -     0 scsi_e Oct13 ?        00:00:00  \_ [scsi_eh_0]
1 S root        30     2  0  75  -5 -     0 scsi_e Oct13 ?        00:00:00  \_ [scsi_eh_1]
1 S root        31     2  0  75  -5 -     0 scsi_e Oct13 ?        00:00:00  \_ [scsi_eh_2]
1 S root        32     2  0  75  -5 -     0 scsi_e Oct13 ?        00:00:05  \_ [scsi_eh_3]
1 S root        33     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kstriped]

While scrolling I accidentally deleted a few of these lines and couldn't cut and paste them...only 5 or so lines are missing....

1 S root      1125     2  0  75  -5 -     0 worker Oct13 ?        00:00:00  \_ [kpsmoused]
1 S root      1250     2  0  75  -5 -     0 gamepo Oct13 ?        00:00:00  \_ [kgameportd]
4 S root         1     0  0  80   0 -   771 select Oct13 ?        00:00:01 /sbin/init
5 S root       801     1  0  76  -4 -   556 poll   Oct13 ?        00:00:00 /sbin/udevd --daemon
0 S root      2018     1  0  80   0 -   452 n_tty_ Oct13 tty4     00:00:00 /sbin/getty 38400 tty4
0 S root      2019     1  0  80   0 -   452 n_tty_ Oct13 tty5     00:00:00 /sbin/getty 38400 tty5
0 S root      2026     1  0  80   0 -   452 n_tty_ Oct13 tty2     00:00:00 /sbin/getty 38400 tty2
0 S root      2027     1  0  80   0 -   452 n_tty_ Oct13 tty3     00:00:00 /sbin/getty 38400 tty3
0 S root      2028     1  0  80   0 -   452 n_tty_ Oct13 tty6     00:00:00 /sbin/getty 38400 tty6
1 S root      2098     1  0  80   0 -   551 poll   Oct13 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
5 S syslog    2143     1  0  80   0 -   510 select Oct13 ?        00:00:00 /sbin/syslogd -u syslog
4 S root      2166     1  0  80   0 -   492 syslog Oct13 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
1 S klog      2168     1  0  80   0 -   933 pipe_w Oct13 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
5 S 108       2191     1  0  80   0 -   761 poll   Oct13 ?        00:00:17 /bin/dbus-daemon --system
5 S root      2215     1  0  80   0 -  1359 select Oct13 ?        00:00:00 /usr/sbin/sshd
4 S root     26393  2215  0  80   0 -  2125 unix_s 21:43 ?        00:00:00  \_ sshd: nate [priv]
5 S nate     26401 26393  0  80   0 -  2159 select 21:43 ?        00:00:00      \_ sshd: nate@pts/0
0 R nate     26404 26401  0  80   0 -  1445 -      21:43 pts/0    00:00:00          \_ -bash
0 T nate     26775 26404  0  80   0 -   844 signal 22:06 pts/0    00:00:00              \_ less
0 R nate     27623 26404  0  80   0 -   691 -      22:54 pts/0    00:00:00              \_ ps -elf --forest
0 S nate     27624 26404  0  80   0 -   844 n_tty_ 22:54 pts/0    00:00:00              \_ less
5 S root      2256     1  0  80   0 -  1810 select Oct13 ?        00:00:00 /usr/sbin/nmbd -D
5 S root      2260     1  0  80   0 -  3257 select Oct13 ?        00:00:00 /usr/sbin/smbd -D
1 S root      2284  2260  0  80   0 -  3257 select Oct13 ?        00:00:00  \_ /usr/sbin/smbd -D
4 S root      2281     1  0  80   0 -   951 inet_c Oct13 ?        00:00:00 /usr/sbin/vsftpd
5 S 111       2304     1  0  80   0 -  1667 poll   Oct13 ?        00:00:08 /usr/sbin/hald
0 S root      2370  2304  0  80   0 -   832 poll   Oct13 ?        00:00:00  \_ hald-runner
0 S root      2400  2370  0  80   0 -  1294 poll   Oct13 ?        00:00:00      \_ hald-addon-input: Listening on /dev/input/event1 /dev/input/event0
0 S root      2431  2370  0  80   0 -  1295 poll   Oct13 ?        00:00:04      \_ hald-addon-storage: polling /dev/sr0 (every 2 sec)
4 S 111       2433  2370  0  80   0 -  1258 unix_s Oct13 ?        00:00:00      \_ hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
0 S root      2866  2370  0  80   0 -  1294 poll   Oct13 ?        00:00:00      \_ /usr/lib/hal/hald-addon-rfkill-killswitch
5 S root      2307     1  0  80   0 -  4184 poll   Oct13 ?        00:00:02 /usr/sbin/console-kit-daemon
5 S root      2451     1  0  80   0 -   889 poll   Oct13 ?        00:00:00 /usr/sbin/bluetoothd
1 S root      2486     1  0  80   0 -  3758 poll   Oct13 ?        00:00:00 /usr/sbin/gdm
5 S root      2489  2486  0  80   0 -  3887 select Oct13 ?        00:00:00  \_ /usr/sbin/gdm
4 S root      2493  2489  0  80   0 -  9820 select Oct13 tty7     00:00:19      \_ /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
4 S nate      2812  2489  0  80   0 -  6599 poll   Oct13 ?        00:00:00      \_ x-session-manager
1 S nate      2871  2812  0  80   0 -  1196 select Oct13 ?        00:00:00          \_ /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
1 S nate      2954  2812  0  80   0 -  4775 poll   Oct13 ?        00:00:00          \_ /usr/bin/seahorse-agent --execute x-session-manager
0 S nate      2978  2812  0  80   0 -   468 wait   Oct13 ?        00:00:00          \_ /bin/sh /usr/bin/compiz
0 S nate      3043  2978  0  80   0 -  6804 poll   Oct13 ?        00:00:14          |   \_ /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id 106b21fee180c19d6b125549368285821700000028120019 core ccp
0 S nate      3103  3043  0  80   0 -   468 wait   Oct13 ?        00:00:00          |       \_ /bin/sh -c /usr/bin/compiz-decorator
0 S nate      3104  3103  0  80   0 -   468 wait   Oct13 ?        00:00:00          |           \_ /bin/sh /usr/bin/compiz-decorator
0 S nate      3106  3104  0  80   0 -  5013 poll   Oct13 ?        00:00:03          |               \_ /usr/bin/gtk-window-decorator
0 S nate      3044  2812  0  80   0 -  8878 poll   Oct13 ?        00:00:08          \_ gnome-panel
0 S nate      3045  2812  0  80   0 - 13091 poll   Oct13 ?        00:00:02          \_ nautilus
0 S nate      3050  2812  0  80   0 -  4028 poll   Oct13 ?        00:00:00          \_ bluetooth-applet
0 S nate      3051  2812  0  80   0 -  6999 poll   Oct13 ?        00:00:02          \_ update-notifier --startup-delay=60
0 S nate      3052  2812  0  80   0 -  6959 poll   Oct13 ?        00:00:00          \_ python /usr/share/system-config-printer/applet.py
0 S nate      3054  2812  0  80   0 -  5922 poll   Oct13 ?        00:00:02          \_ nm-applet --sm-disable
0 S nate      3055  2812  0  80   0 - 10660 poll   Oct13 ?        00:00:00          \_ /usr/lib/evolution/2.26/evolution-alarm-notify
5 S root      2515     1  0  80   0 -  2050 poll   Oct13 ?        00:00:13 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
4 S root      2522     1  0  80   0 -  1070 select Oct13 ?        00:00:03 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
4 S root      2526     1  0  80   0 -  1737 poll   Oct13 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
5 S avahi     2539     1  0  80   0 -   764 poll   Oct13 ?        00:00:00 avahi-daemon: running [server.local]
1 S avahi     2540  2539  0  80   0 -   736 unix_s Oct13 ?        00:00:00  \_ avahi-daemon: chroot helper
5 S root      2566     1  0  80   0 -  1527 ep_pol Oct13 ?        00:00:00 /usr/sbin/cupsd
1 S root      2597     1  0  80   0 -  1081 poll   Oct13 ?        00:00:00 /usr/bin/system-tools-backends
1 S daemon    2668     1  0  80   0 -   524 hrtime Oct13 ?        00:00:00 /usr/sbin/atd
1 S root      2696     1  0  80   0 -   870 hrtime Oct13 ?        00:00:00 /usr/sbin/cron
0 S root      2792     1  0  80   0 -   452 n_tty_ Oct13 tty1     00:00:00 /sbin/getty 38400 tty1
1 S nate      2874     1  0  80   0 -   786 select Oct13 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
1 S nate      2875     1  0  80   0 -   767 poll   Oct13 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
1 S nate      2880     1  0  80   0 - 23662 poll   Oct13 ?        00:00:01 /usr/bin/pulseaudio --start
0 S nate      2881  2880  0  80   0 -  1961 poll   Oct13 ?        00:00:00  \_ /usr/lib/pulseaudio/pulse/gconf-helper
0 S nate      2883     1  0  80   0 -  1901 poll   Oct13 ?        00:00:05 /usr/lib/libgconf2-4/gconfd-2
1 S nate      2960     1  0  80   0 -  7297 poll   Oct13 ?        00:00:04 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
0 S nate      2963     1  0  80   0 -  1404 poll   Oct13 ?        00:00:00 /usr/lib/gvfs/gvfsd
1 S nate      2964     1  0  80   0 -  4362 poll   Oct13 ?        00:00:00 gnome-keyring-daemon --start
1 S nate      2972     1  0  80   0 -  7396 futex_ Oct13 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/nate/.gvfs
0 S nate      3047     1  0  80   0 - 10185 poll   Oct13 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
1 S nate      3069     1  0  80   0 -  6191 poll   Oct13 ?        00:00:01 gnome-power-manager
0 S nate      3071     1  0  80   0 -  4388 poll   Oct13 ?        00:00:00 /usr/lib/notify-osd/notify-osd
0 S nate      3076     1  0  80   0 -  5948 poll   Oct13 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
0 S nate      3078     1  0  80   0 -  1959 poll   Oct13 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
0 S nate      3080     1  0  80   0 -  2052 poll   Oct13 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
0 S nate      3083     1  0  80   0 -  1485 poll   Oct13 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
0 S nate      3086     1  0  80   0 -  6816 poll   Oct13 ?        00:00:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=19
0 S nate      3089     1  0  80   0 - 11095 poll   Oct13 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=26
0 S nate      3092     1  0  80   0 -  5637 poll   Oct13 ?        00:00:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=23
0 S nate      3099     1  0  80   0 -  1404 poll   Oct13 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
1 S nate      3117     1  0  80   0 -  4162 poll   Oct13 ?        00:00:05 gnome-screensaver

```

Hope that wasn't just way too much code to put in the code box

and after that whole debacle I learned an important thing about less....I don't know how to properly exit!

```

[2]+  Stopped                 ps -elf --forest | less
nate@server:~$ ps
  PID TTY          TIME CMD
26404 pts/0    00:00:00 bash
26775 pts/0    00:00:00 less
27624 pts/0    00:00:00 less
27625 pts/0    00:00:00 ps
nate@server:~$ sudo kill 26775
[sudo] password for nate:
nate@server:~$ ps
  PID TTY          TIME CMD
26404 pts/0    00:00:00 bash
26775 pts/0    00:00:00 less
27624 pts/0    00:00:00 less
27716 pts/0    00:00:00 ps

```


I was using ctl z, but apparently it is just q....huh

---

### Post by bab1 on 2009-10-15
If you want to see what the users are doing try this at the CLI (terminal prompt)
```
w
```

The ps command lists processes running.  ps -elf adds the details See the man pages for an explanation.
```
man ps
```

---

### Post by sirtrent on 2009-10-15
> will sudo reboot start the machine back up as well? ie. reboot the whole computer? I want to be able to continue to work on my server issues while I'm out of town...probably 3 weeks or so.

Yes 'sudo reboot' will reboot the computer, and it should just go back to the login screen.

As for your ps lists they seem to be quite normal. Most of the processes have to do with gnome. It's true that had you used the server edition there would be fewer processes, but then again you wouldn't get gnome..or any gui for that matter.

The only process I don't quite understand is 'less'. Though (and I'm purely guessing) it may have to do with helping the actual 'ps' command output text.


> ```

nate@server:~$ users
nate nate
```

As for 'nate' appearing to be logged in twice, I'm starting to think it's somewhat normal becasue I get the same thing on my computer.


You may also want to try using 'top'.  It is a bit more feature filled. All the things that are being run by 'root' are system processes.

---

### Post by nvikram on 2009-10-15
The slow-ness caused by ssh is most probably caused by your internet connection. I guess it depends on the speed and how far away you are from you're computer. I've tried accessing my laptop from a England (I live in the US), and it connects, but it is pretty slow, so I am not surprised. 

Also, a ```
sudo reboot
```, will definetly log out anyone else who is currently logged in.

---

### Post by bab1 on 2009-10-15
The 2 instances of nate is due to nate being logged in (1) and a terminal window open (2).  

To see what nate is running use```
ps -ef|grep nate
```
This will show the processes that nate is running.  You can kill the lost numbered PID for the user and it should rmove that login.  Use ```
Kill *PID#*
```

Less formats the stdout (output to the screen) to one page at a time.

---

### Post by bab1 on 2009-10-15
> **nvikram said:**
> The slow-ness caused by ssh is most probably caused by your internet connection. I guess it depends on the speed and how far away you are from you're computer... 


I'll bet it's more about hops (passing through devices) and the encrypted tunnel (with processing overhead) than distance.  The data is traveling at the speed of light.  :D

---

### Post by Neezer on 2009-10-15
Success!!!

I used the reboot command as sudo and all is good...I am connected back to the server and it is running much faster. 

Thanks for all of the help. I really appreciate it.

---

### Post by physeetcosmo on 2010-07-13
Kind of late, but if you want to avoid rebooting the server, try this.

Check **which users are logged on** by using the *finger* command. If you have multiple sessions of your user account "logged in" there will be many instances of your account name.

```
$ finger
```

Next list the process ID's of all apps that YOUR user is currently running on the system:

```
$ ps -eo user,pid,start,comm | egrep -i -e *nate* -e "sshd|bash"
```

or replace *nate* with whatever your exact username is. We are listing all of the processes running, listing only the data columns:

**USER, PID, STARTtime, COMMAND**

and then grep-ing this output, only wanting to see those processes that have YOUR username and the words sshd -OR- bash. The output should look something like:

```
nate    1384  TUE Jul 13 05:57:47 2010 update-notifier
root    2374  TUE Jul 13 14:23:25 2010 sshd
nate    2389  TUE Jul 13 14:23:25 2010 sshd
nate    2390  TUE Jul 13 14:23:25 2010 bash
```

In the list that is output, find the -bash line with YOUR username (or whatever user you want to force-logoff). This STARTtime value will be something from a few days ago or longer (if that session is still running). Next and this is important, you must find the ***root*** process that has the EXACT same TIME AND DATE and has a COMMAND of ***sshd***. Use that PID in the following command:

```
sudo kill *PID*
```

If you've logged in many times and those sessions are still running, you may have to do this a few times!

Hope this helps.

---

