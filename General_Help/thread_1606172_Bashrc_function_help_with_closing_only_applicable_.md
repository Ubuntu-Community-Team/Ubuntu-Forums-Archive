---
title: "Bashrc function help with closing only applicable gnome-terminal"
date: 2010-10-26
forum: General Help
---

### Post by inameiname on 2010-10-26
I wrote this little function that I use from my '~/.bashrc' (from a script I also made, with help) to run a program on a timer, however there is one small issue I'm having.

```

##### Run program on a timer

# Usage: program-timer <program> <runlength (in secs)>
function program-timer()
{
$1 &
mypid=`eval ps ax|grep "$1"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
mins=0
secs=0
startsecs=`eval date +%-S `
starthours=`eval date +%-H`
startmins=`eval date +%-M`

#echo "startsecs=$startsecs starthours=$starthours startmins=$startmins"

while [ $secs -lt "$2" ]; do
    cursecs=`eval date +%-S `
    curhours=`eval date +%-H`
    curmins=`eval date +%-M`
    echo "Aval..."
    secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
    echo "Secs: $secs"
    sleep 1
done
kill "$mypid"
if [ $? -eq 0 ]; then
    echo "Process $mypid was killed"
fi
killall gnome-terminal
}

```Basically, it works just fine, but the issue I'd love to get help with is when the timer runs out, it doesn't shutdown the program. That is, not until I close gnome-terminal. I've tried 'exit' in several places, but it doesn't seem to close it.

Now, the above script does what I want, but using 'killall gnome-terminal' not only closes the gnome-terminal window I am running the function on, but ALL gnome-terminal windows I may have open.

Does anybody see a simple way to fix my small dilemma, to have it close only the gnome-terminal window I'm running the function on?

---

### Post by DaithiF on 2010-10-26
use ps to also grab the pid of your process's parent (which will be gnome-terminal).  If you use the -f flag with ps you get the 'full format' listing, which includes process id and parent process id side-by-side.

---

### Post by inameiname on 2010-10-26
So.....whereabouts would I add the 'ps -f'?

Perhaps on this line 'kill "$mypid"'?

Forgive my ignorance here, I'm not too familiar with ps and whatnot.

---

### Post by Wayne_V on 2010-10-26
PP=`ps -f $mypid | tail -1 | awk '{print $3}'

will return PPID in PP

---

### Post by inameiname on 2010-10-26
Not to sound greedy, but could you put that into the appropriate spot on my script? I'm at a loss of just where it'd go and that would probably be easiest.

---

### Post by DaithiF on 2010-10-26
something like the below.  Note that you'll have to navigate up through two levels of ancestor process to get to the enclosing gnome-terminal.

```
$1 & pid=$!       # execute $1 in background, and grab its pid
parent_pid=$(ps -fp $pid | tail -1 | awk '{print $3}')     # parent_pid will be the bash shell from which you are executing
grandparent_pid=$(ps -fp $parent_pid | tail -1 | awk '{print $3 }')    # grand-parent pid will be the pid of the gnome-terminal in which your shell is running

```

then at the end:
```
kill -9 $grandparent_pid

```

---

### Post by DaithiF on 2010-10-26
note also, if you are using Bash as your shell, then you can save yourself some of this by using the inbuilt $BASHPID variable to get the pid of the current shell process, and then you have only one parent lookup to do:

```
parent_pid=$(ps -fp $BASHPID | tail -1 | awk '{print $3}')

```

---

### Post by inameiname on 2010-10-26
Thank you. Okay, I get the use of PID and what those two replies/codes mean, but I can't seem to figure out where to put them.

If I add it at the beginning, and then the 'kill' command at the end, it does not work. 

```

##### Run program on a timer

# Usage: program-timer <program> <runlength (in secs)>
function program-timer()
{
$1 & pid=$!       # execute $1 in background, and grab its pid
parent_pid=$(ps -fp $pid | tail -1 | awk '{print $3}')     # parent_pid will be the bash shell from which you are executing
grandparent_pid=$(ps -fp $parent_pid | tail -1 | awk '{print $3 }')    # grand-parent pid will be the pid of the gnome-terminal in which your shell is running
mins=0
secs=0
startsecs=`eval date +%-S `
starthours=`eval date +%-H`
startmins=`eval date +%-M`

#echo "startsecs=$startsecs starthours=$starthours startmins=$startmins"

while [ $secs -lt "$2" ]; do
    cursecs=`eval date +%-S `
    curhours=`eval date +%-H`
    curmins=`eval date +%-M`
    echo "Aval..."
    secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
    echo "Secs: $secs"
    sleep 1
done
kill -9 $grandparent_pid
}

```

