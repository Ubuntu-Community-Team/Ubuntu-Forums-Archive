---
title: "lspci and lsmod finding my driver"
date: 2012-02-14
forum: General Help
---

### Post by TheKismet on 2012-02-14
Hi I need to find out what driver my internal wireless card uses.  I did lspci and I found the wireless but I don't know which driver it uses by typing  


lspci:  09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34) 

lsmod: 
 nls_iso8859_1           3301  0  vfat                    8778  0  fat                    49021  1 vfat dm_crypt               14720  0  snd_hda_codec_hdmi     21630  1  snd_hda_codec_idt      55495  1  snd_hda_intel          21661  0  snd_hda_codec          80498  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel snd_hwdep               5424  1 snd_hda_codec snd_pcm_oss            36427  0  snd_mixer_oss          13581  1 snd_pcm_oss snd_pcm                68662  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss snd_seq_dummy           1358  0  snd_seq_oss            26216  0  snd_seq_midi            4460  0  snd_rawmidi            18745  1 snd_seq_midi snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event arc4                    1141  2  snd_timer              17803  2 snd_pcm,snd_seq iwlagn                212988  0  snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq rtl8187                51301  0  dell_wmi                1413  0  mac80211              255996  2 iwlagn,rtl8187 snd                    50697  13 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device eeprom_93cx6            1292  1 rtl8187 dell_laptop             7700  0  btusb                  11267  2  sparse_keymap           3194  1 dell_wmi psmouse                52655  0  soundcore               6048  1 snd bluetooth              78085  5 btusb snd_page_alloc          6801  2 snd_hda_intel,snd_pcm uvcvideo               60284  0  dcdbas                  5557  1 dell_laptop cfg80211              153414  3 iwlagn,rtl8187,mac80211 wmi                     8772  1 dell_wmi lp                      7373  0  rfkill                 14987  4 dell_laptop,bluetooth,cfg80211 videodev               75797  1 uvcvideo mac_hid                 3029  0  serio_raw               3744  0  xhci_hcd               62513  0  parport                29468  1 lp squashfs               25015  1  aufs                  157878  135  nls_cp437               4971  1  isofs                  32015  1  ums_realtek             4307  0  i915                  476096  2  drm_kms_helper         31085  1 i915 usb_storage            40902  1 ums_realtek uas                     7524  0  drm                   178158  2 i915,drm_kms_helper i2c_algo_bit            4916  1 i915 intel_agp               9614  1 i915 intel_gtt              13296  3 i915,intel_agp ahci                   18634  2  libahci                19920  1 ahci agpgart                27414  3 drm,intel_agp,intel_gtt video    

sorry for the bad formatting It was formatted better until i pushed save changes.

---

### Post by mikewhatever on 2012-02-14
It uses **iwlagn**.
Check out the output of **lspci -nnk | grep -iA2 net** .

---

### Post by TheKismet on 2012-02-14
> **mikewhatever said:**
> It uses **iwlagn**.
Check out the output of **lspci -nnk | grep -iA2 net** .

 thanks!

---

