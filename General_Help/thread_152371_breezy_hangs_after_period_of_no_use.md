---
title: "breezy hangs after period of no use"
date: 2006-03-29
forum: General Help
---

### Post by telepathetic on 2006-03-29
Breezy is amazing!  until i leave it alone for the night and come back in the morning-- then it is either completely locked up or incredibly slow to the point that i can tell if anything is happening.   Mouse still works, but clicking on anything is useless.

any ideas?  could this be an acpi apm issue?  i'm admittedly clueless.

thanks for any help!
-telepathetic

---

### Post by ispmarin on 2006-03-29
Once I got a similar problem with a debian install... my /var/log was filled with some crazy logs (avg antivirus), and then the computer was terribly slow... can you post some ps -ef and a top to see if there is any process hanged up or consuming CPU time?

---

### Post by telepathetic on 2006-03-30
so I switched to Dapper thinking it might solve the problem, but still the same problem.  Works really well until i leave it alone overnight, then it will hang something awful-- too awful for me to get a ps -ef in there.  But now after a reboot here's my ps -ef:
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 11:59 ?        00:00:01 init [2]
root         2     1  0 11:59 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 11:59 ?        00:00:00 [watchdog/0]
root         4     1  0 11:59 ?        00:00:00 [events/0]
root         5     1  0 11:59 ?        00:00:00 [khelper]
root         6     1  0 11:59 ?        00:00:00 [kthread]
root         8     6  0 11:59 ?        00:00:00 [kblockd/0]
root         9     6  0 11:59 ?        00:00:00 [kacpid]
root       105     6  0 11:59 ?        00:00:00 [pdflush]
root       106     6  0 11:59 ?        00:00:00 [pdflush]
root       108     6  0 11:59 ?        00:00:00 [aio/0]
root       107     1  0 11:59 ?        00:00:00 [kswapd0]
root       695     6  0 11:59 ?        00:00:00 [kseriod]
root      1796     6  0 11:59 ?        00:00:00 [khubd]
root      1903     1  0 12:00 ?        00:00:00 [kjournald]
root      2124     1  0 12:00 ?        00:00:00 /sbin/udevd --daemon
root      2945     1  0 12:00 ?        00:00:00 [shpchpd_event]
root      3814     1  0 12:00 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acsyslog    3907     1  0 12:00 ?        00:00:00 /sbin/syslogd -u syslog
root      3933     1  0 12:00 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      3935     1  0 12:00 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
105       3954     1  0 12:00 ?        00:00:00 /usr/bin/dbus-daemon --system
114       3969     1  1 12:00 ?        00:00:01 /usr/sbin/hald
root      3970  3969  0 12:00 ?        00:00:00 hald-runner
114       3975  3970  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
114       4025  3970  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
114       4033  3970  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-storage
114       4034  3970  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-storage
root      4291     1  0 12:00 ?        00:00:00 /usr/sbin/gdm
root      4298  4291  0 12:00 ?        00:00:00 /usr/sbin/gdm
root      4303  4298  5 12:00 tty7     00:00:06 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xcupsys    4344     1  0 12:00 ?        00:00:00 /usr/sbin/cupsd
hplip     4363     1  0 12:00 ?        00:00:00 /usr/sbin/hpiod
hplip     4366     1  0 12:00 ?        00:00:00 python /usr/sbin/hpssd
root      4429     1  0 12:00 ?        00:00:00 /usr/sbin/thinkpad-keys
114       4441  3970  0 12:00 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
root      4677     1  0 12:00 ?        00:00:00 hcid: processing events
root      4683     1  0 12:00 ?        00:00:00 /usr/sbin/sdpd
root      4692     1  0 12:00 ?        00:00:00 [krfcommd]
root      4705     1  0 12:00 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -sdaemon    4739     1  0 12:00 ?        00:00:00 /usr/sbin/atd
root      4752     1  0 12:00 ?        00:00:00 /usr/sbin/cron
root      4827     1  0 12:00 tty1     00:00:00 /sbin/getty 38400 tty1
root      4828     1  0 12:00 tty2     00:00:00 /sbin/getty 38400 tty2
root      4829     1  0 12:00 tty3     00:00:00 /sbin/getty 38400 tty3
root      4830     1  0 12:00 tty4     00:00:00 /sbin/getty 38400 tty4
root      4831     1  0 12:00 tty5     00:00:00 /sbin/getty 38400 tty5
root      4832     1  0 12:00 tty6     00:00:00 /sbin/getty 38400 tty6
mrspeck   4849  4298  0 12:00 ?        00:00:00 x-session-manager
mrspeck   4891  4849  0 12:00 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-witmrspeck   4894     1  0 12:00 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session x-sessionmrspeck   4895     1  0 12:00 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6mrspeck   4897     1  0 12:00 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
mrspeck   4900     1  0 12:00 ?        00:00:00 /usr/bin/gnome-keyring-daemon
mrspeck   4902     1  0 12:00 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-servemrspeck   4904     1  1 12:00 ?        00:00:00 /usr/lib/control-center/gnome-settings-daemon --oamrspeck   4906     1  0 12:00 ?        00:00:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18mrspeck   4918     1  1 12:00 ?        00:00:01 /usr/bin/metacity --sm-client-id=default0
mrspeck   4923     1  1 12:00 ?        00:00:01 gnome-panel --sm-client-id default1
mrspeck   4925     1  1 12:00 ?        00:00:01 nautilus --no-default-window --sm-client-id defaulmrspeck   4929     1  0 12:00 ?        00:00:00 update-notifier --sm-client-id default5
mrspeck   4935     1  0 12:00 ?        00:00:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iimrspeck   4938     1  0 12:00 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-actimrspeck   4939     1  0 12:00 ?        00:00:00 gnome-volume-manager --sm-disable
mrspeck   4943     1  0 12:00 ?        00:00:00 gnome-cups-icon --sm-client-id default3
mrspeck   4948     1  0 12:00 ?        00:00:00 gnome-power-manager
mrspeck   4956     1  0 12:00 ?        00:00:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-mrspeck   4960     1  0 12:00 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapping-daemon
mrspeck   4966     1  0 12:01 ?        00:00:00 /usr/lib/gnome-panel/notification-area-applet --oamrspeck   4968     1  1 12:01 ?        00:00:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activatmrspeck   4971     1  0 12:01 ?        00:00:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-imrspeck   4976     1  4 12:01 ?        00:00:02 /usr/lib/firefox/firefox-bin -a firefox
mrspeck   4995     1  0 12:01 ?        00:00:00 gnome-screensaver
mrspeck   5002     1  5 12:01 ?        00:00:02 gnome-terminal
mrspeck   5003  5002  0 12:01 ?        00:00:00 gnome-pty-helper
mrspeck   5004  5002  0 12:01 pts/0    00:00:00 bash
mrspeck   5028  5004  0 12:02 pts/0    00:00:00 ps -ef