Doesn't work.

---

### Post by DaithiF on 2010-10-26
> **inameiname said:**
> Doesn't work.

That doesn't give us much to go on.

How about adding some debug statements to show what pids you are capturing:

```
echo "Process pid is $mypid, parent is $parent_pid, grandparent_pid is $grandparent_pid"
```

and how about you also capture a process listing as the script is running:
```
ps -ef > /home/you/debug-processlisting

```

then compare the two to see how/why the gnome-terminal survives.

by the way, the seconds, minutes, hours stuff is unnecessary.  look at 
```
date +%s

```
instead.

---

### Post by inameiname on 2010-10-26
My bad. What I meant by the above script, with the added tweaking, not working is that it isn't doing the one thing I wanted, to close the terminal and the program. Here is the updated script, with the terminal output below:

```

##### Run program on a timer

# Usage: program-timer <program> <runlength (in secs)>
function program-timer()
{
$1 & pid=$!       # execute $1 in background, and grab its pid
parent_pid=$(ps -fp $pid | tail -1 | awk '{print $3}')     # parent_pid will be the bash shell from which you are executing
grandparent_pid=$(ps -fp $parent_pid | tail -1 | awk '{print $3 }')    # grand-parent pid will be the pid of the gnome-terminal in which your shell is running
#echo "Process pid is $mypid, parent is $parent_pid, grandparent_pid is $grandparent_pid"
mins=0
secs=0
startsecs=`eval date +%-S `
starthours=`eval date +%-H`
startmins=`eval date +%-M`

#echo "startsecs=$startsecs starthours=$starthours startmins=$startmins"

while [ $secs -lt "$2" ]; do
    cursecs=`eval date +%-S `
    curhours=`eval date +%-H`
    curmins=`eval date +%-M`
    echo "Aval..."
    secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
    echo "Secs: $secs"
    sleep 1
done
kill -9 $grandparent_pid
}

``````

[1] 3431
ERROR: Conflicting format options.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
ERROR: List of process IDs must follow -p.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
Aval...
Secs: 0

(viewnior:3431): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
    'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
Aval...
Secs: 1
Aval...
Secs: 2
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

```It's funny, though, as by adding 'echo "Process pid is $mypid, parent is $parent_pid, grandparent_pid is $grandparent_pid"' (without single quotes), it doesn't even give all that. the countdown isn't there, AND so isn't 'kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]' (with the single quotes).

And by adding at the very end, I get these results, showing the same PID: 

ps -ef > /home/me/debug-processlisting 

