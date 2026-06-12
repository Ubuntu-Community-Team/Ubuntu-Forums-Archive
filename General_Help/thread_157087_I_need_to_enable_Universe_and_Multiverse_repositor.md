---
title: "I need to enable Universe and Multiverse repositories, but...."
date: 2006-04-08
forum: General Help
---

### Post by fenderlicious on 2006-04-08
System > Administration > ANYTHING does not open.
All the Wiki says I need to open is the Synaptic Package Manager, but that won't open, as it falls under System > Administration > and I'm really angry at this lack of function.

---

### Post by llamakc on 2006-04-08
Open a terminal (Applications | Accessories | Terminal) and type:

sudo synaptic

Are you logged in as the user you created during the install? Or are you logged in as a different user?

---

### Post by fenderlicious on 2006-04-08
I'm logged in as the user I created during install.
Also, nothing happened when I did that, it asked for password and I entered it, nothing happened.

---

### Post by DeadMazzay on 2006-04-08
Please look at /etc/sudoers. Yur user should be there to be able to run administrative sofrware. It was also strange for me that it didn't report any permission errors if you are not in sudoers.

---

### Post by fenderlicious on 2006-04-08
I can't open it to view it.
And when I try Terminal 1 as root I get the following return:
-bash: /etc/sudoers: Permission Denied

---

### Post by DeadMazzay on 2006-04-08
try running (in a terminal)
gksudo gedit
then open /etc/sudoers file and put a line:
your_username   ALL=(ALL) ALL
and enter your password when it prompts

---

### Post by fenderlicious on 2006-04-08
I tried it in-gnome on the terminal, didn't work. Then I tried it on the tty1 terminal as root, didn't work.

---

### Post by llamakc on 2006-04-08
Is some sort of update-manager or other version of synaptic running? Let us see the output of `ps aux` while you have the Terminal open. Paste all of that here please.

---

