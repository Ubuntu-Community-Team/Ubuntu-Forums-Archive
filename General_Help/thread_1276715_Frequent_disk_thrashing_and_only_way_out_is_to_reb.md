---
title: "Frequent disk thrashing and only way out is to reboot"
date: 2009-09-27
forum: General Help
---

### Post by EliteLegend on 2009-09-27
Hi,

I am not sure if this is a known bug but I'm facing some really serious problems now and then. All of a sudden, the disk activity boosts to a level where I see the disk activity light indicator continuously. Keyboard and mouse die (very slow response). I can't even understand what is being done with the disk. 

I installed VirtualBox a few weeks back and was facing this problem so I thought it was a problem with my VirtualBox build so I stopped using it. But now, even without it, I still keep facing the same problem. 

Here's my pstree if it helps:

```

init&#9472;&#9516;&#9472;NetworkManager
     &#9500;&#9472;acpid
     &#9500;&#9472;adb&#9472;&#9472;&#9472;{adb}
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-autoipd&#9472;&#9472;&#9472;avahi-autoipd&#9472;&#9472;&#9472;avahi-autoipd.a
     &#9500;&#9472;3*[avahi-autoipd&#9472;&#9472;&#9472;avahi-autoipd]
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bluetoothd
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;chrome&#9472;&#9516;&#9472;2*[chrome]
     &#9474;        &#9500;&#9472;chrome&#9472;&#9472;&#9472;3*[{chrome}]
     &#9474;        &#9500;&#9472;chrome-sandbox
     &#9474;        &#9492;&#9472;16*[{chrome}]
     &#9500;&#9472;chrome&#9472;&#9516;&#9472;4*[chrome&#9472;&#9472;&#9472;2*[{chrome}]]
     &#9474;        &#9492;&#9472;chrome&#9472;&#9472;&#9472;{chrome}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;63*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;dhclient
     &#9500;&#9472;dhclient3
     &#9500;&#9472;dnsmasq
     &#9500;&#9472;dropbox&#9472;&#9472;&#9472;4*[{dropbox}]
     &#9500;&#9472;eclipse&#9472;&#9472;&#9472;19*[{eclipse}]
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;2*[{evolution-data-}]
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-excha}
     &#9500;&#9472;fast-user-switc
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;bluetooth-apple
     &#9474;                             &#9500;&#9472;evolution-alarm&#9472;&#9472;&#9472;{evolution-alarm}
     &#9474;                             &#9500;&#9472;gnome-panel
     &#9474;                             &#9500;&#9472;metacity
     &#9474;                             &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9474;                             &#9500;&#9472;nm-applet
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;ssh-agent
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfs-gphoto2-vo
     &#9500;&#9472;gvfs-hal-volume&#9472;&#9472;&#9472;{gvfs-hal-volume}
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-http
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-gene
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9500;&#9472;hald-addon-rfki
     &#9474;                    &#9492;&#9472;hald-addon-stor
     &#9500;&#9472;indicator-apple
     &#9500;&#9472;klogd
     &#9500;&#9472;mixer_applet2&#9472;&#9472;&#9472;{mixer_applet2}
     &#9500;&#9472;mysqld_safe&#9472;&#9472;&#9472;mysqld&#9472;&#9472;&#9472;9*[{mysqld}]
     &#9500;&#9472;nm-system-setti
     &#9500;&#9472;notify-osd
     &#9500;&#9472;pulseaudio&#9472;&#9516;&#9472;gconf-helper
     &#9474;            &#9492;&#9472;2*[{pulseaudio}]
     &#9500;&#9472;sshd
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-service-
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;trashapplet
     &#9500;&#9472;udevd
     &#9500;&#9472;uml_switch
     &#9500;&#9472;winbindd&#9472;&#9472;&#9472;winbindd
     &#9492;&#9472;wpa_supplicant


```

Any thoughts on how I should troubleshoot this problem please?

Thanks

---

### Post by tgalati4 on 2009-09-27
Post the output of:

free

If you don't have enough RAM, then swap will be slow, with lots of disk activity.

---

### Post by doas777 on 2009-09-27
try iotop for determining which process is responsible for the disk activity

---

### Post by EliteLegend on 2009-09-27
> **tgalati4 said:**
> Post the output of:

free

If you don't have enough RAM, then swap will be slow, with lots of disk activity.

Thanks. My system has about 2GB RAM so I doubt if its a RAM problem. Here's the output:

```

             total       used       free     shared    buffers     cached
Mem:       2053532    1993620      59912          0      13748     512760
-/+ buffers/cache:    1467112     586420
Swap:            0          0          0

```

> **doas777 said:**
> try iotop for determining which process is responsible for the disk activity

The problem is that when the io activity starts, my entire system hangs. Everything works but works slowly. If I move the mouse, it reflects the activity after 3 minutes or so. So, if I have to type something on the keyboard, I am not even sure if it will allow me to do that... Is there any other way that you suggest?

Thanks

---

### Post by doas777 on 2009-09-27
> **EliteLegend said:**
> Thanks. My system has about 2GB RAM so I doubt if its a RAM problem. Here's the output:

```

             total       used       free     shared    buffers     cached
Mem:       2053532    1993620      59912          0      13748     512760
-/+ buffers/cache:    1467112     586420
Swap:            0          0          0

```

