---
title: "fixing suspend"
date: 2009-08-27
forum: General Help
---

### Post by westie420 on 2009-08-27
i got nothing in the dell area, even though my computer is a gen 3 xps. it seems that recently my suspend function has ceased to work altogether. if i pull up the menu and click suspend, the computer briefly flashes the screensaver and then pops up the post-suspend login window. it's as if the system isn't set to suspend, so it just continues working. hibernate does the same. either way, is there some script that i can add or edit to get suspend back into operation? i'd much prefer not to leave this massive computer turned on all the time.

---

### Post by P4man on 2009-08-28
what version of ubuntu are you using?
Do you see anything interesting in the output of "dmesg" after the failed suspend?

---

### Post by westie420 on 2009-08-28
9.04. i'm sure that would've been helpful.

just gave it a try and checked dmesg. here's what came up after the attempted suspend:
[ 2228.662817] CPU0 attaching NULL sched-domain.
[ 2228.662824] CPU1 attaching NULL sched-domain.
[ 2228.662899] CPU0 attaching sched-domain:
[ 2228.662902]  domain 0: span 0-1 level SIBLING
[ 2228.662905]   groups: 0 1
[ 2228.662911] CPU1 attaching sched-domain:
[ 2228.662913]  domain 0: span 0-1 level SIBLING
[ 2228.662916]   groups: 1 0
[ 2229.121322] CPU0 attaching NULL sched-domain.
[ 2229.121328] CPU1 attaching NULL sched-domain.
[ 2229.152984] CPU0 attaching sched-domain:
[ 2229.152988]  domain 0: span 0-1 level SIBLING
[ 2229.152991]   groups: 0 1
[ 2229.152996]   domain 1: span 0-1 level CPU
[ 2229.152999]    groups: 0-1
[ 2229.153004] CPU1 attaching sched-domain:
[ 2229.153006]  domain 0: span 0-1 level SIBLING
[ 2229.153009]   groups: 1 0
[ 2229.153012]   domain 1: span 0-1 level CPU
[ 2229.153015]    groups: 0-1

same thing for an attempted hibernate. mind you, i'm running hyper threading mode, and i've never had issue with it and suspend before.

---

### Post by P4man on 2009-08-28
can you attach the output of 

```
cat /var/log/pm-suspend.log 
```

and

```
cat /var/log/pm-powersave.log 
```

---

### Post by westie420 on 2009-08-28
pm-suspend:
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Aug 28 17:09:20 EDT 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux ericwest-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
nvidia               9594888  36 
agpgart                42696  1 nvidia
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
vboxnetflt             91016  0 
vboxdrv               117672  1 vboxnetflt
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
snd_ca0106             39968  1 
snd_ac97_codec        112292  1 snd_ca0106
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15200  1 snd
dcdbas                 15264  0 
psmouse                61972  0 
pcspkr                 10496  0 
ppdev                  15620  0 
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16904  2 snd_ca0106,snd_pcm
serio_raw              13444  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
             total       used       free     shared    buffers     cached
Mem:       2060372     780608    1279764          0      72236     437708
-/+ buffers/cache:     270664    1789708
Swap:      3229024          0    3229024
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/usr/lib/pm-utils/sleep.d/45iwlist suspend suspend: /sbin/iwlist
not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/etc/pm/sleep.d/49sound suspend suspend: /etc/pm/sleep.d/49sound: 1: Syntax error: "(" unexpected
Returned exit code 2.
Fri Aug 28 17:09:20 EDT 2009: Inhibit found, will not perform suspend
Fri Aug 28 17:09:20 EDT 2009: Running hooks for resume
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci resume suspend: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/45iwlist resume suspend: /sbin/iwlist
success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.


pm-powersave:
/usr/lib/pm-utils/power.d/anacron true: success.
/usr/lib/pm-utils/power.d/laptop-mode true: success.
/usr/lib/pm-utils/power.d/sched-powersave true: **sched policy powersave ON
success.

---

### Post by P4man on 2009-08-28
Now we're getting somewhere:

> 
/etc/pm/sleep.d/49sound suspend suspend: /etc/pm/sleep.d/49sound: 1: Syntax error: "(" unexpected
Returned exit code 2.
Fri Aug 28 17:09:20 EDT 2009: Inhibit found, will not perform suspend

Did you change those scripts yourself? I dont even have a "/etc/pm/sleep.d/49sound"

can you post its contents?

```
cat /etc/pm/sleep.d/49sound
```

---

### Post by condamine on 2009-08-28
I had a similar problem with a Dell XPS M1330 laptop. Installing the proprietary Hardware Driver for the NVIDIA video card fixed it.

---

### Post by westie420 on 2009-08-28
it's a script that supposedly makes the sound work after suspend or hibernate. sleep stopped working after i put it on, so i haven't been able to test it.

function kill_sound_apps() {
pidsnd=$(lsof | grep /dev/snd | awk '{ print $2 }')
pidmixer=$(lsof | grep /dev/mixer | awk '{ print $2 }')
piddsp=$(lsof | grep /dev/dsp | awk '{ print $2 }')
kill $pidsnd $pidmixer $piddsp
}

case "$1" in
hibernate|suspend)
kill_sound_apps
echo `date` shut down sound for pm
;;
thaw|resume)
modprobe -r snd_hda_intel
modprobe snd_hda_intel
echo `date` starting sound coming out of pm
;;
*)
;;
esac

exit $?

---

### Post by westie420 on 2009-08-28
and like magic, deleting 49sound immediately made suspend operational again. the only issue is i still lose sound after suspend. that's another thread, i suppose, and hopefully searching will pull up something.

---

### Post by Semus4 on 2010-05-29
Hi.

My suspend stopped working without any special reason some day. Probably after installing some of updates.

I'm on 10.04 right now updated from 9.10 (I'm not sure on which version suspend stopped working).

I found in my /var/log/pm-suspend.log the same problem as yours:

```
/etc/pm/sleep.d/49sound suspend suspend:/etc/pm/sleep.d/49sound: 1: Syntax error: "(" unexpected
Returned exit code 2.
```

I did some research with google - nothing special found. So I decided to open this file and analyze syntax.

```
sudo gedit /etc/pm/sleep.d/49sound
```

First invalid line is:
```
function kill_sound_apps() {
```

So I googled how to write functions in .sh and discovered above line is incorrect. You should change it to:

```
kill_sound_apps() {
```

Save the file, make sure it's executable...

```
sudo chmod +x /etc/pm/sleep.d/49sound
```

... and start being happy ubuntu user with working suspending ;)

If it works for you add [SOLVED] tag to this thread's Title. I couldn't find any solution about this syntax error..

---