```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 19:20 ?        00:00:00 /sbin/init
root         2     0  0 19:20 ?        00:00:00 [kthreadd]
root         3     2  0 19:20 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 19:20 ?        00:00:00 [migration/0]
root         5     2  0 19:20 ?        00:00:00 [watchdog/0]
root         6     2  0 19:20 ?        00:00:00 [migration/1]
root         7     2  0 19:20 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 19:20 ?        00:00:00 [watchdog/1]
root         9     2  0 19:20 ?        00:00:00 [events/0]
root        10     2  0 19:20 ?        00:00:00 [events/1]
root        11     2  0 19:20 ?        00:00:00 [cpuset]
root        12     2  0 19:20 ?        00:00:00 [khelper]
root        13     2  0 19:20 ?        00:00:00 [netns]
root        14     2  0 19:20 ?        00:00:00 [async/mgr]
root        15     2  0 19:20 ?        00:00:00 [pm]
root        17     2  0 19:20 ?        00:00:00 [sync_supers]
root        18     2  0 19:20 ?        00:00:00 [bdi-default]
root        19     2  0 19:20 ?        00:00:00 [kintegrityd/0]
root        20     2  0 19:20 ?        00:00:00 [kintegrityd/1]
root        21     2  0 19:20 ?        00:00:00 [kblockd/0]
root        22     2  0 19:20 ?        00:00:00 [kblockd/1]
root        23     2  0 19:20 ?        00:00:00 [kacpid]
root        24     2  0 19:20 ?        00:00:00 [kacpi_notify]
root        25     2  0 19:20 ?        00:00:00 [kacpi_hotplug]
root        26     2  0 19:20 ?        00:00:00 [ata_aux]
root        27     2  0 19:20 ?        00:00:00 [ata_sff/0]
root        28     2  0 19:20 ?        00:00:00 [ata_sff/1]
root        29     2  0 19:20 ?        00:00:00 [khubd]
root        30     2  0 19:20 ?        00:00:00 [kseriod]
root        31     2  0 19:20 ?        00:00:00 [kmmcd]
root        32     2  0 19:20 ?        00:00:00 [khungtaskd]
root        33     2  0 19:20 ?        00:00:00 [kswapd0]
root        34     2  0 19:20 ?        00:00:00 [ksmd]
root        35     2  0 19:20 ?        00:00:00 [aio/0]
root        36     2  0 19:20 ?        00:00:00 [aio/1]
root        37     2  0 19:20 ?        00:00:00 [ecryptfs-kthrea]
root        38     2  0 19:20 ?        00:00:00 [crypto/0]
root        39     2  0 19:20 ?        00:00:00 [crypto/1]
root        50     2  0 19:20 ?        00:00:00 [scsi_eh_0]
root        51     2  0 19:20 ?        00:00:00 [scsi_eh_1]
root        54     2  0 19:20 ?        00:00:00 [kstriped]
root        55     2  0 19:20 ?        00:00:00 [kmpathd/0]
root        56     2  0 19:20 ?        00:00:00 [kmpathd/1]
root        57     2  0 19:20 ?        00:00:00 [kmpath_handlerd]
root        58     2  0 19:20 ?        00:00:00 [ksnapd]
root        59     2  0 19:20 ?        00:00:00 [kondemand/0]
root        60     2  0 19:20 ?        00:00:00 [kondemand/1]
root        61     2  0 19:20 ?        00:00:00 [kconservative/0]
root        62     2  0 19:20 ?        00:00:00 [kconservative/1]
root       252     2  0 19:20 ?        00:00:00 [scsi_eh_2]
root       279     2  0 19:20 ?        00:00:00 [scsi_eh_3]
root       282     2  0 19:20 ?        00:00:00 [scsi_eh_4]
root       285     2  0 19:21 ?        00:00:00 [scsi_eh_5]
root       286     2  0 19:21 ?        00:00:00 [usb-storage]
root       296     2  0 19:21 ?        00:00:00 [i915]
root       307     2  0 19:21 ?        00:00:00 [kslowd000]
root       308     2  0 19:21 ?        00:00:00 [kslowd001]
root       361     2  0 19:21 ?        00:00:00 [jbd2/sda1-8]
root       362     2  0 19:21 ?        00:00:00 [ext4-dio-unwrit]
root       363     2  0 19:21 ?        00:00:00 [ext4-dio-unwrit]
root       389     2  0 19:21 ?        00:00:00 [flush-8:0]
root       425     1  0 19:21 ?        00:00:00 upstart-udev-bridge --daemon
root       427     1  0 19:21 ?        00:00:00 udevd --daemon
root       587   427  0 19:21 ?        00:00:00 udevd --daemon
root       588   427  0 19:21 ?        00:00:00 udevd --daemon
root       633     2  0 19:21 ?        00:00:00 [kpsmoused]
root       735     2  0 19:21 ?        00:00:00 [cfg80211]
root       804     2  0 19:21 ?        00:00:00 [iwl3945]
root       807     2  0 19:21 ?        00:00:00 [phy0]
root       829     2  0 19:21 ?        00:00:00 [hd-audio0]
root      1008     1  0 19:21 ?        00:00:00 smbd -F
syslog    1018     1  0 19:21 ?        00:00:00 rsyslogd -c4
102       1048     1  0 19:21 ?        00:00:00 dbus-daemon --system --fork
root      1051  1008  0 19:21 ?        00:00:00 smbd -F
root      1072     1  0 19:21 ?        00:00:00 NetworkManager
root      1074     1  0 19:21 ?        00:00:00 gdm-binary
avahi     1081     1  0 19:21 ?        00:00:00 avahi-daemon: running [TJ32H4LSGH9GDW.local]
avahi     1084  1081  0 19:21 ?        00:00:00 avahi-daemon: chroot helper
root      1087     1  0 19:21 ?        00:00:00 /usr/sbin/modem-manager
root      1092     1  0 19:21 ?        00:00:00 /usr/sbin/console-kit-daemon --no-daemon
root      1184  1074  0 19:21 ?        00:00:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1219     1  0 19:21 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1233  1184  5 19:21 tty7     00:01:03 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-bw2lPP/database -nolisten tcp vt7
root      1264     1  0 19:21 ?        00:00:00 /sbin/wpa_supplicant -u -s
root      1281     1  0 19:21 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1285     1  0 19:21 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1296     1  0 19:21 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1300     1  0 19:21 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1306     1  0 19:21 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1308     1  0 19:21 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1310     1  0 19:21 ?        00:00:00 cron
daemon    1311     1  0 19:21 ?        00:00:00 atd
gdm       1591     1  0 19:21 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session
root      1617  1184  0 19:21 ?        00:00:00 /usr/lib/gdm/gdm-session-worker
root      1620     1  0 19:21 ?        00:00:00 /usr/lib/upower/upowerd
root      1642     1  0 19:21 ?        00:00:00 /usr/lib/policykit-1/polkitd
me        1723     1  0 19:21 ?        00:00:00 /usr/bin/gnome-keyring-daemon --daemonize --login
me        1742  1617  0 19:21 ?        00:00:00 gnome-session
me        1772  1742  0 19:21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
me        1775     1  0 19:21 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session gnome-session
me        1776     1  0 19:21 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
me        1781     1  0 19:21 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2
me        1788     1  0 19:21 ?        00:00:01 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
me        1789  1742  0 19:21 ?        00:00:00 gnome-power-manager
me        1794     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfsd
me        1800     1  0 19:21 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
me        1801  1742  1 19:21 ?        00:00:11 compiz
rtkit     1804     1  0 19:21 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
me        1829  1800  0 19:21 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
me        1832     1  0 19:21 ?        00:00:00 syndaemon -i 0.5 -k
me        1836     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1841     1  0 19:21 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      1844  1841  0 19:21 ?        00:00:00 udisks-daemon: polling /dev/sdb /dev/sr0
me        1845  1742  1 19:21 ?        00:00:15 nautilus
me        1847     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
me        1849  1742  0 19:21 ?        00:00:00 gnome-panel
me        1852  1742  0 19:21 ?        00:00:00 gnome-volume-control-applet
me        1853     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
me        1856  1742  0 19:21 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
me        1858  1742  0 19:21 ?        00:00:02 nm-applet --sm-disable
me        1867     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/gvfs/exec_spaw/0
me        1869     1  0 19:21 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=20
me        1881     1  0 19:21 ?        00:00:03 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=22
me        1882     1  0 19:21 ?        00:00:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=34
me        1883     1  0 19:21 ?        00:00:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=28
me        1891  1801  0 19:21 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
me        1892  1891  0 19:21 ?        00:00:01 /usr/bin/gtk-window-decorator
me        1896     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.11 /org/gtk/gvfs/exec_spaw/1
me        1907     1  0 19:21 ?        00:00:00 /usr/bin/python /usr/lib/ubuntu-sso-client/ubuntu-sso-login
me        1927     1  0 19:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
me        1930     1  0 19:21 ?        00:00:00 gnome-screensaver
me        1938  1742  0 19:21 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
root      1939  1072  0 19:21 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-01af51f6-82de-43c9-a3de-ec14d4c7e035-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
me        1945     1  0 19:21 ?        00:00:00 /bin/sh /usr/bin/firefox
me        1958  1945  0 19:21 ?        00:00:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
me        1962  1958 15 19:21 ?        00:02:48 /opt/firefox/firefox-bin
me        1980     1  0 19:21 ?        00:00:00 /usr/lib/notify-osd/notify-osd
root      2039     1  0 19:21 ?        00:00:00 nmbd -D
ntp       2089     1  0 19:21 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 116:125
clamav    2120     1  0 19:21 ?        00:00:00 /usr/sbin/clamd
clamav    2227     1  0 19:21 ?        00:00:00 /usr/bin/freshclam -d --quiet
proxy     2237     1  0 19:21 ?        00:00:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid daemonise=true logFile=/var/log/polipo/polipo.log forbiddenFile=/etc/polipo/forbidden
117       2246     1  0 19:21 ?        00:00:09 /usr/sbin/tor
root      2259     1  0 19:21 ?        00:00:00 /usr/sbin/winbindd
root      2261  2259  0 19:21 ?        00:00:00 /usr/sbin/winbindd
root      2363     1  0 19:21 tty1     00:00:00 /sbin/getty -8 38400 tty1
me        2430  1962  0 19:22 ?        00:00:00 /opt/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so 1962 plugin true
me        2447  1742  0 19:22 ?        00:00:00 update-notifier
root      2456     1  0 19:22 ?        00:00:00 dbus-launch --autolaunch=5b5b90b582349319019609930000000b --binary-syntax --close-stderr
root      2457     1  0 19:22 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      2609     1  0 19:22 ?        00:00:00 /usr/bin/python /usr/lib/system-service/system-service-d
me        3172     1  3 19:30 ?        00:00:18 gedit /home/me/Temp/new file
me        3178  3172  0 19:30 ?        00:00:00 gnome-pty-helper
me        3179  3172  0 19:30 pts/0    00:00:00 /bin/bash
me        3554  1801  0 19:40 ?        00:00:00 /bin/sh -c gnome-terminal
me        3555  3554  2 19:40 ?        00:00:00 gnome-terminal
me        3558  3555  0 19:40 ?        00:00:00 gnome-pty-helper
me        3559  3555  4 19:40 pts/1    00:00:00 bash
me        3592  3559  4 19:40 pts/1    00:00:00 viewnior
me        3629  3559  0 19:40 pts/1    00:00:00 ps -ef

```

