---
title: "Audio Card Not Detected"
date: 2012-09-08
forum: General Help
---

### Post by laserbeak43 on 2012-09-08
Hello
i've been trying to get my soundcard to work. it's an intel; chipset with realtek code. i've ran a list of commands here
```

$ lsmod | grep '^snd'
snd_hda_intel          32765  0 
snd_hda_codec         109562  1 snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
dad@Amon-PC:~$ lspci -vv | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
dad@Amon-PC:~$ cat /proc/asound/cards
--- no soundcards ---
dad@Amon-PC:~$ ^C
dad@Amon-PC:~$ 
dad@Amon-PC:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82Q963/Q965 Memory Controller Hub [8086:2990] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82Q963/Q965 Integrated Graphics Controller [8086:2992] (rev 02)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] [8086:2820] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] [8086:2825] (rev 02)
3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
```
and i've manually installed the linux drivers here:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Could someone please help me figure out what's wrong?
Thanks

---

### Post by laserbeak43 on 2012-09-10
Bump.

---

### Post by laserbeak43 on 2012-09-11
Has no one ever seen something like this before?

---

### Post by laserbeak43 on 2012-09-12
I've just bought a new, USB soundcard to put on, hoping that my problems would be solved, but i still have the same problem. Surely someone can help me????

---

