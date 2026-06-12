---
title: "Ubuntu 11.10 - problems with hibernation, resume from it"
date: 2012-05-26
forum: General Help
---

### Post by firekage on 2012-05-26
Hi.

I've got really anoying problem with hibernation - it doesen't work and i don't know why, because it worked before. Now only works suspend to disk, but not suspend/hibernation to a disk.

I will provide some infos:

AMD x4 955
Asus M4A77
nVidia GTX260 with 180.13 drivers.

Here are some outputs from terminal:

**/etc/fstab**:

```
firekage@deusex:~$ cat /etc/fstab | grep swap
UUID=114c98b3-c532-42af-a84c-cbd07e97e836    none    swap    sw    0  0  
```now what i have in **/etc/initramfs-tools/conf.d/resume**:

```
firekage@deusex:~$ cat /etc/initramfs-tools/conf.d/resume 
RESUME=UUID=114c98b3-c532-42af-a84c-cbd07e97e836
```i have installed hibernate pack (installed trough terminal), so this is output from /etc/uswsusp.conf:

> firekage@deusex:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device =/dev/disk/by-uuid/114c98b3-c532-42af-a84c-cbd07e97e836
splash = y
compress = y
early writeout = y
image size = 1942887383
RSA key file = /etc/uswsusp.key
shutdown method = platform
these are my partirions with UUID's:

```
/dev/zram0: UUID="ec1ba85a-3ab1-4500-b6cd-c99f053a7259" TYPE="swap" 
/dev/sda1: UUID="114c98b3-c532-42af-a84c-cbd07e97e836" TYPE="swap" 
/dev/sda2: UUID="0a2ebb07-8b93-4938-9bee-7eca19168eee" TYPE="ext4" 
/dev/sda5: LABEL="RAZIEL" UUID="3ADE0DB5DE0D6A89" TYPE="ntfs" 
/dev/sdb1: UUID="149ac71c-7444-48aa-bc0c-9fb07bccf74c" TYPE="ext4" 
/dev/sdb2: LABEL="TERESA" UUID="4CE4692BE469190A" TYPE="ntfs" 
/dev/sdc1: LABEL="OBORO" UUID="20FEB393FEB36028" TYPE="ntfs" 
/dev/sdc2: LABEL="TANABE" UUID="88BCE378BCE35F66" TYPE="ntfs" 
/dev/sdd2: LABEL="SAKI" UUID="26E0FD2DE0FD03B9" TYPE="ntfs" 
/dev/sdd5: LABEL="REKI" UUID="F408618A08614CA4" TYPE="ntfs" 
/dev/sde1: LABEL="SAYA" UUID="B88440648440276A" TYPE="ntfs" 
/dev/sde2: LABEL="MOTOKO" UUID="F0005CEB005CB9F4" TYPE="ntfs" 
/dev/sdf1: UUID="f2d547ed-164e-4d90-bb32-ad3c57046d4f" TYPE="ext4" 
/dev/sdf2: LABEL="CLARE" UUID="DA7C0A647C0A3BAF" TYPE="ntfs" 
/dev/mapper/truecrypt1: UUID="3E0006BE00067CE1" TYPE="ntfs" 
/dev/mapper/truecrypt2: UUID="A2E0E88CE0E867CD" TYPE="ntfs" 
/dev/mapper/truecrypt3: UUID="C6D061EDD061E3E1" TYPE="ntfs" 
/dev/mapper/truecrypt4: UUID="28D82F4DD82F1918" TYPE="ntfs" 
/dev/mapper/truecrypt5: UUID="640400580400301A" TYPE="ntfs" 
```
I think that everything is ok (exept that there is zram, (i didn't install it - it came by itself?), and it is in one other swap partition.


Can you help me? Suspend/hibernation to disk doesen't work. When i switch, computer goes silently into "sleep" mode (i see that s2d is writing file) but after resuming computer either freezes on purple wallpaper with bouncing orange balls (boot screen of ubuntu) or if either works fine...it's in fact reebooted not resumed because my apps doesen't run in background:

---

### Post by Toz on 2012-06-01
Try disabling the zram ramdisk prior to running the hibernate function (pm-hibernate or s2disk). It maybe that the system is using it (zram0) instead of the swap file to save the image.

Suspend is a different issue because it does not write an image file to the swap partition.

---

### Post by firekage on 2012-06-01
> **Toz said:**
> Try disabling the zram ramdisk prior to running the hibernate function (pm-hibernate or s2disk). It maybe that the system is using it (zram0) instead of the swap file to save the image.

Suspend is a different issue because it does not write an image file to the swap partition.

Can you tell me how to disable zram? I tried to find it but i haven't found how to do it.

---

### Post by Toz on 2012-06-01
Is there a file something like **/etc/init.d/zramswap** file on your system? If so, try:
```
sudo service zramswap stop
```
...or
```
sudo /etc/init.d/zramswap stop
```

---

### Post by firekage on 2012-06-03
No, there is not such a file, but i have something called zram here:
```

firekage@deusex:/etc/init.d$ locate -i zram
/lib/modules/3.0.0-16-generic-pae/kernel/drivers/staging/zram
/lib/modules/3.0.0-16-generic-pae/kernel/drivers/staging/zram/zram.ko
/usr/src/linux-headers-3.0.0-16/drivers/staging/zram
/usr/src/linux-headers-3.0.0-16/drivers/staging/zram/Kconfig
/usr/src/linux-headers-3.0.0-16/drivers/staging/zram/Makefile
/usr/src/linux-headers-3.0.0-16-generic-pae/include/config/zram.h

```

---

### Post by Toz on 2012-06-03
Try this:
```
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
```
...then try hibernating.

---

### Post by idoitprone on 2012-06-03
> **Toz said:**
> Try this:
```
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
```...then try hibernating.


free -m

did you check his swap and ram size?

---

### Post by firekage on 2012-06-04
> **idoitprone said:**
> free -m

did you check his swap and ram size?

```
firekage@deusex:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4028       3604        423          0        596        864
-/+ buffers/cache:       2143       1884
Swap:        11552         33      11518
```

---

### Post by firekage on 2012-06-04
> **Toz said:**
> Try this:
```
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
```...then try hibernating.

I understand 2 command from above, but what does this mean:

```
echo 1 > /sys/block/zram0/reset
```

---

### Post by idoitprone on 2012-06-04
> **firekage said:**
> I understand 2 command from above, but what does this mean:

```
echo 1 > /sys/block/zram0/reset
```

he is passing a parameter to file named /sys/blockzram0/reset

the original unix works with the idea of a file philsophy

by turning everything ranging from data to kernel services to files there is a unviersal method of accessing your operating system

You have read kernel docs to figure your which part of the kernel this is /sys/block/zram0/reset

[http://en.wikipedia.org/wiki/Sysfs](http://en.wikipedia.org/wiki/Sysfs)

---

### Post by Toz on 2012-06-04
> **firekage said:**
> I understand 2 command from above, but what does this mean:

```
echo 1 > /sys/block/zram0/reset
```

It resets the node (the compressed fs).

---

### Post by firekage on 2012-06-07
> **Toz said:**
> Try this:
```
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
```...then try hibernating.

I had time and checked it.

```
firekage@deusex:~$ sudo swapoff /dev/zram0
[sudo] password for firekage: 
```

and:

```
firekage@deusex:~$ umount /dev/zram0
umount: /dev/zram0 nie jest zamontowany (wg mtaba)
```

( /dev/zram0 is not mounted according mtab)

and:

```
firekage@deusex:~$ echo 1 > /sys/block/zram0/reset
bash: /sys/block/zram0/reset: Brak dost&#281;pu
```

and:

```
firekage@deusex:~$ sudo echo 1 > /sys/block/zram0/reset
bash: /sys/block/zram0/reset: Brak dost&#281;pu
firekage@deusex:~$ 
```

no acces to it.

So, if i think correctly, it won't work at all?

---

### Post by idoitprone on 2012-06-07
> **firekage said:**
> I had time and checked it.

```
firekage@deusex:~$ sudo swapoff /dev/zram0
[sudo] password for firekage: 
```and:

```
firekage@deusex:~$ umount /dev/zram0
umount: /dev/zram0 nie jest zamontowany (wg mtaba)
```( /dev/zram0 is not mounted according mtab)

and:

```
firekage@deusex:~$ echo 1 > /sys/block/zram0/reset
bash: /sys/block/zram0/reset: Brak dost&#281;pu
```and:

```
firekage@deusex:~$ sudo echo 1 > /sys/block/zram0/reset
bash: /sys/block/zram0/reset: Brak dost&#281;pu
firekage@deusex:~$ 
```no acces to it.

So, if i think correctly, it won't work at all?

put the commands in a subshell

```
sudo sh -c '[COMMAND]'
``````
sudo sh -c 'echo 1 > /sys/block/zram0/reset'
```the echo does not need the elevated right, but the redirect

In order to  get around this issue is to put the whole thing into a subshell

---

### Post by firekage on 2012-06-07
Maybe my english is not that good - what is subshell? You mean terminal?

BTW, i found something similar:

[http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from](http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from)

This person also have zram. I, just like him, have zram and it looks like it is from casper. I have installed casper because i have installed remastersys (or remastersys installed it anyway cause i don't remember installing casper by myself). 

If i remove casper (it makes something in initram-tools and add something to a kernel) than remastersys is unable to load, but i want to have remastersys :(

---

### Post by idoitprone on 2012-06-07
> **firekage said:**
> Maybe my english is not that good - what is subshell? You mean terminal?

BTW, i found something similar:

[http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from](http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from)

This person also have zram. I, just like him, have zram and it looks like it is from casper. I have installed casper because i have installed remastersys (or remastersys installed it anyway cause i don't remember installing casper by myself). 

If i remove casper (it makes something in initram-tools and add something to a kernel) than remastersys is unable to load, but i want to have remastersys :(

terminal is a bash emulator [http://en.wikipedia.org/wiki/Terminal_emulation](http://en.wikipedia.org/wiki/Terminal_emulation)
bash is a type of shell [http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29](http://en.wikipedia.org/wiki/Bash_%28Unix_shell%29)
a shell is a commandline interpreter, in order words a user environment in which you input text
[http://en.wikipedia.org/wiki/Unix_shell](http://en.wikipedia.org/wiki/Unix_shell)
A subshell is a shell within a shell

That is all the vocabulary in a nutshell

Yes put those commands in the terminal

---

### Post by firekage on 2012-06-10
> **idoitprone said:**
> put the commands in a subshell

```
sudo sh -c '[COMMAND]'
``````
sudo sh -c 'echo 1 > /sys/block/zram0/reset'
```the echo does not need the elevated right, but the redirect

In order to  get around this issue is to put the whole thing into a subshell

I tried it. It doesen't work.

-i entered command above in terminal
-i hibernated my computer
-i waked up from hibernation but it wasn't resumet, it just booted like when we start for the first time computer

So, in other words, i don't know what to do.

---

### Post by Toz on 2012-06-10
Did you enter all 3 commands?
```
sudo bash
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
pm-hibernate
```

Post back contents of /var/log/pm-suspend.log.

---

### Post by firekage on 2012-06-11
> **Toz said:**
> Did you enter all 3 commands?
```
sudo bash
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
pm-hibernate
```Post back contents of /var/log/pm-suspend.log.

I did not execute pm-hibernate. I hibernated it trough taskbar (this thing with upper right corner, i hibernated it from there). Still post contents of /var/log/pm-suspend.log or try to pm-hibernate trough terminal and then post contents of it?

---

### Post by Toz on 2012-06-12
Do it through the terminal first with pm-hibernate and post the contents of the pm-suspend.log file.

---

### Post by firekage on 2012-06-13
> **Toz said:**
> Did you enter all 3 commands?
```
sudo bash
swapoff /dev/zram0
umount /dev/zram0
echo 1 > /sys/block/zram0/reset
pm-hibernate
```Post back contents of /var/log/pm-suspend.log.

Strange. I entered again all of it starting from sudo bash, and do a pm-hibernate. After resuming my session was resumed and everything is like i left it before hibernating my system.

Don't know why it worked trough terminal.

Only thing that shown me a warning was umound /dev/zram0 because after it i had message that /dev/zram0 is not mounted.

This is output from /var/log/pm-suspend.log:

```
root@deusex:/var/log# cat /var/log/pm-suspend.log
Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
root@deusex:/var/log# 

```

Hope it helps.

---

### Post by Toz on 2012-06-13
Thats good - hibernate works with zram disabled. Now lets automate it so that it happens automatically when the system goes into hibernate.

1. Create the script file:
```
sudo gedit /etc/pm/sleep.d/05zram_disable
```

2. Copy/paste the following content:
```

#!/bin/bash

case "${1}" in
    hibernate)
       swapoff /dev/zram0
       umount /dev/zram0
       echo 1 > /sys/block/zram0/reset
       ;;
    thaw)
       mkswap /dev/zram0
       swapon /dev/zram0
       ;;
esac
```

3. Save the file.

4. Test by using normally methods of hibernation.

---

### Post by firekage on 2012-06-14
I will try this. Thank you very much.

Can you tell me one more thing? Where i could learn something like this? I've been using linux for more than year but i still don't know how to deal with this kind of thing when there is a need of creating scripts and why it must be created (how to create, where to create, in what kind of file - in this example in 05zram_disable) in order to something work (normal hibernation worked for me, than something happened, zram0 showed themselved and hibernation was broken). I understand swapoff, umount but command with 

```

echo 1 > /sys/block/zram/reset 
;;
thaw)
```is something that i don't understand, and why after it there is created mkswap with zram0 and again swapon with zram0?

Youre some kind of developer?

BTW - when i put "umount /dev/zra0" i have warning that it is not mounted, so it should still be there?

---

### Post by Toz on 2012-06-14
> **firekage said:**
> I will try this. Thank you very much.

Can you tell me one more thing? Where i could learn something like this? I've been using linux for more than year but i still don't know how to deal with this kind of thing when there is a need of creating scripts and why it must be created (how to create, where to create, in what kind of file - in this example in 05zram_disable) in order to something work (normal hibernation worked for me, than something happened, zram0 showed themselved and hibernation was broken). 
Most of this stuff I've picked up from fixing my own suspend/hibernation issues or researching on the internet. The Arch wiki is really good, but you have to be able to pick out the info as not everything will work as written on ubuntu. For example: [https://wiki.archlinux.org/index.php/Pm-utils]("https://wiki.archlinux.org/index.php/Pm-utils"). I would highly recommend installing and setting up an Arch or gentoo system (in a vm using Virtualbox if you don't have a spare computer) if you want to get a much deeper understanding of the inner workings of linux. 
 
> I understand swapoff, umount but command with 

```

echo 1 > /sys/block/zram/reset 
;;
thaw)
```is something that i don't understand, and why after it there is created mkswap with zram0 and again swapon with zram0?This is to recreate the compressed ramdisk after your system resumes so that it is back to normal. At a high level, here is what we are doing:
- turn off compressed ram disk
- hibernate
- resume (thaw)
- turn back on compressed ram disk

> Youre some kind of developer?Although I have done development in the past, I don't consider myself a developer. I have held jobs as a unix system administrator for a few years. 

> BTW - when i put "umount /dev/zra0" i have warning that it is not mounted, so it should still be there?
/dev/zra0? Is this a typo? It should be /dev/zram0. Does:
```
swapon -s
``` show that it is mounted?

---

### Post by firekage on 2012-06-14
Thank You very much.


```

/dev/zra0? Is this a typo? It should be /dev/zram0. Does:
[code]swapon -s
``` show that it is mounted?[/code]Yes, it is a typo. It should be /dev/zram0

I rebooted my machine in order to properly put output of swapon -s:

```
firekage@deusex:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/zram0                              partition    2062336    0    100
/dev/sda1                               partition    9767484    0    -1
firekage@deusex:~$ 
```BTW - could i create ```
05_zram_disable
``` or it should be exacly like you wrote?

---

### Post by Toz on 2012-06-14
You can call the file whatever you want, but it would be a good idea to preface it with **95_** (sorry, I had 05_ above) so that it is run later in the sequence (in case anything is dependent on it). The scripts are run alphabetically in order during hibernate starting at 00 and in reverse when thawing.

So, **95_zram_disable** should be okay.

---

### Post by firekage on 2012-06-14
Thank you. I will try it now and post later what happened.

---

### Post by firekage on 2012-06-15
This is log from /var/log/pm-suspend.log

```
Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2593944    1530732          0     652052    1020816
-/+ buffers/cache:     921076    3203600
Swap:      9767484      45832    9721652

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:43:19 CEST 2012: performing suspend
Thu Jun 14 13:52:43 CEST 2012: Awake.
Thu Jun 14 13:52:43 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 13:52:44 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 16:15:18 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  60 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
tveeprom               17009  1 cx88xx
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
v4l2_common            15793  3 tuner,cx8800,cx88xx
i2c_piix4              13093  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
k10temp                12990  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
sata_sil24             17797  1 
ahci                   21634  9 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3886136     238540          0     648092    1666304
-/+ buffers/cache:    1571740    2552936
Swap:     11829820         32   11829788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05zram_disable suspend suspend:

/etc/pm/sleep.d/05zram_disable suspend suspend: not executable.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 16:15:22 CEST 2012: performing suspend
Thu Jun 14 20:44:53 CEST 2012: Awake.
Thu Jun 14 20:44:53 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
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
Running hook /etc/pm/sleep.d/05zram_disable resume suspend:

/etc/pm/sleep.d/05zram_disable resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 20:44:55 CEST 2012: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Jun 15 04:48:01 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tea5767                13113  0 
ir_rc5_decoder         12490  0 
snd_ctxfi              85448  2 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
nvidia              10390874  50 
snd_seq_midi           13132  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 cx88xx
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
r8169                  47200  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3393928     730748          0     637256    1140508
-/+ buffers/cache:    1616164    2508512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 04:48:04 CEST 2012: performing hibernate
Fri Jun 15 04:48:10 CEST 2012: Awake.
Fri Jun 15 04:48:10 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
```I hibernated trough Unity panel and computer did not hibernate. I had message: **pm not enough free swap place**. And it freezed with this warning.

It's strange because it worked trough terminal, also i created script and have 10GB partition for a swap.

---

### Post by firekage on 2012-06-15
I started my computer again, worked with it for a few minutes and did another hibernation trough panel - not trough terminal. Computer switched off properly, i waked up it but there was not resume, he just booted like without suspend, from normal start - my session wasn't resumed.

log:

```

Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21
```

I will try it trough termianl. This is swapon -s

```
firekage@deusex:/$ swapon -s
Filename                Type        Size    Used    Priority
/dev/zram0                              partition    2062336    0    100
/dev/sda1                               partition    9767484    0    -1
firekage@deusex:/$ 

```

---

### Post by firekage on 2012-06-15
I tried to do something more. I hibernated it trough terminal with pm-suspend after running my computer again. It hibernated, switched off properly but again pm-hibernate doesen't work. It just starts to boot from zero, from the start without resuming session. Just like there was no place to read from saved session.

```
Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2593944    1530732          0     652052    1020816
-/+ buffers/cache:     921076    3203600
Swap:      9767484      45832    9721652

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:43:19 CEST 2012: performing suspend
Thu Jun 14 13:52:43 CEST 2012: Awake.
Thu Jun 14 13:52:43 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 13:52:44 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 16:15:18 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  60 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
tveeprom               17009  1 cx88xx
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
v4l2_common            15793  3 tuner,cx8800,cx88xx
i2c_piix4              13093  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
k10temp                12990  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
sata_sil24             17797  1 
ahci                   21634  9 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3886136     238540          0     648092    1666304
-/+ buffers/cache:    1571740    2552936
Swap:     11829820         32   11829788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05zram_disable suspend suspend:

/etc/pm/sleep.d/05zram_disable suspend suspend: not executable.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 16:15:22 CEST 2012: performing suspend
Thu Jun 14 20:44:53 CEST 2012: Awake.
Thu Jun 14 20:44:53 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
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
Running hook /etc/pm/sleep.d/05zram_disable resume suspend:

/etc/pm/sleep.d/05zram_disable resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 20:44:55 CEST 2012: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Jun 15 04:48:01 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tea5767                13113  0 
ir_rc5_decoder         12490  0 
snd_ctxfi              85448  2 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
nvidia              10390874  50 
snd_seq_midi           13132  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 cx88xx
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
r8169                  47200  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3393928     730748          0     637256    1140508
-/+ buffers/cache:    1616164    2508512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 04:48:04 CEST 2012: performing hibernate
Fri Jun 15 04:48:10 CEST 2012: Awake.
Fri Jun 15 04:48:10 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
Initial commandline parameters: 
Fri Jun 15 10:08:20 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda9887                17874  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
tda8290                22216  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10390874  80 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
sp5100_tco             13495  0 
asus_atk0110           17742  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              12600  1 snd
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
ppdev                  12849  0 
k10temp                12990  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
sata_sil24             17797  0 
pata_atiixp            12967  4 
ati_agp                13242  0 
r8169                  47200  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3460064     664612          0     654600    1753300
-/+ buffers/cache:    1052164    3072512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 10:08:24 CEST 2012: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:15:01 CEST: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  60 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1876808    2247868          0     226828     679048
-/+ buffers/cache:     970932    3153744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
pi&#261;, 15 cze 2012, 10:15:03 CEST: performing suspend
pi&#261;, 15 cze 2012, 10:15:21 CEST: Awake.
pi&#261;, 15 cze 2012, 10:15:21 CEST: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: not executable.
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
pi&#261;, 15 cze 2012, 10:15:25 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:16:07 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  64 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1938880    2185796          0     226828     680120
-/+ buffers/cache:    1031932    3092744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:16:09 CEST: performing hibernate
```


Maybe this script should be marked with chmod +x or some file permission?

---

### Post by firekage on 2012-06-15
I did another thing. I hibernated it trough terminal using pm-suspend but right now i entered commands that you provided earlier:

```

sudo bash swapoff /dev/zram0 umount /dev/zram0 echo 1 > /sys/block/zram0/reset pm-hibernate
```

My computer was properly hibernated, resumed, session was resumed!

I don't understand it. Why now it worked, while it doesen't work trogh panel from Unity, or even terminal when i do not write this commands?

```

Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2593944    1530732          0     652052    1020816
-/+ buffers/cache:     921076    3203600
Swap:      9767484      45832    9721652

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:43:19 CEST 2012: performing suspend
Thu Jun 14 13:52:43 CEST 2012: Awake.
Thu Jun 14 13:52:43 CEST 2012: Running hooks for resume
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
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 13:52:44 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 16:15:18 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  60 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
tveeprom               17009  1 cx88xx
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
v4l2_common            15793  3 tuner,cx8800,cx88xx
i2c_piix4              13093  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
k10temp                12990  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
sata_sil24             17797  1 
ahci                   21634  9 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3886136     238540          0     648092    1666304
-/+ buffers/cache:    1571740    2552936
Swap:     11829820         32   11829788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05zram_disable suspend suspend:

/etc/pm/sleep.d/05zram_disable suspend suspend: not executable.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 16:15:22 CEST 2012: performing suspend
Thu Jun 14 20:44:53 CEST 2012: Awake.
Thu Jun 14 20:44:53 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

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
Running hook /etc/pm/sleep.d/05zram_disable resume suspend:

/etc/pm/sleep.d/05zram_disable resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 20:44:55 CEST 2012: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Jun 15 04:48:01 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tea5767                13113  0 
ir_rc5_decoder         12490  0 
snd_ctxfi              85448  2 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
nvidia              10390874  50 
snd_seq_midi           13132  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 cx88xx
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
r8169                  47200  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3393928     730748          0     637256    1140508
-/+ buffers/cache:    1616164    2508512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 04:48:04 CEST 2012: performing hibernate
Fri Jun 15 04:48:10 CEST 2012: Awake.
Fri Jun 15 04:48:10 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
Initial commandline parameters: 
Fri Jun 15 10:08:20 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda9887                17874  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
tda8290                22216  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10390874  80 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
sp5100_tco             13495  0 
asus_atk0110           17742  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              12600  1 snd
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
ppdev                  12849  0 
k10temp                12990  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
sata_sil24             17797  0 
pata_atiixp            12967  4 
ati_agp                13242  0 
r8169                  47200  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3460064     664612          0     654600    1753300
-/+ buffers/cache:    1052164    3072512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 10:08:24 CEST 2012: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:15:01 CEST: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  60 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1876808    2247868          0     226828     679048
-/+ buffers/cache:     970932    3153744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
pi&#261;, 15 cze 2012, 10:15:03 CEST: performing suspend
pi&#261;, 15 cze 2012, 10:15:21 CEST: Awake.
pi&#261;, 15 cze 2012, 10:15:21 CEST: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: not executable.
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
pi&#261;, 15 cze 2012, 10:15:25 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:16:07 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  64 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1938880    2185796          0     226828     680120
-/+ buffers/cache:    1031932    3092744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:16:09 CEST: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:23:47 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  60 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1828064    2296612          0     213276     681140
-/+ buffers/cache:     933648    3191028
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:23:50 CEST: performing hibernate
pi&#261;, 15 cze 2012, 10:25:33 CEST: Awake.
pi&#261;, 15 cze 2012, 10:25:33 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 15 cze 2012, 10:25:35 CEST: Finished.
```


I thing this is lost case. Randomly doesen't work, works trough terminal when entering this command, doesen't work when i have script - should be some file permission with chmod +x and so on?

---

### Post by firekage on 2012-06-15
I did another pm-hibernation trough terminal but after entering commands earlier. No i only did pm-hibernation and it worked again! Strange.

```
Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2593944    1530732          0     652052    1020816
-/+ buffers/cache:     921076    3203600
Swap:      9767484      45832    9721652

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:43:19 CEST 2012: performing suspend
Thu Jun 14 13:52:43 CEST 2012: Awake.
Thu Jun 14 13:52:43 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 13:52:44 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 16:15:18 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  60 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
tveeprom               17009  1 cx88xx
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
v4l2_common            15793  3 tuner,cx8800,cx88xx
i2c_piix4              13093  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
k10temp                12990  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
sata_sil24             17797  1 
ahci                   21634  9 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3886136     238540          0     648092    1666304
-/+ buffers/cache:    1571740    2552936
Swap:     11829820         32   11829788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05zram_disable suspend suspend:

/etc/pm/sleep.d/05zram_disable suspend suspend: not executable.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 16:15:22 CEST 2012: performing suspend
Thu Jun 14 20:44:53 CEST 2012: Awake.
Thu Jun 14 20:44:53 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
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
Running hook /etc/pm/sleep.d/05zram_disable resume suspend:

/etc/pm/sleep.d/05zram_disable resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 20:44:55 CEST 2012: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Jun 15 04:48:01 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tea5767                13113  0 
ir_rc5_decoder         12490  0 
snd_ctxfi              85448  2 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
nvidia              10390874  50 
snd_seq_midi           13132  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 cx88xx
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
r8169                  47200  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3393928     730748          0     637256    1140508
-/+ buffers/cache:    1616164    2508512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 04:48:04 CEST 2012: performing hibernate
Fri Jun 15 04:48:10 CEST 2012: Awake.
Fri Jun 15 04:48:10 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
Initial commandline parameters: 
Fri Jun 15 10:08:20 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda9887                17874  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
tda8290                22216  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10390874  80 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
sp5100_tco             13495  0 
asus_atk0110           17742  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              12600  1 snd
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
ppdev                  12849  0 
k10temp                12990  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
sata_sil24             17797  0 
pata_atiixp            12967  4 
ati_agp                13242  0 
r8169                  47200  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3460064     664612          0     654600    1753300
-/+ buffers/cache:    1052164    3072512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 10:08:24 CEST 2012: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:15:01 CEST: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  60 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1876808    2247868          0     226828     679048
-/+ buffers/cache:     970932    3153744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
pi&#261;, 15 cze 2012, 10:15:03 CEST: performing suspend
pi&#261;, 15 cze 2012, 10:15:21 CEST: Awake.
pi&#261;, 15 cze 2012, 10:15:21 CEST: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: not executable.
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
pi&#261;, 15 cze 2012, 10:15:25 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:16:07 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  64 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1938880    2185796          0     226828     680120
-/+ buffers/cache:    1031932    3092744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:16:09 CEST: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:23:47 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  60 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1828064    2296612          0     213276     681140
-/+ buffers/cache:     933648    3191028
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:23:50 CEST: performing hibernate
pi&#261;, 15 cze 2012, 10:25:33 CEST: Awake.
pi&#261;, 15 cze 2012, 10:25:33 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 15 cze 2012, 10:25:35 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:29:02 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  64 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1421724    2702952          0      85384     375948
-/+ buffers/cache:     960392    3164284
Swap:      9767484        172    9767312

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:29:04 CEST: performing hibernate
pi&#261;, 15 cze 2012, 10:30:44 CEST: Awake.
pi&#261;, 15 cze 2012, 10:30:44 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 15 cze 2012, 10:30:45 CEST: Finished.
```

Thank you for your time and for helping me out. It's some kind of magic. Don;t understand it. On Slackware it worked like a charm.

---

### Post by firekage on 2012-06-15
One more try with pm-hibernation from unity panel - it worked!

```
Initial commandline parameters: 
&#347;ro, 13 cze 2012, 23:56:06 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  2 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  60 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  18 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    3076512    1048164          0     574816    1046972
-/+ buffers/cache:    1454724    2669952
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
&#347;ro, 13 cze 2012, 23:56:08 CEST: performing hibernate
&#347;ro, 13 cze 2012, 23:57:52 CEST: Awake.
&#347;ro, 13 cze 2012, 23:57:53 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
&#347;ro, 13 cze 2012, 23:58:06 CEST: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Thu Jun 14 01:07:39 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2130616    1994060          0     602172     717844
-/+ buffers/cache:     810600    3314076
Swap:      9767484      46856    9720628

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 01:07:41 CEST 2012: performing suspend
Thu Jun 14 08:36:32 CEST 2012: Awake.
Thu Jun 14 08:36:32 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 08:36:33 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:43:16 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_hda_codec_via      61329  1 
snd_ctxfi              85448  2 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
snd_hda_intel          28358  4 
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
i2c_algo_bit           13199  1 cx88xx
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_ctxfi,snd_hda_intel,snd_hda_codec
tveeprom               17009  1 cx88xx
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
v4l2_common            15793  3 tuner,cx8800,cx88xx
nvidia              10390874  64 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
snd                    55902  21 snd_hda_codec_via,snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
i2c_piix4              13093  0 
btcx_risc              13400  2 cx8800,cx88xx
snd_page_alloc         14108  3 snd_ctxfi,snd_hda_intel,snd_pcm
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
ahci                   21634  9 
hid                    77367  1 usbhid
sundance               26629  0 
r8169                  47200  0 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    2593944    1530732          0     652052    1020816
-/+ buffers/cache:     921076    3203600
Swap:      9767484      45832    9721652

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:43:19 CEST 2012: performing suspend
Thu Jun 14 13:52:43 CEST 2012: Awake.
Thu Jun 14 13:52:43 CEST 2012: Running hooks for resume
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

/dev/sdf:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdf:
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 13:52:44 CEST 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 16:15:18 CEST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia              10390874  60 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
tveeprom               17009  1 cx88xx
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
v4l2_common            15793  3 tuner,cx8800,cx88xx
i2c_piix4              13093  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
k10temp                12990  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
sata_sil24             17797  1 
ahci                   21634  9 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3886136     238540          0     648092    1666304
-/+ buffers/cache:    1571740    2552936
Swap:     11829820         32   11829788

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/05zram_disable suspend suspend:

/etc/pm/sleep.d/05zram_disable suspend suspend: not executable.
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
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 16:15:22 CEST 2012: performing suspend
Thu Jun 14 20:44:53 CEST 2012: Awake.
Thu Jun 14 20:44:53 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
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
Running hook /etc/pm/sleep.d/05zram_disable resume suspend:

/etc/pm/sleep.d/05zram_disable resume suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 20:44:55 CEST 2012: Finished.
Initial commandline parameters: --quirk-dpms-suspend
--quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
Fri Jun 15 04:48:01 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
tda9887                17874  1 
ir_jvc_decoder         12490  0 
tda8290                22216  0 
ir_rc6_decoder         12490  0 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tea5767                13113  0 
ir_rc5_decoder         12490  0 
snd_ctxfi              85448  2 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
nvidia              10390874  50 
snd_seq_midi           13132  0 
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 cx88xx
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
soundcore              12600  1 snd
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
k10temp                12990  0 
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
pata_atiixp            12967  4 
sata_sil24             17797  0 
r8169                  47200  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3393928     730748          0     637256    1140508
-/+ buffers/cache:    1616164    2508512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 04:48:04 CEST 2012: performing hibernate
Fri Jun 15 04:48:10 CEST 2012: Awake.
Fri Jun 15 04:48:10 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:
Initial commandline parameters: 
Fri Jun 15 10:08:20 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  4 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda9887                17874  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
tda8290                22216  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
ir_sony_decoder        12493  0 
snd                    55902  21 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia              10390874  80 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
sp5100_tco             13495  0 
asus_atk0110           17742  0 
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
soundcore              12600  1 snd
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
i2c_piix4              13093  0 
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
ppdev                  12849  0 
k10temp                12990  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
ahci                   21634  9 
libahci                25761  1 ahci
sata_sil24             17797  0 
pata_atiixp            12967  4 
ati_agp                13242  0 
r8169                  47200  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    3460064     664612          0     654600    1753300
-/+ buffers/cache:    1052164    3072512
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 10:08:24 CEST 2012: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:15:01 CEST: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  60 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1876808    2247868          0     226828     679048
-/+ buffers/cache:     970932    3153744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
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
Running hook /etc/pm/sleep.d/95_zram_disable suspend suspend:

/etc/pm/sleep.d/95_zram_disable suspend suspend: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
pi&#261;, 15 cze 2012, 10:15:03 CEST: performing suspend
pi&#261;, 15 cze 2012, 10:15:21 CEST: Awake.
pi&#261;, 15 cze 2012, 10:15:21 CEST: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /etc/pm/sleep.d/95_zram_disable resume suspend:

/etc/pm/sleep.d/95_zram_disable resume suspend: not executable.
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
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
pi&#261;, 15 cze 2012, 10:15:25 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:16:07 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
nvidia              10390874  64 
snd_ctxfi              85448  2 
snd_hwdep              13276  1 snd_hda_codec
tda9887                17874  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
snd_seq_midi           13132  0 
tda8290                22216  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12493  0 
tuner                  26836  2 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
soundcore              12600  1 snd
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
i2c_algo_bit           13199  1 cx88xx
tveeprom               17009  1 cx88xx
sp5100_tco             13495  0 
i2c_piix4              13093  0 
k10temp                12990  0 
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
videobuf_dma_sg        18786  2 cx8800,cx88xx
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
btcx_risc              13400  2 cx8800,cx88xx
asus_atk0110           17742  0 
ppdev                  12849  0 
parport_pc             32114  1 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
ahci                   21634  9 
libahci                25761  1 ahci
r8169                  47200  0 
sata_sil24             17797  0 
ati_agp                13242  0 
zram                   18007  1 
             total       used       free     shared    buffers     cached
Mem:       4124676    1938880    2185796          0     226828     680120
-/+ buffers/cache:    1031932    3092744
Swap:     11829820          0   11829820

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:16:09 CEST: performing hibernate
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:23:47 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  60 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1828064    2296612          0     213276     681140
-/+ buffers/cache:     933648    3191028
Swap:      9767484          0    9767484

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:23:50 CEST: performing hibernate
pi&#261;, 15 cze 2012, 10:25:33 CEST: Awake.
pi&#261;, 15 cze 2012, 10:25:33 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 15 cze 2012, 10:25:35 CEST: Finished.
Initial commandline parameters: 
pi&#261;, 15 cze 2012, 10:29:02 CEST: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  64 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1421724    2702952          0      85384     375948
-/+ buffers/cache:     960392    3164284
Swap:      9767484        172    9767312

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
pi&#261;, 15 cze 2012, 10:29:04 CEST: performing hibernate
pi&#261;, 15 cze 2012, 10:30:44 CEST: Awake.
pi&#261;, 15 cze 2012, 10:30:44 CEST: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
pi&#261;, 15 cze 2012, 10:30:45 CEST: Finished.
Initial commandline parameters: 
Fri Jun 15 10:36:33 CEST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux deusex 3.0.0-16-generic-pae #28-Ubuntu SMP Fri Jan 27 19:24:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
xts                    12644  30 
gf128mul               14503  1 xts
decnet                 66297  0 [permanent]
binfmt_misc            17292  1 
dm_crypt               22565  5 
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
tda9887                17874  1 
snd_hda_codec          91859  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
tda8290                22216  0 
snd_ctxfi              85448  2 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_ctxfi
tea5767                13113  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
snd_rawmidi            25241  1 snd_seq_midi
ir_jvc_decoder         12490  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ir_nec_decoder         12490  0 
tuner                  26836  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10390874  64 
snd                    55902  18 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cx8800                 33328  0 
cx88xx                 83026  1 cx8800
rc_core                25797  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
i2c_algo_bit           13199  1 cx88xx
soundcore              12600  1 snd
tveeprom               17009  1 cx88xx
v4l2_common            15793  3 tuner,cx8800,cx88xx
videodev               85626  4 tuner,cx8800,cx88xx,v4l2_common
asus_atk0110           17742  0 
videobuf_dma_sg        18786  2 cx8800,cx88xx
wmi                    18744  0 
ppdev                  12849  0 
parport_pc             32114  1 
sp5100_tco             13495  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
snd_page_alloc         14108  3 snd_hda_intel,snd_ctxfi,snd_pcm
videobuf_core          25409  3 cx8800,cx88xx,videobuf_dma_sg
i2c_piix4              13093  0 
k10temp                12990  0 
btcx_risc              13400  2 cx8800,cx88xx
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
sundance               26629  0 
pata_atiixp            12967  4 
r8169                  47200  0 
ahci                   21634  9 
sata_sil24             17797  0 
libahci                25761  1 ahci
ati_agp                13242  0 
zram                   18007  0 
             total       used       free     shared    buffers     cached
Mem:       4124676    1777148    2347528          0     282504     447156
-/+ buffers/cache:    1047488    3077188
Swap:      9767484        168    9767316

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable hibernate hibernate:

/etc/pm/sleep.d/95_zram_disable hibernate hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Jun 15 10:36:35 CEST 2012: performing hibernate
Fri Jun 15 10:38:13 CEST 2012: Awake.
Fri Jun 15 10:38:13 CEST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sdd:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sde:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /etc/pm/sleep.d/95_zram_disable thaw hibernate:

/etc/pm/sleep.d/95_zram_disable thaw hibernate: not executable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Fri Jun 15 10:38:14 CEST 2012: Finished.
```

Of course, all this was after entering commands from terminal. I did it for a first time today, and after that, of course, all my tries were succesful, it worked from terminal, from unity panel but i had to put commands in terminal just for once. 

Strange.

---

### Post by Toz on 2012-06-15
Interesting, but I'm glad its working for you. Can you post back the contents of /etc/pm/sleep.d/95_zram_disable one more time - there is a "not executable" error happening. And also:
```
ls -l /etc/pm/sleep.d/95_zram_disable
```

---

### Post by firekage on 2012-06-15
> **Toz said:**
> Interesting, but I'm glad its working for you. Can you post back the contents of /etc/pm/sleep.d/95_zram_disable one more time - there is a "not executable" error happening. And also:
```
ls -l /etc/pm/sleep.d/95_zram_disable
```

Yes, it works/worked when i manually entered command in terminal, but it doesen't work trough the script - i think so.


 **95_zram_disable**

```
firekage@deusex:/etc/init.d$ cat /etc/pm/sleep.d/95_zram_disable 
#!/bin/bash

case "${1}" in
    hibernate)
       swapoff /dev/zram0
       umount /dev/zram0
       echo 1 > /sys/block/zram0/reset
       ;;
    thaw)
       mkswap /dev/zram0
       swapon /dev/zram0
       ;;
esac
firekage@deusex:/etc/init.d$ 

```[B]95_zram_disable
[/B]
```
firekage@deusex:/etc/init.d$ ls -l /etc/pm/sleep.d/95_zram_disable 
-rw-r--r-- 1 root root 218 2012-06-14 15:24 /etc/pm/sleep.d/95_zram_disable
```

---

### Post by Toz on 2012-06-15
Try making the script executable:
```
sudo chmod +x /etc/pm/sleep.d/95_zram_disable
```

---

### Post by firekage on 2012-06-16
I would like to thank You very much for Your time (especially for the time cause it took us few days on different  time of a day), for your hard work and helping me out to solve my problem. 

I think that it works now - i won't close this topic (marked as a solved) for few days - i will be trying with hibernation in various occasion, i will be trying to use it as much as i could in order to see what happens. If some problem occurs than i will write another post but so far everything, after chmod +x, works fine and as should be.

For now it works, again - thank You very much. Two tries in a row and two tries ended succesfully. I wouldn't be able to solve it by myself because i don't know this voo-doo magic with scripts. It there is a need to install something, configure it trough modifying scripts - ok, but what You told me is far more advanced for me than simple scripts edition - configuring when they exist.


BTW - i forgot to ask about 2 things. 

1. That number in created scripts, 95 means priority of starting service? It is in seconds? Could be number greater than 100?

2. It is possible to block completly zram? If yes then were and how?

---

### Post by Toz on 2012-06-16
> **firekage said:**
> I would like to thank You very much for Your time (especially for the time cause it took us few days on different  time of a day), for your hard work and helping me out to solve my problem.Now worries, its why we're here.

> 1. That number in created scripts, 95 means priority of starting service? It is in seconds? Could be number greater than 100?
Kind of. Its purely order of execution and its alphabetical (00 comes before 55, but 100 will also come before 55 - think of the numbers as characters, not numbers -> 0123456789abcdefgh......)

> 2. It is possible to block completly zram? If yes then were and how?
The bigger question is how did it get installed? Its not part of the default install and if you didn't mean to install it, then it must be a dependency of another package you installed. If so, that package may require it and may not work without it. Do you have casper installed? See: [http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from]("http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from")

---

### Post by firekage on 2012-06-16
> **Toz said:**
> 
Kind of. Its purely order of execution and its alphabetical (00 comes before 55, but 100 will also come before 55 - think of the numbers as characters, not numbers -> 0123456789abcdefgh......)


Ok, understood.
> 
The bigger question is how did it get installed? Its not part of the default install and if you didn't mean to install it, then it must be a dependency of another package you installed. If so, that package may require it and may not work without it. Do you have casper installed? See: [http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from](http://askubuntu.com/questions/102786/where-did-this-zram-swap-come-from)

Yes, casper is present in my system because, it is propably dependancy  from remastersys, a backup utility. If i remove casper than remastersys doesen't work - i cant run it.


```
firekage@deusex:~$ sudo dpkg -S /usr/share/initramfs-tools/conf.d/compcache
casper: /usr/share/initramfs-tools/conf.d/compcache
```

---