Finally, as for the date suggestion, I thought most of that hours, minutes, seconds was unnessary, I just don't know how to go about removing it. This isn't originally my script. I've just tweaked it a little to work in the terminal.

---

### Post by inameiname on 2010-10-26
Bump

---

### Post by inameiname on 2010-10-27
Nevermind. I ended up finding a much simpler and easier bashrc function to use:

```

##### Run program on a timer

# Example: program-timer 20 viewnior arg1
program-timer() { perl -e 'alarm shift; exec @ARGV' "$@" & exit; }

```

It does exactly as the one above. I even added the 'exit' at the end so it'll automatically close the 'gnome-terminal'. 

Thanks for all of your help, though. 

Nonetheless, I decided to keep my "Program-Timer.sh" script, which is essentially the same as above, as it works in that form:

```

#!/bin/bash
#sample script to start a program, permit it to run for a predefined amount of wallclock time, then kill it.  Specify time in seconds
#
progID=$(zenity --entry --text="What is the desired program you would like to run?")
$progID &
mypid=`eval ps ax|grep "$progID"|grep -iv "grep"| awk '{print $1}'`
echo "mypid $mypid"
mins=0
secs=0
killmins=$(zenity --entry --text="How long would you like it to run? (in seconds)")
startsecs=`eval date +%-S `
starthours=`eval date +%-H`
startmins=`eval date +%-M`

#echo "startsecs=$startsecs starthours=$starthours startmins=$startmins"

while [ $secs -lt $killmins ]; do
    cursecs=`eval date +%-S `
    curhours=`eval date +%-H`
    curmins=`eval date +%-M`
    echo "Aval..."
    secs=$(( (curhours-starthours)*3600 + (curmins-startmins)*60 - startsecs + cursecs ))
    echo "Secs: $secs"
    sleep 1
done
kill "$mypid"
if [ $? -eq 0 ]; then
    echo "Process $mypid was killed"
fi

```

