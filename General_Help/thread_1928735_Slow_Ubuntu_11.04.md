---
title: "Slow Ubuntu 11.04"
date: 2012-02-20
forum: General Help
---

### Post by Nism0.sdt on 2012-02-20
Hi there.
As first, I want to say, that I've been searched around the Internet for help but I can't get it. Anyway, my problem is very slow as for my machine (I think it should work nice on my hardware) Ubuntu 11.04. I was trying to change many apps to their equivalent eg I changed GNOME to LXDE (and it's pretty much faster than GNOME), pidgin to finch, rythmbox to audicious and a few others, but it's still slow. I'm not using Unity ofc, and I'm not using any graphic effects. My hardware box is :

756 MB RAM
AMD Durown 1,2Ghz (overclocked to 1,6 Ghz)
GF 5200FX

I was trying to turn off some apps working in background, but it doesn't work too. I think that RAM could be the problem , I mean 756 mb RAM is not to much (especially when running apps are using over 550 mb of RAM).
I'm using Google Chrome as the web browser and it's pretty heavy, but I don't want to change it because it's very usefull as for me, anyway I don't think that Chome could be the biggest problem in this case ;>

PS : Sorry for my English ;) 

Any hint will be helpfull.

---

### Post by Paddy Landau on 2012-02-21
If you have a slow computer with low RAM, Ubuntu will not run well.

