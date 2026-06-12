---
title: "Ubuntu 12.04 LTS Suspend not working FIX"
date: 2012-05-11
forum: General Help
---

### Post by DragonNinja9 on 2012-05-11
Hi! Finally after a  long time of searching and messing around I have figure out a temporary  work around solution until this bug gets patched in future kernel  releases. Please see below:

Use this script only if you have been experiencing issues with resuming from standby/suspend in Ubuntu 12.04 LTS and the screen remains lit but black when you wake your machine.


 Step 1:
 Open up a terminal and create a script file as follows:
```
 sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
```
 Step 2:
 Copy the entire script below into the file you just created and save it:
 ```
#!/bin/sh
#inspired by [http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19](http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19)
#...and [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)
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
   #for bus in $EHCI_BUSES; do
     echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/unbind
 # done
   done
 }
 bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      #for bus in $EHCI_BUSES; do
          echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/bind
      #done
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
   chvt 1
  chvt 7
}
 EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
case "$1" in
    hibernate|suspend)
 unbindDev;;
     resume|thaw)
 bindDev;;
 esac
```
 Step 3:
Give the script run permissions by typing:
```
 sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```
 This script should work or your money back guaranteed (Joking this is  open source project so use at own risk :P ), as it forces the graphic  card to reboot itself using a good old kick from chvt1 and chvt7 commands  which simulate what I used to do manually using Ctrl + Alt + F1 and  Ctrl + Alt + F7 to refresh the GUI.

---

### Post by Derek Karpinski on 2012-05-11
Interesting.  I'll have to give it a shot.

Could you please edit your post and put your script in code tags?

---

### Post by Sionek on 2012-05-22
I almost can't believe it! Suspend has never worked for me on my laptops and this has worked like a charm!

Many thanks bud! :D

---

### Post by Derek Karpinski on 2012-05-22
Same code wrapped in code tags for clarity:

Step 1:
```
gksudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
```

Step 2 (paste this into gedit and save):
```
#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost...0&postcount=19
#...and http://thecodecentral.com/2011/01/18...ot-working-bug
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
    #for bus in $EHCI_BUSES; do
    echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/unbind
    # done
    done
}
bindDev() {
    if [ -s $DEV_LIST ]; then
    while read driver dev; do
        DDIR=$DRIVERS_DIR/${driver}_hcd
        #for bus in $EHCI_BUSES; do
        echo -n $bus > /sys/bus/pci/drivers/ehci_hcd/bind
        #done
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
    chvt 1
    chvt 7
}
EHCI_BUSES="0000:00:1a.0 0000:00:1d.0"
case "$1" in
    hibernate|suspend)
    unbindDev;;
    resume|thaw)
    bindDev;;
esac
```

Step 3:
```
sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

---

### Post by alexpalka23 on 2012-06-10
I honestly can't believe it. I have been having problems with the suspend option on my Asus laptop since i installed Ubuntu onto it. This fixed it completely. You're my freaking hero. I actually made an account on here just to thank you for being the coolest person ever born. 

Thank you! haha

---

### Post by DragonNinja9 on 2012-06-10
Now although I have tested the latest kernel 3.4 ppa release and I must say it does run quite well and fixes some of the major bugs in Ubuntu 12.04 including of course the bug mentioned here regarding standby/suspend, it is still not a release version and I am still using kernel 3.2.0-24-generic release version.
Now since this version many of you probably noticed that the script I have posted before providing a quick fix for this bug no longer works. At least for me it no longer works. If for you it still works then don't touch it. It seems for me however some issues may have been attempted to fix regarding sleep and wake up driver issues. As a result the previous script no longer works, however I have written a simplified version which takes in consideration these fixes and this seems to work like a charm for me.

As previously...
Step 1: Open up a terminal and create a scrip file as follows:

```
sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
```

Step 2: If and only if you have problems with your current script and your machine refuses to sleep or wake up on kernel 3.2.0-24-generic then replace the entire code with the following:

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)

        ;;
        resume|thaw)

     chvt 1
     chvt 7
        ;;
esac

```
Step 3:
Give the script permission to run by typing the following in the terminal:

