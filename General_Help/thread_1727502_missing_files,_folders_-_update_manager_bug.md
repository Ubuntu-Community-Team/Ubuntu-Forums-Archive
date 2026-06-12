---
title: "missing files, folders - update manager bug?"
date: 2011-04-12
forum: General Help
---

### Post by jimww on 2011-04-12
i have a serious error, which i need to resolve. files and folders are missing after a restart, probably caused by the upgrade manager.

i had been working on a file in blender, for several hours, creating and updating image files, and creating directories. the upgrade manager started in the background, but was having problems connecting. i left it to run while i continued to work, assuming it was a network error. i went back to see if there was any progress connecting, expecting to see the update information, but it locked up the computer instead, no cursor control, no keyboard input. had to manually force a restart. 

on restart, checked all drives, which had mounted read only, all of which checked out fine, no errors, mounted fine. but all the files and directories i created are gone. the file i was working on is corrupt, console message states that it is 'incomplete'. i was able to recover it from the blender temp folder, but it has references to the missing folders and directories. which do not exist. anywhere. checked that it was not a permissions issue, or written to a different directory. i had done some renders, which i saved, which are also gone. 

there are numerous in-out errors in the log file, relating to an update manager error, which also references some other modules:

Apr 12 12:02:40 jimww-desktop kernel: [40640.061248] BUG: soft lockup - CPU#2 stuck for 61s! [update-manager:27894]
Apr 12 12:02:40 jimww-desktop kernel: [40640.061251] Modules linked in: usb_storage binfmt_misc parport_pc ppdev nls_utf8 hfsplus iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack nf_defrag_ipv4 iptable_mangle iptable_filter ip_tables x_tables nvidia(P) snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd applesmc led_class input_polldev wacom i5000_edac soundcore edac_core i5k_amb ioatdma snd_page_alloc i7300_idle(+) dca sbp2 shpchp ieee1394 lp parport raid10 raid456 async_pq async_xor xor async_memcpy async_raid6_recov raid6_pq async_tx hid_apple raid1 usbhid hid raid0 firewire_ohci firewire_core crc_itu_t e1000e multipath linear

i could understand these files being missing if they were temp files, but they were written to disk, and saved multiple times, as i revised them. a crash could leave an open file in a corrupt state, but to erase all references? this error makes no sense. trying to repeat it to file a bug report is problematic as well. any advice would be helpful, on how to resolve the error, or how to go about reporting it as a bug. thanks.

---

### Post by jimww on 2011-04-13
it happened again today, but without the file loss. upgrade manager was the culprit again. lots of IO errors in the log again. but after a restart and drive checks, i did get it to run the updates, and i have turned off auto update.

a bit more info:

ubuntu 10.10 64bit
MacPro

---

