---
title: "gateway ML3109 no sound"
date: 2010-02-06
forum: General Help
---

### Post by rflores2323 on 2010-02-06
I have a gateway ML3109 laptop.  everything is working however I do not have any sound.  I tried to do system > admin > system drivers but nothing shows up.

I am running 9.10.  the driver is an ati radeon 200M.

What can I do to get this working.  I have read some threads however they are not for 9.10 and go all the way back to 7.04

any help?? 

here are some outputs

```
corina@corina-laptop:~$ /sbin/lspci -v | grep audio
bash: /sbin/lspci: No such file or directory
corina@corina-laptop:~$ /sbin/lsmod | grep snd
snd_hda_intel         435252  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
corina@corina-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0500000 irq 16
corina@corina-laptop:~$ 

```

Thanks

:p

---

### Post by rflores2323 on 2010-02-06
anyone have an answer?

---

