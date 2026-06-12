---
title: "686 Kernel OpenGL Software Rasterizing ?"
date: 2009-11-02
forum: General Help
---

### Post by WitchCraft on 2009-11-02
Question:

I recently installed linux kernel 2.6.30-686-bigmem.

But something is wrong, presumably with my intel 915 firmware...
When I installed 686-bigmem, OpenGL switched to Software Rasterizing.

While direct rendering is true, it uses Software GL emulation instead of hardware GL. Well, wouldn't be a problem if only it wasn't slower than a snail...

I copied the firmware from the old kernel to a folder with name 2.6.30-686-bigmem, which is what uname -r returns, and restarted.

That didn't help.
I have the very same problem also with ArchLinux, only that there it's only kernel 686, without bigmem.

I seem to do something wrong.
Anybody knows how I get it working with 686/bigmem ?

---

### Post by Giblet5 on 2009-11-02
I don't have an intel GPU, but I'm fairly certain that you must install a hardware driver before OpenGL will use hardware acceleration.

Boot the old kernel.

Make a list of the driver modules loaded: ```
lsmod > oldkernel.mods
```

Boot the new kernel.

Make a list of the driver modules loaded: ```
lsmod > newkernel.mods
```

The answer lies in the diff between those two lists. Sorry I can't just give you an answer, but I have a Real GPU®. ;)

---

### Post by WitchCraft on 2009-11-04
> **Giblet5 said:**
> I don't have an intel GPU, but I'm fairly certain that you must install a hardware driver before OpenGL will use hardware acceleration.

Boot the old kernel.

Make a list of the driver modules loaded: ```
lsmod > oldkernel.mods
```

Boot the new kernel.

Make a list of the driver modules loaded: ```
lsmod > newkernel.mods
```

The answer lies in the diff between those two lists. Sorry I can't just give you an answer, but I have a Real GPU®. ;)

interesting, will try it asap.

---

