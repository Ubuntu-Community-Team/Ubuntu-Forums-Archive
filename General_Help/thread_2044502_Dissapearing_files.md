---
title: "Dissapearing files"
date: 2012-08-19
forum: General Help
---

### Post by migrena6 on 2012-08-19
Hello. 

I want to be sure, that my problem is caused by failing HDD and there cannot be other cause for that.

Technical information:
Xubuntu 12.04, HP Compaq NX8220, 40 GB HDD Fujitsu MHT 2040AH.

Problem:
I have noticed of disapearing of my files only from my home directory, I think. Only some of the files in subdirectories disappeared, not all of them. It seems that they are disappearing randomly after reboot and turn on from sleep mode. 

There were also some damaged icons ("Downloads","Trash") in Thunar in side panel (actually not only bookmarks, but directories itself)- white icon with "x". Both of the directories were restored, but bookmark was restored only for trash. 

My music collection (about 700 songs) is not affected yet. That is a little strange, I think.

I need to know if there is other possibility  that is causing that problem.

Thanks for any responds.

---

### Post by black veils on 2012-08-19
i cannot answer that, but, you can do a hdd scan:

1.  open **disk utility**

2.  choose your hdd device from the left pane

3.  in the right pane, at the top-right, where it says **SMART status**, what is the status?

4.  below **SMART status**, select [B]SMART data

[/B]5.  select [B]run self-tests



[/B]

---

### Post by migrena6 on 2012-08-19
Hi and thanks. 

3. Green light- disk has a few bad sectors.
4.  Selftest: ID 5- Number of reallocated sectors. Value: 131 076. The other fields has green or gray lights. 

I also tested my disk using utility from Fujitsu, running comprehensive test with "passed".
I also used application Viva for surface testing. No bad sectors were found.

---

### Post by migrena6 on 2012-08-21
So, I will try to ask by another way.

Is there any chance, that it is caused by software?

I have had suspicion about disappearing files on Mint 13 XFCE too (which was installed before Xubuntu). But I tried many distributions before and none of them had such problem.

An another question. Is there any way to monitor of disappearing files?

Thanks.

---

### Post by dino99 on 2012-08-21
which are those files ? are they system files (and which ones) or your personal files ?

you does not need to care, for example, of:
- tmp files
- files created by suspend/hibernation mode

---

### Post by migrena6 on 2012-08-21
Some PDF documents (/home/michal/Documents in different directories)and probably movie (/home/michal/Video).

---

### Post by matt_symes on 2012-08-21
Hi

You are using extX ?

Have you ran a filing system check in using the -N switch. 

> 
-N     Don't execute, just show what would be done.To see if there are problems, run fsck from a LiveCD or recovery console with / (root) mounted read only.

If fsck is run from a LiveCD, just ensure the root partition is not mounted.

If you choose the recovery console to run fsck instead: to mount root read only from the recovery console, you can edit the grub command line and add  ```
ro
``` The newest version of Ubuntu will mount root read only from the recovery console by default.

Then open a terminal and type...

```
sudo fsck -N /dev/sdXY
```where sdXY is the root partition. If it shows corruption then run it without the -N switch top attempt to fix the errors.

It is possible you have filing system corruption and the above will attempt to fix it is that is the problem.

It is also possible the filling system is not being sycned and unmounted correctly at shutdown. Have you checked this possibility ?

---

### Post by migrena6 on 2012-08-21
Hi.
I am running Kubuntu 12.04 Live CD (do not have Xubuntu CD) at the moment.
Root partition is /dev/sda1. The HDD is separated on sda1 and swap.

After running the command:

```
kubuntu@kubuntu:~$ sudo fsck -N /dev/sda1
```

Output:
```
fsck from util-linux 2.20.1
[/sbin/fsck.ext4 (1) -- /dev/sda1] fsck.ext4 /dev/sda1 
```

> It is also possible the filling system is not being sycned and unmounted correctly at shutdown.
How can I check this?

---

### Post by matt_symes on 2012-08-21
Hi

> fsck from util-linux 2.20.1 
[/sbin/fsck.ext4 (1) -- /dev/sda1] fsck.ext4 /dev/sda1There looks to be no corruption, currently, on your root directory (sda1).

> How can I check this?It should be being unmounted by the init scripts at shutdown.

Can you post the output of

```
ls -l /etc/rc?.d/*umountfs*
```and 

```
ls -l /etc/init.d/umountfs
```You can also make the init scripts log more information.

A couple more questions first though.

Have you looked in the "lost+found" folder to see if there are orphaned files in there ? You will need to be root to look in that directory.

When you lose the files, is fsck being run on the boot that the files are being lost ?

Have you taken a look in syslog to see if there is anything in there that may point to hard drive problems ?

```
grep sda1 syslog
```You may post that back here if you want.

This may, of course, be barking up the wrong tree but it is worth checking :)

Kind regards

---

### Post by bryncoles on 2012-08-21
I also experienced weird shenanigans with Xubuntu and Thunar.  Directories would forget they were directories and appear as dead icons.  Renaming them made them remember what they were.  Turned out the problem was Thunar.  

Open Thunar, open preferences (edit -> preferences) and in the 'display' tab, uncheck 'show thumbnails'.  See if it helps.  It helped me.

---

### Post by migrena6 on 2012-08-21
First output:

```
$ ls -l /etc/rc?.d/*umountfs*
lrwxrwxrwx 1 root root 18 júl 24 15:02 /etc/rc0.d/S40umountfs -> ../init.d/umountfs
lrwxrwxrwx 1 root root 18 júl 24 15:02 /etc/rc6.d/S40umountfs -> ../init.d/umountfs

```Second output:

```
~$ ls -l /etc/init.d/umountfs
-rwxr-xr-x 1 root root 2800 apr 14 11:26 /etc/init.d/umountfs

```> Have you looked in the "lost+found" folder to see if there are orphaned  files in there ? You will need to be root to look in that directory.
Lost+found is empty (according superuser mc).

> When you lose the files, is fsck being run on the boot that the files are being lost ?
I recognized that the files disappeared by broken links to them. It is possible, that they disappeared after turn on from sleep mode (not sure) and that files were probably open before suspend. I know only about three missing files. 

> Have you taken a look in syslog to see if there is anything in there that may point to hard drive problems ?```
~$ cat /var/log/syslog | grep sda1
Aug 21 15:38:25 100Pc kernel: [    1.141138]  sda: sda1 sda2 < sda5 >
Aug 21 15:38:25 100Pc kernel: [    1.708450] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 21 15:38:25 100Pc kernel: [    7.726135] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 21 15:59:30 100Pc kernel: [    1.118949]  sda: sda1 sda2 < sda5 >
Aug 21 15:59:30 100Pc kernel: [    1.745824] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Aug 21 15:59:30 100Pc kernel: [    1.745829] EXT4-fs (sda1): write access will be enabled during recovery
Aug 21 15:59:30 100Pc kernel: [    4.950367] EXT4-fs (sda1): recovery complete
Aug 21 15:59:30 100Pc kernel: [    4.951046] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 21 15:59:30 100Pc kernel: [   25.069391] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Aug 21 16:08:21 100Pc kernel: [    1.184484]  sda: sda1 sda2 < sda5 >
Aug 21 16:08:21 100Pc kernel: [    1.638696] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Aug 21 16:08:21 100Pc kernel: [    1.638701] EXT4-fs (sda1): write access will be enabled during recovery
Aug 21 16:08:21 100Pc kernel: [    2.091029] EXT4-fs (sda1): recovery complete
Aug 21 16:08:21 100Pc kernel: [    2.091814] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Aug 21 16:08:21 100Pc kernel: [   22.396052] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

```

---

### Post by matt_symes on 2012-08-21
Hi

> **bryncoles said:**
> I also experienced weird shenanigans with Xubuntu and Thunar.  Directories would forget they were directories and appear as dead icons.  Renaming them made them remember what they were.  Turned out the problem was Thunar.  

