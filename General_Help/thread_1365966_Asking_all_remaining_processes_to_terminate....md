---
title: "Asking all remaining processes to terminate..."
date: 2009-12-27
forum: General Help
---

### Post by drdanielfc on 2009-12-27
Hello,
  I installed this ubuntu system several weeks ago and all has worked fine until now. The problem is that on shutdown the system hangs on "Asking all remaining processes to terminate...". The problem is NOT the same as others i have seen as mine figures itself out after about 2 minutes. It is more of an annoyance than anything. I have no idea what could have caused it had been a while since the last restart. Here are the messages that show up:

```
*Stopping ipmi drivers.
 ...done.
*unloading kvm module kvm_intel
*stopping the winbind daemon winbind
*Shutting down ALSA...
*Asking all remaining processes to terminate...
```
*SYSTEM HANGS HERE*
*This flashes for several seconds, I needed to take a picture:*
```
*Deconfiguring network interfaces...
*Deactivating swap...
*Will now halt
```

Not sure if this will help but here are the running processes before shutdown:
```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 netns
   14 ?        00:00:00 async/mgr
   15 ?        00:00:00 kintegrityd/0
   16 ?        00:00:00 kintegrityd/1
   17 ?        00:00:00 kblockd/0
   18 ?        00:00:00 kblockd/1
   19 ?        00:00:00 kacpid
   20 ?        00:00:00 kacpi_notify
   21 ?        00:00:00 kacpi_hotplug
   22 ?        00:00:00 ata/0
   23 ?        00:00:00 ata/1
   24 ?        00:00:00 ata_aux
   25 ?        00:00:00 ksuspend_usbd
   26 ?        00:00:00 khubd
   27 ?        00:00:00 kseriod
   28 ?        00:00:00 kmmcd
   29 ?        00:00:00 bluetooth
   30 ?        00:00:00 khungtaskd
   31 ?        00:00:00 pdflush
   32 ?        00:00:00 pdflush
   33 ?        00:00:00 kswapd0
   34 ?        00:00:00 aio/0
   35 ?        00:00:00 aio/1
   36 ?        00:00:00 ecryptfs-kthrea
   37 ?        00:00:00 crypto/0
   38 ?        00:00:00 crypto/1
   42 ?        00:00:00 scsi_eh_0
   43 ?        00:00:00 scsi_eh_1
   44 ?        00:00:00 scsi_eh_2
   45 ?        00:00:00 scsi_eh_3
   47 ?        00:00:00 scsi_eh_4
   49 ?        00:00:00 scsi_eh_5
   53 ?        00:00:00 kstriped
   54 ?        00:00:00 kmpathd/0
   55 ?        00:00:00 kmpathd/1
   56 ?        00:00:00 kmpath_handlerd
   57 ?        00:00:00 ksnapd
   58 ?        00:00:00 kondemand/0
   59 ?        00:00:00 kondemand/1
   60 ?        00:00:00 kconservative/0
   61 ?        00:00:00 kconservative/1
   62 ?        00:00:00 krfcommd
  355 ?        00:00:00 khpsbpkt
  356 ?        00:00:00 scsi_eh_6
  357 ?        00:00:00 usb-storage
  367 ?        00:00:00 knodemgrd_0
  468 ?        00:00:00 kjournald2
  528 ?        00:00:00 upstart-udev-br
  531 ?        00:00:00 udevd
  812 ?        00:00:00 tifm
  833 ?        00:00:00 kpsmoused
  906 ?        00:00:00 iwl3945
  907 ?        00:00:00 phy0
  935 ?        00:00:00 pccardd
  994 ?        00:00:00 dd
  995 ?        00:00:00 hd-audio0
  996 ?        00:00:00 dbus-daemon
  999 ?        00:00:00 rsyslogd
 1015 ?        00:00:00 cifsoplockd
 1023 ?        00:00:00 avahi-daemon
 1024 ?        00:00:00 avahi-daemon
 1029 ?        00:00:00 NetworkManager
 1033 ?        00:00:00 hald
 1037 ?        00:00:00 modem-manager
 1045 ?        00:00:00 console-kit-dae
 1116 ?        00:00:00 hald-runner
 1232 ?        00:00:00 udevd
 1248 ?        00:00:00 udevd
 1295 ?        00:00:00 hald-addon-rfki
 1297 ?        00:00:00 wpa_supplicant
 1319 ?        00:00:00 hald-addon-gene
 1326 ?        00:00:00 hald-addon-leds
 1350 ?        00:00:00 hald-addon-inpu
 1368 ?        00:00:00 hald-addon-stor
 1369 ?        00:00:00 hald-addon-cpuf
 1370 ?        00:00:00 hald-addon-acpi
 1373 tty4     00:00:00 getty
 1375 tty5     00:00:00 getty
 1380 tty2     00:00:00 getty
 1381 tty3     00:00:00 getty
 1383 tty6     00:00:00 getty
 1387 ?        00:00:00 acpid
 1444 ?        00:00:00 cron
 1445 ?        00:00:00 atd
 1454 ?        00:00:00 nmbd
 1458 ?        00:00:00 smbd
 1459 ?        00:00:00 smbd
 1497 ?        00:00:00 winbindd
 1498 ?        00:00:00 winbindd
 1535 ?        00:00:00 bluetoothd
 1569 ?        00:00:00 cupsd
 1811 tty1     00:00:00 getty
 1848 ?        00:00:00 gdm-binary
 1855 ?        00:00:00 gdm-simple-slav
 1856 tty7     00:00:13 Xorg
 1895 ?        00:00:00 dbus-launch
 1900 ?        00:00:00 devkit-power-da
 1955 ?        00:00:00 gdm-session-wor
 1985 ?        00:00:00 gnome-keyring-d
 2000 ?        00:00:00 gnome-session
 2040 ?        00:00:00 ssh-agent
 2043 ?        00:00:00 dbus-launch
 2044 ?        00:00:00 dbus-daemon
 2048 ?        00:00:00 pulseaudio
 2054 ?        00:00:00 gconf-helper
 2056 ?        00:00:00 gconfd-2
 2063 ?        00:00:00 seahorse-daemon
 2067 ?        00:00:00 gnome-settings-
 2070 ?        00:00:00 gvfsd
 2076 ?        00:00:00 gvfs-fuse-daemo
 2104 ?        00:00:00 notify-osd
 2105 ?        00:00:00 compiz
 2141 ?        00:00:00 syndaemon
 2175 ?        00:00:02 compiz.real
 2176 ?        00:00:02 gnome-panel
 2177 ?        00:00:01 nautilus
 2179 ?        00:00:00 bonobo-activati
 2186 ?        00:00:05 skype
 2187 ?        00:00:00 emerald
 2191 ?        00:00:00 nm-applet
 2195 ?        00:00:00 bluetooth-apple
 2198 ?        00:00:00 update-notifier
 2202 ?        00:00:00 geyes_applet2
 2204 ?        00:00:00 gdu-notificatio
 2205 ?        00:00:00 evolution-alarm
 2207 ?        00:00:00 gnome-volume-co
 2208 ?        00:00:00 gnome-power-man
 2209 ?        00:00:00 polkit-gnome-au
 2215 ?        00:00:00 devkit-disks-da
 2216 ?        00:00:00 devkit-disks-da
 2217 ?        00:00:00 gnome-screensav
 2235 ?        00:00:00 polkitd
 2252 ?        00:00:00 gvfsd-trash
 2254 ?        00:00:00 indicator-apple
 2258 ?        00:00:00 indicator-messa
 2260 ?        00:00:00 gvfs-gdu-volume
 2263 ?        00:00:00 gvfs-gphoto2-vo
 2284 ?        00:00:00 gvfsd-burn
 2289 ?        00:00:00 gvfsd-metadata
 2298 ?        00:00:00 mount.ntfs
 2310 ?        00:00:00 dhclient
 2381 ?        00:00:00 cifsd
 2382 ?        00:00:00 cifsd
 2394 ?        00:00:12 chrome
 2397 ?        00:00:00 chrome
 2399 ?        00:00:00 chrome
 2410 ?        00:00:03 chrome
 2456 ?        00:00:00 evolution-data-
 2460 ?        00:00:00 evolution-excha
 2488 ?        00:00:00 aptd
 2495 ?        00:00:02 chrome
 2503 ?        00:00:07 gnome-system-mo
 2507 ?        00:00:02 chrome
 2516 ?        00:00:00 exe
 2524 ?        00:00:00 gnome-terminal
 2525 ?        00:00:00 gnome-pty-helpe
 2526 pts/0    00:00:00 bash
 2545 pts/0    00:00:00 ps
```