The problem is that when the io activity starts, my entire system hangs. Everything works but works slowly. If I move the mouse, it reflects the activity after 3 minutes or so. So, if I have to type something on the keyboard, I am not even sure if it will allow me to do that... Is there any other way that you suggest?

Thanks
then just keep it going and wait and see. how intermittent is the issue?

---

### Post by EliteLegend on 2009-09-27
It was occurring once every 4-5 days but now its gone up to at least once everyday... If I am not mistaken, I think it happens mostly after I bring back my system from standby... Don't know if this has anything to with it but thought of mentioning it...

---

### Post by foobic on 2009-09-27
> **EliteLegend said:**
> ```

             total       used       free     shared    buffers     cached
Mem:       2053532    1993620      59912          0      13748     512760
-/+ buffers/cache:    1467112     586420
Swap:            0          0          0

```
I've seen something similar a couple of times, and with very similar memory usage (2GB, no swap - SSD?). Seems to happen as the memory gets filled up, even with lots of buffer and cache usage that should be available. For me, kswapd0 was hyperactive when it happened, even though I had no swap partition.

Testing now with a 1GB swap partition...

FYI, Ctrl-Alt-Backspace to kill your X session (or the alternative Ubuntu key-combo that always escapes my memory) may be a gentler way to get out of it.

---

### Post by EliteLegend on 2009-09-27
Hmm... that's really strange... I have a 6 GB swap partition and am not sure why it shows as 0! I checked:

```

legend7@laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ea2a34f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3274    26298373+   7  HPFS/NTFS
/dev/sda2            9420        9729     2490075   82  Linux swap / Solaris
/dev/sda3            3275        9419    49359712+  83  Linux

Partition table entries are not in disk order


```

And /etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=14b03976-7dc0-4980-a655-56d5df0bcd45 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cd125fe6-25ee-44b1-9094-b38a193490db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

And df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              47G   42G  2.8G  94% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  224K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  164K 1003M   1% /dev
tmpfs                1003M  224K 1003M   1% /dev/shm
lrm                  1003M  2.2M 1001M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sr0              699M  699M     0 100% /media/cdrom0

```

Is something obviously wrong and I'm not seeing it?

Thanks

---

### Post by lswb on 2009-09-27
I believe this is your problem:
/dev/sda3              47G   42G  2.8G  94% /

Try to free some space on your / partition.

---

### Post by foobic on 2009-09-27
> **EliteLegend said:**
> 
```
UUID=cd125fe6-25ee-44b1-9094-b38a193490db none    swap    sw    0   0
```
Strange. IDK why free shows no swap. Perhaps try:
```
ls -l /dev/disk/by-uuid |grep cd125fe6-25ee-44b1-9094-b38a193490db
``` (should be a symlink to sda2)

---

### Post by EliteLegend on 2009-09-28
Thanks. I guess it will show me a change when I restart the system. 

@lswb: Sure. I will free up a few gigs now...

---

### Post by tgalati4 on 2009-09-28
sudo swapon /dev/sda6
free

Definitely free up space on your root partition.  You should always have 10% free space or more, otherwise bad things will happen.

---

### Post by EliteLegend on 2009-10-02
Thank You and sorry for the delay. I finally got some time to erase a bunch of things. Right now, it is:


```

$ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              47G   39G  5.4G  88% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  244K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  164K 1003M   1% /dev
tmpfs                1003M  8.6M  995M   1% /dev/shm
lrm                  1003M  2.2M 1001M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sr0              699M  699M     0 100% /media/cdrom0


```

and

```

$ free
             total       used       free     shared    buffers     cached
Mem:       2053532    1451248     602284          0      22160     398540
-/+ buffers/cache:    1030548    1022984
Swap:      2490064          0    2490064


```

Thanks tgalati4 for your suggestion. Just a final one: Do I have to add that to a file to make it use swap every time I restart my machine or does it work anyways?

---

### Post by napzilla on 2009-10-06
Hey! I'm having this issue too! It's the same thing for me, I'll go away for a little while and the system will turn off the display and such, and then when I sit down to use it, the memory and CPU usage is through the roof! Here's the output from "free"
```

             total       used       free     shared    buffers     cached
Mem:       2060740    2000832      59908          0       5452     106740
-/+ buffers/cache:    1888640     172100
Swap:      3028212    1131996    1896216

```

When I ran top, I found that it was hald that was using all the resources--99% of the CPU and 65% of the memory. I thought that perhaps it was a graphics driver issue (I got that warning on upgrade), but I'm using the ati driver and I don't use compiz. Does my computer have an unclean spirit?

---

### Post by sandy8925 on 2009-10-06
When it goes on standby I think it saves important stuff to swap. The going slow and lots of hard disk activity happens for any system that goes into standby. Maybe it's going into hibernation and not standby ?

---

### Post by cc123-1 on 2011-06-03
This problem is not a lack of disk space as I have 318GB free with 4GB of main memory and also have the identical problem. If my computer, a Dell laptop, sits idle for more than a few hours, the problem occurs. This disks thrash continuously. The only thing that seems to operate correctly, sometimes, is that I can move windows around the screen. Rebooting is always a cure. Sometimes walking away for, maybe, half an hour works.

By the way, I have my computer set to not hibernate or standby.

---