### Post by WitchCraft on 2009-11-04
newbigmemkernelmods.txt
```

Module                  Size  Used by
isofs                  27592  0 
udf                    67284  0 
nls_base                6416  2 isofs,udf
crc_itu_t               2148  1 udf
binfmt_misc             7120  1 
ppdev                   6348  0 
lp                      8012  0 
parport                31144  2 ppdev,lp
i915                  149420  0 
drm                   138584  1 i915
acpi_cpufreq            7640  0 
cpufreq_stats           3520  0 
cpufreq_userspace       2768  0 
cpufreq_conservative     6256  0 
cpufreq_powersave       1292  0 
fuse                   47752  1 
loop                   13324  0 
snd_hda_codec_idt      49836  1 
snd_hda_intel          22284  2 
snd_hda_codec          63580  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6120  1 snd_hda_codec
snd_pcm_oss            32232  0 
snd_mixer_oss          12368  1 snd_pcm_oss
snd_pcm                62552  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            5688  0 
snd_rawmidi            18596  1 snd_seq_midi
snd_seq_midi_event      6212  1 snd_seq_midi
snd_seq                42436  2 snd_seq_midi,snd_seq_midi_event
snd_timer              17436  2 snd_pcm,snd_seq
snd_seq_device          6136  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             3164  0 
snd                    49060  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8676  0 
rfkill                  9668  1 dell_laptop
soundcore               6184  1 snd
snd_page_alloc          8252  2 snd_hda_intel,snd_pcm
rng_core                3672  0 
ipw2200               120012  0 
libipw                 24644  1 ipw2200
lib80211                6048  2 ipw2200,libipw
iTCO_wdt                9712  0 
dcdbas                  6780  1 dell_laptop
psmouse                37528  0 
serio_raw               4560  0 
evdev                   8028  17 
processor              34568  2 acpi_cpufreq
button                  5060  0 
battery                 6012  0 
ac                      2960  0 
ext3                  107172  1 
jbd                    41036  1 ext3
mbcache                 6924  1 ext3
ide_gd_mod             19856  3 
ide_cd_mod             24484  0 
cdrom                  30328  1 ide_cd_mod
ata_generic             4340  0 
libata                151324  1 ata_generic
scsi_mod              131800  1 libata
ide_pci_generic         3632  0 
b44                    22524  0 
uhci_hcd               19216  0 
ssb                    37720  1 b44
pcmcia                 24304  1 ssb
piix                    5680  2 
pcmcia_core            31240  2 ssb,pcmcia
mii                     4664  1 b44
ehci_hcd               30208  0 
ide_core               88012  4 ide_gd_mod,ide_cd_mod,ide_pci_generic,piix
video                  18044  1 i915
output                  2604  1 video
intel_agp              23244  1 
intelfb                30880  0 
i2c_algo_bit            4860  2 i915,intelfb
agpgart                30860  4 drm,intel_agp,intelfb
i2c_core               20844  4 i915,drm,intelfb,i2c_algo_bit
usbcore               126404  3 uhci_hcd,ehci_hcd
thermal                12580  0 
fan                     4044  0 
thermal_sys            13140  4 processor,video,thermal,fan

```
oldmods.mods
```

Module                  Size  Used by
isofs                  27752  0 
udf                    67220  0 
crc_itu_t               1772  1 udf
binfmt_misc             7104  1 
ppdev                   5772  0 
lp                      8048  0 
parport                31348  2 ppdev,lp
i915                  184320  1 
drm                   139568  2 i915
i2c_algo_bit            4940  1 i915
i2c_core               20028  3 i915,drm,i2c_algo_bit
ipv6                  236976  30 
acpi_cpufreq            7560  0 
cpufreq_stats           3656  0 
cpufreq_userspace       2632  0 
cpufreq_conservative     6360  0 
cpufreq_ondemand        6152  1 
freq_table              4016  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       1240  0 
fuse                   52488  1 
loop                   13764  0 
snd_hda_codec_idt      50392  1 
snd_hda_intel          23384  1 
snd_hda_codec          58184  2 snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            32416  0 
snd_mixer_oss          13436  1 snd_pcm_oss
snd_pcm                65296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2384  0 
snd_seq_oss            23244  0 
snd_seq_midi            5612  0 
snd_rawmidi            19016  1 snd_seq_midi
snd_seq_midi_event      6260  2 snd_seq_oss,snd_seq_midi
snd_seq                42668  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18136  2 snd_pcm,snd_seq
snd_seq_device          6300  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48216  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt                9820  0 
joydev                  8860  0 
soundcore               6380  1 snd
snd_page_alloc          8092  2 snd_hda_intel,snd_pcm
processor              34848  2 acpi_cpufreq
rng_core                3676  0 
ac                      3844  0 
battery                 9968  0 
button                  5160  0 
psmouse                37800  0 
serio_raw               4788  0 
ipw2200               123832  0 
libipw                 25188  1 ipw2200
lib80211                5992  2 ipw2200,libipw
dcdbas                  6708  0 
evdev                   8324  12 
ext3                  107512  1 
jbd                    41808  1 ext3
mbcache                 7000  1 ext3
ide_gd_mod             14264  3 
ide_cd_mod             24000  0 
cdrom                  29884  1 ide_cd_mod
ata_generic             4316  0 
ata_piix               22024  0 
libata                153724  2 ata_generic,ata_piix
uhci_hcd               19204  0 
scsi_mod              137696  1 libata
ide_pci_generic         3592  0 
b44                    24420  0 
video                  18780  1 i915
output                  2596  1 video
ehci_hcd               30856  0 
ssb                    37996  1 b44
pcmcia                 31156  1 ssb
pcmcia_core            31256  2 ssb,pcmcia
mii                     4708  1 b44
piix                    5696  2 
ide_core               89596  4 ide_gd_mod,ide_cd_mod,ide_pci_generic,piix
usbcore               131244  3 uhci_hcd,ehci_hcd
nls_base                6780  3 isofs,udf,usbcore
intel_agp              23324  1 
agpgart                31152  3 drm,intel_agp
thermal                12748  0 
fan                     4060  0 
thermal_sys            13588  4 processor,video,thermal,fan

```


what now ?

---

### Post by WitchCraft on 2009-11-08
bump

---

### Post by WitchCraft on 2009-11-10
bump.

---

### Post by WitchCraft on 2009-11-12
bump.

---

### Post by WitchCraft on 2009-11-26
Solved. Anyway had to reinstall the entire operating system.
Now it works.

---

