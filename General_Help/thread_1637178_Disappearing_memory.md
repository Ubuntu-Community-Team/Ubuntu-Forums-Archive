---
title: "Disappearing memory"
date: 2010-12-04
forum: General Help
---

### Post by jjguitars on 2010-12-04
If I just run free -m immediately after I boot the computer (amd quad with 6gb ) and then leave the computer alone for a while and then run free -m again, the figures are completely different and if I leave the computer for about an hour applications will not start but the desktop is responsive. I have to reboot.
Below is what a few iterations of free give me

*Immediately after boot*
@-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5983       1046       4937          0        106        426
-/+ buffers/cache:        513       5469
Swap:         2925          0       2925

*then after 30 minutes (computer not used at all)*

@-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5983       2761       3222          0        125       2086
-/+ buffers/cache:        549       5434
Swap:         2925          0       2925

*then after 1 hour on no usage*

@jeremy-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5983       2812       3170          0        125       2136
-/+ buffers/cache:        550       5433
Swap:         2925          0       2925

Any suggestions as to what may be causing this and what I should do to fix it would be appreciated. TIA.

---

### Post by TeoBigusGeekus on 2010-12-04
```
top
```
to see what's using all this memory (even better: htop)

---

### Post by jjguitars on 2010-12-04
htop gives me this



  1  [|||||||||||||||||||||||||||||                              43.9%]     Tasks: 263 total, 1 running
  2  [||||||||||||||||||||||||||||||||||||                       55.6%]     Load average: 0.87 0.78 0.80 
  3  [||||||||||||                                               16.9%]     Uptime: 01:28:09
  4  [|||||||||                                                  13.0%]
  Mem[||||||||||||||||||||||||||||||||||||||||||||||||      913/5983MB]
  Swp[                                                        0/2925MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 1487 root      20   0  148M 49284 17404 S 18.0  0.8 10:50.13 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-G7fpO5/database -nolisten tc
 1850 jeremy    20   0 58536  7348  2544 S  9.0  0.1  9:35.07 /usr/lib/libgconf2-4/gconfd-2
 1733 jeremy    20   0  230M  9792  6212 S  3.0  0.2  3:39.46 gnome-session
 1845 jeremy    20   0 25308  2064   620 S  3.0  0.0  3:36.00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 1932 jeremy    20   0  368M 63800 21520 S  3.0  1.0  3:44.58 compiz --replace
 3753 jeremy    20   0  366M 28760 12960 S  2.0  0.5  1:44.89 /usr/bin/python /usr/share/system-config-printer/applet.py
 1857 jeremy    20   0  378M 13748  9416 S  2.0  0.2  2:07.99 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
29852 jeremy    20   0  383M 16604 11620 S  1.0  0.3  0:19.73 gnome-terminal
26586 jeremy    20   0 19928  1680  1080 R  1.0  0.0  0:00.20 htop
 1877 jeremy    20   0  429M 26052 16244 S  1.0  0.4  1:09.42 gnome-panel --sm-config-prefix /gnome-panel-drvPgW/ --sm-client-id 10b239a00d24fa8f1b12
 1898 jeremy    20   0  728M 36804 22844 S  1.0  0.6  0:51.18 nautilus --sm-client-id 10b239a00d24fa8f1b125731814672913200000017170028 --sm-client-st
 1903 jeremy    20   0  660M 54184 25624 S  1.0  0.9  0:47.82 cairo-dock -c
27546 jeremy    20   0  156M  6748  5240 S  1.0  0.1  0:00.03 /usr/bin/metacity
 1915 jeremy    20   0 91880 39148 16508 S  0.0  0.6  1:05.20 skype -session 10bf5960f511834bb4126147406610665700000017070042_1264418496_601097
 1976 jeremy    20   0  350M 15860 12400 S  0.0  0.3  0:20.10 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory -
 2510 jeremy    20   0  851M 44924 13680 S  0.0  0.7  0:03.08 /opt/google/chrome/chrome --type=extension --lang=en-US --force-fieldtest=ConnCountImpa
 2473 jeremy    20   0  598M 64812 27248 S  0.0  1.1  0:00.11 /opt/google/chrome/google-chrome
    1 root      20   0 23884  2028  1292 S  0.0  0.0  0:00.89 /sbin/init
  431 root      20   0 17096   888   592 S  0.0  0.0  0:00.04 upstart-udev-bridge --daemon
  562 root      16  -4 17564  1348   344 S  0.0  0.0  0:00.04 udevd --daemon
  764 root      18  -2 17560  1228   252 S  0.0  0.0  0:00.00 udevd --daemon
 1111 syslog    20   0  123M  1940  1056 S  0.0  0.0  0:00.00 rsyslogd -c4
 1171 syslog    20   0  123M  1940  1056 S  0.0  0.0  0:00.00 rsyslogd -c4
 1172 syslog    20   0  123M  1940  1056 S  0.0  0.0  0:00.05 rsyslogd -c4
22396 syslog    20   0  123M  1940  1056 S  0.0  0.0  0:00.08 rsyslogd -c4
 1113 messageb  20   0 24380  1924   868 S  0.0  0.0  0:00.38 dbus-daemon --system --fork
 1139 root      20   0 88200  4384  3496 S  0.0  0.1  0:00.03 NetworkManager
 1158 root      20   0 88200  4384  3496 S  0.0  0.1  0:00.00 NetworkManager
 1141 root      20   0 60196  2628  2048 S  0.0  0.0  0:00.01 /usr/sbin/modem-manager
 1144 root      20   0 28400  1928  1556 S  0.0  0.0  0:00.00 /sbin/wpa_supplicant -u -s
 1145 root      20   0  6600  1108   936 S  0.0  0.0  0:00.00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclie
 1156 avahi     20   0 34108  1748  1436 S  0.0  0.0  0:00.01 avahi-daemon: running [jeremy-desktop.local]
 1157 avahi     20   0 33984   476   212 S  0.0  0.0  0:00.00 avahi-daemon: chroot helper
 1197 root      20   0  6128   624   520 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty4
 1205 nobody    20   0 12512   736   592 S  0.0  0.0  0:00.01 /usr/bin/gdomap -I /var/run/gdomap.pid -p
 1217 root      20   0  6128   628   524 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty5
 1235 root      20   0  6128   628   524 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty2
 1237 root      20   0  6128   632   524 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty3
 1241 root      20   0  6128   628   524 S  0.0  0.0  0:00.00 /sbin/getty -8 38400 tty6
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

---

### Post by TeoBigusGeekus on 2010-12-04
Is this immediately after boot or after an hour or so?

---

### Post by jjguitars on 2010-12-04
Htop was run immediately after boot. My first post with the details of freee -m was done after boot then after about an hour. Sorry for delay in responding, I am in Australia and went to bed.

---

### Post by TeoBigusGeekus on 2010-12-04
Post us the htop after an hour from booting as well.

---

### Post by jjguitars on 2010-12-04
Tried htop after 1hour, but computer is behaving at the moment. It is in use and is generally Ok. I will post another htop later, one immediately after boot and another 1 hr after inactivity.

---

