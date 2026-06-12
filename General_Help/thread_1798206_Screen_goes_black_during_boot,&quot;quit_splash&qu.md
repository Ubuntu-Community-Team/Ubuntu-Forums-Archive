---
title: "Screen goes black during boot,&quot;quit splash&quot; off"
date: 2011-07-06
forum: General Help
---

### Post by vehemoth on 2011-07-06
Hi
I disabled quit splash in the grub file.
However during boot the screen goes black then after a while it goes back to the text output
Is this fixable and is this caused by plymouth.
Thanks in advance

---

### Post by DanneStrat on 2011-07-06
> **vehemoth said:**
> Hi
I disabled quit splash in the grub file.
However during boot the screen goes black then after a while it goes back to the text output
Is this fixable and is this caused by plymouth.
Thanks in advance

Hi.

Could you post the contents of the grub config file?

You can do:

```
cat /etc/default/grub
```

and post the output.

---

### Post by vehemoth on 2011-07-06
Here you go
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by DanneStrat on 2011-07-06
Deleted

---

### Post by DanneStrat on 2011-07-06
If you have mail notifications on this thread, just ignore what I wrote in 

the previous post.

Your grub file looks fine, so there's no problem there.

What do you want to accomplish?

Is there a specific problem you need to fix?

---

### Post by vehemoth on 2011-07-06
On boot there is a text output, halfway through the boot the screen goes black and stays so for about 3-5 seconds, the text then carries on.
I would like to get rid of that black screen in the middle and just have the text output the whole time, until it gets to gdm.

---

### Post by DanneStrat on 2011-07-06
> **vehemoth said:**
> On boot there is a text output, halfway through the boot the screen goes black and stays so for about 3-5 seconds, the text then carries on.
I would like to get rid of that black screen in the middle and just have the text output the whole time, until it gets to gdm.

Alright.

What graphics card do you have?

Are you using non-free drivers?

KMS (kernel mode setting) was introduced to make the startup sequence 

flicker-free by setting the right video mode early in the boot. If you're 

using a proprietary driver like catalyst or nvidia, which are incompatible 

with kms, you may experience a black screen with a blinking cursor when 

switching video modes which is normal.

---

### Post by DanneStrat on 2011-07-06
If you're using a proprietary driver, you can always try to boot with 

"nomodeset" which disables kms.

From my experience, this is normally not necessary, but in your case

it may help.

If you want to try it just do:

```
gksudo gedit /etc/default/grub
```

And get to the same line as before and append "nomodeset" like this:

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Save the file and reboot.

---

### Post by vehemoth on 2011-07-06
The graphics chipset is Intel® GMA 3150
I don't think that there are propriety drivers and I just used whatever came with ubuntu.

---

### Post by DanneStrat on 2011-07-07
> **vehemoth said:**
> The graphics chipset is Intel® GMA 3150
I don't think that there are propriety drivers and I just used whatever came with ubuntu.

OK, the intel drivers in ubuntu has support for kms so you should 

have seemless video switching at startup. However, I found an 

interesting article that may explain the cause of the black 

screen. Even though the article is from the gentoo wiki, chances are

the same applies to ubuntu:

[http://en.gentoo-wiki.com/wiki/Intel_GMA](http://en.gentoo-wiki.com/wiki/Intel_GMA)

> Kernel Modesetting Causes Blackscreen
If you have blackscreens on boot, it may be because you've built both Framebuffer Console support and the i915 driver (with KMS enabled) as modules. i915 loads & enables KMS, but fbcon never loads so nothing is displayed.
Here is the fatal combo: DRM_I915=m DRM_I915_KMS=y FRAMEBUFFER_CONSOLE=m
It is highly recommended to build in the i915 driver and fbcon support, rather than building them as modules. See the following upstream bug report for details:
[https://bugs.freedesktop.org/show_bug.cgi?id=22674](https://bugs.freedesktop.org/show_bug.cgi?id=22674)
On the other side you might circumvent this by explicitely loading the module fbcon, eg. put this into the file /etc/conf.d/modules:
modules_2_6="${modules_2_6} fbcon" module_fbcon_args_2_6=""

Do a

```
lsmod
```

so we can find out what modules you have.

---

### Post by vehemoth on 2011-07-08
Sorry for the late reply
```

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  206 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
dm_crypt               22463  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ath9k                 103633  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k_hw              300328  2 ath9k,ath9k_common
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13666  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
psmouse                73312  0 
serio_raw              12990  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
drm_kms_helper         40745  1 i915
ahci                   21591  1 
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
atl1c                  36237  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

---