Open Thunar, open preferences (edit -> preferences) and in the 'display' tab, uncheck 'show thumbnails'.  See if it helps.  It helped me.

Interesting post bryncoles. I'm glad you posted.

@OP. Have you checked to see the files are actually missing using the terminal ?

EDIT: There is nothing to suggest there is any problem with the filing system from what you posted above.

You could try syncing before sleeping but first verify the files are definitely gone using the terminal. Enusre the problem is not with Thunar as suggested by bryncoles.

Kind regards

---

### Post by migrena6 on 2012-08-21
To bryncoles:

I have problems with bookmark (on the side panel of Thunar) of "Downloads" and later of "Trash". Bookmark of "Downloads"  disappeared, bookmark of "Trash" has been recovered. 
Both directories are fine.
[]("http://ubuntuforums.org/member.php?u=472929")

---

### Post by matt_symes on 2012-08-21
Hi

@migrena6

We are cross posting :( That makes communication hard.

Take a look a post #12. You have verified the files are missing using the terminal ?

Kind regards
[]("http://ubuntuforums.org/member.php?u=1721140")

---

### Post by migrena6 on 2012-08-21
> You have verified the files are missing using the terminal ?Yes, I verified by using terminal that the files are missing.
Sorry for misunderstanding, I did not recognize "@OP".

---

### Post by matt_symes on 2012-08-21
Hi

> **migrena6 said:**
> Yes, I verified by using terminal that the files are missing.

I have just looked at the pm-utils scripts. 

They should be used by default when you suspend your machine and file system syncing should happen automatically. 

This should ensure that all cached writable data is written to the drive (or at least passed to the drive to be written).

```

matthew-Aspire-7540:/usr/lib/pm-utils % grep -A5 -B3 sync /usr/lib/pm-utils/bin/pm-action
if run_hooks sleep "$ACTION $METHOD"; then
        # Sleep only if we know how and if a hook did not inhibit us.
        log "$(date): performing $METHOD"
        **sync**
        "do_$METHOD" || r=128
        log "$(date): Awake."
else
        log "$(date): Inhibit found, will not perform $METHOD"
fi
matthew-Aspire-7540:/usr/lib/pm-utils % 
```Can you supply any more information on when the files get lost, because at the moment SMART is reporting the drive is healthy (not foolproof as i have had dodgy drives with good SMART status), the filing system seems to be in order and the filing system should be being synced when suspending.

Any extra information you supply would help to narrow down what may be causing the problem as it is obviously an intermittent problem and only happens very infrequently.

You can ensure the filing system is syncing correctly by creating a script in

```
/etc/pm/sleep.d
```...but i would be surprised if this were the problem.

At the moment, apart from the script above, i am not sure what to suggest.

Trawl through the logs on the days you lost the files and see if there is anything in them for that time period.

> Sorry for misunderstanding, I did not recognize "@OP".No need to apologise. I learn something new everyday as well :)

Kind regards

---