---

### Post by DaithiF on 2010-10-27
Hi, agreed that the perl way is better.

just for the record, I don't know why the other method didn't work for you ... heres a stripped down version I've tried just now that works fine for me:
```

function timer() {
    start_time=$(date +%s)
    end_time=$(( $start_time + $2))

    $1 & pid=$!

    parent=$(ps -fp $pid | tail -1 | awk '{print $3}')
    grandparent=$(ps -fp $parent | tail -1 | awk '{print $3}')

    secs=$(date +%s)
    while [ $secs -le $end_time ]
    do
        sleep 1
        secs=$(date +%s)
    done
    kill -9 $pid
    kill -9 $grandparent
}

```

---

### Post by inameiname on 2010-10-27
Thanks for the updated version. Unfortunately, it doesn't work for me as it is in your above code. I get this error when testing it out. It does close the program, but not the terminal window:

```

[1] 27418
ERROR: Conflicting format options.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy
ERROR: List of process IDs must follow -p.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users
x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy

(viewnior:27418): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
    'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
me@~ $ [1]+  Killed                  $1

```

---

### Post by DaithiF on 2010-10-28
I guess it doesn't much matter, but the 'ERROR: Conflicting format options' error arises at this line:
```
parent=$(ps -fp $pid | tail -1 | awk '{print $3}')
```
which causes $parent to be blank, and thus gives the 'ERROR: List of process IDs must follow -p.'  at this line:
```
grandparent=$(ps -fp $parent | tail -1 | awk '{print $3}')
```

The root cause is either a typo in your version of the parent=... line, or else you are getting an incorrect $pid from earlier such that $pid has some trailing characters that ps then complains about.

---

### Post by inameiname on 2010-10-28
Strange. I literally just copied and pasted yours above, so if you said it worked for you, I'm not sure why it doesn't for me. Hopefully it's not a sign of some more serious issue regarding bad 'pid' assignments or whatever, if that makes any sense.

---

