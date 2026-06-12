---
title: "Failure to Resume from Suspend on Aspire One KAV60. Ub11.10"
date: 2012-03-22
forum: General Help
---

### Post by Jackalux on 2012-03-22
Hi, Noob here.

First ever Linux install; Ubuntu 11.10.  As with many others, I have failure to resume from closed lid (That's a 'Suspend', right?) on my Acer Aspire One KAV60 (D250).  On opening lid, screen remains blank and only option is forced boot (pressing and holding power button until killed).  I've tried: waiting, various key presses including Enter, CtrlAltDel, Esc etc; single presses on the power button, mousepad use, etc.  Nothing works...

I've searched various fora for answers and unsure how answers for previous versions and other machines apply to 11.10.  I'm a bit lost and frustrated.  I'd have joined this to another thread but none were perfect match.  [Here's a thread that was too hard for me to follow,]("http://ubuntuforums.org/showthread.php?p=9261807") linked from another KAV60 user.  Perhaps I just need talked through it? Or perhaps it's now obsolete under 11.10?

Here is some info that you might want (which doesn't mean I know what I'm doing! I've just seen it asked for elsewhere):

```
free -m
             total       used       free     shared    buffers     cached
Mem:           992        920         71          0         17        438
-/+ buffers/cache:        464        527
Swap:         1011        172        839
``````
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             112G   38G   69G  36% /
udev                  487M  4.0K  487M   1% /dev
tmpfs                 199M  812K  198M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  497M  712K  496M   1% /run/shm
/home/myself/.Private
                      112G   38G   69G  36% /home/myself
``````
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e8afb645-8fe3-4c84-9c90-38dfb23b911e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=7d4d075f-0c36-429d-b646-c3f3e7cd093c none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```Should the second UUID line have a hash at the start? (Guessing)

Should I be using the Netbook remix that I've read about?  Or am I by default?
I'd rather not mess around for ages as I installed Ubuntu to ditch M$ Windoze and just start working.

Thanks for your time and patience.
Jackalux

---

### Post by nothingspecial on 2012-03-23
*Thread moved to **General Help**.*

---

### Post by Toz on 2012-03-23
Can you post back the contents of your /var/log/pm-suspend.log file so that we can see if the computer is suspending or hibernating when you close the lid. 

> #UUID=7d4d075f-0c36-429d-b646-c3f3e7cd093c none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
If it is hibernate, note that hibernation on an encrypted swap partition is not currently supported (working).

As for the script you reference, there is an easier to implement version located here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug"). In a nutshell:

1. Open a terminal window and enter the following command to create the necessary file:
```
gksudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
```

2. Copy/paste the following information into the window that opens:
```

#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)

VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac

```
...and save the file

3. Make that file executable:
```
sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

Then try again. Remember, that suspend/hibernate information is logged to the file /var/log/pm-suspend.log.

---

### Post by Jackalux on 2012-03-23
> **Toz said:**
> Can you post back the contents of your /var/log/pm-suspend.log file so that we can see if the computer is suspending or hibernating when you close the lid. 


If it is hibernate, note that hibernation on an encrypted swap partition is not currently supported (working).

As for the script you reference, there is an easier to implement version located here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug).

Thanks for the reply; I do have an encrypted partition.  Would a repartition with a separate encrypted home partition and unencrypted ubuntu one work better?  If so, what size does Ubuntu need?

/var/log/pm-suspend.log is empty.
/var/log/pm-suspend.log.1 has some old data, prior to most recent lid closure attempts.  There are no other pm-suspend.log file versions
I'll try again now and see if anything changes in those files.

Will see if anything changed...
Will also try a menu chosen suspend
Again check if anything changes in log file(s)
Then will check forum for any further messages (about 10 mins) and then try the solution you mentioned.

Back in a bit

---

### Post by Jackalux on 2012-03-23
Okay... a little weird.

Suspend from menu works fine.  Results in successful suspend, flashing orange power button, resume on power button press and data entered into formerly empty pm-suspend.log

Lid closure does not suspend, but does black screen as lid closes.  Does not go into any suspension mode; merely unpowered screen.  No entry made to rm-suspend.log

Nor does it seem to change file size of pm-powersave.log (entries are undated so can't tell when events occur)

It is possible that I've never attempted a menu initiated Suspend, for fear that it would crash system, as hibernate did.  I now know the difference, and would obviously like more energy efficient hibernate function if possible.

FYI: pm-suspend.log
```
Initial commandline parameters: 
Fri Mar 23 12:37:20 GMT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux myself-AspireOne 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
uvcvideo               67271  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  1 uvcvideo
ath5k                 145100  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
psmouse                73673  0 
serio_raw              12990  0 
mac80211              393421  1 ath5k
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  3 ath5k,ath,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  509519  3 
atl1c                  36638  0 
ahci                   21634  2 
libahci                25727  1 ahci
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
             total       used       free     shared    buffers     cached
Mem:       1016252     640872     375380          0      48436     339168
-/+ buffers/cache:     253268     762984
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Mar 23 12:37:26 GMT 2012: performing suspend
Fri Mar 23 12:37:38 GMT 2012: Awake.
Fri Mar 23 12:37:38 GMT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Mar 23 12:37:42 GMT 2012: Finished.
Initial commandline parameters: 
Fri Mar 23 12:44:49 GMT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux myself-AspireOne 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
arc4                   12473  2 
uvcvideo               67271  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  1 uvcvideo
ath5k                 145100  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19387  1 ath5k
psmouse                73673  0 
serio_raw              12990  0 
mac80211              393421  1 ath5k
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  3 ath5k,ath,mac80211
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  509519  3 
atl1c                  36638  0 
ahci                   21634  2 
libahci                25727  1 ahci
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
             total       used       free     shared    buffers     cached
Mem:       1016252     648452     367800          0      50252     352764
-/+ buffers/cache:     245436     770816
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Mar 23 12:44:54 GMT 2012: performing suspend
Fri Mar 23 12:45:24 GMT 2012: Awake.
Fri Mar 23 12:45:24 GMT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Mar 23 12:45:28 GMT 2012: Finished.
```

I'm tempted to leave system alone, except that I would like hibernate available.  What do you think, including to repartitioning advice I asked before, so that swap is non-encrypted?  Is it easy to do this without reinstalling?  I've heard it makes Ubuntu upgrades and reinstalls easier and safer, as home directory is separate and additionally more safely shared with XP (I kept this machine dual boot in case I really HAVE to use M$ Losedows)

Cheers again,
Jackalux

---

### Post by Toz on 2012-03-23
Okay. So closing the lid only blanks the screen. The problem is when you open the lid, the screen stays blank. Maybe its the screen brightness. Can you try increasing the screen brightness to see if you get an image back?

Since suspend works, another option would be to set the laptop to suspend on all lid closures.

With respect to hibernate, you would have to re-create your swap file so that it is not encrypted. Personally, I've never done this, but here is a link to a resource that explains how it can be done: [http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155").

---

### Post by Jackalux on 2012-03-23
No Toz, lid opening started working, whereas it wasn't some time before my OP.  I can't work out what happened or changed.  The screen goes black on lid-close and comes back on at lid-open.  It doesn't go into suspend though.  No need for a password (unless I've waited long enough for the power save lockout, I imagine.  I haven't tried leaving it shut for longer than the 10 mins after which screen lock is timed too kick in).  Perhaps I need to do that for a complete test of this.  I wonder if longer inactivity leads to a faulty version of Suspend and it's this that it's not resuming from?  I'll try now.

As a temporary measure, you're right about the menu instigated suspend each time I guess.  It's a bit of a dirty solution but not too onerous.

I need to get on using the system - rather than all my time tinkering - so might revisit that link another time to look into creating a different swap file that allows hibernate to work.

Thanks again for the help; I appreciate your time.

---

### Post by Jackalux on 2012-03-23
OK, so it isn't solved...  I guess that I just hadn't left the lid closed long enough.

What I did:
Closed the lid (without menu initiated Suspend). Went for a walk.  Returned and opened the lid.  Saw a kernel panic report, shown in the attached photo.

The power light is obviously on (solid green) and the caps light is flashing about 4x per second.  Netbook is unresponsive to mousepad, key presses incl Ctrl+Alt+Del.  About to power off and reboot.

Feedback?

---

### Post by Toz on 2012-03-23
Can you replicate this kernel panic? Does it happen every time after x minutes with the lid closed? It will be somewhat of a cumbersome task to try to find some commonality in the crashes, but it would help. 

The panic is related to an "out of memory" condition. 
- How much RAM do you have?
- Are you using a swap partition?
- What programs were running?
- Perhaps running a memtest (from the Live CD) might help to eliminate bad memory.

---

### Post by Jackalux on 2012-03-23
> **Toz said:**
> The panic is related to an "out of memory" condition. 
- How much RAM do you have?
- Are you using a swap partition?
- What programs were running?
- Perhaps running a memtest (from the Live CD) might help to eliminate bad memory.

Thought so from the text dump.

- Got 1GB RAM (or actually 992MB)
- Also 1GB SWAP (or rather 1011MB) (I think those figures are right... free -m results are in my original post if that's the answer. Swap may be encrypted, as either the partition or my Home folder is)
- Banshee, Gedit, possibly Vidalia & TOR (although I may have closed Vid/Tor to simplify)
- Got to prep for gf's birthday tomorrow.  Mem tests next time.

Cheers for your attention Toz.  I'm trying to repeat error now (closed lid, no progs running)

Inabit
J

---