and here's my top:
4976 mrspeck   16   0 98908  34m  17m S  4.0  5.6   0:31.90 firefox-bin
4303 root      15   0  152m  16m 6612 S  3.3  2.6   0:22.89 Xorg
5002 mrspeck   15   0 32088  13m 8688 S  2.0  2.1   0:04.58 gnome-terminal
4918 mrspeck   15   0 14800 8988 6412 S  0.3  1.4   0:01.79 metacity
5132 mrspeck   16   0  2196 1092  856 R  0.3  0.2   0:00.02 top
    1 root      16   0  1564  524  460 S  0.0  0.1   0:01.39 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  105 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  106 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  108 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  107 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0


any ideas?
also-- in case it's useful-- this is happening after a fresh default install of breezy and upgrade to dapper.  I've added no extra packages yet, just upgraded all existing.  

thanks so much for the help!
-telepathetic

---

### Post by ispmarin on 2006-03-30
It is a thinkpad laptop? Try do desabilitate the gnome-power-manager (one thing that I can imagine that can hangs your computer) and sees if it helps. Also, try, when it freezes, to switch to a terminal (with a CRTL+ALT+F1) and sees if it works. If works, then try to get a top and a ps -ef...  or try to kill the X (CRTL+ALT+BACKSPACE on the X, then /etc/init.d/gdm stop)
and sees if from a terminal "startx" works. 
Hope it helps!

