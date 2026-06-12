---
title: "Asus P5W DH: CPU Scaling Frequency not supported"
date: 2010-05-05
forum: General Help
---

### Post by madbyte on 2010-05-05
Hi,

This is a problem I have since Ubuntu 9.10 64 bits (My first Ubuntu experience). After a fresh install of Ubuntu 10.04 64 bits the problem still persist. I have Windows 7 and Windows XP and the scaling frequency is working ok, but I can't get it to work in Ubuntu. My mb is an Asus P5W DH Deluxe, 6Gb Ram, Intel CoreDuo 6400 with the SpeedStep enabled in the Bios. After adding the Frequency Monitor Applet and booting again, I'm getting the same warning: Scaling Frequency not Supported. 
Here some information:

```

ramiro@ramiro-desktop:~$ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  1 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
rtl8187                53204  0 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515131  2 
mac80211              238128  1 rtl8187
led_class               3732  1 rtl8187
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
cfg80211              148386  2 rtl8187,mac80211
eeprom_93cx6            1765  1 rtl8187
joydev                 11072  0 
psmouse                64608  0 
cypress_m8             20185  0 
usbserial              39067  1 cypress_m8
serio_raw               4918  0 
asus_atk0110           10033  0 
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i82975x_edac            3159  0 
drm                   198770  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
edac_core              45423  1 i82975x_edac
lp                      9336  0 
parport                37160  2 ppdev,lp
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
usbhid                 40988  0 
hid                    83376  1 usbhid
floppy                 63156  0 
sky2                   48803  0 
ahci                   37646  3 
ramiro@ramiro-desktop:~$ 
ramiro@ramiro-desktop:~$ cat/proc/cpuinfo
bash: cat/proc/cpuinfo: No existe el fichero ó directorio
ramiro@ramiro-desktop:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping    : 6
cpu MHz        : 2136.857
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4273.71
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping    : 6
cpu MHz        : 2136.857
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips    : 4274.00
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

ramiro@ramiro-desktop:~$ sudo modprobe acpi-cpufreq
[sudo] password for ramiro: 
FATAL: Module acpi_cpufreq not found.
ramiro@ramiro-desktop:~$ 

```Any help?

Thank you.

---

