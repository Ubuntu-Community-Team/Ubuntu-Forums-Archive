---
title: "Sony vaio sound problem"
date: 2010-03-15
forum: General Help
---

### Post by schwabdale on 2010-03-15
Hello,
I have a Sony Vaio with an I3 processor. I installed Ubuntu 10.04 and the sound is not working. Can someone please tell me how to fix this?
Here is the link to the laptop.

[http://www.bestbuy.com/site/Sony+-+VAIO+Laptop+with+Intel%26%23174%3B+Core%26%23153%3B+i3+Processor+-+Silvery+White/9765452.p?id=1218169694401&skuId=9765452](http://www.bestbuy.com/site/Sony+-+VAIO+Laptop+with+Intel%26%23174%3B+Core%26%23153%3B+i3+Processor+-+Silvery+White/9765452.p?id=1218169694401&skuId=9765452)

---

### Post by thegod_slayer on 2010-03-15
lsmod | grep snd

post me the output of the above command

---

### Post by Cuppa-Chino on 2010-03-15
Hi, two things:

a)```
$ lsmod | grep snd
snd_hda_codec_atihdmi     2927  1 
snd_hda_codec_realtek   317207  1 
snd_hda_intel          25370  2 
snd_hda_codec         103619  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7002  1 snd_hda_codec
snd_pcm_oss            47321  0 
snd_mixer_oss          15862  1 snd_pcm_oss
snd_pcm                95335  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1910  0 
snd_seq_oss            34818  0 
snd_seq_midi            6149  0 
snd_rawmidi            23795  1 snd_seq_midi
snd_seq_midi_event      7171  2 snd_seq_oss,snd_seq_midi
snd_seq                61264  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23657  2 snd_pcm,snd_seq
snd_seq_device          6978  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77137  20 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8788  2 snd_hda_intel,snd_pcm

```

and more importantly b) there are now a number of threads about this topic (I also have one of the sony vaio E-series laptops) the most active is this one:

[http://ubuntuforums.org/showthread.php?t=1424795]("http://ubuntuforums.org/showthread.php?t=1424795")

I would suggest to gather all requests there. Some things (ie sound and discrete graphics) are not fully working yet on 10.04 alpha3. But should be available soon.

---

### Post by schwabdale on 2010-03-15
snd_hda_codec_intelhdmi    11590  1 
snd_hda_codec_realtek   203072  1 
snd_hda_intel          21717  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35244  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70758  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19024  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47231  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19066  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54116  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm

---

### Post by davehn on 2010-06-20
> **schwabdale said:**
> Hello,
I have a Sony Vaio with an I3 processor. I installed Ubuntu 10.04 and the sound is not working. Can someone please tell me how to fix this?
Here is the link to the laptop.

[http://www.bestbuy.com/site/Sony+-+VAIO+Laptop+with+Intel%26%23174%3B+Core%26%23153%3B+i3+Processor+-+Silvery+White/9765452.p?id=1218169694401&skuId=9765452](http://www.bestbuy.com/site/Sony+-+VAIO+Laptop+with+Intel%26%23174%3B+Core%26%23153%3B+i3+Processor+-+Silvery+White/9765452.p?id=1218169694401&skuId=9765452)


I had the same problem with my sony vio i3 E series. I had to upgrade the alsa driver and kernel to 2.6.32.22-generic in this link you'll find the solution it worked for me read carefully comment #39 and #48
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695:popcorn:](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/comment-page-2/#comment-695:popcorn:)

---

