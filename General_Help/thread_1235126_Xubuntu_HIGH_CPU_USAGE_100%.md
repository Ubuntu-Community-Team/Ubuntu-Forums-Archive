---
title: "Xubuntu HIGH CPU USAGE 100%"
date: 2009-08-08
forum: General Help
---

### Post by dtrot55 on 2009-08-08
I just installed Xubnutu on my Dell Inspiron 9200 and once I updated to 9.04 my cpu is now being used at 100% no matter what I'm doing...I dont even do anything but log in and my cpu fan is going nutz and cpu usage is 100%....anyone has some ideas?

---

### Post by mikewhatever on 2009-08-08
Can you check what processes use CPU the most. If you don't know how, just post the output of **ps aux** command.

---

### Post by bodyharvester on 2009-08-08
check System Monitor and then open a terminal ant type "top" then compare the results, screenshots might help

---

### Post by dtrot55 on 2009-08-08
Here is my stuff from ps aux:


dtrot@dtrot-xubuntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.1   3084  1888 ?        Ss   21:16   0:02 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   21:16   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   21:16   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   21:16   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:16   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   21:16   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   21:16   0:00 [khelper]
root         8  0.0  0.0      0     0 ?        S<   21:16   0:00 [kstop/0]
root         9  0.0  0.0      0     0 ?        S<   21:16   0:00 [kintegrityd/0]
root        10  0.0  0.0      0     0 ?        S<   21:16   0:00 [kblockd/0]
root        11  0.0  0.0      0     0 ?        S<   21:16   0:00 [kacpid]
root        12  0.0  0.0      0     0 ?        S<   21:16   0:00 [kacpi_notify]
root        13  0.0  0.0      0     0 ?        S<   21:16   0:00 [cqueue]
root        14  0.0  0.0      0     0 ?        S<   21:16   0:00 [ata/0]
root        15  0.0  0.0      0     0 ?        S<   21:16   0:00 [ata_aux]
root        16  0.0  0.0      0     0 ?        S<   21:16   0:00 [ksuspend_usbd]
root        17  0.0  0.0      0     0 ?        S<   21:16   0:00 [khubd]
root        18  0.0  0.0      0     0 ?        S<   21:16   0:00 [kseriod]
root        19  0.0  0.0      0     0 ?        S<   21:16   0:00 [kmmcd]
root        20  0.0  0.0      0     0 ?        S<   21:16   0:00 [btaddconn]
root        21  0.0  0.0      0     0 ?        S<   21:16   0:00 [btdelconn]
root        22  0.0  0.0      0     0 ?        S    21:16   0:00 [pdflush]
root        23  0.0  0.0      0     0 ?        S    21:16   0:00 [pdflush]
root        24  0.0  0.0      0     0 ?        S<   21:16   0:00 [kswapd0]
root        25  0.0  0.0      0     0 ?        S<   21:16   0:00 [aio/0]
root        26  0.0  0.0      0     0 ?        S<   21:16   0:00 [ecryptfs-kthr]
root        29  0.0  0.0      0     0 ?        S<   21:16   0:00 [scsi_eh_0]
root        30  0.0  0.0      0     0 ?        S<   21:16   0:00 [scsi_eh_1]
root        31  0.0  0.0      0     0 ?        S<   21:16   0:00 [kstriped]
root        32  0.0  0.0      0     0 ?        S<   21:16   0:00 [kmpathd/0]
root        33  0.0  0.0      0     0 ?        S<   21:16   0:00 [kmpath_handle]
root        34  0.0  0.0      0     0 ?        S<   21:16   0:00 [ksnapd]
root        35  0.0  0.0      0     0 ?        S<   21:16   0:00 [kondemand/0]
root        36  0.0  0.0      0     0 ?        S<   21:16   0:00 [krfcommd]
root       254  0.0  0.0      0     0 ?        S<   21:16   0:00 [khpsbpkt]
root       350  0.0  0.0      0     0 ?        S<   21:16   0:00 [knodemgrd_0]
root       685  0.0  0.0      0     0 ?        S<   21:16   0:00 [kjournald]
root       819  0.0  0.0   2224   568 ?        S<s  21:16   0:00 /sbin/udevd --d
root      1301  0.0  0.0      0     0 ?        S<   21:16   0:00 [kpsmoused]
root      1459  0.0  0.0      0     0 ?        S<   21:16   0:00 [ipw2200/0]
root      1525  0.0  0.0      0     0 ?        S<   21:16   0:00 [pccardd]
root      2088  0.0  0.0   1808   532 tty4     Ss+  21:16   0:00 /sbin/getty 384
root      2089  0.0  0.0   1808   528 tty5     Ss+  21:16   0:00 /sbin/getty 384
root      2095  0.0  0.0   1808   528 tty2     Ss+  21:16   0:00 /sbin/getty 384
root      2097  0.0  0.0   1808   524 tty3     Ss+  21:16   0:00 /sbin/getty 384
root      2098  0.0  0.0   1808   528 tty6     Ss+  21:16   0:00 /sbin/getty 384
root      2163  0.0  0.1   2204  1088 ?        Ss   21:16   0:00 /usr/sbin/acpid
syslog    2212  0.0  0.0   2040   684 ?        Ss   21:16   0:00 /sbin/syslogd -
root      2235  0.0  0.0   1968   540 ?        S    21:16   0:00 /bin/dd bs 1 if
klog      2237  0.0  0.2   3732  2488 ?        Ss   21:16   0:00 /sbin/klogd -P
105       2260  0.0  0.1   2936  1284 ?        Ss   21:16   0:00 /bin/dbus-daemo
108       2308  0.0  0.4   6504  4432 ?        Ss   21:16   0:00 /usr/sbin/hald
root      2311  0.0  0.2  16356  2580 ?        Ssl  21:16   0:00 /usr/sbin/conso
root      2374  0.0  0.1   3328  1156 ?        S    21:16   0:00 hald-runner
root      2404  0.0  0.2   5176  2116 ?        S    21:16   0:00 /usr/lib/hal/ha
root      2407  0.0  0.1   5176  1792 ?        S    21:16   0:00 hald-addon-inpu
root      2454  0.0  0.1   5180  1804 ?        S    21:16   0:00 hald-addon-stor
root      2456  0.0  0.1   5188  1780 ?        S    21:16   0:00 /usr/lib/hal/ha
108       2458  0.0  0.1   5032  1808 ?        S    21:16   0:00 hald-addon-acpi
root      2477  0.0  0.1   3556  1664 ?        Ss   21:16   0:00 /usr/sbin/bluet
root      2511  0.0  0.1  15032  1772 ?        Ss   21:16   0:00 /usr/sbin/gdm -
root      2514  0.0  0.3  15588  3308 ?        S    21:16   0:00 /usr/sbin/gdm -
root      2518  0.5  2.2  37168 23432 tty7     Ss+  21:16   0:03 /usr/bin/X :0 -
root      2542  0.0  0.2  16428  2792 ?        Ssl  21:16   0:00 /usr/sbin/Netwo
root      2546  0.0  0.1   4280  1872 ?        S    21:16   0:00 /sbin/wpa_suppl
root      2551  0.0  0.3   6936  3104 ?        S    21:16   0:00 /usr/sbin/nm-sy
avahi     2570  0.0  0.1   2944  1480 ?        Ss   21:16   0:00 avahi-daemon: r
avahi     2575  0.0  0.0   2944   508 ?        Ss   21:16   0:00 avahi-daemon: c
root      2604  0.0  0.2   6108  2316 ?        Ss   21:16   0:00 /usr/sbin/cupsd
root      2624  0.0  0.1   4324  1156 ?        Ss   21:16   0:00 /usr/bin/system
daemon    2699  0.0  0.0   2096   456 ?        Ss   21:16   0:00 /usr/sbin/atd
root      2727  0.0  0.1   3480  1032 ?        Ss   21:16   0:00 /usr/sbin/cron
root      2820  0.0  0.0   1808   528 tty1     Ss+  21:16   0:00 /sbin/getty 384
dtrot     2992  0.0  0.2  17344  2328 ?        S    21:17   0:00 /usr/bin/gnome-
dtrot     3007  0.0  0.0   1872   532 ?        Ss   21:17   0:00 /bin/sh /etc/xd
dtrot     3143  0.0  0.0   4784   604 ?        Ss   21:17   0:00 /usr/bin/ssh-ag
dtrot     3146  0.0  0.0   3144   688 ?        S    21:17   0:00 /usr/bin/dbus-l
dtrot     3147  0.0  0.1   2932  1044 ?        Ss   21:17   0:00 //bin/dbus-daem
dtrot     3157  0.0  0.6  25208  6680 ?        Sl   21:17   0:00 /usr/bin/xfce4-
dtrot     3159  0.0  0.3   6416  3220 ?        S    21:17   0:00 /usr/lib/libgco
dtrot     3161  0.0  0.1   3664  1772 ?        S    21:17   0:00 /usr/lib/xfconf
dtrot     3166  0.0  0.3  15488  3224 ?        S    21:17   0:00 xfsettingsd
dtrot     3168  0.1  1.1  21440 12160 ?        S    21:17   0:01 xfwm4 --sm-clie
dtrot     3169  0.0  0.3  16508  3880 ?        Ss   21:17   0:00 gnome-screensav
dtrot     3174  0.0  0.6  18588  6972 ?        S    21:17   0:00 Thunar --sm-cli
dtrot     3176  0.0  0.1   3060  1216 ?        S    21:17   0:00 /usr/lib/gamin/
dtrot     3178  0.1  1.4  28312 14888 ?        S    21:17   0:01 xfce4-panel -r
dtrot     3179  0.2  1.7  49596 17664 ?        S    21:17   0:01 xfdesktop --sm-
dtrot     3180  0.0  0.4  17960  4160 ?        S    21:17   0:00 xfce4-settings-
dtrot     3181  0.4  2.7  53252 28464 ?        S    21:17   0:02 pidgin --sessio
dtrot     3182  0.1  1.6  35052 17344 ?        S    21:17   0:00 update-notifier
dtrot     3195  0.0  0.8  24756  8648 ?        Ss   21:17   0:00 gnome-power-man
dtrot     3197  0.0  0.1   5616  2048 ?        S    21:17   0:00 /usr/lib/gvfs/g
dtrot     3201  0.1  1.3  29004 14256 ?        S    21:17   0:00 /usr/lib/xfce4/
dtrot     3202  0.1  1.3  28916 14248 ?        S    21:17   0:00 /usr/lib/xfce4/
dtrot     3263  0.1  1.5  32460 15600 ?        Ss   21:18   0:01 nm-applet --sm-
dtrot     3269  0.0  1.3  27816 14184 ?        Ss   21:18   0:00 python /usr/sha
dtrot     3274  0.1  1.0  24696 11080 ?        Ss   21:18   0:00 bluetooth-apple
dtrot     3276  0.1  1.4  29964 14700 ?        S    21:18   0:00 xfce4-settings-
dtrot     3278  0.0  0.5  17672  6016 ?        S    21:18   0:00 /usr/lib/notifi
dtrot     3280  0.1  1.5  30888 15784 ?        R    21:18   0:00 xfce4-terminal
root      3363  0.0  0.0   2276   984 ?        S    21:18   0:00 /sbin/dhclient
dtrot     3429  0.0  1.0  24388 10596 ?        S    21:18   0:00 /usr/lib/thunar
dtrot     3430  0.0  0.0   2036   696 ?        S    21:18   0:00 gnome-pty-helpe
dtrot     3431  0.0  0.3   5876  3156 pts/0    Ss   21:18   0:00 bash
dtrot     4554  0.0  0.1   2768  1032 pts/0    R+   21:27   0:00 ps aux

