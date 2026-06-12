---
title: "Constant Graphics? crashes"
date: 2012-08-23
forum: General Help
---

### Post by Velvet Karuda Leopard on 2012-08-23
Not sure where to put this.

I don't know what is going on.  Ever since I installed Ubuntu 12.04 I have had crashes whenever I use any type of online flash along with programs like VLC or Blender.  I can't watch a Youtube video longer than 20 minutes without crashing.  It never crashes on its own, just when I run multiple flash or other graphic tools.

Computer stats:

Ubuntu 12.04 64-bit
Kernel Linux 3.2.0-29-generic
GNOME 3.4.2

Memory:  15.7 GiB
Processor:  AMD Phenom II X6 1100T Processor x 6 3.84GHz each

AMD Radeon HD 6800 Series Graphics Card

Upon installation the system gave me a 16 GiB swap partition to match the RAM.

I have plenty of drive space, so I don't think it could be a hard drive issue.

I don't know how to trouble shoot anything.  Any help would be awesome.  I need to be able to use my computer for more than 30 minutes at a time.

If I need to post any kind of outputs, please let me know.

---

### Post by QIII on 2012-08-23
My first guess is that you are overheating.  With an AMD/ATI GPU, most of the Flash work gets dumped on your CPU.  Adobe snubbed ATI.   That's probably overheating and giving you a thermal shutdown.

You can install some sensors and then use something like gkrellm to monitor your temps.  gkrellm isn't the greatest thing in the world, but it is easy to set up.

When you look at the sensors, remember that the readings your AMD processor will report are between 6 and 10 degrees lower than actual.

```
sudo apt-get install lm-sensors
``````
sudo sensors-detect
```Answer yes to everything.  At the end you will be told you need to restart some services.  Do that.

You can see that it is working by 

```
sensors
```The temperature for your processor will be in the k10temp-pci section.  Remember that is 6 to 10 degrees low.

If you want, you can start running some flash and just go back to the terminal occasionally and doing

```
sensors
```That, or you can install gkrellm and set up the CPU temp stuff.

---

### Post by Velvet Karuda Leopard on 2012-08-23
Well, I did the 'sensors' method and it shows my Northbridge and CPU at about ten degrees above "HIGH", but they never got more than that.  No where near the displayed critical numbers.  All other stats were below "HIGH" like voltages, even when running all the graphical stuff.

The thing is I was able to run all this on this very same machine with the previous version of Ubuntu and it never crashed, even when running multiple movies, VLC music folders, flash animations, as well as rendering with Blender.

During the sensors test it did not crash.  I tried to repeat the situation, I went to facebook and did a game while watching TV episodes on a website.  Nothing.  It seems to be a random occurance.

I will get me some extra 22mm fans for the side of my case, but I don't think the temps are what is causing my crashes.

Like I said earlier this hardware never saw a problem until I installed 12.04.

Are there any other tests I can run?

---

### Post by QIII on 2012-08-23
This is what I'm getting on my 1100T with a Noctua NH-D14 at 70 degrees room temperature at idle

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +19.5°C  (high = +70.0°C)
                       (crit = +71.0°C, hyst = +66.0°C)

```I add 10 to it for my conky.

I've never seen it go above 50 degrees (corrected) at a 100% load for 30 minutes when it stabilizes.

What do the last few lines of things like syslog, kern.log, dmesg say at about the time of the crash when you start back up?  That should all be in /var/log

---

### Post by Velvet Karuda Leopard on 2012-08-24
Well, it says:

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +85.0°C)

syslog.2:

Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413190] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413199] IP: [<ffffffffa01c0291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413245] PGD 0 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413247] Oops: 0002 [#1] SMP 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413249] CPU 5 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413250] Modules linked in: nls_utf8 udf nls_iso8859_1 nls_cp437 vfat fat parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi sp5100_tco snd_hda_codec_via binfmt_misc serio_raw k10temp edac_core edac_mce_amd uvcvideo videodev v4l2_compat_ioctl32 snd_usb_audio snd_usbmidi_lib i2c_piix4 snd_hda_intel snd_hda_codec snd_hwdep fglrx(P) snd_ctxfi snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc asus_atk0110 mac_hid wmi lp parport usbhid hid uas usb_storage pata_jmicron pata_atiixp sky2 firewire_ohci firewire_core crc_itu_t
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413272] 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413274] Pid: 1324, comm: Xorg Tainted: P           O 3.2.0-29-generic #46-Ubuntu System manufacturer System Product Name/Crosshair IV Formula
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413277] RIP: 0010:[<ffffffffa01c0291>]  [<ffffffffa01c0291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413300] RSP: 0018:ffff8803f9daf9c0  EFLAGS: 00010297
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413301] RAX: ffff8803f9e08008 RBX: ffffc90013176150 RCX: 0000000000000000
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413302] RDX: 0000000000000000 RSI: ffffc90013176018 RDI: ffff8803f9e08e30
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413303] RBP: 0000000000000002 R08: ffffffffa01f0eb0 R09: ffff8803f9e08008
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413305] R10: ffffc90013176090 R11: ffff8803f9e08008 R12: ffffAug 21 16:39:59 TsiEnDalMoset kernel: imklog 5.8.6, log source = /proc/kmsg started.

kern.log:

Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413190] BUG: unable to handle kernel NULL pointer dereference at 0000000000000008
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413199] IP: [<ffffffffa01c0291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413245] PGD 0 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413247] Oops: 0002 [#1] SMP 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413249] CPU 5 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413250] Modules linked in: nls_utf8 udf nls_iso8859_1 nls_cp437 vfat fat parport_pc ppdev rfcomm bnep bluetooth snd_hda_codec_hdmi sp5100_tco snd_hda_codec_via binfmt_misc serio_raw k10temp edac_core edac_mce_amd uvcvideo videodev v4l2_compat_ioctl32 snd_usb_audio snd_usbmidi_lib i2c_piix4 snd_hda_intel snd_hda_codec snd_hwdep fglrx(P) snd_ctxfi snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc asus_atk0110 mac_hid wmi lp parport usbhid hid uas usb_storage pata_jmicron pata_atiixp sky2 firewire_ohci firewire_core crc_itu_t
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413272] 
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413274] Pid: 1324, comm: Xorg Tainted: P           O 3.2.0-29-generic #46-Ubuntu System manufacturer System Product Name/Crosshair IV Formula
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413277] RIP: 0010:[<ffffffffa01c0291>]  [<ffffffffa01c0291>] _ZN20CMMHeap_SystemMemory8pushPoolEP7CMMPool+0x11/0x40 [fglrx]
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413300] RSP: 0018:ffff8803f9daf9c0  EFLAGS: 00010297
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413301] RAX: ffff8803f9e08008 RBX: ffffc90013176150 RCX: 0000000000000000
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413302] RDX: 0000000000000000 RSI: ffffc90013176018 RDI: ffff8803f9e08e30
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413303] RBP: 0000000000000002 R08: ffffffffa01f0eb0 R09: ffff8803f9e08008
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413305] R10: ffffc90013176090 R11: ffff8803f9e08008 R12: ffff8803f9e08e30
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413306] R13: 0000000000000040 R14: 0000000000000000 R15: 0000000000000000
Aug 21 16:38:58 TsiEnDalMoset kernel: [152236.413307] FS:  00007f5c0b996880(0000) GS:ffff88042fd40000(0000) knlGS:0000000000000Aug 21 16:39:59 TsiEnDalMoset kernel: imklog 5.8.6, log source = /proc/kmsg started.

dmesg has lots of lines, but I don't see any times to check.  How do I read the dmesg file?

---

