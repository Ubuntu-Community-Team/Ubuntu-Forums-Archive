---
title: "Laptop disconnects when lid closed."
date: 2011-06-04
forum: General Help
---

### Post by joelstitch on 2011-06-04
I notice that if I close the lip for my laptop the computer disconnects from the internet. I have it set up so when I close the lid the screen goes black but it doesnt suspend or hibernate. I dont have the option to spin down the hard drive or dim display when idle. Any ideas what's wrong?

---

### Post by joelstitch on 2011-06-05
I've searched a lot and still haven't found how to fix the issue.

---

### Post by dFlyer on 2011-06-05
Here is a link I found on a quick google search, don't know if it will help, but I suggest you try the link but search before requesting help. If you search and can't find help than ask.

[http://ubuntuforums.org/showthread.php?t=780081](http://ubuntuforums.org/showthread.php?t=780081)

---

### Post by joelstitch on 2011-06-05
> **dFlyer said:**
> Here is a link I found on a quick google search, don't know if it will help, but I suggest you try the link but search before requesting help. If you search and can't find help than ask.

[http://ubuntuforums.org/showthread.php?t=780081](http://ubuntuforums.org/showthread.php?t=780081)

I already read that and in case you didnt notice there was no real fix on that issue. And in case you didnt read my last post "**I've searched a lot and still haven't found how to fix the issue.**" That topic is from 2008 and no fixed so I decided to start a new one.

---

### Post by joelstitch on 2011-06-05
Also, on the **When laptop lid is closed** I don't have the **Do Nothing** option. I also didn't used to have the Hibernate option and I remember adding it some how but cant remember hoe I did it.

---

### Post by dFlyer on 2011-06-05
How about providing a little information on your laptop if you want the help. Otherwise everyone will be guessing on issues.

---

### Post by joelstitch on 2011-06-05
HP Pavilion dv6629us
Ubuntu 10.04.2 LTS
Gnome 2.30.2
Power Management Options:
   On AC Power > When Laptop Lid is Closed > Bank Screen
   On Battery Power > When Laptop Lid is Closed > Bank Screen

---

### Post by dFlyer on 2011-06-05
I don't have an answer to your linux problem, but a search on google, shows that even this computer with windows has had this problem. Are you dual booting? If so are you having the problem with the dual boot or were you able to find a fix?

---

### Post by joelstitch on 2011-06-05
I dual boot fine. The problem started a few days ago and I don't know why, I cant see why would it be the dual booting because it used to work fine.

---

### Post by Toz on 2011-06-05
It's almost like it starts the suspend process but backs out (normal suspend process will disable networking and re-enable one resume). A few things to check:

1. Since you said that it started a few days ago, what updates have you applied in the last week? You can get a history of updates from **/var/log/apt/history.log**

2. Closing the lid should fire off the lid.sh script. Can you search for this file:```
locate lid.sh
```and post back the results.

3. If it is starting the suspend process, something should be logged to **/var/log/pm-suspend**. Is there anything logged when you close the lid?

4. Can you also post back the contents of **/etc/default/acpi-support**. There are some settings there that can disable lid sleep and suspend functionality.

---

### Post by joelstitch on 2011-06-05
> **Toz said:**
> It's almost like it starts the suspend process but backs out (normal suspend process will disable networking and re-enable one resume). A few things to check:

1. Since you said that it started a few days ago, what updates have you applied in the last week? You can get a history of updates from **/var/log/apt/history.log**

2. Closing the lid should fire off the lid.sh script. Can you search for this file:```
locate lid.sh
```and post back the results.

3. If it is starting the suspend process, something should be logged to **/var/log/pm-suspend**. Is there anything logged when you close the lid?

4. Can you also post back the contents of **/etc/default/acpi-support**. There are some settings there that can disable lid sleep and suspend functionality.

**History.log**
```

Start-Date: 2011-06-01  21:53:38
Install: network-manager (0.8-0ubuntu3.2), network-manager-gnome (0.8-0ubuntu3)
End-Date: 2011-06-01  21:54:07

Start-Date: 2011-06-01  23:49:56
Install: vidalia (0.2.12-1~lucid1)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2011-06-01  23:49:56

Start-Date: 2011-06-01  23:50:17
Install: vidalia (0.2.12-1~lucid1)
End-Date: 2011-06-01  23:50:42

Start-Date: 2011-06-02  01:13:58
Remove: tor-geoipdb (0.2.1.30-1~lucid+1), tor (0.2.1.30-1~lucid+1)
End-Date: 2011-06-02  01:14:08

Start-Date: 2011-06-02  01:26:19
Install: tor-geoipdb (0.2.1.30-1~lucid+1), tor (0.2.1.30-1~lucid+1)
End-Date: 2011-06-02  01:26:33

Start-Date: 2011-06-02  01:33:36
Install: privoxy (3.0.15-3)
End-Date: 2011-06-02  01:33:48

Start-Date: 2011-06-02  01:43:00
Remove: vidalia (0.2.12-1~lucid1)
End-Date: 2011-06-02  01:43:15

Start-Date: 2011-06-02  10:14:58
Install: vidalia (0.2.12-1~lucid1)
End-Date: 2011-06-02  10:15:24

Start-Date: 2011-06-02  12:37:20
Upgrade: libpam0g (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.3), bind9-host (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), libpam-modules (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.3), dnsutils (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), wine1.3 (1.3.19-0ubuntu1~lucid1~ppa1, 1.3.21-0ubuntu1~lucid1~ppa1), libpam-runtime (1.1.1-2ubuntu5, 1.1.1-2ubuntu5.3), libdns64 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), libisccc60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), liblwres60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), libbind9-60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), wine (1.2.3-0ubuntu1~ppa1, 1.2.3-0ubuntu1~ppa2~lucid1), libisccfg60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2), libisc60 (9.7.0.dfsg.P1-1ubuntu0.1, 9.7.0.dfsg.P1-1ubuntu0.2)
End-Date: 2011-06-02  12:38:43

Start-Date: 2011-06-02  16:01:24
Remove: firefox-globalmenu (4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1)
End-Date: 2011-06-02  16:01:43

Start-Date: 2011-06-02  16:07:46
Install: firefox-globalmenu (4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1)
End-Date: 2011-06-02  16:08:05

Start-Date: 2011-06-02  16:13:23
Remove: privoxy (3.0.15-3)
End-Date: 2011-06-02  16:13:31

Start-Date: 2011-06-02  16:46:49
Install: privoxy (3.0.15-3)
End-Date: 2011-06-02  16:47:08

Start-Date: 2011-06-02  16:56:58
Install: menu (2.1.43ubuntu1), bum (2.5.2-1)
End-Date: 2011-06-02  16:57:17

Start-Date: 2011-06-02  16:59:01
Remove: polipo (1.0.4.1-1.1~lucid1)
End-Date: 2011-06-02  16:59:07

Start-Date: 2011-06-02  17:13:21
Install: polipo (1.0.4.1-1.1~lucid1)
End-Date: 2011-06-02  17:13:37

Start-Date: 2011-06-02  17:15:49
End-Date: 2011-06-02  17:16:01

Start-Date: 2011-06-02  17:23:42
Remove: polipo (1.0.4.1-1.1~lucid1), privoxy (3.0.15-3)
End-Date: 2011-06-02  17:23:47

Start-Date: 2011-06-02  17:24:42
Install: polipo (1.0.4.1-1.1~lucid1), privoxy (3.0.15-3)
End-Date: 2011-06-02  17:24:55

Start-Date: 2011-06-02  17:25:14
Purge: privoxy (3.0.15-3)
End-Date: 2011-06-02  17:25:18

Start-Date: 2011-06-02  17:25:30
Install: privoxy (3.0.15-3)
End-Date: 2011-06-02  17:25:40

Start-Date: 2011-06-02  17:25:55
Purge: polipo (1.0.4.1-1.1~lucid1)
End-Date: 2011-06-02  17:26:01

Start-Date: 2011-06-02  17:26:18
Install: polipo (1.0.4.1-1.1~lucid1)
End-Date: 2011-06-02  17:26:26

Start-Date: 2011-06-02  17:27:11
Purge: vidalia (0.2.12-1~lucid1)
End-Date: 2011-06-02  17:27:29

Start-Date: 2011-06-02  17:30:08
Remove: tor-geoipdb (0.2.1.30-1~lucid+1)
Purge: polipo (1.0.4.1-1.1~lucid1), tor (0.2.1.30-1~lucid+1), privoxy (3.0.15-3)
End-Date: 2011-06-02  17:30:21

Start-Date: 2011-06-02  17:31:43
Install: polipo (1.0.4.1-1.1~lucid1), tor-geoipdb (0.2.1.30-1~lucid+1), vidalia (0.2.12-1~lucid1), tor (0.2.1.30-1~lucid+1), privoxy (3.0.15-3)

Start-Date: 2011-06-03  16:11:30
Purge: privoxy (3.0.15-3)
End-Date: 2011-06-03  16:11:42

Start-Date: 2011-06-04  10:01:33
Remove: wicd (1.7.0+ds1-2)
End-Date: 2011-06-04  10:01:39

Start-Date: 2011-06-04  11:00:24
Install: ubuntu-tweak (0.5.14-1~lucid1)
End-Date: 2011-06-04  11:00:48

Start-Date: 2011-06-04  11:06:05
Install: python-utidylib (0.2-3.2ubuntu2), python-gtkmozembed (2.25.3-4.1ubuntu4), libtidy-0.99-0 (20091223cvs-1), python-feedparser (4.1-14), screenlets (0.1.2-7ubuntu1)
End-Date: 2011-06-04  11:06:35

Start-Date: 2011-06-05  19:30:40
Upgrade: ttf-symbol-replacement-wine1.3 (1.3.19-0ubuntu1~lucid1~ppa1, 1.3.21-0ubuntu1~lucid1~ppa1), dolphin-emu (2.0+svn7564-0ubuntu1~lucid, 2.0+svn7583-0ubuntu1~lucid)
End-Date: 2011-06-05  19:30:56
```

**lid.sh**
```
#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"        
        . /usr/share/acpi-support/screenblank
    fi
    done
else
    for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    if [ x"$XAUTHORITY" != x"" ]; then
        export DISPLAY=":$displaynum"
        grep -q off-line /proc/acpi/ac_adapter/*/state
        if [ $? = 1 ]
        then
        if pidof xscreensaver > /dev/null; then 
            su $user -c "xscreensaver-command -unthrottle"
        fi
        fi
        if [ x$RADEON_LIGHT = xtrue ]; then
        [ -x /usr/sbin/radeontool ] && radeontool light on
        fi
        if [ `pidof xscreensaver` ]; then
        su $user -c "xscreensaver-command -deactivate"
        fi
        su $user -c "xset dpms force on"
    fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post
```

[B]pm-suspend
[/B]```
Initial commandline parameters: 
Thu Jun  2 12:49:57 CDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
arc4                    1153  2 
b43                   163556  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
mac80211              205402  1 b43
nvidia               9961216  40 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
serio_raw               3978  0 
ricoh_mmc               2923  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
k8temp                  3152  0 
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ssb                    38934  1 b43
ahci                   32360  2 
ieee1394               81181  1 ohci1394
forcedeth              49556  0 
pata_amd                8766  0 
             total       used       free     shared    buffers     cached
Mem:       3031560    1848100    1183460          0     111924    1045556
-/+ buffers/cache:     690620    2340940
Swap:      4207608          0    4207608
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Thu Jun  2 12:50:02 CDT 2011: performing hibernate
Thu Jun  2 15:15:10 CDT 2011: Awake.
Thu Jun  2 15:15:12 CDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.73 -> dest=:1.72 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/91wicd thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Thu Jun  2 15:16:19 CDT 2011: Finished.
Initial commandline parameters: 
Fri Jun  3 14:10:07 CDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8933  0 
fat                    47767  1 vfat
aes_i586                7268  0 
aes_generic            26863  1 aes_i586
xts                     2031  0 
gf128mul                8015  1 xts
dm_crypt               11331  0 
usbhid                 36110  0 
hid                    67096  1 usbhid
usb_storage            39841  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
arc4                    1153  2 
snd_hda_intel          22069  4 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  3 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   163556  0 
joydev                  8740  0 
snd                    54244  18 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205402  1 b43
fbcon                  35102  71 
tileblit                1999  1 fbcon
nvidia               9961216  40 
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
k8temp                  3152  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_nforce2             5199  0 
agpgart                31724  1 nvidia
vga16fb                11385  1 
vgastate                8961  1 vga16fb
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ssb                    38934  1 b43
forcedeth              49556  0 
ieee1394               81181  1 ohci1394
ahci                   32360  2 
pata_amd                8766  0 
             total       used       free     shared    buffers     cached
Mem:       3031560    2935420      96140          0      84408    2101204
-/+ buffers/cache:     749808    2281752
Swap:      4207608          0    4207608
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jun  3 14:10:12 CDT 2011: performing hibernate
Fri Jun  3 14:53:54 CDT 2011: Awake.
Fri Jun  3 14:53:56 CDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.91 -> dest=:1.90 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/91wicd thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Fri Jun  3 14:54:55 CDT 2011: Finished.
Initial commandline parameters: 
Fri Jun  3 20:58:39 CDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9961216  40 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
agpgart                31724  1 nvidia
b43                   163556  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      7028  0 
joydev                  8740  0 
sdhci_pci               5470  0 
vga16fb                11385  1 
parport                32635  2 ppdev,lp
i2c_nforce2             5199  0 
video                  17375  0 
ricoh_mmc               2923  0 
sdhci                  15462  1 sdhci_pci
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
output                  1871  1 video
soundcore               6620  1 snd
k8temp                  3152  0 
mac80211              205402  1 b43
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
forcedeth              49556  0 
pata_amd                8766  0 
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       3031560    2268724     762836          0      62716    1463064
-/+ buffers/cache:     742944    2288616
Swap:      4207608          0    4207608
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd suspend suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Jun  3 20:58:44 CDT 2011: performing suspend
Fri Jun  3 21:39:14 CDT 2011: Awake.
Fri Jun  3 21:39:14 CDT 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.85 -> dest=:1.84 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/91wicd resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Fri Jun  3 21:39:19 CDT 2011: Finished.
Initial commandline parameters: 
Fri Jun  3 21:51:33 CDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9961216  44 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
agpgart                31724  1 nvidia
b43                   163556  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      7028  0 
joydev                  8740  0 
sdhci_pci               5470  0 
vga16fb                11385  1 
parport                32635  2 ppdev,lp
i2c_nforce2             5199  0 
video                  17375  0 
ricoh_mmc               2923  0 
sdhci                  15462  1 sdhci_pci
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
output                  1871  1 video
soundcore               6620  1 snd
k8temp                  3152  0 
mac80211              205402  1 b43
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
forcedeth              49556  0 
pata_amd                8766  0 
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       3031560    2237568     793992          0      64236    1464436
-/+ buffers/cache:     708896    2322664
Swap:      4207608          0    4207608
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jun  3 21:51:38 CDT 2011: performing hibernate
Fri Jun  3 21:57:54 CDT 2011: Awake.
Fri Jun  3 21:57:56 CDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.109 -> dest=:1.108 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/91wicd thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Fri Jun  3 21:59:14 CDT 2011: Finished.
Initial commandline parameters: 
Fri Jun  3 22:05:16 CDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9961216  44 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
agpgart                31724  1 nvidia
b43                   163556  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      7028  0 
joydev                  8740  0 
sdhci_pci               5470  0 
vga16fb                11385  1 
parport                32635  2 ppdev,lp
i2c_nforce2             5199  0 
video                  17375  0 
ricoh_mmc               2923  0 
sdhci                  15462  1 sdhci_pci
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
output                  1871  1 video
soundcore               6620  1 snd
k8temp                  3152  0 
mac80211              205402  1 b43
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
forcedeth              49556  0 
pata_amd                8766  0 
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       3031560     688264    2343296          0      20948     163792
-/+ buffers/cache:     503524    2528036
Swap:      4207608     388400    3819208
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Fri Jun  3 22:05:22 CDT 2011: performing hibernate
Sat Jun  4 09:03:19 CDT 2011: Awake.
Sat Jun  4 09:03:19 CDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.137 -> dest=:1.136 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/91wicd thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Sat Jun  4 09:03:40 CDT 2011: Finished.
Initial commandline parameters: 
Sat Jun  4 09:17:11 CDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux pag-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6751  0 
vboxnetflt             18785  0 
vboxdrv               214714  2 vboxnetadp,vboxnetflt
snd_hda_codec_conexant    22705  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nvidia               9961216  44 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
agpgart                31724  1 nvidia
b43                   163556  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      7028  0 
joydev                  8740  0 
sdhci_pci               5470  0 
vga16fb                11385  1 
parport                32635  2 ppdev,lp
i2c_nforce2             5199  0 
video                  17375  0 
ricoh_mmc               2923  0 
sdhci                  15462  1 sdhci_pci
snd                    54244  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
output                  1871  1 video
soundcore               6620  1 snd
k8temp                  3152  0 
mac80211              205402  1 b43
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126144  2 b43,mac80211
led_class               2864  2 b43,sdhci
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ssb                    38934  1 b43
forcedeth              49556  0 
pata_amd                8766  0 
ahci                   32360  2 
             total       used       free     shared    buffers     cached
Mem:       3031560     919316    2112244          0      30080     361272
-/+ buffers/cache:     527964    2503596
Swap:      4207608     303912    3903696
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/91wicd suspend suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Sat Jun  4 09:17:15 CDT 2011: performing suspend
Sat Jun  4 09:31:55 CDT 2011: Awake.
Sat Jun  4 09:31:55 CDT 2011: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend:success.
/usr/lib/pm-utils/sleep.d/99video resume suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:success.
/usr/lib/pm-utils/sleep.d/95packagekit resume suspend:method return sender=:1.159 -> dest=:1.158 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend:success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:success.
/usr/lib/pm-utils/sleep.d/91wicd resume suspend:success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend:not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:success.
/etc/pm/sleep.d/10_grub-common resume suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend:success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend:success.
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:success.
Sat Jun  4 09:32:00 CDT 2011: Finished.
```

[B]acpi-support
[/B]```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
```

So I fugured out how to add the **What to do in laptop lid closed** Do Nothing option and now when I close the lid the computer screen still goes blank but it doesnt disconnects the wifi.

---