Thanks ahead of time,
~Dan

---

### Post by QrK0 on 2009-12-28
Sorry, but I don't understand where the system hags. Which line is the last you see?
*Asking all remaining processes to terminate...
or
*Will now halt
??

---

### Post by drdanielfc on 2009-12-28
The system hangs on "Asking all remaining processes to terminate..." for about 2 minutes and then the other messages flash for a quick second and the system shuts down. I know this doesn't seem like a big deal but it is very annoying and is almost painful to watch this screen.

---

### Post by Fandi Kurnia on 2009-12-28
[SIZE=3][SIZE=2]I got same issue. When I update upstart 6.11 all my process not running well, then I downgrade upstart 6.10, and the night mare is coming.

when I try to start ubuntu with gnome. it is will look like fine. but on 2 minutes, GUI is crash, and I get statement[/SIZE][/SIZE] :
..
..
..
[SIZE=2]Asking All remaining processes to terminate

[/SIZE]

---

### Post by john newbuntu on 2009-12-28
Next time you shutdown your computer, run this and see if that hangs.
sudo /etc/init.d/networking stop
Then shut it down to see if it is any faster.

---

### Post by drdanielfc on 2009-12-28
Thanks for the quick reply!

I performed the command and recieved:
```
* not deconfiguring network interfaces: network file systems still mounted.
```

