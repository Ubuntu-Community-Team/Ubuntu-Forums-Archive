---
title: "Problem suspend with IR receiver in USB connected"
date: 2010-08-12
forum: General Help
---

### Post by alda2 on 2010-08-12
I have a nvidia based pc. When I have connected USB device IR receiver  IgorCesko suspend to RAM and to Disk isn't working.  System will jump into black screen with blinking cursor in upper left  corner. Only power off is possible. When usb devices is disconnected,  than suspend is working correctly. Tested on ubuntu 9.10 and 10.04 - for  both the same problem.

I found that my problem is lirc_igorplugusb module in lsmod :

xbmc@XBMCLive:~$ lsmod
Module                  Size  Used by
udf                    80900  1
crc_itu_t               1852  1 udf
lirc_mceusb            15520  0
snd_hda_codec_nvhdmi     4828  1
snd_hda_codec_realtek   203328  1
snd_hda_intel          26920  3
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
ses                     6524  0
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
enclosure               7840  1 ses
snd_timer              22276  3 snd_pcm,snd_seq
nvidia               8880868  38
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0
shpchp                 32272  0
agpgart                34988  1 nvidia
lp                      8964  0
parport                35340  1 lp
[COLOR=Red]lirc_igorplugusb        5116  1[/COLOR]
lirc_dev               10804  4 lirc_mceusb,lirc_igorplugusb
usb_storage            52576  2
usbhid                 38208  0
forcedeth              54152  0



I tried to kill him :


 xbmc@XBMCLive:~$ rmmod lirc_igorplugusb
ERROR: Module lirc_igorplugusb is in use


 Next step which I did :
I stopped lirc :

root@XBMCLive:~# sudo /etc/init.d/lirc stop
* Stopping remote control daemon(s): LIRC [ OK ]


 and tried again stop lirc_igorplugusb module :


 root@XBMCLive:~# rmmod lirc_igorplugusb
Killed


 after this I used pm-suspend. On the screen I can see :


 PM: Syncing filesystems....done
PM: Preparing system for mem sleep
Freezing user space processes...( elapsed 0.00 seconds ) done
Freezing remaining freezable tasks...( elapsed 0.00 seconds ) done
PM:entering mem sleep
Suspending console(s) ( use no_console_suspend to debug )


and pc freeze.



                 so I checked again lsmod and lirc_igorplugusb module is still here  :
 root@XBMCLive:~# lsmod
Module                  Size  Used by
snd_hda_codec_nvhdmi     4828  1
snd_hda_codec_realtek   203328  1
snd_hda_intel          26920  3
snd_hda_codec          75708  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dm_crypt               12928  0
nvidia               8880868  38
[COLOR=Red]lirc_igorplugusb        5116  0[/COLOR]
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0
lirc_dev               10804  1 lirc_igorplugusb
shpchp                 32272  0
agpgart                34988  1 nvidia
lp                      8964  0
parport                35340  1 lp
usb_storage            52576  0
usbhid                 38208  0
forcedeth              54152  0


 I tried next rmmod :
 root@XBMCLive:~# rmmod -f lirc_igorplugusb
ERROR: Removing 'lirc_igorplugusb': Device or resource busy


 and I also tested rmmod on lirc_dev :


 root@XBMCLive:~# rmmod lirc_dev
ERROR: Module lirc_dev is in use by lirc_igorplugusb


 What can I do to kill this module and get suspend running ?


 Alda

---