The best thing for you is to back up your data; install [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"); and restore your data. Lubuntu will run nicely on your machine.

---

### Post by Nism0.sdt on 2012-02-22
Thanks for reply !
I've downloaded Lubuntu as you suggest and than ran it from LiveCD, but I still don't see big difference. When I ran Chromium, audicious I've got over 90% of CPU usage. I agree that Lubuntu is faster than Ubuntu but not much (in this case anyway).  I don't think that 756mb RAM is too less for Ubuntu with LXDE or even for Lubuntu as well. So, I think it might be CPU fault or other component ? I can't figure it out ...

Greetings Nism0.

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Thanks for reply !
I've downloaded Lubuntu as you suggest and than ran it from LiveCD, but I still don't see big difference. When I ran Chromium, audicious I've got over 90% of CPU usage. I agree that Lubuntu is faster than Ubuntu but not much (in this case anyway).  I don't think that 756mb RAM is too less for Ubuntu with LXDE or even for Lubuntu as well. So, I think it might be CPU fault or other component ? I can't figure it out ...

Greetings Nism0.

Once you gain more experience,
you might wanna think about using ubuntu server and just installing the gui components/tools you need.

Did it myself, avg. mem: 200mb; When firefox is on it goes up to 300mb but FF is just heavy.

---

### Post by Nism0.sdt on 2012-02-22
One thing is interesting for me. Why task manager shows 100% CPU usage, while when I'm looking at each task it takes less than a few %'s. What's wrong with it ? Near 300mb RAM usage is not too high too so why it's running so slow ? I've got Windows XP on another HDD on the same box, and it is running much faster than ubuntu/lubuntu.

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> One thing is interesting for me. Why task manager shows 100% CPU usage, while when I'm looking at each task it takes less than a few %'s. What's wrong with it ? Near 300mb RAM usage is not too high too so why it's running so slow ? I've got Windows XP on another HDD on the same box, and it is running much faster than ubuntu/lubuntu.
Try running
```

ps ax | grep "apt-xapian-index"

```
and give me the output.

---

### Post by Nism0.sdt on 2012-02-22
```

ubuntu@ubuntu:~$ ps ax | grep "apt-xapian-index"
 3514 pts/0    S+     0:00 grep --color=auto apt-xapian-index
ubuntu@ubuntu:~$ 

```

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> ```

ubuntu@ubuntu:~$ ps ax | grep "apt-xapian-index"
 3514 pts/0    S+     0:00 grep --color=auto apt-xapian-index
ubuntu@ubuntu:~$ 

```
Was the cpu still  100% when you ran that?

---

### Post by Nism0.sdt on 2012-02-22
I just found that Xorg takes about 80% of CPU. Why so many ? Is it really so heavy (to be honest - I don't think so ;> ).

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> I just found that Xorg takes about 80% of CPU. Why so many ? Is it really so heavy (to be honest - I don't think so ;> ).
Post the output of the following command (please between code tags):
```

sudo ps ax

```

---

### Post by Nism0.sdt on 2012-02-22
```


ubuntu@ubuntu:~$ sudo ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    6 ?        S      0:00 [migration/0]
    7 ?        S<     0:00 [cpuset]
    8 ?        S<     0:00 [khelper]
    9 ?        S<     0:00 [netns]
   10 ?        S      0:00 [sync_supers]
   11 ?        S      0:00 [bdi-default]
   12 ?        S<     0:00 [kintegrityd]
   13 ?        S<     0:00 [kblockd]
   14 ?        S<     0:00 [kacpid]
   15 ?        S<     0:00 [kacpi_notify]
   16 ?        S<     0:00 [kacpi_hotplug]
   17 ?        S<     0:00 [ata_sff]
   18 ?        S      0:00 [khubd]
   19 ?        S<     0:00 [md]
   22 ?        S      0:00 [khungtaskd]
   23 ?        S      0:00 [kswapd0]
   24 ?        SN     0:00 [ksmd]
   25 ?        S      0:00 [fsnotify_mark]
   26 ?        S<     0:00 [aio]
   27 ?        S      0:00 [ecryptfs-kthrea]
   28 ?        S<     0:00 [crypto]
   32 ?        S<     0:00 [kthrotld]
   34 ?        S      0:00 [scsi_eh_0]
   35 ?        S      0:00 [scsi_eh_1]
   38 ?        S<     0:00 [kmpathd]
   39 ?        S<     0:00 [kmpath_handlerd]
   40 ?        S<     0:00 [kondemand]
   41 ?        S<     0:00 [kconservative]
  211 ?        S<     0:00 [nouveau]
  214 ?        S<     0:00 [ttm_swap]
  445 ?        S<     0:01 [loop0]
 1236 ?        S      0:00 upstart-udev-bridge --daemon
 1247 ?        Sl     0:00 rsyslogd -c4
 1253 ?        Ss     0:01 dbus-daemon --system --fork --activation=upstart
 1275 ?        S<s    0:00 udevd --daemon
 1436 ?        Ssl    0:01 NetworkManager
 1448 ?        S      0:00 upstart-socket-bridge --daemon
 1488 ?        S      0:00 /usr/sbin/modem-manager
 1491 ?        Sl     0:00 /usr/lib/policykit-1/polkitd
 1635 ?        S      0:00 /sbin/wpa_supplicant -u -s
 1642 ?        Ss     0:00 lxdm-binary
 1645 ?        S<     0:00 [cfg80211]
 1652 tty4     Ss     0:00 /bin/login -f       
 1662 tty5     Ss     0:00 /bin/login -f       
 1683 tty2     Ss     0:00 /bin/login -f       
 1684 tty3     Ss     0:00 /bin/login -f       
 1687 tty6     Ss     0:00 /bin/login -f       
 1691 ?        Ss     0:00 cron
 1701 ?        Ss     0:00 atd
 1783 tty7     Rs+   39:17 /usr/bin/X :0 vt07 -nolisten tcp
 2062 tty4     S+     0:01 -bash
 2063 tty3     S+     0:01 -bash
 2064 tty5     S+     0:01 -bash
 2065 tty2     S+     0:01 -bash
 2066 tty6     S+     0:01 -bash
 2091 ?        S<     0:00 udevd --daemon
 2092 ?        S<     0:00 udevd --daemon
 2110 ?        S      0:08 [irq/16-0000:00:]
 2138 ?        Ss     0:00 /usr/sbin/cupsd -F
 2173 tty1     Ss     0:00 /bin/login -f       
 2240 tty1     S+     0:01 -bash
 2479 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
 2552 ?        Ss     0:00 /usr/bin/lxsession -s Lubuntu -e LXDE
 2911 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-
 2914 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/st
 2915 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-addre
 2923 ?        S      0:05 openbox --config-file /home/ubuntu/.config/openbox/l
 2925 ?        Sl     0:02 nm-applet
 2928 ?        S      0:45 lxpanel --profile Lubuntu
 2929 ?        R      0:12 xscreensaver -no-splash
 2930 ?        Sl     0:00 gnome-power-manager
 2931 ?        S      0:16 pcmanfm --desktop --profile lubuntu
 2932 ?        Sl     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authenticati
 2936 ?        Sl     0:00 update-notifier
 2941 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=p
 2945 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=s
 2946 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=s
 2955 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 2957 ?        S      0:00 /usr/lib/gvfs/gvfsd
 2959 ?        Sl     0:00 /usr/lib/upower/upowerd
 2961 ?        Sl     0:00 /usr/lib/udisks/udisks-daemon
 2965 ?        S      0:01 udisks-daemon: polling /dev/sr0
 2966 ?        S      0:00 /usr/lib/libmenu-cache1/libexec/menu-cached
 2972 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ubuntu/.gvfs
 3068 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 3071 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 3073 ?        Sl     0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
 3084 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-
 3161 ?        Ss     0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 103:108
 3173 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/g
 3221 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda8 /media/Media -o rw,nosuid
 3241 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda5 /media/Docs -o rw,nosuid,
 3284 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda7 /media/Instalki -o rw,nos
 3323 ?        SLl    4:17 audacious2
 3342 ?        R      6:12 lxtask
 3363 ?        Sl     1:01 /usr/lib/chromium-browser/chromium-browser
 3365 ?        S      0:00 /usr/lib/chromium-browser/chromium-browser
 3367 ?        S      0:00 /usr/lib/chromium-browser/chromium-browser --type=zy
 3410 ?        Sl     1:03 /usr/lib/chromium-browser/chromium-browser --type=re
 3435 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=gp
 3443 ?        S      0:14 [kworker/0:2]
 3455 ?        Rl     0:02 lxterminal
 3456 ?        S      0:00 gnome-pty-helper
 3457 pts/0    Ss     0:00 /bin/bash
 3567 ?        S      0:00 [kworker/u:2]
 3577 ?        S      0:00 [kworker/u:0]
 3581 ?        S      0:00 [kworker/0:1]
 3589 ?        S      0:00 [kworker/u:1]
 3590 ?        S      0:00 [kworker/0:0]
 3594 pts/0    S+     0:00 sudo ps ax
 3596 pts/0    R+     0:00 ps ax


```

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> ```


ubuntu@ubuntu:~$ sudo ps ax
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [kthreadd]
    3 ?        S      0:00 [ksoftirqd/0]
    6 ?        S      0:00 [migration/0]
    7 ?        S<     0:00 [cpuset]
    8 ?        S<     0:00 [khelper]
    9 ?        S<     0:00 [netns]
   10 ?        S      0:00 [sync_supers]
   11 ?        S      0:00 [bdi-default]
   12 ?        S<     0:00 [kintegrityd]
   13 ?        S<     0:00 [kblockd]
   14 ?        S<     0:00 [kacpid]
   15 ?        S<     0:00 [kacpi_notify]
   16 ?        S<     0:00 [kacpi_hotplug]
   17 ?        S<     0:00 [ata_sff]
   18 ?        S      0:00 [khubd]
   19 ?        S<     0:00 [md]
   22 ?        S      0:00 [khungtaskd]
   23 ?        S      0:00 [kswapd0]
   24 ?        SN     0:00 [ksmd]
   25 ?        S      0:00 [fsnotify_mark]
   26 ?        S<     0:00 [aio]
   27 ?        S      0:00 [ecryptfs-kthrea]
   28 ?        S<     0:00 [crypto]
   32 ?        S<     0:00 [kthrotld]
   34 ?        S      0:00 [scsi_eh_0]
   35 ?        S      0:00 [scsi_eh_1]
   38 ?        S<     0:00 [kmpathd]
   39 ?        S<     0:00 [kmpath_handlerd]
   40 ?        S<     0:00 [kondemand]
   41 ?        S<     0:00 [kconservative]
  211 ?        S<     0:00 [nouveau]
  214 ?        S<     0:00 [ttm_swap]
  445 ?        S<     0:01 [loop0]
 1236 ?        S      0:00 upstart-udev-bridge --daemon
 1247 ?        Sl     0:00 rsyslogd -c4
 1253 ?        Ss     0:01 dbus-daemon --system --fork --activation=upstart
 1275 ?        S<s    0:00 udevd --daemon
 1436 ?        Ssl    0:01 NetworkManager
 1448 ?        S      0:00 upstart-socket-bridge --daemon
 1488 ?        S      0:00 /usr/sbin/modem-manager
 1491 ?        Sl     0:00 /usr/lib/policykit-1/polkitd
 1635 ?        S      0:00 /sbin/wpa_supplicant -u -s
 1642 ?        Ss     0:00 lxdm-binary
 1645 ?        S<     0:00 [cfg80211]
 1652 tty4     Ss     0:00 /bin/login -f       
 1662 tty5     Ss     0:00 /bin/login -f       
 1683 tty2     Ss     0:00 /bin/login -f       
 1684 tty3     Ss     0:00 /bin/login -f       
 1687 tty6     Ss     0:00 /bin/login -f       
 1691 ?        Ss     0:00 cron
 1701 ?        Ss     0:00 atd
 1783 tty7     Rs+   39:17 /usr/bin/X :0 vt07 -nolisten tcp
 2062 tty4     S+     0:01 -bash
 2063 tty3     S+     0:01 -bash
 2064 tty5     S+     0:01 -bash
 2065 tty2     S+     0:01 -bash
 2066 tty6     S+     0:01 -bash
 2091 ?        S<     0:00 udevd --daemon
 2092 ?        S<     0:00 udevd --daemon
 2110 ?        S      0:08 [irq/16-0000:00:]
 2138 ?        Ss     0:00 /usr/sbin/cupsd -F
 2173 tty1     Ss     0:00 /bin/login -f       
 2240 tty1     S+     0:01 -bash
 2479 ?        Sl     0:00 /usr/sbin/console-kit-daemon --no-daemon
 2552 ?        Ss     0:00 /usr/bin/lxsession -s Lubuntu -e LXDE
 2911 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-
 2914 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/st
 2915 ?        Ss     0:00 //bin/dbus-daemon --fork --print-pid 5 --print-addre
 2923 ?        S      0:05 openbox --config-file /home/ubuntu/.config/openbox/l
 2925 ?        Sl     0:02 nm-applet
 2928 ?        S      0:45 lxpanel --profile Lubuntu
 2929 ?        R      0:12 xscreensaver -no-splash
 2930 ?        Sl     0:00 gnome-power-manager
 2931 ?        S      0:16 pcmanfm --desktop --profile lubuntu
 2932 ?        Sl     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authenticati
 2936 ?        Sl     0:00 update-notifier
 2941 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=p
 2945 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=s
 2946 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --start --components=s
 2955 ?        S      0:00 /usr/lib/libgconf2-4/gconfd-2
 2957 ?        S      0:00 /usr/lib/gvfs/gvfsd
 2959 ?        Sl     0:00 /usr/lib/upower/upowerd
 2961 ?        Sl     0:00 /usr/lib/udisks/udisks-daemon
 2965 ?        S      0:01 udisks-daemon: polling /dev/sr0
 2966 ?        S      0:00 /usr/lib/libmenu-cache1/libexec/menu-cached
 2972 ?        Ssl    0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ubuntu/.gvfs
 3068 ?        S      0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
 3071 ?        S      0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 3073 ?        Sl     0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
 3084 ?        S      0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-
 3161 ?        Ss     0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 103:108
 3173 ?        S      0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.11 /org/gtk/g
 3221 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda8 /media/Media -o rw,nosuid
 3241 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda5 /media/Docs -o rw,nosuid,
 3284 ?        Ss     0:00 /sbin/mount.ntfs /dev/sda7 /media/Instalki -o rw,nos
 3323 ?        SLl    4:17 audacious2
 3342 ?        R      6:12 lxtask
 3363 ?        Sl     1:01 /usr/lib/chromium-browser/chromium-browser
 3365 ?        S      0:00 /usr/lib/chromium-browser/chromium-browser
 3367 ?        S      0:00 /usr/lib/chromium-browser/chromium-browser --type=zy
 3410 ?        Sl     1:03 /usr/lib/chromium-browser/chromium-browser --type=re
 3435 ?        Sl     0:00 /usr/lib/chromium-browser/chromium-browser --type=gp
 3443 ?        S      0:14 [kworker/0:2]
 3455 ?        Rl     0:02 lxterminal
 3456 ?        S      0:00 gnome-pty-helper
 3457 pts/0    Ss     0:00 /bin/bash
 3567 ?        S      0:00 [kworker/u:2]
 3577 ?        S      0:00 [kworker/u:0]
 3581 ?        S      0:00 [kworker/0:1]
 3589 ?        S      0:00 [kworker/u:1]
 3590 ?        S      0:00 [kworker/0:0]
 3594 pts/0    S+     0:00 sudo ps ax
 3596 pts/0    R+     0:00 ps ax


```

Try killing chromium (browser); seems to be hogging cpu, heavy loading Xorg as a result.

---

### Post by Paddy Landau on 2012-02-22
> **Nism0.sdt said:**
> I've downloaded Lubuntu as you suggest and than ran it from LiveCD...
It will run slower from CD than from a proper installation.

However, you do have an older computer. Lubuntu is the lightest of the Ubuntu family.

If you are interested in looking at something even lighter, consider moving away from the Ubuntu family, such as [Bodhi]("http://www.bodhilinux.com/"), [Crunchbang]("http://crunchbanglinux.org/"), or even [Puppy]("http://puppylinux.org/") (extremely light and basic).

---

### Post by Nism0.sdt on 2012-02-22
> **Paddy Landau said:**
> It will run slower from CD than from a proper installation.

However, you do have an older computer. Lubuntu is the lightest of the Ubuntu family.

If you are interested in looking at something even lighter, consider moving away from the Ubuntu family, such as [Bodhi]("http://www.bodhilinux.com/"), [Crunchbang]("http://crunchbanglinux.org/"), or even [Puppy]("http://puppylinux.org/") (extremely light and basic).

I think that previous versions of Ubuntu eg 9.04 Jaunty Jackalope (my first ubuntu) was working nicely. It's quite strange that Xorg "eats" about 90% of CPU . I don't want to change distro because I'm using Ubuntu over 2 years. I used also Debian, Slackware and Backtrack, but Ubuntu was best for me.
So, what's wrong with this Xorg ?

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> I think that previous versions of Ubuntu eg 9.04 Jaunty Jackalope (my first ubuntu) was working nicely. It's quite strange that Xorg "eats" about 90% of CPU . I don't want to change distro because I'm using Ubuntu over 2 years. I used also Debian, Slackware and Backtrack, but Ubuntu was best for me.
So, what's wrong with this Xorg ?
I'd guess some program is heavily using graphics, this causes loads of work for Xorg.

---

### Post by Nism0.sdt on 2012-02-22
I think it might be google chrome, but even it's true, how can I solve this problem ? I think that might be graphic driver fault. I use Nvidia drivers, but in drivers centrum I see notification like this : 
```

This driver is enabled, but it isn't in use 

```

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> I think it might be google chrome, but even it's true, how can I solve this problem ? I think that might be graphic driver fault. I use Nvidia drivers, but in drivers centrum I see notification like this : 
```

This driver is enabled, but it isn't in use 

```
Give us the output of:
```

sudo lshw -C display

```
Note: Command takes time, appears hung but is just scanning.

---

### Post by Nism0.sdt on 2012-02-22
Out of curiosity - what is this command do exacly ?

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Out of curiosity - what do this command exacly ?
lshw lists hardware (needs to run under sudo).
sudo lshw -C display tells us about your display hardware (GFX-card).

---

### Post by Nism0.sdt on 2012-02-22
```


nism0@satellite:~$ sudo lshw -C display
[sudo] password for nism0: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:e0000000-e0ffffff memory:d8000000-dfffffff memory:e1000000-e101ffff
nism0@satellite:~$ 

```

I did this from my ubuntu natty narwhal not form Lubuntu LiveCD .

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> ```


nism0@satellite:~$ sudo lshw -C display
[sudo] password for nism0: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:e0000000-e0ffffff memory:d8000000-dfffffff memory:e1000000-e101ffff
nism0@satellite:~$ 

```I did this from my ubuntu natty narwhal not form Lubuntu LiveCD .
Installed nvidia-current?

---

### Post by Nism0.sdt on 2012-02-22
I don't know is that Nvidia current honestly. I can only say that it is Nvidia v173 hardware accelerated tested by ubuntu recommended.

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> I don't know is that Nvidia current honestly. I can only say that it is Nvidia v173 hardware accelerated tested by ubuntu recommended.
Try:
```

sudo apt-get install nvidia-current

```

---

### Post by Nism0.sdt on 2012-02-22
Ok, it's installing. I guess I should turn off actual driver.

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Ok, it's installing. I guess I should turn off actual driver.
no, the installer will do that

---

### Post by Nism0.sdt on 2012-02-22
Better for me than ;)

// Edit

Ok, it's installed. What now ? Is it solve the problem ?

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Better for me than ;)
yup

---

### Post by Nism0.sdt on 2012-02-22
Anyway what I should do next ? Is it solve the problem ?

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Anyway what I should do next ? Is it solve the problem ?
Do you still get the notice?
If so, you can probably ignore it (what's wrong with an extra driver?)
If not, SOLVED.

---

### Post by Nism0.sdt on 2012-02-22
Huh, it doesnt even start now (ubuntu). It's failing while booting...

I sent this msg from my smartphone

---

### Post by roelforg on 2012-02-22
> **Nism0.sdt said:**
> Huh, it doesnt even start now (ubuntu). It's failing while booting...

I sent this msg from my smartphone
Shall we create a new thread for that?
I don't wanna derail this one even more.

---

### Post by Nism0.sdt on 2012-02-22
I dont thnk so cause the problem with nvidia driver is solved, i just ran it in recovery mode and restart xserver. Anyway, ubuntu is still slow...

---

### Post by Nism0.sdt on 2012-02-23
Issue with the nvidia driver isn't solve anyway, so I decided to backup my files and install Lubuntu. We'll see what next.
Topic is "solved" (not exactly but I think we can mark it as solved ).

Thanks everyone for help ;)

---

### Post by Paddy Landau on 2012-02-23
> **Nism0.sdt said:**
> ... I decided to backup my files and install Lubuntu.Let us know if it does what you need.

> **Nism0.sdt said:**
> Topic is "solved" (not exactly but I think we can mark it as solved ).In case you don't know: [How to mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

