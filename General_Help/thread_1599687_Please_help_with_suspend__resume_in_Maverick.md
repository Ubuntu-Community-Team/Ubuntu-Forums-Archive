---
title: "Please help with suspend / resume in Maverick"
date: 2010-10-18
forum: General Help
---

### Post by FokkerCharlie on 2010-10-18
Hello!

I recently upgraded (the approved upgrade method, not a fresh install) to Maverick from Lucid on my lappy.  Unfortunately, I now have a problem after resuming from standby.

Going in to standby seems to go fine.  When the computer wakes up, i am presented with a password request as normal, and then my desktop appears... however, it starts slowly.  And continues.  Typically, the mouse pointer does not render at all, an although I can make selections using the mouse (eg by moving to the top RH corner into the shutdown menu) things happen extremely slowly.  Around 10 seconds tends to elapse between a click and a reaction.

I also have the system monitor applet in the panel, which updates every 15 seconds or so, rather than smoothly as normal.  Restarting X fixes the problem.

I have a Toshiba A660, with Corei7, nVidia GT330M.  Proprietary drivers installed via the repos.

Please give me a clue on how to try to get this fixed... I like standby!

Charlie

---

### Post by FokkerCharlie on 2010-10-23
Hello!

OK, I know this is a difficult issue, but I'm still struggling...

I tried disabling the nVidia driver in jockey, the problem persists.  I also tried adding acpi_sleep=nonvs to the kernel options in grub, to no avail.

I blacklisted the following modules:
 video
 toshiba_bluetooth
 bluetooth

to no good effect.

My lsmod:

```
$ lsmod
Module                  Size  Used by
snd_seq_dummy           1806  0 
sha1_generic            2255  0 
ppp_mppe                6458  0 
ppp_async               8070  0 
crc_ccitt               1699  1 ppp_async
michael_mic             2188  8 
arc4                    1497  4 
cryptd                  8140  0 
aes_x86_64              7936  2270 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
joydev                 11363  0 
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792984  2 vboxnetadp,vboxnetflt
snd_hda_codec_nvhdmi    14587  4 
nfsd                  306275  11 
lockd                  75956  1 nfsd
nfs_acl                 2701  1 nfsd
auth_rpcgss            44898  1 nfsd
sunrpc                229541  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4226  1 nfsd
hid_a4tech              2638  0 
snd_usb_audio         105727  1 
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_hda_codec_realtek   299533  1 
usbhid                 42062  0 
hid                    84678  2 hid_a4tech,usbhid
snd_hda_intel          26019  2 
nvidia              10219518  41 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
uvcvideo               62379  0 
snd_seq                57512  4 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
videodev               49359  1 uvcvideo
snd_timer              23850  2 snd_pcm,snd_seq
lib80211_crypt_tkip     8732  0 
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
snd_seq_device          6912  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms               8667  0 
i7core_edac            18090  0 
snd                    64117  18 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1965231  0 
memstick               10185  1 jmb38x_ms
psmouse                62080  0 
serio_raw               4910  0 
edac_core              46822  1 i7core_edac
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lib80211                6175  2 lib80211_crypt_tkip,wl
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
libahci                26167  4 ahci
r8169                  42222  0 
mii                     5261  1 r8169
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci

```

Any suggestions?

Charlie

---

### Post by FokkerCharlie on 2010-11-04
For the benefit of anyone else who might have this issue, it looks like it was a problem related to compiz and sync-to-vblank.  Here's the fix:

CCSM > General Options > Display Settings:
Disable sync to v-blank.

Charlie

---