On a hunch I tried:
```
sudo smbumount /mnt/Music
sudo smbumount /mnt/UkieMusic
```

And the restart worked fine!
Is there any way I could automate this on shutdown? I'm not very good with scripts and would like some help setting one up for the shutdown routine

Edit:
Oh sorry forgot to include that on startup I have those 2 samba shares being mounted automatically

---

### Post by QrK0 on 2009-12-28
Maybe you need to umount the samba shares before shutdown the computer. Maybe you have a music player program (amarok, banshee...) that have a file (mp3?) or playlist openened, causing the shutdown sequence to wait for something.

---

### Post by john newbuntu on 2009-12-28
If it has to do with samba, look at: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) and search for:
**CIFS VFS: Server not responding**

---

### Post by drdanielfc on 2009-12-29
> **john newbuntu said:**
> If it has to do with samba, look at: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) and search for:
**CIFS VFS: Server not responding**

The problem is definatly with the samba shares needing to be unmounted. If I issue the commands:

```
sudo smbumount /mnt/Music
sudo smbumount /mnt/UkieMusic
```

All works fine. However I cannot seem to figure out how to get these setup with a shutdown/restart script. Can someone please guide me through the process? The tutorials I find online I cannot figure out (sorry but I could never figure out the sh scripts for some reason)

---

### Post by QrK0 on 2009-12-29
> **drdanielfc said:**
> The problem is definatly with the samba shares needing to be unmounted. If I issue the commands:

```
sudo smbumount /mnt/Music
sudo smbumount /mnt/UkieMusic
```

All works fine. However I cannot seem to figure out how to get these setup with a shutdown/restart script. Can someone please guide me through the process? The tutorials I find online I cannot figure out (sorry but I could never figure out the sh scripts for some reason)

Just a question, when you umount manually the smb shares, does it take some time to umount, or it is inmediately?

---

### Post by drdanielfc on 2009-12-29
> **QrK0 said:**
> Just a question, when you umount manually the smb shares, does it take some time to umount, or it is inmediately?

Immediate - it takes longer to copy and paste then actually perform the command

---