### Post by fenderlicious on 2006-04-09
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.3   1704   596 ?        S    03:04   0:02 init [2]
root         2  0.0  0.0      0     0 ?        SN   03:04   0:00 [ksoftirqd/0]
root         3  0.1  0.0      0     0 ?        S<   03:04   0:03 [events/0]
root         4  0.0  0.0      0     0 ?        S<   03:04   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   03:04   0:00 [kthread]
root        13  0.0  0.0      0     0 ?        S<   03:04   0:00 [kblockd/0]
root        45  0.0  0.0      0     0 ?        S    03:04   0:00 [pdflush]
root        46  0.0  0.0      0     0 ?        S    03:04   0:00 [pdflush]
root        48  0.0  0.0      0     0 ?        S<   03:04   0:00 [aio/0]
root        47  0.0  0.0      0     0 ?        S    03:04   0:01 [kswapd0]
root       626  0.0  0.0      0     0 ?        S    03:04   0:00 [khubd]
root      1138  0.0  0.0      0     0 ?        S    03:04   0:00 [kjournald]
root      1268  0.0  0.3   1948   588 ?        S<s  03:04   0:00 udevd --daemon
root      1822  0.0  0.0      0     0 ?        S    03:04   0:00 [scsi_eh_0]
dhcp      3589  0.0  0.6   2916  1220 ?        S<s  03:06   0:00 dhclient3 -pf /
root      3977  0.0  0.2   1708   460 ?        Ss   03:06   0:00 /bin/dd bs 1 if
klog      3979  0.0  0.8   2548  1532 ?        Ss   03:06   0:00 /sbin/klogd -P
105       3992  0.0  0.6   2708  1208 ?        Ss   03:06   0:00 /usr/bin/dbus-d
hal       4005  0.0  1.4   5348  2768 ?        Ss   03:06   0:00 /usr/sbin/hald
hal       4018  0.0  0.3   2260   680 ?        S    03:06   0:00 hald-addon-stor
root      4043  0.0  1.4  15840  2792 ?        Ss   03:06   0:00 /usr/sbin/gdm
root      4050  0.0  1.6  16564  3112 ?        S    03:06   0:00 /usr/sbin/gdm
root      4112 12.5 14.9  43060 28616 ?        S    03:06   3:47 /usr/X11R6/bin/
hplip     4145  0.0  0.6  22108  1196 ?        Ssl  03:06   0:00 /usr/sbin/hpiod
hplip     4159  0.0  1.4  12196  2748 ?        S    03:06   0:00 python /usr/sbi
root      4271  0.0  0.3   2328   760 ?        Ss   03:06   0:00 hcid: processin
root      4277  0.0  0.2   1836   524 ?        Ss   03:06   0:00 /usr/sbin/sdpd
root      4287  0.0  0.0      0     0 ?        S<   03:06   0:00 [krfcommd]
daemon    4319  0.0  0.3   2156   636 ?        Ss   03:06   0:00 /usr/sbin/atd
root      4332  0.0  0.4   2360   872 ?        Ss   03:06   0:00 /usr/sbin/cron
root      4355  0.0  0.2   1700   480 tty2     Ss+  03:06   0:00 /sbin/getty 384
root      4356  0.0  0.2   1700   480 tty3     Ss+  03:06   0:00 /sbin/getty 384
root      4357  0.0  0.2   1700   480 tty4     Ss+  03:06   0:00 /sbin/getty 384
root      4358  0.0  0.2   1700   480 tty5     Ss+  03:06   0:00 /sbin/getty 384
root      4359  0.0  0.2   1700   480 tty6     Ss+  03:06   0:00 /sbin/getty 384
joe       4384  0.1  4.5  26124  8616 ?        Ss   03:06   0:01 x-session-manag
joe       4422  0.0  0.4   3940   824 ?        Ss   03:06   0:00 /usr/bin/ssh-ag
joe       4425  0.0  0.3   3324   700 ?        S    03:06   0:00 /usr/bin/dbus-l
joe       4426  0.0  0.5   2708  1072 ?        Ss   03:06   0:00 dbus-daemon --f
joe       4428  0.3  3.5  14972  6808 ?        S    03:06   0:05 /usr/lib/gconf2
joe       4458  0.0  0.4   2924   932 ?        S    03:07   0:00 /usr/bin/gnome-
joe       4460  0.1  0.7   7396  1488 ?        S    03:07   0:02 /usr/bin/esd -n
joe       4462  0.0  1.5   9300  2920 ?        Ss   03:07   0:00 /usr/lib/bonobo
joe       4464  0.1  3.9  28300  7596 ?        S    03:07   0:02 /usr/lib/contro
joe       4467  0.0  0.7   3308  1404 ?        S    03:07   0:01 /usr/lib/gamin/
joe       4479  0.0  1.1   9280  2112 ?        S    03:07   0:00 xscreensaver -n
joe       4503  0.9  4.0  18972  7800 ?        Ss   03:07   0:16 /usr/bin/metaci
joe       4508  0.3  6.5  30844 12600 ?        Ssl  03:07   0:05 gnome-panel --s
joe       4510  0.8  8.5  47212 16344 ?        Ssl  03:07   0:15 nautilus --no-d
joe       4512  0.0  3.5  25208  6860 ?        Ss   03:07   0:00 gnome-volume-ma
joe       4518  0.0  5.2  26616 10132 ?        Ss   03:07   0:01 update-notifier
joe       4520  0.9  6.1  28644 11788 ?        S    03:07   0:16 /usr/lib/gnome-
joe       4522  0.0  4.8  47132  9288 ?        Ssl  03:07   0:01 gnome-cups-icon
joe       4524  0.0  2.3  17792  4564 ?        S    03:07   0:00 /usr/lib/notifi
joe       4527  0.0  1.9  12464  3732 ?        Sl   03:07   0:00 /usr/lib/gnome-
joe       4529  0.0  4.6  27292  8808 ?        Sl   03:07   0:00 /usr/lib/gnome-
joe       4542  0.2  5.9  28164 11424 ?        S    03:07   0:04 /usr/lib/gnome-
joe       4544  0.0  4.6  25456  8852 ?        S    03:07   0:00 /usr/lib/gnome-
joe       4546  0.1  5.3  30120 10244 ?        S    03:07   0:02 /usr/lib/gnome-
joe       4548  0.5  4.7  31716  9096 ?        S    03:07   0:09 /usr/lib/gnome-
joe       4550  0.0  0.4   2860   868 ?        S    03:07   0:00 /usr/lib/nautil
joe       4552  0.2  4.5  26824  8768 ?        S    03:07   0:03 /usr/lib/gnome-
joe       4554  0.9  5.0  27576  9616 ?        S    03:07   0:15 /usr/lib/gnome-
joe       4559 18.2  2.7  13468  5192 pts/0    Rs+  03:07   5:17 perl /usr/share
root      5095  0.0  0.4   3392   788 ttyS0    Ss+  03:08   0:01 /usr/sbin/pppd
root      5203  0.0  0.2   1700   480 tty1     Ss+  03:08   0:00 /sbin/getty 384
joe       6307  0.0  2.5  81172  4788 ?        Sl   03:08   0:00 /usr/lib/evolut
joe       6557  0.0  4.8  68700  9336 ?        Sl   03:09   0:01 /usr/lib/evolut
joe       6750 18.8 23.4 163000 44912 ?        Sl   03:09   5:09 /usr/lib/mozill
cupsys   10550  0.1  1.4   7496  2724 ?        SNs  03:12   0:02 /usr/sbin/cupsd
joe      14316  8.9 12.5  48308 24060 ?        S    03:16   1:48 gaim
syslog   22840  0.0  0.4   2168   864 ?        SNs  03:21   0:00 /sbin/syslogd -
joe       8694 15.7  8.0  46716 15312 ?        Sl   03:36   0:02 gnome-terminal
joe       8929  0.2  0.4   2924   812 ?        S    03:36   0:00 gnome-pty-helpe
joe       8930  2.6  1.1   6076  2232 pts/1    Ss   03:36   0:00 bash
joe       9022  0.0  0.5   5084  1112 pts/1    R+   03:36   0:00 ps aux
joe       9032  0.0  2.7  13468  5192 pts/0    R+   03:36   0:00 perl /usr/share