### Post by migrena6 on 2012-08-21
Sorry, I do not know what should I do with this script (I am totally beginner in scripting:().
The files disappeared probably 17 th August. 

When I reading logs i did not find anything except  something like this, but earlier than files disappearing :
```
ext4_orphan_cleanup: deleting unreferenced inode
```

---

### Post by matt_symes on 2012-08-21
Hi

Please understand, i do not expect this script to make the blindest bit of difference as the system should be synced for you anyway by the pm-utils scripts.

but for the record...

Open a terminal and copy and paste below into it.

(Copy the text below, open terminal, right click in terminal and select paste, hit the enter key)

```
cat <<'EOF' >> ~/99_sync
#!/bin/sh
LOGFILE="/var/log/sleep.log"

case "$1" in
        suspend)
                echo "syncing filing system" >> "$LOGFILE"
                sync
                ;;
esac
EOF
```Check the file by typing this...

```
cat ~/99_sync 
```Make sure it looks like this

```
#!/bin/sh
LOGFILE="/var/log/sleep.log"

case "$1" in
        suspend)
                echo "syncing filing system" >> "$LOGFILE"
                sync
                ;;
esac
```

Then type....

```
sudo mv ~/99_sync /etc/pm/sleep.d/
```Enter your password. It will not be echoed to the screen.

Finally type...

```
sudo chmod 755 /etc/pm/sleep.d/99_sync 
```Like i said though, i don't expect that file to make any difference at all.

I will have a think tonight and see if i can come up with any other reasons you may have lost the files.

Kind regards

---

### Post by migrena6 on 2012-08-21
Thanks for advice.

I am going to monitoring number of files in my home directory (all disappeared files were from there). When I notice that the number has changed, I post reply possibly with info from logs.

---

### Post by matt_symes on 2012-08-21
Hi

Do you have any program running that would delete the files from your hard drive ?

Have you taken a look at your running processes ?

Did all the files go missing on the same day ? If not, did they go missing at a predictable interval ? i.e say one week apart ?

Kind regards

---

### Post by migrena6 on 2012-08-21
> Do you have any program running that would delete the files from your hard drive ?
I doubt about it and yes, I looked on running processes. I am going to control every process, but it will take some time. 

Two files disappeared at the same time (PDFs), the third (movie) disappeared circa two days after PDFs.


There is no erasing programs in running processes.

---

### Post by migrena6 on 2012-08-22
Today disappeared entire program (KSystemlog). It looks like that the program was uninstalled by user, but I did not do that. I am the only one who knows password.

There is entire syslog from today:

```
22.08.2012 10:39:50    100Pc    anacron[10252]    Job `cron.daily' terminated
22.08.2012 10:39:50    100Pc    anacron[10252]    Normal exit (1 job run)
22.08.2012 10:41:15    100Pc    dbus[532]    [system] Activating service name='org.debian.apt' (using servicehelper)
22.08.2012 10:41:15    100Pc    AptDaemon    INFO: Initializing daemon
22.08.2012 10:41:15    100Pc    dbus[532]    [system] Successfully activated service 'org.debian.apt'
22.08.2012 10:41:15    100Pc    AptDaemon    INFO: CommitPackages() was called: dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'libnss3'), dbus.String(u'libnss3-1d')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
22.08.2012 10:41:16    100Pc    AptDaemon.Trans    INFO: Queuing transaction /org/debian/apt/transaction/22e3663343254e3b9e3db2b64bfe4f8c
22.08.2012 10:41:16    100Pc    AptDaemon.Worker    INFO: Simulating trans: /org/debian/apt/transaction/22e3663343254e3b9e3db2b64bfe4f8c
22.08.2012 10:41:17    100Pc    AptDaemon.Worker    INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'libnss3'), dbus.String(u'libnss3-1d')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
22.08.2012 10:41:20    100Pc    AptDaemon.Worker    INFO: Processing transaction /org/debian/apt/transaction/22e3663343254e3b9e3db2b64bfe4f8c
22.08.2012 10:41:39    100Pc    AptDaemon.Worker    INFO: Finished transaction /org/debian/apt/transaction/22e3663343254e3b9e3db2b64bfe4f8c
22.08.2012 10:47:15    100Pc    AptDaemon    INFO: Quitting due to inactivity
22.08.2012 10:47:15    100Pc    AptDaemon    INFO: Quitting was requested
22.08.2012 11:14:33    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 11:14:33    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 11:14:33    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3279 seconds.
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info> (eth1): DHCPv4 state changed bound -> renew
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   address 192.168.1.4
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   prefix 24 (255.255.255.0)
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   gateway 192.168.1.1
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   hostname 'dhcppc2'
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   nameserver '195.146.128.60'
22.08.2012 11:14:33    100Pc    NetworkManager[751]    <info>   nameserver '195.146.132.59'
22.08.2012 11:14:33    100Pc    dbus[532]    [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
22.08.2012 11:14:33    100Pc    dbus[532]    [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
22.08.2012 11:17:01    100Pc    CRON[11389]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> sleep requested (sleeping: no  enabled: yes)
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> sleeping or disabling...
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth0): now unmanaged
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth0): cleaning up...
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth0): taking down device.
22.08.2012 11:17:24    100Pc    pulseaudio[1444]    [alsa-sink] alsa-sink.c: Systém ALSA inicializoval zápis nových dát do zariadenia, no nebolo práve &#269;o zapísa&#357;!
22.08.2012 11:17:24    100Pc    pulseaudio[1444]    [alsa-sink] alsa-sink.c: Pravdepodobne je to spôsobené chybou v ovláda&#269;i ALSA „snd_intel8x0“. Nahláste tento problém vývojárom systému ALSA.
22.08.2012 11:17:24    100Pc    pulseaudio[1444]    [alsa-sink] alsa-sink.c: Inicializovaná bola sada POLLOUT -- no následná operácia snd_pcm_avail() vrátila 0 alebo inú hodnotu menšiu ako je povolená.
22.08.2012 11:17:24    100Pc    kernel    [29482.824464] tg3 0000:10:00.0: PME# enabled
22.08.2012 11:17:24    100Pc    kernel    [29482.824487] tg3 0000:10:00.0: wake-up capability enabled by ACPI
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): now unmanaged
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): deactivating device (reason 'sleeping') [37]
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): canceled DHCP transaction, DHCP client pid 10482
22.08.2012 11:17:24    100Pc    dnsmasq[10488]    exiting on receipt of SIGTERM
22.08.2012 11:17:24    100Pc    wpa_supplicant[1214]    CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> DNS: starting dnsmasq...
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): writing resolv.conf to /sbin/resolvconf
22.08.2012 11:17:24    100Pc    dnsmasq[11396]    started, version 2.59 cache disabled
22.08.2012 11:17:24    100Pc    dnsmasq[11396]    compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
22.08.2012 11:17:24    100Pc    dnsmasq[11396]    warning: no upstream servers configured
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): cleaning up...
22.08.2012 11:17:24    100Pc    NetworkManager[751]    <info> (eth1): taking down device.
22.08.2012 11:17:24    100Pc    dbus[532]    [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
22.08.2012 11:17:24    100Pc    dbus[532]    [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
22.08.2012 11:17:25    100Pc    anacron[11485]    Anacron 2.3 started on 2012-08-22
22.08.2012 11:17:25    100Pc    anacron[11485]    Normal exit (0 jobs run)
22.08.2012 11:17:26    100Pc    kernel    [29484.491707] PM: Syncing filesystems ... done.
22.08.2012 11:17:26    100Pc    kernel    [29484.509439] PM: Preparing system for mem sleep
22.08.2012 16:31:43    100Pc    bluetoothd[545]    HCI dev 0 down
22.08.2012 16:31:43    100Pc    bluetoothd[545]    Adapter /org/bluez/545/hci0 has been disabled
22.08.2012 16:31:43    100Pc    bluetoothd[545]    HCI dev 0 unregistered
22.08.2012 16:31:43    100Pc    bluetoothd[545]    Stopping hci0 event socket
22.08.2012 16:31:43    100Pc    bluetoothd[545]    Unregister path: /org/bluez/545/hci0
22.08.2012 16:31:43    100Pc    acpid    client 1256[0:0] has disconnected
22.08.2012 16:31:43    100Pc    bluetoothd[545]    HCI dev 0 registered
22.08.2012 16:31:43    100Pc    bluetoothd[545]    Listening for HCI events on hci0
22.08.2012 16:31:43    100Pc    kernel    [29484.519836] Freezing user space processes ... (elapsed 0.01 seconds) done.
22.08.2012 16:31:43    100Pc    kernel    [29484.536070] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
22.08.2012 16:31:43    100Pc    kernel    [29484.552078] PM: Entering mem sleep
22.08.2012 16:31:43    100Pc    kernel    [29484.552099] Suspending console(s) (use no_console_suspend to debug)
22.08.2012 16:31:43    100Pc    kernel    [29484.552865] sd 0:0:0:0: [sda] Synchronizing SCSI cache
22.08.2012 16:31:43    100Pc    kernel    [29484.595016] parport_pc 00:03: disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.599077] sdhci-pci 0000:02:06.4: PCI INT C disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.599150] ACPI handle has no context!
22.08.2012 16:31:43    100Pc    kernel    [29484.599156] tifm_7xx1 0000:02:06.3: PCI INT B disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.599164] ACPI handle has no context!
22.08.2012 16:31:43    100Pc    kernel    [29484.599241] ACPI handle has no context!
22.08.2012 16:31:43    100Pc    kernel    [29484.599275] eth1: Going into suspend...
22.08.2012 16:31:43    100Pc    kernel    [29484.619433] snd_intel8x0 0000:00:1e.2: PCI INT A disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.619617] uhci_hcd 0000:00:1d.1: PCI INT B disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.619761] ipw2200 0000:02:04.0: PCI INT A disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.632095] uhci_hcd 0000:00:1d.2: PCI INT C disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.632109] uhci_hcd 0000:00:1d.0: PCI INT A disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.650518] sd 0:0:0:0: [sda] Stopping disk
22.08.2012 16:31:43    100Pc    kernel    [29484.672034] ehci_hcd 0000:00:1d.7: PCI INT A disabled
22.08.2012 16:31:43    100Pc    kernel    [29484.816065] radeon 0000:01:00.0: Refused to change power state, currently in D0
22.08.2012 16:31:43    100Pc    kernel    [29484.816076] PM: suspend of drv:radeon dev:0000:01:00.0 complete after 216.766 msecs
22.08.2012 16:31:43    100Pc    kernel    [29484.816089] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 196.425 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632330] PM: suspend of drv:sd dev:0:0:0:0 complete after 1079.469 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632342] PM: suspend of drv:scsi dev:target0:0:0 complete after 1079.384 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632351] PM: suspend of drv:scsi dev:host0 complete after 1036.400 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632478] ata_piix 0000:00:1f.1: PCI INT A disabled
22.08.2012 16:31:43    100Pc    kernel    [29485.632483] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 1013.262 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632493] PM: suspend of drv: dev:pci0000:00 complete after 1012.782 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632499] PM: suspend of devices complete after 1080.187 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.632502] PM: suspend devices took 1.080 seconds
22.08.2012 16:31:43    100Pc    kernel    [29485.633308] ehci_hcd 0000:00:1d.7: PME# enabled
22.08.2012 16:31:43    100Pc    kernel    [29485.648401] PM: late suspend of devices complete after 15.893 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.648963] ACPI: Preparing to enter system sleep state S3
22.08.2012 16:31:43    100Pc    kernel    [29485.649167] PM: Saving platform NVS memory
22.08.2012 16:31:43    100Pc    kernel    [29485.649250] Disabling non-boot CPUs ...
22.08.2012 16:31:43    100Pc    kernel    [29485.649250] ACPI: Low-level resume complete
22.08.2012 16:31:43    100Pc    kernel    [29485.649250] PM: Restoring platform NVS memory
22.08.2012 16:31:43    100Pc    kernel    [29485.649250] Force enabled HPET at resume
22.08.2012 16:31:43    100Pc    kernel    [29485.649365] ACPI: Waking up from system sleep state S3
22.08.2012 16:31:43    100Pc    kernel    [29485.804367] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0xc010a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804379] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
22.08.2012 16:31:43    100Pc    kernel    [29485.804413] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x4010a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804425] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x84518441)
22.08.2012 16:31:43    100Pc    kernel    [29485.804432] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xc830c800)
22.08.2012 16:31:43    100Pc    kernel    [29485.804438] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x6060)
22.08.2012 16:31:43    100Pc    kernel    [29485.804448] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
22.08.2012 16:31:43    100Pc    kernel    [29485.804456] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
22.08.2012 16:31:43    100Pc    kernel    [29485.804505] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x40200)
22.08.2012 16:31:43    100Pc    kernel    [29485.804518] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x84318421)
22.08.2012 16:31:43    100Pc    kernel    [29485.804524] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0x84108400)
22.08.2012 16:31:43    100Pc    kernel    [29485.804531] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x5050)
22.08.2012 16:31:43    100Pc    kernel    [29485.804541] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
22.08.2012 16:31:43    100Pc    kernel    [29485.804548] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
22.08.2012 16:31:43    100Pc    kernel    [29485.804588] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804602] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x8 (was 0x1, writing 0x3001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804616] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804630] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
22.08.2012 16:31:43    100Pc    kernel    [29485.804644] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x3021)
22.08.2012 16:31:43    100Pc    kernel    [29485.804658] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804671] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
22.08.2012 16:31:43    100Pc    kernel    [29485.804685] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x3041)
22.08.2012 16:31:43    100Pc    kernel    [29485.804699] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804720] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x10a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804740] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xc8c00000)
22.08.2012 16:31:43    100Pc    kernel    [29485.804749] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
22.08.2012 16:31:43    100Pc    kernel    [29485.804768] ehci_hcd 0000:00:1d.7: PME# disabled
22.08.2012 16:31:43    100Pc    kernel    [29485.804788] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x83f18001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804794] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xc870c840)
22.08.2012 16:31:43    100Pc    kernel    [29485.804800] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800010, writing 0x22804040)
22.08.2012 16:31:43    100Pc    kernel    [29485.804813] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100001, writing 0x100107)
22.08.2012 16:31:43    100Pc    kernel    [29485.804835] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0xf (was 0x100, writing 0x10b)
22.08.2012 16:31:43    100Pc    kernel    [29485.804850] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0x7 (was 0x0, writing 0xc8c02000)
22.08.2012 16:31:43    100Pc    kernel    [29485.804856] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0x6 (was 0x0, writing 0xc8c01000)
22.08.2012 16:31:43    100Pc    kernel    [29485.804862] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0x5 (was 0x1, writing 0x3201)
22.08.2012 16:31:43    100Pc    kernel    [29485.804869] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0x4 (was 0x1, writing 0x3101)
22.08.2012 16:31:43    100Pc    kernel    [29485.804877] snd_intel8x0 0000:00:1e.2: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900003)
22.08.2012 16:31:43    100Pc    kernel    [29485.804899] pci 0000:00:1e.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804917] pci 0000:00:1e.3: restoring config space at offset 0x5 (was 0x1, writing 0x3501)
22.08.2012 16:31:43    100Pc    kernel    [29485.804923] pci 0000:00:1e.3: restoring config space at offset 0x4 (was 0x1, writing 0x3401)
22.08.2012 16:31:43    100Pc    kernel    [29485.804932] pci 0000:00:1e.3: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900001)
22.08.2012 16:31:43    100Pc    kernel    [29485.804982] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x10a)
22.08.2012 16:31:43    100Pc    kernel    [29485.804996] ata_piix 0000:00:1f.1: restoring config space at offset 0x8 (was 0x1, writing 0x3581)
22.08.2012 16:31:43    100Pc    kernel    [29485.805010] ata_piix 0000:00:1f.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2880005)
22.08.2012 16:31:43    100Pc    kernel    [29485.805037] radeon 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
22.08.2012 16:31:43    100Pc    kernel    [29485.805043] radeon 0000:01:00.0: restoring config space at offset 0x1 (was 0x100403, writing 0x100407)
22.08.2012 16:31:43    100Pc    kernel    [29485.805101] tg3 0000:10:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf8fd0000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805125] tg3 0000:10:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
22.08.2012 16:31:43    100Pc    kernel    [29485.805134] tg3 0000:10:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
22.08.2012 16:31:43    100Pc    kernel    [29485.805177] ipw2200 0000:02:04.0: restoring config space at offset 0xf (was 0x18030100, writing 0x1803010b)
22.08.2012 16:31:43    100Pc    kernel    [29485.805203] ipw2200 0000:02:04.0: restoring config space at offset 0x4 (was 0x0, writing 0xc8400000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805210] ipw2200 0000:02:04.0: restoring config space at offset 0x3 (was 0x0, writing 0x4010)
22.08.2012 16:31:43    100Pc    kernel    [29485.805219] ipw2200 0000:02:04.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900006)
22.08.2012 16:31:43    100Pc    kernel    [29485.805248] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c0010b)
22.08.2012 16:31:43    100Pc    kernel    [29485.805255] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xe (was 0x0, writing 0x40fc)
22.08.2012 16:31:43    100Pc    kernel    [29485.805262] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xd (was 0x0, writing 0x4000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805269] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xc (was 0x0, writing 0x44fc)
22.08.2012 16:31:43    100Pc    kernel    [29485.805277] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xb (was 0x0, writing 0x4400)
22.08.2012 16:31:43    100Pc    kernel    [29485.805284] yenta_cardbus 0000:02:06.0: restoring config space at offset 0xa (was 0x0, writing 0x8bfff000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805291] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x9 (was 0x0, writing 0x88000000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805299] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x8 (was 0x0, writing 0x83fff000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805306] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x7 (was 0x0, writing 0x80000000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805313] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x6 (was 0x0, writing 0xb0060302)
22.08.2012 16:31:43    100Pc    kernel    [29485.805323] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x4 (was 0x0, writing 0xc8401000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805330] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x3 (was 0x820000, writing 0x82a810)
22.08.2012 16:31:43    100Pc    kernel    [29485.805339] yenta_cardbus 0000:02:06.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100007)
22.08.2012 16:31:43    100Pc    kernel    [29485.805390] firewire_ohci 0000:02:06.2: restoring config space at offset 0xf (was 0x4020300, writing 0x402030a)
22.08.2012 16:31:43    100Pc    kernel    [29485.805414] firewire_ohci 0000:02:06.2: restoring config space at offset 0x5 (was 0x0, writing 0xc8404000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805422] firewire_ohci 0000:02:06.2: restoring config space at offset 0x4 (was 0x0, writing 0xc8402000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805429] firewire_ohci 0000:02:06.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
22.08.2012 16:31:43    100Pc    kernel    [29485.805438] firewire_ohci 0000:02:06.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
22.08.2012 16:31:43    100Pc    kernel    [29485.805466] tifm_7xx1 0000:02:06.3: restoring config space at offset 0xf (was 0x40702ff, writing 0x407020a)
22.08.2012 16:31:43    100Pc    kernel    [29485.805492] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x4 (was 0x0, writing 0xc8408000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805499] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
22.08.2012 16:31:43    100Pc    kernel    [29485.805508] tifm_7xx1 0000:02:06.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
22.08.2012 16:31:43    100Pc    kernel    [29485.805536] sdhci-pci 0000:02:06.4: restoring config space at offset 0xf (was 0x40703ff, writing 0x407030a)
22.08.2012 16:31:43    100Pc    kernel    [29485.805558] sdhci-pci 0000:02:06.4: restoring config space at offset 0x6 (was 0x0, writing 0xc840c000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805565] sdhci-pci 0000:02:06.4: restoring config space at offset 0x5 (was 0x0, writing 0xc840b000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805572] sdhci-pci 0000:02:06.4: restoring config space at offset 0x4 (was 0x0, writing 0xc840a000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805579] sdhci-pci 0000:02:06.4: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
22.08.2012 16:31:43    100Pc    kernel    [29485.805589] sdhci-pci 0000:02:06.4: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
22.08.2012 16:31:43    100Pc    kernel    [29485.805616] pci 0000:02:06.5: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
22.08.2012 16:31:43    100Pc    kernel    [29485.805636] pci 0000:02:06.5: restoring config space at offset 0x7 (was 0x0, writing 0xc8410000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805643] pci 0000:02:06.5: restoring config space at offset 0x6 (was 0x0, writing 0xc840f000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805650] pci 0000:02:06.5: restoring config space at offset 0x5 (was 0x0, writing 0xc840e000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805657] pci 0000:02:06.5: restoring config space at offset 0x4 (was 0x0, writing 0xc840d000)
22.08.2012 16:31:43    100Pc    kernel    [29485.805668] pci 0000:02:06.5: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100002)
22.08.2012 16:31:43    100Pc    kernel    [29485.806346] PM: early resume of devices complete after 2.180 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.806514] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
22.08.2012 16:31:43    100Pc    kernel    [29485.806522] uhci_hcd 0000:00:1d.0: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806547] usb usb2: root hub lost power or was reset
22.08.2012 16:31:43    100Pc    kernel    [29485.806562] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
22.08.2012 16:31:43    100Pc    kernel    [29485.806569] uhci_hcd 0000:00:1d.1: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806592] usb usb3: root hub lost power or was reset
22.08.2012 16:31:43    100Pc    kernel    [29485.806606] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
22.08.2012 16:31:43    100Pc    kernel    [29485.806613] uhci_hcd 0000:00:1d.2: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806637] usb usb4: root hub lost power or was reset
22.08.2012 16:31:43    100Pc    kernel    [29485.806653] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
22.08.2012 16:31:43    100Pc    kernel    [29485.806660] ehci_hcd 0000:00:1d.7: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806687] pci 0000:00:1e.0: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806697] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
22.08.2012 16:31:43    100Pc    kernel    [29485.806702] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
22.08.2012 16:31:43    100Pc    kernel    [29485.806708] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
22.08.2012 16:31:43    100Pc    kernel    [29485.806713] snd_intel8x0 0000:00:1e.2: power state changed by ACPI to D0
22.08.2012 16:31:43    100Pc    kernel    [29485.806720] snd_intel8x0 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
22.08.2012 16:31:43    100Pc    kernel    [29485.806727] snd_intel8x0 0000:00:1e.2: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806762] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
22.08.2012 16:31:43    100Pc    kernel    [29485.806768] ata_piix 0000:00:1f.1: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806788] radeon 0000:01:00.0: setting latency timer to 64
22.08.2012 16:31:43    100Pc    kernel    [29485.806797] radeon 0000:01:00.0: f1651200 unpin not necessary
22.08.2012 16:31:43    100Pc    kernel    [29485.940174] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
22.08.2012 16:31:43    100Pc    kernel    [29485.940193] eth1: Coming out of suspend...
22.08.2012 16:31:43    100Pc    kernel    [29485.940202] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
22.08.2012 16:31:43    100Pc    kernel    [29485.943779] ata2: port disabled--ignoring
22.08.2012 16:31:43    100Pc    kernel    [29485.943801] tifm_7xx1 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
22.08.2012 16:31:43    100Pc    kernel    [29485.943827] sdhci-pci 0000:02:06.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
22.08.2012 16:31:43    100Pc    kernel    [29485.943996] PM: resume of drv: dev:platform complete after 137.514 msecs
22.08.2012 16:31:43    100Pc    kernel    [29485.998438] sd 0:0:0:0: [sda] Starting disk
22.08.2012 16:31:43    100Pc    kernel    [29486.000202] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
22.08.2012 16:31:43    100Pc    kernel    [29486.000268] radeon 0000:01:00.0: WB enabled
22.08.2012 16:31:43    100Pc    kernel    [29486.000310] [drm] radeon: ring at 0x00000000A0001000
22.08.2012 16:31:43    100Pc    kernel    [29486.000330] [drm] ring test succeeded in 1 usecs
22.08.2012 16:31:43    100Pc    kernel    [29486.000350] [drm] ib test succeeded in 0 usecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113736] PM: resume of drv:hub dev:2-0:1.0 complete after 169.804 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113784] PM: resume of drv: dev:ep_00 complete after 169.845 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113792] PM: resume of drv: dev:ep_81 complete after 169.857 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113799] PM: resume of drv:hub dev:4-0:1.0 complete after 115.423 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113808] PM: resume of drv: dev:ep_00 complete after 115.393 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.113815] PM: resume of drv: dev:ep_81 complete after 115.420 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.218625] PM: resume of drv:radeon dev:0000:01:00.0 complete after 411.841 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.218638] PM: resume of drv:hub dev:3-0:1.0 complete after 274.688 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.218647] PM: resume of drv: dev:ep_00 complete after 246.262 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.218674] PM: resume of drv: dev:ep_81 complete after 274.720 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.218849] firewire_core: skipped bus generations, destroying all nodes
22.08.2012 16:31:43    100Pc    kernel    [29486.218965] tg3 0000:10:00.0: wake-up capability disabled by ACPI
22.08.2012 16:31:43    100Pc    kernel    [29486.218997] tg3 0000:10:00.0: PME# disabled
22.08.2012 16:31:43    100Pc    kernel    [29486.219002] PM: resume of drv:tg3 dev:0000:10:00.0 complete after 278.814 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.256495] PM: resume of drv:battery dev:PNP0C0A:00 complete after 311.992 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.277496] parport_pc 00:03: activated
22.08.2012 16:31:43    100Pc    kernel    [29486.328073] usb 3-1: reset full-speed USB device number 2 using uhci_hcd
22.08.2012 16:31:43    100Pc    kernel    [29486.484975] PM: resume of drv:usbhid dev:3-1:1.0 complete after 484.624 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.484983] PM: resume of drv:usbhid dev:3-1:1.1 complete after 479.162 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.484990] PM: resume of drv: dev:ep_00 complete after 447.333 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.484997] PM: resume of drv: dev:ep_81 complete after 479.194 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.485003] PM: resume of drv: dev:ep_82 complete after 447.351 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.576070] usb 3-2: reset full-speed USB device number 3 using uhci_hcd
22.08.2012 16:31:43    100Pc    kernel    [29486.716046] firewire_core: rediscovered device fw0
22.08.2012 16:31:43    100Pc    kernel    [29486.729967] btusb 3-2:1.0: no reset_resume for driver btusb?
22.08.2012 16:31:43    100Pc    kernel    [29486.729970] btusb 3-2:1.1: no reset_resume for driver btusb?
22.08.2012 16:31:43    100Pc    kernel    [29486.945933] PM: resume of drv:snd_intel8x0 dev:0000:00:1e.2 complete after 1139.237 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980224] PM: resume of drv:usb dev:3-2:1.0 complete after 942.559 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980234] PM: resume of drv:usb dev:3-2:1.1 complete after 916.194 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980243] PM: resume of drv:usb dev:3-2:1.2 complete after 866.461 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980251] PM: resume of drv:usb dev:3-2:1.3 complete after 866.445 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980257] PM: resume of drv: dev:ep_00 complete after 866.443 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980263] PM: resume of drv: dev:ep_81 complete after 942.592 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980269] PM: resume of drv: dev:ep_82 complete after 942.579 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980275] PM: resume of drv: dev:ep_02 complete after 922.702 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980281] PM: resume of drv: dev:ep_83 complete after 916.221 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980287] PM: resume of drv: dev:ep_03 complete after 866.543 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980293] PM: resume of drv: dev:ep_84 complete after 866.503 msecs
22.08.2012 16:31:43    100Pc    kernel    [29486.980299] PM: resume of drv: dev:ep_04 complete after 866.501 msecs
22.08.2012 16:31:43    100Pc    kernel    [29488.620400] ata1.01: ACPI cmd ef/03:0c:00:00:00:b0 (SET FEATURES) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.620406] ata1.01: ACPI cmd ef/03:22:00:00:00:b0 (SET FEATURES) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.932392] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.932397] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.932402] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.932407] ata1.00: ACPI cmd b1/c1:00:00:00:00:a0 (DEVICE CONFIGURATION OVERLAY) filtered out
22.08.2012 16:31:43    100Pc    kernel    [29488.932741] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
22.08.2012 16:31:43    100Pc    kernel    [29488.988610] ata1.00: configured for UDMA/100
22.08.2012 16:31:43    100Pc    kernel    [29489.004279] ata1.01: configured for MWDMA2
22.08.2012 16:31:43    100Pc    kernel    [29489.020106] PM: resume of drv:sd dev:0:0:0:0 complete after 3021.667 msecs
22.08.2012 16:31:43    100Pc    kernel    [29489.020117] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 3019.899 msecs
22.08.2012 16:31:43    100Pc    kernel    [29489.020125] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2740.349 msecs
22.08.2012 16:31:43    100Pc    kernel    [29489.177176] PM: resume of devices complete after 3370.759 msecs
22.08.2012 16:31:43    100Pc    kernel    [29489.403275] PM: resume devices took 3.596 seconds
22.08.2012 16:31:43    100Pc    kernel    [29489.403325] PM: Finishing wakeup.
22.08.2012 16:31:43    100Pc    kernel    [29489.403327] Restarting tasks ... done.
22.08.2012 16:31:43    100Pc    acpid    client connected from 1256[0:0]
22.08.2012 16:31:43    100Pc    acpid    1 client rule loaded
22.08.2012 16:31:43    100Pc    kernel    [29489.517621] video LNXVIDEO:00: Restoring backlight state
22.08.2012 16:31:43    100Pc    kernel    [29489.517928] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
22.08.2012 16:31:43    100Pc    bluetoothd[545]    HCI dev 0 up
22.08.2012 16:31:43    100Pc    bluetoothd[545]    input-headset driver probe failed for device 00:1D:28:1C:65:90
22.08.2012 16:31:43    100Pc    bluetoothd[545]    Adapter /org/bluez/545/hci0 has been enabled
22.08.2012 16:31:44    100Pc    anacron[11904]    Anacron 2.3 started on 2012-08-22
22.08.2012 16:31:44    100Pc    anacron[11904]    Normal exit (0 jobs run)
22.08.2012 16:31:46    100Pc    anacron[12058]    Anacron 2.3 started on 2012-08-22
22.08.2012 16:31:46    100Pc    anacron[12058]    Normal exit (0 jobs run)
22.08.2012 16:31:46    100Pc    NetworkManager[751]    <info> wake requested (sleeping: yes  enabled: yes)
22.08.2012 16:31:47    100Pc    kernel    [29492.526462] ADDRCONF(NETDEV_UP): eth0: link is not ready
22.08.2012 16:31:47    100Pc    kernel    [29492.533221] ADDRCONF(NETDEV_UP): eth1: link is not ready
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> waking up and re-enabling...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth0): now managed
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth0): bringing up device.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth0): preparing device.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth0): deactivating device (reason 'managed') [2]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): now managed
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): bringing up device.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): preparing device.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): deactivating device (reason 'managed') [2]
22.08.2012 16:31:47    100Pc    wpa_supplicant[1214]    nl80211: Driver does not support authentication/association or connect commands
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): supplicant interface state: starting -> ready
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): supplicant interface state: ready -> inactive
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <warn> Trying to remove a non-existant call id.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Auto-activating connection 'domaca siet'.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) starting connection 'domaca siet'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1/wireless): access point 'domaca siet' has security, but secrets are required.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1/wireless): connection 'domaca siet' has security, and secrets exist.  No new secrets needed.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: added 'ssid' value 'domaca siet'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: added 'scan_ssid' value '1'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: added 'key_mgmt' value 'NONE'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: added 'wep_key0' value '<omitted>'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: added 'wep_tx_keyidx' value '0'
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> Config: set interface ap_scan to 1
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): supplicant interface state: inactive -> scanning
22.08.2012 16:31:47    100Pc    wpa_supplicant[1214]    Trying to associate with f0:7d:68:3f:07:57 (SSID='domaca siet' freq=2412 MHz)
22.08.2012 16:31:47    100Pc    wpa_supplicant[1214]    Association request to the driver failed
22.08.2012 16:31:47    100Pc    NetworkManager[751]    <info> (eth1): supplicant interface state: scanning -> associating
22.08.2012 16:31:48    100Pc    wpa_supplicant[1214]    Associated with f0:7d:68:3f:07:57
22.08.2012 16:31:48    100Pc    wpa_supplicant[1214]    CTRL-EVENT-CONNECTED - Connection to f0:7d:68:3f:07:57 completed (auth) [id=0 id_str=]
22.08.2012 16:31:48    100Pc    kernel    [29493.694307] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> (eth1): supplicant interface state: associating -> completed
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'domaca siet'.
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> dhclient started with pid 12140
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1) Beginning IP6 addrconf.
22.08.2012 16:31:48    100Pc    dhclient    Internet Systems Consortium DHCP Client 4.1-ESV-R4
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
22.08.2012 16:31:48    100Pc    dhclient    Copyright 2004-2011 Internet Systems Consortium.
22.08.2012 16:31:48    100Pc    dhclient    All rights reserved.
22.08.2012 16:31:48    100Pc    dhclient    For info, please visit https://www.isc.org/software/dhcp/
22.08.2012 16:31:48    100Pc    dhclient    
22.08.2012 16:31:48    100Pc    dhclient    Listening on LPF/eth1/00:15:00:2a:17:0d
22.08.2012 16:31:48    100Pc    dhclient    Sending on   LPF/eth1/00:15:00:2a:17:0d
22.08.2012 16:31:48    100Pc    dhclient    Sending on   Socket/fallback
22.08.2012 16:31:48    100Pc    dhclient    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
22.08.2012 16:31:48    100Pc    NetworkManager[751]    <info> (eth1): DHCPv4 state changed nbi -> preinit
22.08.2012 16:31:51    100Pc    dhclient    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
22.08.2012 16:31:58    100Pc    dhclient    DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
22.08.2012 16:31:58    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 255.255.255.255 port 67
22.08.2012 16:31:58    100Pc    dhclient    DHCPOFFER of 192.168.1.4 from 192.168.1.1
22.08.2012 16:31:58    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info> (eth1): DHCPv4 state changed preinit -> bound
22.08.2012 16:31:58    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 2785 seconds.
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   address 192.168.1.4
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   prefix 24 (255.255.255.0)
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   gateway 192.168.1.1
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   hostname 'dhcppc2'
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   nameserver '195.146.128.60'
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info>   nameserver '195.146.132.59'
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
22.08.2012 16:31:58    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
22.08.2012 16:31:58    100Pc    kernel    [29504.376035] eth1: no IPv6 routers present
22.08.2012 16:31:59    100Pc    dnsmasq[11396]    exiting on receipt of SIGTERM
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> DNS: starting dnsmasq...
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> (eth1): writing resolv.conf to /sbin/resolvconf
22.08.2012 16:31:59    100Pc    dnsmasq[12147]    started, version 2.59 cache disabled
22.08.2012 16:31:59    100Pc    dnsmasq[12147]    compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
22.08.2012 16:31:59    100Pc    dnsmasq[12147]    using nameserver 195.146.132.59#53
22.08.2012 16:31:59    100Pc    dnsmasq[12147]    using nameserver 195.146.128.60#53
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> (eth1): roamed from BSSID F0:7D:68:3F:07:57 (domaca siet) to (none) ((none))
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> Policy set 'domaca siet' (eth1) as default for IPv4 routing and DNS.
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> Activation (eth1) successful, device activated.
22.08.2012 16:31:59    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
22.08.2012 16:31:59    100Pc    dbus[532]    [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
22.08.2012 16:31:59    100Pc    dbus[532]    [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
22.08.2012 16:32:09    100Pc    ntpdate[12187]    step time server 91.189.94.4 offset 1.824677 sec
22.08.2012 16:32:10    100Pc    NetworkManager[751]    <info> (eth1): IP6 addrconf timed out or failed.
22.08.2012 16:32:10    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
22.08.2012 16:32:10    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
22.08.2012 16:32:10    100Pc    NetworkManager[751]    <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
22.08.2012 17:17:01    100Pc    CRON[12614]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 17:18:24    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 17:18:24    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 17:18:24    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3575 seconds.
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info> (eth1): DHCPv4 state changed bound -> renew
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   address 192.168.1.4
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   prefix 24 (255.255.255.0)
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   gateway 192.168.1.1
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   hostname 'dhcppc2'
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   nameserver '195.146.128.60'
22.08.2012 17:18:24    100Pc    NetworkManager[751]    <info>   nameserver '195.146.132.59'
22.08.2012 17:18:24    100Pc    dbus[532]    [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
22.08.2012 17:18:24    100Pc    dbus[532]    [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
22.08.2012 18:17:01    100Pc    CRON[12769]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 18:18:00    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 18:18:00    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 18:18:00    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3573 seconds.
22.08.2012 19:17:02    100Pc    CRON[13122]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 19:17:33    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 19:17:33    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 19:17:33    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3434 seconds.
22.08.2012 20:14:47    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 20:14:47    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 20:14:47    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3390 seconds.
22.08.2012 20:17:01    100Pc    CRON[13225]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 21:11:17    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 21:11:17    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 21:11:17    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 3481 seconds.
22.08.2012 21:17:01    100Pc    CRON[13588]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
22.08.2012 21:27:57    100Pc    kernel    [47261.642566] type=1400 audit(1345663677.813:25): apparmor="DENIED" operation="exec" parent=1 profile="/usr/bin/evince" name="/usr/bin/exo-open" pid=13758 comm="evince" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
22.08.2012 21:28:00    100Pc    kernel    [47264.459363] type=1400 audit(1345663680.629:26): apparmor="DENIED" operation="exec" parent=1 profile="/usr/bin/evince" name="/usr/bin/exo-open" pid=13760 comm="evince" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0
22.08.2012 21:52:37    100Pc    dbus[532]    [system] Activating service name='org.debian.apt' (using servicehelper)
22.08.2012 21:52:38    100Pc    AptDaemon    INFO: Initializing daemon
22.08.2012 21:52:38    100Pc    dbus[532]    [system] Successfully activated service 'org.debian.apt'
22.08.2012 21:53:09    100Pc    AptDaemon    INFO: RemovePackages() was called: 'dbus.Array([dbus.String(u'kde-runtime-data')], signature=dbus.Signature('s'))'
22.08.2012 21:53:09    100Pc    AptDaemon.Trans    INFO: Queuing transaction /org/debian/apt/transaction/1482794f4052452f99688656cd7243da
22.08.2012 21:53:17    100Pc    AptDaemon.Worker    INFO: Simulating trans: /org/debian/apt/transaction/1482794f4052452f99688656cd7243da
22.08.2012 21:53:17    100Pc    AptDaemon.Worker    INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'kde-runtime-data')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
22.08.2012 21:53:20    100Pc    AptDaemon.Worker    INFO: Processing transaction /org/debian/apt/transaction/1482794f4052452f99688656cd7243da
22.08.2012 21:53:53    100Pc    dbus[532]    [system] Reloaded configuration
22.08.2012 21:54:37    100Pc    AptDaemon.Worker    INFO: Finished transaction /org/debian/apt/transaction/1482794f4052452f99688656cd7243da
22.08.2012 21:55:24    100Pc    AptDaemon    INFO: CommitPackages() was called: dbus.Array([dbus.String(u'pybackpack')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
22.08.2012 21:55:24    100Pc    AptDaemon.Trans    INFO: Queuing transaction /org/debian/apt/transaction/c52b4c7933f94456b56d7302b1448c69
22.08.2012 21:55:24    100Pc    AptDaemon.Worker    INFO: Simulating trans: /org/debian/apt/transaction/c52b4c7933f94456b56d7302b1448c69
22.08.2012 21:55:25    100Pc    AptDaemon.Worker    INFO: Committing packages: dbus.Array([dbus.String(u'pybackpack')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
22.08.2012 21:55:28    100Pc    AptDaemon.Worker    INFO: Processing transaction /org/debian/apt/transaction/c52b4c7933f94456b56d7302b1448c69
22.08.2012 21:55:48    100Pc    AptDaemon.Worker    INFO: Finished transaction /org/debian/apt/transaction/c52b4c7933f94456b56d7302b1448c69
22.08.2012 21:58:30    100Pc    AptDaemon    INFO: CommitPackages() was called: dbus.Array([dbus.String(u'ksystemlog')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
22.08.2012 21:58:31    100Pc    AptDaemon.Trans    INFO: Queuing transaction /org/debian/apt/transaction/b52800b1780c40ffb828da9cb6b4e5dd
22.08.2012 21:58:38    100Pc    AptDaemon.Worker    INFO: Simulating trans: /org/debian/apt/transaction/b52800b1780c40ffb828da9cb6b4e5dd
22.08.2012 21:58:39    100Pc    AptDaemon.Worker    INFO: Committing packages: dbus.Array([dbus.String(u'ksystemlog')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
22.08.2012 21:58:42    100Pc    AptDaemon.Worker    INFO: Processing transaction /org/debian/apt/transaction/b52800b1780c40ffb828da9cb6b4e5dd
22.08.2012 21:58:45    100Pc    dbus[532]    [system] Reloaded configuration
22.08.2012 21:59:10        dbus[532]    last message repeated 5 times
22.08.2012 21:59:10    100Pc    AptDaemon.Worker    INFO: Finished transaction /org/debian/apt/transaction/b52800b1780c40ffb828da9cb6b4e5dd
22.08.2012 22:04:38    100Pc    AptDaemon    INFO: Quitting due to inactivity
22.08.2012 22:04:38    100Pc    AptDaemon    INFO: Quitting was requested
22.08.2012 22:04:38    100Pc    dbus[532]    [system] Activating service name='org.debian.apt' (using servicehelper)
22.08.2012 22:04:38    100Pc    AptDaemon    INFO: Initializing daemon
22.08.2012 22:04:38    100Pc    dbus[532]    [system] Successfully activated service 'org.debian.apt'
22.08.2012 22:09:18    100Pc    dhclient    DHCPREQUEST of 192.168.1.4 on eth1 to 192.168.1.1 port 67
22.08.2012 22:09:18    100Pc    dhclient    DHCPACK of 192.168.1.4 from 192.168.1.1
22.08.2012 22:09:18    100Pc    dhclient    bound to 192.168.1.4 -- renewal in 2809 seconds.
22.08.2012 22:09:39    100Pc    AptDaemon    INFO: Quitting due to inactivity
22.08.2012 22:09:39    100Pc    AptDaemon    INFO: Quitting was requested
22.08.2012 22:09:39    100Pc    dbus[532]    [system] Activating service name='org.debian.apt' (using servicehelper)
22.08.2012 22:09:39    100Pc    AptDaemon    INFO: Initializing daemon
22.08.2012 22:09:39    100Pc    dbus[532]    [system] Successfully activated service 'org.debian.apt'
22.08.2012 22:14:40    100Pc    AptDaemon    INFO: Quitting due to inactivity
22.08.2012 22:14:40    100Pc    AptDaemon    INFO: Quitting was requested
22.08.2012 22:17:01    100Pc    CRON[17369]    (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

---

### Post by bryncoles on 2012-08-23
Yikes!  I have no idea what to do with that output, but this message will serve as a nice *bump* to get you back on the front page.  

Meantime, you can open a terminal and type 

```
who
```
to see who's logged in.  Try 
```
 who -a 
who -u
```

I would back up all data and reinstall the system at this point, myself.  Let's see if there's someone with a more moderated viewpoint to help though.

---

### Post by migrena6 on 2012-08-23
Hi.

```
$ who -a
           system boot  2012-08-21 16:08
           úrove&#328;-behu 2 2012-08-21 16:08
LOGIN      tty4         2012-08-21 16:08               858 id=4
LOGIN      tty5         2012-08-21 16:08               863 id=5
LOGIN      tty2         2012-08-21 16:08               877 id=2
LOGIN      tty3         2012-08-21 16:08               882 id=3
LOGIN      tty6         2012-08-21 16:08               884 id=6
LOGIN      tty1         2012-08-21 16:08              1268 id=1
michal   + tty7         2012-08-21 16:08  dávn       1354

``````
~$ who -u
michal   tty7         2012-08-21 16:08  dávn       1354

```What is so shocking?

Translation: " úrove&#328;-behu"=run-level
                        "dávn"                =old(?)

> ...this message will serve as a nice *bump* to get you back on the front page.  
Sorry, do not understand.

---

### Post by bryncoles on 2012-08-23
I'm shocked at software being uninstalled by the user, but apparently not by yourself.  

Also: a 'bump' is some activity on the thread which doesn't necessarily help, but which moves the thread back to the front page of the forum.  Thus, allowing more people to see the thread, and potentially get more help.  

Now, look's like you're the only person logged into your computer...

---

### Post by matt_symes on 2012-08-23
Hi

Why do you think the software was uninstalled ? This thread has gone from losing files at reboot, to losing them at suspend to someone uninstalling your files. 

Is this speculation on your part or do you know this is happening ?

Can we check on the software.

From the terminal, please post the output of these commands. You may find it easier to copy and paste them into the terminal and copy and paste the output back into your next post.

```
dpkg -l ksystemlog
```Small L after dpkg.

```
apt-cache policy ksystemlog
``````
which ksystemlog
``````

grep ksystemlog /var/log/apt/history.log && zgrep ksystemlog /var/log/apt/history.log.*
``````
grep ksystemlog /var/log/dpkg.log*
```Kind regards

---

### Post by migrena6 on 2012-08-23
Hi.

I installed KSystemlog for viewing logs and was using it day before yesterday. Yesterday when I wanted to see some logs there was no icon for this program in Applications-> System. I  tried to run "ksystemlog" on terminal with error **" The program 'ksystemlog' is currently not installed..."**. 

```
~$ dpkg -l ksystemlog
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ksystemlog     4:4.8.4-0ubunt system log viewer

``````
:~$ apt-cache policy ksystemlog
ksystemlog:
  Installed: 4:4.8.4-0ubuntu0.1
  Candidate: 4:4.8.4-0ubuntu0.1
  Version table:
 *** 4:4.8.4-0ubuntu0.1 0
        500 http://sk.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     4:4.8.2-0ubuntu1 0
        500 http://sk.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
``````
~$ which ksystemlog
/usr/bin/ksystemlog

``````
~$ grep ksystemlog /var/log/apt/history.log && zgrep ksystemlog /var/log/apt/history.log.*
Install: ksystemlog:i386 (4.8.4-0ubuntu0.1)
Remove: qapt-batch:i386 (1.3.1-0ubuntu2), ksystemlog:i386 (4.8.4-0ubuntu0.1), libkldap4:i386 (4.8.4-0ubuntu0.2), kubuntu-debug-installer:i386 (11.10ubuntu1), kdepim-runtime:i386 (4.8.4-0ubuntu0.2), libkpimtextedit4:i386 (4.8.4-0ubuntu0.2), libprison0:i386 (1.0+dfsg-1), libkcalutils4:i386 (4.8.4-0ubuntu0.2), libmicroblog4:i386 (4.8.4-0ubuntu0.2), mysql-client-core-5.5:i386 (5.5.24-0ubuntu0.12.04.1), akonadi-backend-mysql:i386 (1.7.2-0ubuntu1), libkalarmcal2:i386 (4.8.4-0ubuntu0.2), kde-runtime-data:i386 (4.8.4-0ubuntu0.1), libqrencode3:i386 (3.1.1-1ubuntu1), libkmbox4:i386 (4.8.4-0ubuntu0.2), mysql-server-core-5.5:i386 (5.5.24-0ubuntu0.12.04.1), akregator:i386 (4.8.4a-0ubuntu0.3), libkcalcore4:i386 (4.8.4-0ubuntu0.2), libmailtransport4:i386 (4.8.4-0ubuntu0.2), libakonadi-kde4:i386 (4.8.4-0ubuntu0.2), libkabc4:i386 (4.8.4-0ubuntu0.2), libkresources4:i386 (4.8.4-0ubuntu0.2), libkdepim4:i386 (4.8.4a-0ubuntu0.3), libkpimutils4:i386 (4.8.4-0ubuntu0.2), libkpimidentities4:i386 (4.8.4-0ubuntu0.2), libakonadi-notes4:i386 (4.8.4-0ubuntu0.2), libkcal4:i386 (4.8.4-0ubuntu0.2), libakonadi-calendar4:i386 (4.8.4-0ubuntu0.2), libkimap4:i386 (4.8.4-0ubuntu0.2), libkmime4:i386 (4.8.4-0ubuntu0.2), libakonadi-contact4:i386 (4.8.4-0ubuntu0.2), libakonadi-kabc4:i386 (4.8.4-0ubuntu0.2), kde-runtime:i386 (4.8.4-0ubuntu0.1), libkholidays4:i386 (4.8.4-0ubuntu0.2), akonadi-server:i386 (1.7.2-0ubuntu1), libakonadiprotocolinternals1:i386 (1.7.2-0ubuntu1), libakonadi-kcal4:i386 (4.8.4-0ubuntu0.2), libsyndication4:i386 (4.8.4-0ubuntu0.2), libakonadi-kmime4:i386 (4.8.4-0ubuntu0.2), kdepimlibs-kio-plugins:i386 (4.8.4-0ubuntu0.2), okular:i386 (4.8.4-0ubuntu0.1), libdmtx0a:i386 (0.7.2-1build2), libkontactinterface4:i386 (4.8.4-0ubuntu0.2)
Install: qapt-batch:i386 (1.3.1-0ubuntu2, automatic), ksystemlog:i386 (4.8.4-0ubuntu0.1), kubuntu-debug-installer:i386 (11.10ubuntu1, automatic), kde-runtime-data:i386 (4.8.4-0ubuntu0.1, automatic), kde-runtime:i386 (4.8.4-0ubuntu0.1, automatic)

``````
~$ grep ksystemlog /var/log/dpkg.log*
/var/log/dpkg.log:2012-08-21 19:15:10 install ksystemlog <none> 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:10 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:11 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:11 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:11 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:12 configure ksystemlog 4:4.8.4-0ubuntu0.1 <none>
/var/log/dpkg.log:2012-08-21 19:15:12 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:12 status half-configured ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-21 19:15:13 status installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:47 status installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:47 remove ksystemlog 4:4.8.4-0ubuntu0.1 <none>
/var/log/dpkg.log:2012-08-22 21:53:47 status half-configured ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:47 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:47 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:48 status config-files ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:48 status config-files ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:48 status config-files ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:53:48 status not-installed ksystemlog <none>
/var/log/dpkg.log:2012-08-22 21:58:53 install ksystemlog <none> 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:58:53 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:58:53 status half-installed ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:58:53 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:58:53 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:59:07 configure ksystemlog 4:4.8.4-0ubuntu0.1 <none>
/var/log/dpkg.log:2012-08-22 21:59:07 status unpacked ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:59:07 status half-configured ksystemlog 4:4.8.4-0ubuntu0.1
/var/log/dpkg.log:2012-08-22 21:59:07 status installed ksystemlog 4:4.8.4-0ubuntu0.1

```It seems strange. **I uninstalled Nepomuk File Indexing Controller ( with Nepomuk Backup), not KSystemlog, but Nepomuk (both of them) is according Ubuntu Software Center still installed!! **I do not understand it, but it is probably different problem from that one with missing files.

I wrote everything I remembered.  **I do not know exact time of losing my files, so there are two possibilities of losing my files- after reboot or after suspend, likely after suspend.**

---

### Post by matt_symes on 2012-08-25
Hi

Sorry for the late reply. Been busy.

KSystemlog is installed according to dpkg, apt and the log files.

Open a terminal and type

```
/usr/bin/ksystemlog
```

Post the output of that entire command and its text into your next post.

Kind regards

---

### Post by migrena6 on 2012-08-26
I appologoize for this solutionm- my intention was to resolve this problem, but I did not have time, because I need my comp for school. So I formatted HDD, created special partitition for root and installed Mageia Linux 2.

I have had constantly problems (technical, not practical) with Ubuntu or Mint since Ubuntu 11.04 but I was very satisfied with Ubuntu 10.04 (a little old).
I will  return to using Ubuntu when I get better and newer machine.

Sorry, but when I saw your post I have already had formated HDD with new Linux distribution. 

Regards

Michal

---