```
sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

Hope that helps and it works for me nicely. :-)

---

### Post by frusso on 2012-06-10
Many thanks, now suspend works on my Samsung NP530U3B-A01

---

### Post by miatawnt2b on 2012-06-11
Oh yes... suspend works now on my samsung Chronos Series 7.

Only problem I see right away is that I have Samsung-tools installed and tell it to keep bluetooth disabled. When I wake from suspend, bluetooth is on. Other things might be flaky as well, but this is one that stood out.

Any thoughts?

---

### Post by satianv on 2012-06-12
This is absolutely amazing. I take my hat off to you all for being such Gurus. After months of no Suspend on my iterations of Ubuntu versions, I can finally put my Lenovo S10-3 to sleep and resume without a single hitch. Thank you Thank you Thank you

---

### Post by WBMachinery on 2012-06-13
Another confirm success story from my part, I have an asus U56E and were to experiencing problems with suspend and this made it posible.

---

### Post by codingman on 2012-06-13
Nice script! Works like magic...

---

### Post by antrromet on 2012-06-14
I am using Ubuntu 12.04 on my HP Pavilion G4 1009TU model and it didnt work for me :( . Could you please suggest me what could be the problem? I tried both the scripts but none of them works :|

---

### Post by ykee on 2012-06-18
Thank you, DragonNinja9! 
It's working fine on T420.

---

### Post by apierrecardoso on 2012-06-27
Thank you so much DragonNinja9. Worked like a charm on a samsung series 5.

---

### Post by JanuaryJones on 2012-07-04
Thanks a lot! Now suspend works on my Samsung 530U3B also!

---

### Post by Ctulhu on 2012-07-05
Neither script works on a Dell Latitude E 6500 (Kubuntu 12.04, with Linux 3.2.0-26) :-(

---

### Post by Ruination2 on 2012-07-18
Neither script works for me, either. I'm running Ubuntu 12.04 on an Acer eMachines E527-2537.

---

### Post by Serafim221 on 2012-07-23
Neither works for me. HP Compaq 311. :(

---

### Post by illumilore on 2012-07-29
Neither seems to work for me. Xubuntu 12.04, MB=m2n-sli, when suspending, the screen blanks momentarily, then I see text messages from bootup and it just stays awake at that screen and I have to hard reboot. Kernel=3.5

---

### Post by gianninardoia on 2012-08-05
Neither works for me. DELL M6400

---

### Post by TheNessus on 2012-08-05
amazing. it works. Dell n3010

thank you

---

### Post by Tekippie on 2012-08-10
Thanks, fixed it for me :) 

Zotac motherboard with CULV cpu and Nvidia ION chipset..

---

### Post by skhansj on 2012-08-10
The second script worked for me.

Ubuntu 12.04 on Lenovo Ideapad Z570.

---

### Post by bluecactus5181 on 2012-08-16
neither works for me....:mad:
HP Elitebook 8530w

---

### Post by aliaomt on 2012-08-28
so bad :-X
it's not working for me  ](*,)
Asus 1215B 
ubuntu 12.04

---

### Post by giltbrook on 2012-09-03
New user help please.

When I get to the step:-

Step 2 (paste this into gedit and save)

What do I save the file as?

Update, in case anyone else needs this.

I think I have found the cause of my problem.
I had pressed 'Save' after editing, but when I tried to close gedit, it was asking me about 'Untitled 1' and what I wanted it  Saved As.
I had not even noticed Untitled 1 as an extra Tab in gedit, and therefore didn't realise it contained no information, so it could presumably be closed without saving, which I have now done.

---

### Post by sailorboy on 2012-09-03
This irritated me on Lucid also- after it HAD worked fine for a few years. I hoped 12.04 would solve it but no luck. I'm using a desktop Dell 4700 with a nvidia 9400gt with Gnome, compiz, nouveau and nvidia 295.40- nuked fglrx.
 It seems to suspend but resume locks up with blank screen and a roaring drive/fan. A decent workaround for me:
 In terminal- $ gksu gedit /etc/default/acpi-support
  I then changed the option for ACPI sleep to standby (as the remark suggested) and then rebooted to BIOS and switched to S1 (from S3) in power management.
 Not ideal, main screen blanks but stays lit (DVI)- but easy enough to turn off.
 Oddly- hibernate worked fine, turns clean off but must cache all processes to HDD since on next boot-up it requests log in (it's set for auto-log on) and then resumes all apps that were running.
 Pretty neat but rebooting was what I wanted to avoid. Sidenote- noticed the 40g boot SATA still has 9.1 marked on it- we're both getting old.

---

### Post by clockworktri on 2012-09-09
> **miatawnt2b said:**
> Oh yes... suspend works now on my samsung Chronos Series 7.

Only problem I see right away is that I have Samsung-tools installed and tell it to keep bluetooth disabled. When I wake from suspend, bluetooth is on. Other things might be flaky as well, but this is one that stood out.

Any thoughts?

I have this problem on my Chronos 7 as well. More problematic is that it turns off my wireless, and I can't turn it back on. I have to reboot to get internet again. Anyone have any ideas on this? (using the first script, not the second)

---

### Post by hscriber on 2012-09-11
Neither worked for me, HP Pavillion DV6 laptop.

---

### Post by CampLife on 2012-09-11
> **giltbrook said:**
> New user help please.

When I get to the step:-

Step 2 (paste this into gedit and save)

What do I save the file as?

Update, in case anyone else needs this.

I think I have found the cause of my problem.
I had pressed 'Save' after editing, but when I tried to close gedit, it was asking me about 'Untitled 1' and what I wanted it  Saved As.
I had not even noticed Untitled 1 as an extra Tab in gedit, and therefore didn't realise it contained no information, so it could presumably be closed without saving, which I have now done.

New user here, about thirty minutes into Ubuntu...
I have same question--in step 2, what did you save as?  Or, did you just close the tab?
I have not been successful with this workaround, yet.
Thanks!

---

### Post by Toz on 2012-09-11
Hello and welcome to the forums CampLife.

If you are following the above directions, just save the file (it will be saved as  /etc/pm/sleep.d/20_custom-ehci_hcd as per step 1). The original source for this workaround is located here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug").

---

### Post by CampLife on 2012-09-11
Hi, and thanks for the welcome.
Is this the right sequence?

Open terminal, insert script as defined in step one.
This opens another window, a text editor.  Enter script as defined in step 2. Then, click save.
Return to terminal screen, insert script as defined in step three.
Close text editor.
Close terminal screen.

Is that correct?  That is the way I did it, no luck.

---

### Post by LilLZ on 2012-09-11
Not working for me, HP Folio 13, just flashes then shows my desktop background but with no menus or anything clickable.
```
Initial commandline parameters: 
Sun Sep  9 15:17:38 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473035  4 
iwlwifi               332525  0 
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
drm                   242038  5 i915,drm_kms_helper
mac80211              506816  1 iwlwifi
psmouse                87692  0 
serio_raw              13211  0 
hp_wmi                 18092  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
rts_pstor             445196  0 
sparse_keymap          13890  1 hp_wmi
wmi                    19256  1 hp_wmi
mei                    41616  0 
cfg80211              205544  2 iwlwifi,mac80211
mac_hid                13253  0 
tpm_tis                18804  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784    1994036    1999748          0     112080    1008372
-/+ buffers/cache:     873584    3120200
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
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
Sun Sep  9 15:17:40 MDT 2012: performing suspend
Initial commandline parameters: 
Mon Sep 10 18:08:11 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
joydev                 17693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rts_pstor             445196  0 
i915                  473035  3 
drm_kms_helper         46978  1 i915
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
iwlwifi               332525  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  4 i915,drm_kms_helper
psmouse                87692  0 
mei                    41616  0 
mac_hid                13253  0 
wmi                    19256  1 hp_wmi
soundcore              15091  1 snd
mac80211              506816  1 iwlwifi
serio_raw              13211  0 
cfg80211              205544  2 iwlwifi,mac80211
tpm_tis                18804  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784    1271128    2722656          0     114052     532980
-/+ buffers/cache:     624096    3369688
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
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
Mon Sep 10 18:08:12 MDT 2012: performing suspend
Initial commandline parameters: 
Mon Sep 10 18:36:37 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
i915                  473035  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
tpm_tis                18804  0 
i2c_algo_bit           13423  1 i915
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
video                  19596  1 i915
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
joydev                 17693  0 
arc4                   12529  2 
uvcvideo               72627  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac_hid                13253  0 
iwlwifi               332525  0 
rts_pstor             445196  0 
psmouse                87692  0 
mei                    41616  0 
wmi                    19256  1 hp_wmi
serio_raw              13211  0 
parport                46562  3 parport_pc,ppdev,lp
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784     830688    3163096          0      26464     446996
-/+ buffers/cache:     357228    3636556
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
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
Mon Sep 10 18:36:39 MDT 2012: performing suspend
Initial commandline parameters: 
Mon Sep 10 18:48:41 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12529  2 
iwlwifi               332525  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
i915                  473035  3 
drm_kms_helper         46978  1 i915
tpm_tis                18804  0 
drm                   242038  4 i915,drm_kms_helper
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
i2c_algo_bit           13423  1 i915
parport_pc             32866  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
ppdev                  17113  0 
snd_hwdep              13668  1 snd_hda_codec
lp                     17799  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                 18092  0 
psmouse                87692  0 
sparse_keymap          13890  1 hp_wmi
serio_raw              13211  0 
rts_pstor             445196  0 
soundcore              15091  1 snd
wmi                    19256  1 hp_wmi
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
video                  19596  1 i915
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784     781380    3212404          0      28684     416240
-/+ buffers/cache:     336456    3657328
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
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
Mon Sep 10 18:48:42 MDT 2012: performing suspend
Initial commandline parameters: 
Mon Sep 10 18:56:06 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12529  2 
joydev                 17693  0 
i915                  473035  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
tpm_tis                18804  0 
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
video                  19596  1 i915
parport                46562  3 parport_pc,ppdev,lp
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
iwlwifi               332525  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
rts_pstor             445196  0 
mac_hid                13253  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                87692  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
wmi                    19256  1 hp_wmi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
mei                    41616  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  1 iwlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
uas                    18180  0 
usb_storage            49198  2 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784    1066612    2927172          0      32256     616132
-/+ buffers/cache:     418224    3575560
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
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
Mon Sep 10 18:56:07 MDT 2012: performing suspend
Initial commandline parameters: 
Mon Sep 10 19:13:47 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
arc4                   12529  2 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
iwlwifi               332525  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
i915                  473035  3 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              506816  1 iwlwifi
soundcore              15091  1 snd
rts_pstor             445196  0 
cfg80211              205544  2 iwlwifi,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
hp_wmi                 18092  0 
i2c_algo_bit           13423  1 i915
mei                    41616  0 
mac_hid                13253  0 
psmouse                87692  0 
serio_raw              13211  0 
sparse_keymap          13890  1 hp_wmi
video                  19596  1 i915
wmi                    19256  1 hp_wmi
tpm_tis                18804  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784    1330852    2662932          0      43480     777000
-/+ buffers/cache:     510372    3483412
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
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
Mon Sep 10 19:13:49 MDT 2012: performing suspend
Initial commandline parameters: 
Tue Sep 11 19:23:26 MDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
iwlwifi               332525  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
i915                  473035  3 
videodev               98259  1 uvcvideo
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506816  1 iwlwifi
v4l2_compat_ioctl32    17128  1 videodev
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
drm_kms_helper         46978  1 i915
psmouse                87692  0 
rts_pstor             445196  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hp_wmi                 18092  0 
serio_raw              13211  0 
drm                   242038  4 i915,drm_kms_helper
cfg80211              205544  2 iwlwifi,mac80211
sparse_keymap          13890  1 hp_wmi
mei                    41616  0 
mac_hid                13253  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
wmi                    19256  1 hp_wmi
tpm_tis                18804  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  2 
uas                    18180  0 
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3993784     998280    2995504          0      56964     526492
-/+ buffers/cache:     414824    3578960
Swap:      1046524          0    1046524

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan1'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
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
Tue Sep 11 19:23:28 MDT 2012: performing suspend
Initial commandline parameters: 
Tue Sep 11 21:20:38 MDT 2012: Running hooks for suspend.
```

Update: fixed, didn't see the updated version

---

### Post by DogMatix on 2012-09-18
Has not worked for me either. Running Ubuntu 12.04  with 3.2.0-30-generic

System seems to go into suspend but then immediately wakes up again.

ASRock mobo. with NVIDEA graphics card with current-proprietary driver enabled.

Checked var/log/pm-suspend.log and found

```
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
**Having NetworkManager put all interaces to sleep...Failed**.
```

Any ideas?

---

### Post by bach22 on 2012-09-26
Neither works for me.
Acer Extensa 4420 :(

---

### Post by stchman on 2012-09-29
Neither script worked for me.

ASUS P5K
Nvidia 8800GT
No swap file (do not want to hibernate, just suspend)

Thanks.

---

### Post by tmichaelmcn on 2012-10-08
Unfortunately, no luck for me either with either script:  Thinkpad R32

---

### Post by simonnomis on 2012-10-12
Hi, I tried script 2, didn't work (asus ux32vd). I deleted the file again and now my keyboard doesn't work. A few keys work (tab, alt, ½, sometimes a) bu notable esc and return doesn't work. This even prevents me from booting from an usb (keyboard also doesn't work during startup). I cannot verify 100% the two things are related, but I did no messing around after this, just shut down and came back a few hours later. Any ideas?

Edit: If I plug in an external keyboard that works, so I might have a hardware problem.

---

### Post by Mihailoo on 2012-10-14
Sadly, no luck here either, tried both scripts- Toshiba Satellite A135 S2276 :(

---

### Post by FishRCynic on 2012-10-14
2nd script from comment 20 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674/comments/20](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674/comments/20) works for me (2nd script in this thread).  

You might try comment #32 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674/comments/32) 

"sml.lima (sml-lima) wrote on 2012-09-22: 	#32

I also had problems with suspend/Resume on my LG T1 Express dual laptop with the new 12.04 release. The first time i tried to suspend it did without any problems, but after i was unable to suspend it due to some problem with my TPM chip.
What i did was to manualy unbind or unload the tpm_tis driver using the

sudo modprobe -r tpm_tis

After all the suspend/Resume did function without any problem.

SO i still don't know why this module is creating problems with the suspend action only at the second try, but at least this hack helps to suspend and resume without hiccups :)"

---

### Post by salsaHOT on 2012-11-05
So, I tried this and not only did it not work, but now I have the same problem when I start up my computer (Toshiba Satellite L755D) after turning it off. Has anyone had the same experience, and could somebody help me fix it? I'm not sure where to begin.

---

### Post by il_Wentu on 2012-11-14
I am extremeley sorry to say neither of the scripts are working for me either.
The only positive effect they had is that the led of the charging battery now seems to work properly. before the scripts it never turned on.
basically if i suspend and click the ON button, the disk spins, something seems to work but the screen is pitch black. If i force the laptop (Amilo 1718 Li) off and i boot again, it doesnt work UNLESS i physically remove the charge wire and all USB devices connected.

are there any news about this topic?

thx

W.

---

### Post by LilLZ on 2012-11-16
No longer works on 12.10 and of course no one here helps me (or many others) to get it to work.

---

### Post by Pabx on 2012-11-27
WORKING ON UBUNTU 12.10 WITH THE SAME ISSUE!

so you add it to the first post...

this is the first google option, and it is heaven.

---

### Post by lopcaf on 2012-12-08
Hi all, 

unfortunately, the scripts described above do not work for me in a Samsung Series 5 NP535U4C-A01 (with Nvidia video card) running Ubuntu 12.10 (linux kernel 3.5.0-19-generic). I am using the following driver

X.Org X Server -- AMD/ATI display driver wrapper from xserver-org-video-ati

As mentioned before, when I try to wake up the laptop from suspend mode, the monitor is just black (not even with the back light). Interestingly, if I use the driver of Nvidia, I can resume from suspend mode with no problem. Unluckily, the Nvidia driver has some issues, such as bright management, that's why I would prefer to use the X.Org driver.

The output of my suspend log (pm-suspend.log) is attached. 

Does anyone have any idea/solution?

Thanks!

---

### Post by Fallen40 on 2013-01-05
This seems to be a problem for me as well,  HP Pavilion g6, just wiped Windows 8 and installed 12.10.   Is there any hope of a fix/workaround soon?  Kind of a fundamental feature being able to utilise suspend/sleep on a laptop.  Any other ways to force a change in state from the command line or anything?  My laptop seems to be getting awfully hot now I have removed HP coolsense and have to keep it running most of the time.

---

### Post by lopcaf on 2013-01-05
> **Fallen40 said:**
> This seems to be a problem for me as well,  HP Pavilion g6, just wiped Windows 8 and installed 12.10.   Is there any hope of a fix/workaround soon?  Kind of a fundamental feature being able to utilise suspend/sleep on a laptop.  Any other ways to force a change in state from the command line or anything?  My laptop seems to be getting awfully hot now I have removed HP coolsense and have to keep it running most of the time.

Hi,

as this thread is solved, I started a new one in  

[http://ubuntuforums.org/showthread.php?t=2096577&goto=newpost](http://ubuntuforums.org/showthread.php?t=2096577&goto=newpost)

Best wishes!

---

### Post by sinj on 2013-01-11
neither works for me....
Toshiba Satellite L500

---

### Post by lasanthafdo on 2013-01-23
Worked wonderfully for me with HP-Probook 4540s. Thanks loads for this solution!!

---

### Post by professgreen on 2013-01-23
The second script worked for me on Lenovo 3000 v100 Ubuntu 12.04.1 LTS. Thanks!

---

### Post by snacki on 2013-02-15
Second version of script works fine on my machine, thanks. 

Ubuntu 12.04
Kernel 3.2.0-37-generic-pae
Graphics nvidia 304.61
Hardware MacBook Pro 3-1

---

### Post by salihumon on 2013-02-16
I tried everything you suggested, but no success :(
Actually, mine does get back to the home screen, but the keyboard and touchpad is not functional. Simply nothing works. So what I have to do every time, is to shut it down forcibly, and then turn on normally :S

Please Help!

---

### Post by longint on 2013-02-22
Same here, suspend and hibernate is just not working while it was working wothout any issue running Fedora before...

---

### Post by snacki on 2013-02-26
No longer workig with kernel 3.2.0-38-generic-pae

> **snacki said:**
> Second version of script works fine on my machine, thanks. 

Ubuntu 12.04
Kernel 3.2.0-37-generic-pae
Graphics nvidia 304.61
Hardware MacBook Pro 3-1

---

### Post by steel_j on 2013-03-18
March 18th 2013 with 12.04 LTS and all updates and the later, simpler code, fixed it for me too.  Thank you so much!

---

### Post by 1leenie on 2013-03-21
sailorboy, I also have a Dell Dimension 4700. My graphics card is a Diamond Radeon HD 5450. Look in your bios settings-the bit about the graphics cards (F2 to go to setup>maintenance>serr dmi message--SHUT IT OFF). My resume from suspend works after looking for the answer for nearly 4 weeks!

I found I had to push the power button to resume sometimes.  I installed hibernate and resume from suspend seems to work as it should now.

---

### Post by thatstheway on 2013-04-09
Unfortunately this didn't work for me. My machine wakes fine from  Suspend if I issue the command, but not if I close the lid (yup, I'm on a  laptop). If I do, it wakes to a black screen and I have to reboot. I've  got 1.2GB of RAM and a 2GB swap partition. When I try the first script,  I get a few errors: 

```
[COLOR=#000000][FONT=Arial](gedit:2198):   Gtk-WARNING **: Attempting to store changes into   `/root/.local/share/recently-used.xbel', but failed: Failed to create   file '/root/.local/share/recently-used.xbel.87N6UW': No such file or   directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
(gedit:2198):   Gtk-WARNING **: Attempting to set the permissions of   `/root/.local/share/recently-used.xbel', but failed: No such file or   directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
(gedit:2198): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel[/FONT][/COLOR]

```
And then it doesn't work. When I try the second script, I don't get any  errors, but it still doesn't work. I'm using a Toshiba Portege R100. Any  ideas?

---

### Post by Mr. Shannon on 2013-04-26
Thanks DrangonNinga9, the second script (post #6) fixed this for my Linux Mint 13 install (based on Ubuntu 12.04) running Linux 3.2.0-40-generic (64 bit).  So, one more kernel version your script works for.

---

### Post by xylemtg on 2013-05-22
Darn -- though from above these fixes seem to work for many, not for myself -- running Ubuntu (wubuntu) 12.04 on a Sony Vaio with kernel:  3.5.0-30-generic

And neither of DragonNinja's 2 fixes above fix my problem: every time i suspend, bringing the machine back up makes it go into a full reboot. 
 
This problem is intermittent also -- suspend *was* working fine after a few weeks ago i installed the simple last line change fix to /etc/acpi/sleep.sh recommended on this page:

 [http://askubuntu.com/questions/24048/suspend-fails-reboot-on-resume-and-no-hibernate-option](http://askubuntu.com/questions/24048/suspend-fails-reboot-on-resume-and-no-hibernate-option)

But then just stopped working again recently (i do normally install the recommended updates whenever the window pops up for this, though).

Any help on this would be appreciated -- i've spent a fair amount of time Googling around already and not found it, though on the whole, i do dig the Ubuntu community for being so amazingly helpful all around! :->

---

### Post by algabr on 2013-06-24
Unfortunately, neither script solved my problem with suspend on Toshiba Tecra A6. I have Ubuntu 12.04.2 LTS (kernel 3.5.0-34-generic i686). The suspend works fine first time after a reboot, then resumes normally, but then fails to suspend until the next reboot (the screen goes black momentarily but then prompts me to enter my password). I looked in /var/log/pm-suspend.log for lines containing "Failed", and all of them refer to NetworkManager or wpa_supplicant, so I guess the problem is probably cased by my wireless connection. Any help would be appreciated.

---

### Post by thanuntu on 2013-08-17
Neither script worked for me.

Toshiba Satellite L505 / Ubuntu 12.04 AMD64 / kernel 3.5.0-37-generic

Thanks for the effort anyway!

---

### Post by james_ashcroft on 2013-08-21
OH MY GOSH life saver for a really old laptop that needs to save battery but had to be turned off if was put in suspence. [COLOR=#ff0000][SIZE=5]***THANK YOU!!!!! ***[/SIZE][/COLOR]:guitar:

---

### Post by thanuntu on 2013-08-22
My system: Toshiba Satellite L505.

Running Ubuntu 10.04: The problem had appeared at some point but then disappeared _probably_ after some kernel upgrade or other (don't really remember)

Running Ubuntu 12.04: After a recent fresh install no problem with suspend. After I had installed gnome-session-fallback no problem either. I then went and installed gnome-shell, kubuntu-desktop, plus a bunch of other packages. At some point during tweaking (?), the system could no longer suspend. None of the above solutions worked for me, neither did tuxonice.
I then deleted a bunch of config (dot) files from my home directory and did yet another fresh install. Then I just installed gnome-session-fallback. The problem was solved! I did a kernel upgrade (now using 3.5.0.37) and still no problem (I am running the gnome-classic session with compiz). I didn't have to touch my BIOS, nor my kernel.

I have now installed a lot of other packages I needed, but no additional desktop environments, since I realized that it most probably was neither a kernel nor a hardware problem.

There seems to be no universal solution so, just in case, I have backed up my sources, PPAs and my installed packages, so that I would be ready for a quick reinstall should the problem arise anew. Fortunately, with proper backups, Linux offers the possibility to restore our system within 1-2 hours, should the need arise.

---

### Post by Prziborowski on 2013-08-28
I have tried both fixes and no fix as of yet.  Computer is a Desktop with Asus Motherboard P5B.  Nothing to special.
I did get the Hibernation to work but not suspend.  After the computer suspend it does shut down but when trying to come back out of suspend the keyboard flashes.

---

### Post by thanuntu on 2013-08-31
Guys, no promises, but I think I may be on to something. I will need you to verify this, though.

After a clean install of Ubuntu 12.04 on my Toshiba Satellite, suspend/resume was working just fine. Actually, I spent a whole week suspending/resuming my laptop by closing/opening its lid and I didn't have to reboot once. But _suddenly_ (I don't know how) the same problem occurred again! :mad:

I tried removing the latest packages I had previously installed (using kernel 3.5.0-37): NOTHING
I tried dist-upgrading the kernel (to 3.5.0-39): NOTHING
I even tried with a kernel I had compiled for my own CPU (from 3.5.7-16): NOTHING

Taking inspiration from [this solution]("http://askubuntu.com/questions/9518/ubuntu-wont-suspend-anymore-but-it-did-upon-install/10579#10579"), I checked to see if I have acpi-support installed on my system. I did. But I also observed on the Software Center description page that:
> This program is run from [FONT=Courier New]acpi_fakekey[/FONT]

So, I opened a terminal, issued ```
acpi_fakekey
``` and closed my lid. Then I opened it again and... SUCCESS! My session resumed!
Then I closed my lid again and... NO RESUME.

Then I made several tests with three different kernel versions. The results: each time I issued a [FONT=Courier New]acpi_fakekey[/FONT] command BEFORE closing the lid I could suspend/resume.

So, I suspect that the [FONT=Courier New]acpi_fakekey[/FONT] command needs to be inserted at the beginning of the suspend sequence, and/or at the end of the resume sequence.

However, this needs verification. Could you see if this is reproducible?

**[EDIT: Moved to new thread [here]("http://ubuntuforums.org/showthread.php?t=2171672&p=12775723#post12775723")]**

---

### Post by surati on 2013-09-15
Seems not actual anymore...? On Ubuntu 12.4 /3.5.0-40-generic -it does not function:confused:.

---

### Post by roi2 on 2013-10-14
Working on my ubuntu 12.04!! Thanks a lot!!:grin:

---

### Post by -=gr!n=- on 2014-01-27
At first I thought it was working, but now I understand that the laptop does not react on lid closure

---

### Post by Cavsfan on 2014-01-27
I had this same problem a while back but it was because my BIOS was reset. It was reset to S1 sleep mode. This greyed out Suspend but made Hibernate available and working well.
By changing this setting in BIOS to S3 my Suspend was back and Hibernate disappeared.

Just my 2 cents.

---

### Post by yan_solo on 2014-01-29
It does not work for me, it does nto go in suspend anymore manually. How can I disable that script.

---

### Post by The Trickster on 2014-01-30
Neither works for me, the laptop MSI EX630 goes to suspend, but immediatelly exit, and return to the normal state (guess something is waking it up)...

edit: solved with this [http://askubuntu.com/questions/148481/how-do-i-prevent-immediate-wake-up-from-suspend-and-or-hibernation](http://askubuntu.com/questions/148481/how-do-i-prevent-immediate-wake-up-from-suspend-and-or-hibernation)

---

### Post by ianni67 on 2014-02-18
The first script worked for me perfectly on elementaryOS stable 64bit, fully updated. My notebook is an Asus T101MT. The problem I had is that after suspend/resume, the touch screen did not work anymore and disappeared from xinput --list.
Now everything works again. THANK YOU!!!!

---

### Post by simas2 on 2014-03-13
Tried everything on this thread, didn't work.

Then after tinkering with various random stuff i got it working with 3.13.6 kernel but then my opengl would fail. So i rolled back to 3.11 kernel and bam it was working great.

I'm not sure what actually got it working but i think it was one of these commands:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
sudo apt-get purge acpi-support && sudo apt-get install acpi-support[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
By the way now I'm using fglrx-updates as radeon drivers, without them suspend/hibernation were absolutely fine, i just wanted opengl to work properly.

Hope this helps to someone [/FONT][/COLOR]:KS

---

### Post by majidalig on 2014-03-16
the second script worked like a charm. Thanks man!!

ASUS G53SX | Ubuntu 12.04 LTS | 3.11.0-18

---

### Post by slagter.maarten on 2014-03-18
Thank you so much! This worked for me, as opposed to the first solution which crashed my system.

---

### Post by pikku-pikkunen on 2014-05-01
The secind script worked on my Samsung 535U3C with Kubuntu 14.04, thank you DragonNinja!

---

### Post by e-San on 2014-07-24
Hi all!

The solution does not work for me ;(
pikku-pikkunen, do you own an Samsung with AMD A4-4355M APU?

Regards!

---

### Post by lucianoporta97 on 2014-07-27
Thanks dude! That totally did the trick for me! Finally I can decently use elementary OS :) Again, thank you so much!

---

### Post by jon.ti on 2014-09-27
I'm using 14.04 on my old desktop Dell. After upgrading from 12.04 suspend worked much better (I could only use S1 in the bios before the upgrade, but now I can use S3). But after suspend, on resume I was just getting a totally black screen using compiz, or a juddering display without a mouse pointer with metacity. I was having to use the ctrl-alt-f1 then ctrl-alt-f7 trick after resume to restart video, then all was well.

The second script sorted that for me, although occasionally the video has the juddering display for a couple or three seconds instead of starting cleanly, but it settles down ok.

Many thanks :KS

---

### Post by max59 on 2014-10-17
It's work!
[http://chriseiffel.com/everything-linux/how-i-got-suspend-and-hibernate-working-in-linux-ubuntu-11-04-mint-11/](http://chriseiffel.com/everything-linux/how-i-got-suspend-and-hibernate-working-in-linux-ubuntu-11-04-mint-11/)

---

### Post by Rajesh_Khundrakpam on 2014-10-24
I am new to Linux and I have the same problem that we are discussing in this thread and I complete all the three steps but at step three I run this command sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd and I am still waiting for this exicution to be finished but I have no idea how long it will take and when I try to close it says There is still a process running in this terminal. Closing the terminal will kill it. but after Taking so much time it ask for password I gave it and then I closed it but Now I can't even suspend my computer it wakes up right in the moment i click suspend. Should I try your updated commands or what else I am using Ubuntu 14.04 LTS (I am aware that in the Thread it says 12.04 LTS but I am giving a try Sir) Help me I cannot suspend my PC.

---

### Post by Rajesh_Khundrakpam on 2014-10-24
Now I also tried your updated commands as you updated on the latter part of the thread 
I mean this 

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)

        ;;
        resume|thaw)

     chvt 1
     chvt 7
        ;;
esac
(I exactly follow what you say and still it doesn't solve the problem, I can't suspend now , I keeps awake now, Problem is now Altered :D ..)
Anyway Kindly Help me ..

---

### Post by Sadi58 on 2014-11-08
Unfortunately, neither of the two scripts helped my Dell Latitude to Wake up from Suspend on Ubuntu 14.10 64-bit.

---

### Post by Sadi58 on 2014-11-08
Unfortunately, neither of the two scripts helped my Dell Latitude to Wake up from Suspend on Ubuntu 14.10 64-bit.

---

### Post by frankennetbook on 2014-11-13
Simply fantastic! Thank you.

---

### Post by Julie_Arnold_ on 2014-11-23
[COLOR=#d3d3d3]The **second** script also fixed my suspend issue as of 11/23/14 on 14.04[/COLOR]. So it *can* work for you, but it may not. EDIT: Okay, never mind. It worked once and then never again.

---

### Post by sajish-francis100 on 2014-12-12
worked for me . Thanks a lot.

---

### Post by jim_cor2 on 2015-04-01
How do I stop the script my pc keeps reswaking after suspend. Please help anyone.  edited  Tried your other script now works perfectly.

---

### Post by Watchtow3r on 2015-04-13
The second post worked perfectly for me.

---

### Post by bediinderjit on 2015-04-21
The second post worked for me, I am using Dell Vostro 2420, but suspend works only once, when I try to put laptop to suspend the second time it won't work.

After restarting the laptop again suspend works but only once.

---

### Post by John_Okrasa on 2015-05-08
I have to ask is this really allowing Ubuntu to suspend in the first place?  When I select suspend from the power off menu it cycles quickly back to awake.  When i close the lid and peak inside it appears to go black ( is suspended ?)  but the power button on the laptop stays illuminated, doesn't blink as it should do if truly suspended ( as it does with windows).

Aren't we fooling ourselves by keeps the laptop live and out of suspend?

What are the pros and cons of doing this?  Is Ubuntu in fact going in and out of suspend ? how can we prove/test this?

The blinking power pilot light in windows shows suspend... with the script installed in Ubuntu it remains solid which leads me to believe it doesn't go into suspend at all but cycles out of it.

( maybe it does because the screen goes black, again how can we prove it ? )


Any ideas ??

P.S.  I am running Ubuntu 14.04  on lenovo yoga 2 pro i7 64 bit

---

### Post by czammit156 on 2015-05-12
I have very little hope of getting any resolution since nobody else seems to have, but I will throw in my experience as well.

I am using an HP dv4 (64-bit, intel centrino) and very much enjoying Ubuntu 14.04, which is my first ever Ubuntu install. That said, my stupid laptop will NOT suspend. Closing the lid will turn the screen off, but the system does not suspend, it stays running. If I manually tell it to suspend, the screen will go black for just a moment and then come back on at the lock/login screen. That's it.

I've tried everything in this thread and nothing works. Typing the last line of code, nothing seems to happen after hitting enter and then nothing is changed. I have looked all over the internet for a solution to this problem and I just keep coming up empty.

I really hope this can be addressed, because it's really annoying having to shut my computer down every time I stop using it. :/

edit: I would also like to note that I can get the system to hibernate with "sudo pm-hibernate", but "sudo pm-suspend" does not do anything. And I can't seem to find a way to hibernate the laptop through the UI.

edit 2: I was able to fix the problem! By updating my laptop's BIOS using HP's software (I had to put my Windows HDD back in, download and install, then swap back to the Ubuntu HDD) everything now works just fine. I'm not sure if those scripts were even necessary.

If you're having this problem - try updating your BIOS!

---

### Post by RadiantPhoenix on 2015-05-26
Computer: Thinkpad W500
OS: Xubuntu 12.04
Kernel: linux-image-3.2.0-84-generic

Neither script worked, but using Synaptic to replace the package "cgroup-bin" with "cgroup-lite" did.

Found the answer in [this bug](https://bugs.launchpad.net/ubuntu/+source/libcgroup/+bug/838729)

---

### Post by antivirtel on 2015-06-12
I have Ubuntu 14.04 LTS upgraded from 12.04 LTS previously on a [Lenovo Thinkpad Edge E525]("http://shop.lenovo.com/us/en/laptops/thinkpad/e-series/e525/") with an AMD chip ([cpuinfo]("http://paste2.org/tnNgZFWh")). Since the upgrade, I have serious problems with suspend (and also had with 12.04 LTS too, but not that critical).

Now mine is sometimes not returning/waking up from suspend mode at all, it looks like that something has been stuck, and the CPU has very very high load (the fan's RPM is extremely high), and it can't display the GUI at all. (The backlight returns, so there is no hardware issue.)
This error also occurs, when I try to send the laptop to suspend mode, but it is more rare.

The problem not happens after a reboot at all: if I manually long press the power button, and restart the machine (if I'm not using the suspend function at all!).

Which script can I place to the mentioned **/etc/pm/sleep.d/20_custom-ehci_hcd** file?

Thank you!

---

### Post by dryan775 on 2015-06-12
Is there an update for this to work on 14.04?  I used to get just a black screen on resume and would have to power off to get any control back.
With this, the screen goes off, then within 5 seconds turns back on (a step in the right direction), but not really a suspend.

---

### Post by antivirtel on 2015-06-12
Yes, the same here. However the symptoms looked like the same on both LTS releases. Maybe one of the previous scripts were fit, but I don't know which...

---

### Post by Carlos_Dunick on 2015-06-30
Hi

after trying your script i get this in terminal

(gedit:3691): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

any suggestions?

You guys in the forum here are the only ones having results (nothing in askubuntu)

---

### Post by Bio-eco-evology on 2015-12-29
apparently ubuntu devs work closely with lenovo. However this bug has remained for several years.

Lenovo thinkpad e335
ubuntu 15.10

Suspend resume doesn't work. ( black screen on resume).

Install windows 7 on the above laptop for energy saving reasons.

Neither scripts work on Thinkpad e335 .

---

### Post by tom_slab2 on 2016-01-08
Hello, It almost works, but usb ports are off, does not help to reconnect usb stick, still off. Only restart helps. Do you have any clue? Thankx

---