---

### Post by dtrot55 on 2009-08-08
here is results after top:

[IMG]http://i103.photobucket.com/albums/m142/dtrot55/top.jpg[/IMG]

---

### Post by kerry_s on 2009-08-08
that looks fine to me, it's not running at 100%.

---

### Post by bodyharvester on 2009-08-09
> **kerry_s said:**
> that looks fine to me, it's not running at 100%.

i agree, but was that you said about the fan? maybe you need a new one?

seems fine to me

---

### Post by gjoellee on 2009-08-09
You're using 10% CPU on that screenshot. Looks fine.

---

### Post by dtrot55 on 2009-08-09
yeah knowing my luck...I unplugged the computer for over an hour and rebooted and it didnt happen...if I have the issue again i will be sure to do both of those and re post...but for awhile there i couldnt do anything because the computer was so sluggish...thanks for the help

---

### Post by Barafu Albino Cheetah on 2009-08-09
If CPU overheats, it begins to skip every second Hz. On some systems/COPUs it is said to show up 50% load.

---

### Post by dtrot55 on 2009-08-09
EVerything was running fine until I went to a site with flash....now back up to 90%-100% cpu usage...and once this happens it doesn't quit until I turn off the computer totally.  See screen shot after doing "Top" again:

[IMG]http://i103.photobucket.com/albums/m142/dtrot55/cpu.png[/IMG]

---

### Post by kerry_s on 2009-08-09
then it sounds like you got flash issue, try right clicking the flash> settings & turn off hardware acceleration, have you tried removing and reinstalling it?

it's perfectly normal for it to be at 100% when loading or playing flash, it usually goes up & down depending on the vid. i've seen that a lot on my older systems where the cpu is just straining to keep up with vid. sometimes you can right click an select to use a lower quality.

looking at your screenshot it looks perfectly normal firefox is not using 100%, but all the process's combined is whats causing it to max out.

what is your cpu specs? (cat /proc/cpuinfo)

---

### Post by dtrot55 on 2009-08-10
Firefox seems to be one issue but I have been having times where im not really doing anything and the fan kicks in and CPU usage goes up...Right now I am running a Dell Inspiron 9200...Think it has a Pent M 2.0ghz processor with 1 gig of ram...it runs fine until sometime triggers the cpu to go weird...don't know exactly what is causing it yet but Firefox and flash are 1 of the things that do....mostly if there is a flash stream it does it...but it doesn't go away even after i close FF it still eats up the processor.  Anyone have some ideas?

---

