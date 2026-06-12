---
title: "suspend to ram not working 9.10"
date: 2009-11-08
forum: General Help
---

### Post by dencamel on 2009-11-08
Hello,

When trying to suspend to ram I see my screen goes blank but the system starts up again and a login screen is shown... 
I've searched these forums but no result..

Thanks for any reply on this.

---

### Post by musarraf172 on 2009-11-28
> **dencamel said:**
> Hello,

When trying to suspend to ram I see my screen goes blank but the system starts up again and a login screen is shown... 
I've searched these forums but no result..

Thanks for any reply on this.

Same problem with my IBM R51 laptop.. But hibernate is working..

---

### Post by dencamel on 2009-11-30
> **musarraf172 said:**
> Same problem with mu IBM R51 laptop.. But hibernate is working..

Hibernate is not even working on my laptop (Targa Traveller 1561) it only shuts the pc down.

---

### Post by musarraf172 on 2009-11-30
> **dencamel said:**
> Hibernate is not even working on my laptop (Targa Traveller 1561) it only shuts the pc down.

Can you tell me what message are  you getting while hibernating ??
And what medium you are using a swap file or a swap partition?

---

### Post by dencamel on 2009-12-01
Hi,

Thanks for your help.

I have a swap partititon of 2.57GB since my RAM consists of 1.8GB I suppose this is enough...
When I start to hibernate I see the drive is starting up and the state is probably written but then the system just shuts down...

Here's the logs of pm-suspend as far as I can see it there are no errors:

Initial commandline parameters: 
Tue Dec  1 18:19:36 CET 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux kc-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78216  0 
vboxnetflt             84776  0 
vboxdrv               121064  1 vboxnetflt
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
ecb                     2524  2 
rt61pci                20576  0 
crc_itu_t               1852  1 rt61pci
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
rt2x00pci               7900  1 rt61pci
rt2x00lib              29756  2 rt61pci,rt2x00pci
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00pci,rt2x00lib
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
joydev                 10272  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               9586440  38 
cfg80211               93052  2 rt2x00lib,mac80211
psmouse                56500  0 
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
lp                      8964  0 
parport                35340  2 ppdev,lp
k8temp                  4188  0 
ip_tables              11692  1 iptable_filter
eeprom_93cx6            1916  1 rt61pci
serio_raw               5280  0 
agpgart                34988  1 nvidia
i2c_nforce2             6784  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
x_tables               16544  1 ip_tables
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
forcedeth              54152  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:       1932192     614508    1317684          0      21448     277940
-/+ buffers/cache:     315120    1617072
Swap:      2690848          0    2690848
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Tue Dec  1 18:19:38 CET 2009: performing hibernate

---

### Post by musarraf172 on 2009-12-01
> **dencamel said:**
> Hi,

Thanks for your help.

I have a swap partititon of 2.57GB since my RAM consists of 1.8GB I suppose this is enough...
When I start to hibernate I see the drive is starting up and the state is probably written but then the system just shuts down...

Here's the logs of pm-suspend as far as I can see it there are no errors:

Initial commandline parameters: 
Tue Dec  1 18:19:36 CET 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000record hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk hibernate hibernate: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: Linux kc-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78216  0 
vboxnetflt             84776  0 
vboxdrv               121064  1 vboxnetflt
snd_hda_codec_si3054     4636  1 
snd_hda_codec_realtek   203328  1 
arc4                    1660  2 
ecb                     2524  2 
rt61pci                20576  0 
crc_itu_t               1852  1 rt61pci
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
rt2x00pci               7900  1 rt61pci
rt2x00lib              29756  2 rt61pci,rt2x00pci
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00pci,rt2x00lib
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
joydev                 10272  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               9586440  38 
cfg80211               93052  2 rt2x00lib,mac80211
psmouse                56500  0 
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
lp                      8964  0 
parport                35340  2 ppdev,lp
k8temp                  4188  0 
ip_tables              11692  1 iptable_filter
eeprom_93cx6            1916  1 rt61pci
serio_raw               5280  0 
agpgart                34988  1 nvidia
i2c_nforce2             6784  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
x_tables               16544  1 ip_tables
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
forcedeth              54152  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
             total       used       free     shared    buffers     cached