---

### Post by fenderlicious on 2006-04-11
Um, so I gave the list.

---

### Post by DeadMazzay on 2006-04-11
Oh yes,  if you are not in sudoers you will not be able to execute sudo or gksudo...

Can you just log-in as root in tty1?
Can you do "su" followed by root password after prompt (in Gnome terminal)?

If one these works, edit /etc/sudoers and add yourself as I mentioned above.
By the way can you post your /etc/sudoers file here? (cat /etc/sudoers in terminal)?

---

### Post by DeadMazzay on 2006-04-11
Thie problem is (I hope) that Ubunti doesn't tell you about insufficient permissions if you run administrative tasks from Gnome menu.

---

### Post by fenderlicious on 2006-04-11
[QUOTE=DeadMazzay]Oh yes,  if you are not in sudoers you will not be able to execute sudo or gksudo...

Can you just log-in as root in tty1?
Can you do "su" followed by root password after prompt (in Gnome terminal)?

If one these works, edit /etc/sudoers and add yourself as I mentioned above.
By the way can you post your /etc/sudoers file here? (cat /etc/sudoers in terminal)?[/QUOTE]


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

---

### Post by DeadMazzay on 2006-04-11
So you are almost done! 
Login as root on tty1, edit this file (the most common way would be "nano /etc/sudoers" which brings up 'nano' text editor) and add a line below "root..." with your username, so you should get 
```

# User privilege specification
root ALL=(ALL) ALL
your_username ALL=(ALL) ALL

```

---

### Post by fenderlicious on 2006-04-11
XD I used visudo instead, I started calling up info on the sudoers command, and played around and found it! I really really appreciate your help!

---

### Post by Ramses de Norre on 2006-04-11
By adding this line: ```
# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```
you get the default lay out which makes that every member of the admin group is allowed to use sudo,  you then just add the privileged users to admin.

---

