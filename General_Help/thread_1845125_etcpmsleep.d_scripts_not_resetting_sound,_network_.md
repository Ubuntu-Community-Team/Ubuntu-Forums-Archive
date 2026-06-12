---
title: "/etc/pm/sleep.d scripts not resetting sound, network manager"
date: 2011-09-16
forum: General Help
---

### Post by iconoclast hero on 2011-09-16
xubuntu 10.04 on a Thinkpad T20:  It goes into hibernate when the lid is closed.  Upon resume|thaw, it won't play sound and the networking is dead.  After doing a little digging I made the following script for sound:
```
thinkpadt20:/etc/pm/sleep.d$ cat 30_alsa-force-reload~
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload
                ;;
        *) exit $NA
                ;;
esac

```

then doing a bit more digging I changed the script to include the initial #!/bin/bash and changed the exit $ line content and location:

```
thinkpadt20:/etc/pm/sleep.d$ cat 30_alsa-force-reload
#!/bin/bash

## from http://ubuntuforums.org/showthread.php?t=1484156 9/16/011
case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                /sbin/alsa force-reload
                ;;
        *)
                ;;
esac
exit $?

```

now upon resume, the manual execution of ```
sudo /sbin/alsa force-reload
``` resets the sound driver, but this script doesn't seem to do it automatically as I want.

For the networking, I used the following script I found:
```
thinkpadt20:/etc/pm/sleep.d$ cat 20_pkill-NetworkManager
#!/bin/sh

## from http://ubuntuforums.org/showthread.php?t=1522146 9/15/011
case "$1" in
resume|thaw)
pkill NetworkManager
;;
suspend|hibernate)
# Do nothing
;;
esac

```
this script does not have the exit $ clause and uses /bin/sh and after digging up the url for this, I see I missed the one for lucid so I tried that:

```

thinkpadt20:/etc/pm/sleep.d$ cat 20_network-manager_restart
#!/bin/sh

## http://ubuntuforums.org/showthread.php?t=1522146

case "$1" in
        resume|thaw)
                service network-manager restart
                ;;
        suspend|hibernate)
                # Do nothing
                ;;
esac

```
and after just hibernating that did not work although, again, manually executing ```
sudo service network-manager restart
``` did as does```
sudo ifconfig eth0 down
sudo ifconfig eth0 up 
``` (though combining the two on the same line with '&&' doesn't seem to).

Here is my /etc/pm/sleep.d:```
thinkpadt20:/etc/pm/sleep.d$ ll
total 32
drwxr-xr-x 2 root root 4096 2011-09-16 10:32 ./
drwxr-xr-x 5 root root 4096 2011-02-11 08:13 ../
-rwxr-xr-x 1 root root  210 2011-01-20 12:28 10_grub-common*
-rwxr-xr-x 1 root root  682 2011-01-10 12:54 10_unattended-upgrades-hibernate*
-rwxr-xr-x 1 root root  245 2011-09-16 10:28 20_network-manager_restart*
-r--r--r-- 1 root root  154 2011-09-16 10:26 20_pkill-NetworkManager
-rwxr-xr-x 1 root root  589 2011-09-16 01:31 30_alsa-force-reload*
-rw-r--r-- 1 root root  240 2011-09-16 10:32 30_alsa-force-reload~
lrwxrwxrwx 1 root root   34 2011-07-03 10:05 action_wpa -> ../../wpa_supplicant/action_wpa.sh*

```

I don't know why these commands work when manually executed but do not work upon resume|thaw.

---

### Post by iconoclast hero on 2011-09-17
Also wondering if there is anyway to use the ifconfig eth0 down/up commands instead of the service network-manager restart which I'm not sure works the first time 100% of the time, i.e. it seemed like I had to run it twice to get the desired effect.

---

### Post by iconoclast hero on 2011-09-21
bump

---

### Post by iconoclast hero on 2011-09-21
bump

---

### Post by iconoclast hero on 2011-09-26
Ok, no help on this is forthcoming, but perhaps someone could tell me how to get something added to the script that would tell me if it is being run on resume/thaw...  Ideally like popping a window up in the display or something else noticeable.

---

### Post by matt_symes on 2011-09-26
Hi

To make sure it is running correctly, create a file using touch.

```
touch /file_running_correctly
```

Kind regards

---

### Post by iconoclast hero on 2011-09-26
Ok, well I found some new things out starting with pm-action...the questions are all the way at the end.
First, when I close the lid, it does not appear that pm-hibernate or pm-suspend get invoked as the logs /var/log/pm-powersave.log and pm-suspend.log are not generated.  It does put it in a suspend state and the little moon icon lights up.  I do not believe that it is a hibernate state because it happens extremely quickly but I have not actually closed the lid and unplugged it and removed the battery.does

Second, neither going to the logout user menu and selecting suspend nor manually executing 
```
sudo pm-suspend
``` or [/CODE]sudo pm-suspend now[/CODE] at CLI actually appear to do anything and does not create the the /var/log/pm-suspend.log.

Third, manually executing ```
sudo pm-hibernate
``` got hung up with some suspended processes I had running in guake which it flashed on a black screen and when I closed it, it stopped with the process 'gam_server' which apparently was a big PITA a while ago.  When I killed it and tried gksudo pm-hibernate with "Run Program" it went to a black screen that stated:
```
[15829.478510] cs46xx: failure waiting for FIFO command to complete
[15853.737007] Power down
``` at which point I turned off the computer and when I brought it back, the sleep.d scripts did work and here is the pm-hibernate.log
```
Initial commandline parameters: 
Mon Sep 26 11:40:01 EDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux thinkpadt20 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GN
U/Linux
Module                  Size  Used by
snd_cs46xx             76457  1 
gameport                9089  2 snd_cs46xx
snd_ac97_codec        100646  1 snd_cs46xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_cs46xx,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  12 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_
device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_cs46xx,snd_pcm
binfmt_misc             6587  1 
savage                 29488  2 
drm                   162377  3 savage
ppdev                   5259  0 
nfsd                  238871  2 
exportfs                3437  1 nfsd
nfs                   265434  2 
pcmcia                 30784  0 
lockd                  64849  2 nfsd,nfs
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
nfs_acl                 2245  2 nfsd,nfs
yenta_socket           20408  2 
softcursor              1189  1 bitblit
rsrc_nonstatic         10015  1 yenta_socket
vga16fb                11385  1 
intel_agp              24375  1 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
vgastate                8961  1 vga16fb
auth_rpcgss            33767  2 nfsd,nfs
i2c_piix4               8335  0 
agpgart                31724  2 drm,intel_agp
psmouse                63677  0 
shpchp                 28835  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
sunrpc                193476  13 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
3c59x                  31839  0 
mii                     4381  1 3c59x
             total       used       free     shared    buffers     cached
Mem:        250644     243028       7616          0       8140      59712
-/+ buffers/cache:     175176      75468
Swap:       732152     118948     613204
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/etc/pm/sleep.d/20_network-manager_restart hibernate hibernate:success.
/etc/pm/sleep.d/30_alsa-force-reload hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Sep 26 11:40:06 EDT 2011: performing hibernate
Mon Sep 26 11:44:06 EDT 2011: Awake.
Mon Sep 26 11:44:08 EDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/30_alsa-force-reload thaw hibernate:lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
Terminating processes: 8984lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
 8984lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
 8984lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
 8984lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/user/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-cs46xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-raw
midi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-cs46xx snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmi
di snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
success.
/etc/pm/sleep.d/20_network-manager_restart thaw hibernate:network-manager start/running, process 9824
success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Mon Sep 26 11:45:05 EDT 2011: Finished.

```

So that is working but I would really prefer to figure out
1) What is causing the computer to suspend when I close the lid, is this something the BIOS is doing?
2) Is there some way to get the computer to run the scripts it is supposed to when I close the lid and then re open it?
3) If the answer to #2 is no, then how do I get either suspending in the terminal or via the logout menu to work?
4) Should I post this in a new thread so that I can change the topic?
5) Are any of those WARNINGS important?

---