Mem:       1932192     614508    1317684          0      21448     277940
-/+ buffers/cache:     315120    1617072
Swap:      2690848          0    2690848
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
/etc/pm/sleep.d/action_wpa hibernate hibernate: success.
Tue Dec  1 18:19:38 CET 2009: performing hibernate


Everything seems to be fine . Did you add resume parameter in your grub.cfg??

If not , then just open your /etc/default/grub and near 9th line you will find an entry like "GRUB_CMDLINE_LINUX_DEFAULT". 
Here you add "resume=resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66" 
The UUID must be replaced with your swap partition UUID. Then from terminal run "sudo update-grub2"
Now the "resume" parameter should be visible in your /boot/grub/grub.cfg
and resume should be working. The following is a sample of /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66   splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


And the grub.cfg should look like


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
insmod tga
if background_image /boot/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro   resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66  splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro   resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66   splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

---

### Post by dencamel on 2009-12-03
Hello,

I'm sorry but I don't have these files /etc/default/grub and /boot/grub/grub.cfg






Everything seems to be fine . Did you add resume parameter in your grub.cfg??

If not , then just open your /etc/default/grub and near 9th line you will find an entry like "GRUB_CMDLINE_LINUX_DEFAULT". 
Here you add "resume=resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66" 
The UUID must be replaced with your swap partition UUID. Then from terminal run "sudo update-grub2"
Now the "resume" parameter should be visible in your /boot/grub/grub.cfg
and resume should be working. The following is a sample of /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66   splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


And the grub.cfg should look like


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
insmod tga
if background_image /boot/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
linux /boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

---

### Post by musarraf172 on 2009-12-03
> **dencamel said:**
> Hello,

I'm sorry but I don't have these files /etc/default/grub and /boot/grub/grub.cfg






Everything seems to be fine . Did you add resume parameter in your grub.cfg??

If not , then just open your /etc/default/grub and near 9th line you will find an entry like "GRUB_CMDLINE_LINUX_DEFAULT". 
Here you add "resume=resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66" 
The UUID must be replaced with your swap partition UUID. Then from terminal run "sudo update-grub2"
Now the "resume" parameter should be visible in your /boot/grub/grub.cfg
and resume should be working. The following is a sample of /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66   splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


And the grub.cfg should look like


#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
insmod tga
if background_image /boot/grub/Glasses_800_edit.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
linux /boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro resume=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6e9bf6ba-f80a-4009-81c8-fe0f21f48c66
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###





Did you do a fresh install ? If so then you must have those files as GRUB2 is the boot loader. If it is an upgrade from Jaunty (9.04) then u may have legacy grub.If that is the case then you need to edit your "/boot/grub/menu.lst" file.

In terminal , type ,

$ sudo gedit /boot/grub/menu.lst 

and post the o/p here.

---

### Post by dencamel on 2009-12-06
> **musarraf172 said:**
> Did you do a fresh install ? If so then you must have those files as GRUB2 is the boot loader. If it is an upgrade from Jaunty (9.04) then u may have legacy grub.If that is the case then you need to edit your "/boot/grub/menu.lst" file.

In terminal , type ,

$ sudo gedit /boot/grub/menu.lst 

and post the o/p here.

Hello,

Yes it's an upgrade from 9.04 and I didn't do an upgrade to grub2 :-)
Here's the content of the menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

---

### Post by musarraf172 on 2009-12-06
Edit the file as I have shown and replace the resume uuid with your swap partition's uuid. I have marked in red.

you can find the uuid by running " Sudo blkid" in terminal..

Then run 

$ sudo update-initramfs -u 

Then Try to hibernate your computer



## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc  [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc  [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc [COLOR="Red"]resume=UUID=1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc[/COLOR] ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        1b9c449a-5f3d-45b3-9b10-8f3e45c7fabc
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Talion86 on 2009-12-06
Suspend and Hibernate are not working for me either.
Suspend used to work. It first stopped working a few weeks ago (I don't remember whether it happened after some update), but was okay a few restarts later without any particular reason. Now it stopped working again, and this time it seems to be permanent.

dmesg says:
> [  772.932470] PM: Preparing system for mem sleep
[  772.932479] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  772.933990] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  772.934183] PM: Entering mem sleep
[  772.934205] Suspending console(s) (use no_console_suspend to debug)
[  772.934609] pci 0000:00:02.0: PCI INT A disabled
[  772.948151] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  773.190577] sd 0:0:0:0: [sda] Stopping disk
[  773.502905] uvcvideo: Failed to set UVC commit control : -108 (exp. 26).
[  773.502920] uvcvideo 1-5:1.1: resume error -5
[  773.502944] pm_op(): usb_dev_suspend+0x0/0x10 returns -108
[  773.502955] PM: Device 1-5 failed to suspend: error -108
[  773.502963] PM: Some devices failed to suspend
[  773.503047] sd 0:0:0:0: [sda] Starting disk
[  774.624146] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  774.624164] pci 0000:00:02.0: setting latency timer to 64
[  774.625223] uvcvideo: Failed to set UVC commit control : -108 (exp. 26).
[  774.625229] uvcvideo 1-5:1.1: resume error -5
[  774.784359] PM: resume devices took 1.284 seconds
[  774.784668] PM: Finishing wakeup.
[  774.784673] Restarting tasks ... done.
[  774.871939] r8169: eth0: link up
[  775.225040] CPU0 attaching NULL sched-domain.
[  775.225054] CPU1 attaching NULL sched-domain.
[  775.240264] CPU0 attaching sched-domain:
[  775.240279]  domain 0: span 0-1 level SIBLING
[  775.240292]   groups: 0 1
[  775.240314] CPU1 attaching sched-domain:
[  775.240324]  domain 0: span 0-1 level SIBLING
[  775.240335]   groups: 1 0
When I try to suspend, the screen is black for a moment but immediately returns to the normal screen afterwards.

Edit - seems to be already known as an Karmic / MSI Wind U100 issue
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/455408)

---

### Post by dencamel on 2009-12-06
Thanks a lot Musarraf it's working now... 

At first I thought it just shuts the system completely down but then it reloaded the session back in memory...
Just out of curiosity is this a workaround to force a hibernate?
__

---

### Post by musarraf172 on 2009-12-07
> **dencamel said:**
> Thanks a lot Musarraf it's working now... 

At first I thought it just shuts the system completely down but then it reloaded the session back in memory...
Just out of curiosity is this a workaround to force a hibernate?
__

This is not exactly an workaround. If your swap partition is not recognized properly during installation , the resume setting in grub configuration will not be done. These manual steps are required to set up the resume configuration in grub.

Enjoy your karmic kola...

what about your suspend to ram ???

---

### Post by dencamel on 2009-12-08
> **musarraf172 said:**
> This is not exactly an workaround. If your swap partition is not recognized properly during installation , the resume setting in grub configuration will not be done. These manual steps are required to set up the resume configuration in grub.

Enjoy your karmic kola...

what about your suspend to ram ???

Thanks for your explanation, now I understand what's going on :-)

The suspend to ram is not working, I hear the drive stopping but then it wakes up and shows a login screen. I already posted the log output for this but I don't see any errors...

---

### Post by musarraf172 on 2009-12-08
> **dencamel said:**
> Thanks for your explanation, now I understand what's going on :-)

The suspend to ram is not working, I hear the drive stopping but then it wakes up and shows a login screen. I already posted the log output for this but I don't see any errors...

It is neither working for me !! Still I could not figure out this..

---