---

### Post by telepathetic on 2006-04-01
So its happened a few more times, and I managed to get to tty1 and type top.  There it shows that the cpus are all at 0.0%  (which doesn't make sense to me-- i thought they should all add to 100% since idle is included in there?).  Also when i sort by cpu usage or mem usage there is nothing above 1-3%, and everything looks normal just as it was before things started hanging.  And I do see top updating, so i don't think it just happens to be in some frozen state.  So I don't know what is going on.  I wish i could cut and paste it all, and it's too much of a pain to try to duplicate switching back and forth on the kvm.

One thing i noticed is that during normal operation it says there are 2 users in the top display.  NOw it's saying there are 4.  Could this be a clue?  Looks like the current users listed are: syslogd, (myusername), root, haldeamo, cupsys (guess it doesn't count root as a user?).  Looks like the users right after i restart up are just: (myusername), root, haldeamo.
](*,) 

any ideas??
thanks so much for the help!!

---

### Post by ispmarin on 2006-04-03
Well, I ran out of ideas... usually is some hardware conflict, or some daemon that starts and don't like your kernel (or you computer... :mrgreen: ) but really don't know what to say. 
Did you try to desabilitate the apm, acpi and every power manager? Even from bios? 
Can you post the output of a lspci -v? Just in case to see if some hardware is conflicting with one another, or maybe some lost interruption...

---

### Post by telepathetic on 2006-04-03
I've found someone else who also feels my pain!!
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35993/+index](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35993/+index)

I turned off the apm in bios and changed the acpi from S3 to S1 (there is no way to turn it off-- only options are the irq (9,10, or 11) and the type (s1 or s3).
Still same problem.

I've turned off the power management by going to Preferences->Power Management, and setting the computer and monitor to sleep "Never".  Still same problem.

Is there anything else I can do in the os to further turn off the acpi? or apm?  I'm not sure what else to try?

i'll paste in the lspci -v on the next post.

---

### Post by telepathetic on 2006-04-03
:~$ lspci -v

0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Co ntroller/Host-Hub Interface (rev 01)
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G] /GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
        Subsystem: IBM NetVista A30p
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at 88000000 (32-bit, prefetchable) [size=128M]
        Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at 1840 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 201
        Memory at c0080000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00  [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c0100000-c01fffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interfa ce Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev  01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1860 [size=16]
        Memory at 30000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 01)
        Subsystem: IBM NetVista A30p
        Flags: medium devsel, IRQ 9
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 0, IRQ 209
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0080c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0080800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Eth ernet Controller (rev 81)
        Subsystem: IBM NetVista A30p
        Flags: bus master, medium devsel, latency 66, IRQ 217
        Memory at c0100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 2000 [size=64]
        Capabilities: <available only to root>

---

### Post by telepathetic on 2006-04-03
finally found others here with my exact problems! 
[http://ubuntuforums.org/showthread.php?t=47330&highlight=netvista](http://ubuntuforums.org/showthread.php?t=47330&highlight=netvista)

i'll try all that and report back.

---

### Post by Clopy on 2006-04-03
also, turn off the screensaver. You never know...

---

### Post by telepathetic on 2006-04-04
reinstalling with noapic and nolapic flags did the trick!  no more hanging!  not sure what the implications here are, but at least it works now with no more hanging!

:-D

---

