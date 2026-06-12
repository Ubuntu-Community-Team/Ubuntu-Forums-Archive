---
title: "Suspend problems"
date: 2012-01-04
forum: General Help
---

### Post by josephellengar on 2012-01-04
Hello. 11.10, Gnome Fallback, HP dv7t Pavilion laptop

When I resume from suspend I have two problems. In about 2/3 cases, the mouse simply doesn't work. The keyboard still does work, as I can force logout and then log back in, and then the mouse does work. Also, every time I resume from suspend the power manager gives me a warning along the lines of Battery Critical- 6 minutes left/99%. After a few minutes it will switch to 2/3 hours or whatever. Anyway, I'm more concerned about the mouse thing, but does anybody have any suggestions for fixing either of these problems? Thanks!

---

### Post by josephellengar on 2012-01-09
bump

---

### Post by cllewis91592 on 2012-01-09
what kind of mouse are you using? not sure if this info will help others but never hurts to have more information.

---

### Post by josephellengar on 2012-01-09
> **cllewis91592 said:**
> what kind of mouse are you using? not sure if this info will help others but never hurts to have more information.

Synaptic touchpad doesn't work. Wired Logitech external mouse does work, but only if I plug it in after I resume from suspend.

---

### Post by josephellengar on 2012-01-10
bump. Problem still around. The touchpad, especially, never works when I wake up from suspend. Does anybody have any ideas about what  could even be causing this behavior?

---

### Post by Toz on 2012-01-10
Perhaps its just a matter of not suspending or resetting the mouse/touchpad after suspend.

Can you post back the list of running modules? Open a terminal window, type in the following command, and post back the results in code blocks:
```
lsmod
```

Also helpful would be your current boot command line:
```
cat /proc/cmdline
```
...and any messages that might be generated after a suspend attempt:
```
cat /var/log/syslog* | grep PM:
```

---

### Post by josephellengar on 2012-01-10
> **Toz said:**
> Perhaps its just a matter of not suspending or resetting the mouse/touchpad after suspend.

Can you post back the list of running modules? Open a terminal window, type in the following command, and post back the results in code blocks:
```
lsmod
```

Also helpful would be your current boot command line:
```
cat /proc/cmdline
```
...and any messages that might be generated after a suspend attempt:
```
cat /var/log/syslog* | grep PM:
```

Thanks for the response! Here is the code you asked for. This is all when my touchpad and mouse are working. Let me know if you want it when they're not working as well. (Strange symptom: after I unsuspend and the mice aren't working, if I log out and log back in, they start to work)

result of lsmod:
```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_utf8               12557  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
usb_storage            57901  0 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
bnep                   18436  2 
snd_hda_codec_hdmi     32040  4 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
nvidia              11713772  48 
arc4                   12529  2 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_idt      70553  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
i7core_edac            27942  0 
snd_hda_intel          33390  3 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
psmouse                73882  0 
snd_hwdep              13668  1 snd_hda_codec
serio_raw              13166  0 
iwlagn                314213  0 
edac_core              53746  3 i7core_edac
mac80211              462092  1 iwlagn
ir_sony_decoder        12549  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ir_jvc_decoder         12546  0 
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
cfg80211              199587  2 iwlagn,mac80211
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ene_ir                 22796  0 
rc_core                26963  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 hp_wmi
video                  19412  0 
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  5 
libahci                26861  1 ahci
firewire_ohci          40722  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
r8169                  52788  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

```

result of cat /proc/cmdline
```

BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=cd10c0ee-fa36-447e-9ce2-39b2d6891fa3 ro quiet splash vt.handoff=7

```

result of cat /var/log/syslog* | grep PM:
```

Jan 10 14:10:24 ross-Laptop kernel: [99356.118715] PM: Syncing filesystems ... done.
Jan 10 14:10:24 ross-Laptop kernel: [99356.123431] PM: Preparing system for mem sleep
Jan 10 14:10:24 ross-Laptop kernel: [99356.155977] PM: Entering mem sleep
Jan 10 14:10:24 ross-Laptop kernel: [99356.367798] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.204 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.433041] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.139 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.433130] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.084 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.433162] PM: suspend of drv:scsi dev:host0 complete after 275.993 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.447710] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 200.223 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.447804] PM: suspend of drv: dev:pci0000:00 complete after 199.617 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.447837] PM: suspend of devices complete after 291.666 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.447841] PM: suspend devices took 0.292 seconds
Jan 10 14:10:24 ross-Laptop kernel: [99356.511860] PM: late suspend of devices complete after 64.034 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99356.592638] PM: Saving platform NVS memory
Jan 10 14:10:24 ross-Laptop kernel: [99357.220190] PM: Restoring platform NVS memory
Jan 10 14:10:24 ross-Laptop kernel: [99358.157850] PM: early resume of devices complete after 1.765 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.335990] PM: resume of drv:hub dev:2-1:1.0 complete after 177.290 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.335999] PM: resume of drv: dev:ep_00 complete after 177.241 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.336003] PM: resume of drv: dev:ep_81 complete after 177.273 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.501575] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.825 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.501585] PM: resume of drv: dev:ep_00 complete after 342.760 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.501590] PM: resume of drv: dev:ep_01 complete after 342.821 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.501605] PM: resume of drv: dev:ep_81 complete after 342.817 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.501608] PM: resume of drv: dev:ep_82 complete after 342.799 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.507948] PM: resume of drv:sd dev:0:0:0:0 complete after 349.558 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.507965] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.512 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.508004] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 232.905 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.582902] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 424.874 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.710970] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 552.171 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.710984] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 552.150 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.710992] PM: resume of drv: dev:ep_83 complete after 552.176 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99358.710998] PM: resume of drv: dev:ep_00 complete after 552.143 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99359.982620] PM: resume of drv:sd dev:4:0:0:0 complete after 1824.538 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99359.982647] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1824.534 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99359.982732] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1475.175 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99359.985474] PM: resume of devices complete after 1828.137 msecs
Jan 10 14:10:24 ross-Laptop kernel: [99359.985532] PM: resume devices took 1.828 seconds
Jan 10 14:10:24 ross-Laptop kernel: [99359.985555] PM: Finishing wakeup.
Jan 10 14:26:00 ross-Laptop kernel: [99422.101415] PM: Syncing filesystems ... done.
Jan 10 14:26:00 ross-Laptop kernel: [99422.106199] PM: Preparing system for mem sleep
Jan 10 14:26:00 ross-Laptop kernel: [99422.146214] PM: Entering mem sleep
Jan 10 14:26:00 ross-Laptop kernel: [99422.373892] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 116.878 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.439284] PM: suspend of drv:sd dev:0:0:0:0 complete after 277.014 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.439362] PM: suspend of drv:scsi dev:target0:0:0 complete after 277.077 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.439497] PM: suspend of drv:scsi dev:host0 complete after 276.990 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.453832] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 196.918 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.453925] PM: suspend of drv: dev:pci0000:00 complete after 196.621 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.454069] PM: suspend of devices complete after 291.970 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.454071] PM: suspend devices took 0.308 seconds
Jan 10 14:26:00 ross-Laptop kernel: [99422.517945] PM: late suspend of devices complete after 63.922 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99422.598681] PM: Saving platform NVS memory
Jan 10 14:26:00 ross-Laptop kernel: [99423.229935] PM: Restoring platform NVS memory
Jan 10 14:26:00 ross-Laptop kernel: [99424.139149] PM: early resume of devices complete after 1.746 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.317209] PM: resume of drv:hub dev:2-1:1.0 complete after 177.109 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.317213] PM: resume of drv: dev:ep_00 complete after 176.960 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.317224] PM: resume of drv: dev:ep_81 complete after 177.092 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.489113] PM: resume of drv:sd dev:0:0:0:0 complete after 349.491 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.489156] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.524 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.489201] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 229.476 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.527111] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 386.543 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.527114] PM: resume of drv: dev:ep_00 complete after 386.372 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.527118] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 386.399 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.527128] PM: resume of drv: dev:ep_83 complete after 386.429 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.565451] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 426.362 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.646876] PM: resume of drv:usb dev:2-1.3:1.0 complete after 506.720 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.646883] PM: resume of drv: dev:ep_00 complete after 506.487 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.646895] PM: resume of drv: dev:ep_01 complete after 506.705 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.646911] PM: resume of drv: dev:ep_82 complete after 506.575 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99424.646922] PM: resume of drv: dev:ep_81 complete after 506.647 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99425.973098] PM: resume of drv:sd dev:4:0:0:0 complete after 1834.452 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99425.973129] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1485.120 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99425.975680] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1837.000 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99425.975689] PM: resume of devices complete after 1837.975 msecs
Jan 10 14:26:00 ross-Laptop kernel: [99425.975776] PM: resume devices took 1.840 seconds
Jan 10 14:26:00 ross-Laptop kernel: [99425.975799] PM: Finishing wakeup.
Jan 10 15:46:45 ross-Laptop kernel: [102118.959730] PM: Syncing filesystems ... done.
Jan 10 15:46:45 ross-Laptop kernel: [102118.964547] PM: Preparing system for mem sleep
Jan 10 15:46:45 ross-Laptop kernel: [102118.993692] PM: Entering mem sleep
Jan 10 15:46:45 ross-Laptop kernel: [102119.205459] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.634 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.271024] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.407 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.271117] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.410 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.271157] PM: suspend of drv:scsi dev:host0 complete after 276.182 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.285386] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 200.669 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.285432] PM: suspend of drv: dev:pci0000:00 complete after 199.804 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.285452] PM: suspend of devices complete after 291.589 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.285460] PM: suspend devices took 0.292 seconds
Jan 10 15:46:45 ross-Laptop kernel: [102119.349562] PM: late suspend of devices complete after 64.117 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102119.430337] PM: Saving platform NVS memory
Jan 10 15:46:45 ross-Laptop kernel: [102120.057886] PM: Restoring platform NVS memory
Jan 10 15:46:45 ross-Laptop kernel: [102120.959630] PM: early resume of devices complete after 1.732 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.137652] PM: resume of drv:hub dev:2-1:1.0 complete after 176.902 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.137662] PM: resume of drv: dev:ep_00 complete after 176.876 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.137666] PM: resume of drv: dev:ep_81 complete after 176.897 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.303181] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.410 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.303189] PM: resume of drv: dev:ep_00 complete after 342.348 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.303192] PM: resume of drv: dev:ep_01 complete after 342.403 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.303205] PM: resume of drv: dev:ep_81 complete after 342.400 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.303207] PM: resume of drv: dev:ep_82 complete after 342.382 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.317678] PM: resume of drv:sd dev:0:0:0:0 complete after 357.145 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.317740] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 357.189 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.317746] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 241.643 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.385931] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 426.213 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.511760] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.946 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.511776] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.927 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.511784] PM: resume of drv: dev:ep_83 complete after 550.953 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102121.511789] PM: resume of drv: dev:ep_00 complete after 550.921 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102122.807513] PM: resume of drv:sd dev:4:0:0:0 complete after 1847.334 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102122.807602] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1847.405 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102122.807721] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1490.427 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102122.810472] PM: resume of devices complete after 1851.362 msecs
Jan 10 15:46:45 ross-Laptop kernel: [102122.810530] PM: resume devices took 1.852 seconds
Jan 10 15:46:45 ross-Laptop kernel: [102122.810552] PM: Finishing wakeup.
Jan 10 16:00:53 ross-Laptop kernel: [102905.679122] PM: Syncing filesystems ... done.
Jan 10 16:00:53 ross-Laptop kernel: [102905.684975] PM: Preparing system for mem sleep
Jan 10 16:00:53 ross-Laptop kernel: [102905.713993] PM: Entering mem sleep
Jan 10 16:00:53 ross-Laptop kernel: [102905.949827] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.131 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.007329] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.662 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.007408] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.669 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.007434] PM: suspend of drv:scsi dev:host0 complete after 276.417 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.021790] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 190.298 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.021817] PM: suspend of drv: dev:pci0000:00 complete after 189.973 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.021837] PM: suspend of devices complete after 291.898 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.021842] PM: suspend devices took 0.308 seconds
Jan 10 16:00:53 ross-Laptop kernel: [102906.085955] PM: late suspend of devices complete after 64.129 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102906.166732] PM: Saving platform NVS memory
Jan 10 16:00:53 ross-Laptop kernel: [102906.794278] PM: Restoring platform NVS memory
Jan 10 16:00:53 ross-Laptop kernel: [102907.743977] PM: early resume of devices complete after 1.748 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102907.922051] PM: resume of drv:hub dev:2-1:1.0 complete after 176.947 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102907.922057] PM: resume of drv: dev:ep_00 complete after 176.912 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102907.922064] PM: resume of drv: dev:ep_81 complete after 176.943 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.087816] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.693 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.087827] PM: resume of drv: dev:ep_00 complete after 342.634 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.087832] PM: resume of drv: dev:ep_01 complete after 342.692 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.087850] PM: resume of drv: dev:ep_81 complete after 342.693 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.087852] PM: resume of drv: dev:ep_82 complete after 342.675 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.102087] PM: resume of drv:sd dev:0:0:0:0 complete after 357.200 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.102209] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 236.868 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.102229] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 357.321 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.174790] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 430.770 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.297358] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 552.191 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.297373] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 552.171 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.297380] PM: resume of drv: dev:ep_83 complete after 552.197 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102908.297386] PM: resume of drv: dev:ep_00 complete after 552.165 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102909.572078] PM: resume of drv:sd dev:4:0:0:0 complete after 1827.538 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102909.572169] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1470.393 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102909.572180] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1827.613 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102909.574777] PM: resume of devices complete after 1831.340 msecs
Jan 10 16:00:53 ross-Laptop kernel: [102909.574835] PM: resume devices took 1.832 seconds
Jan 10 16:00:53 ross-Laptop kernel: [102909.574858] PM: Finishing wakeup.
Jan 10 17:05:44 ross-Laptop kernel: [104512.574108] PM: Syncing filesystems ... done.
Jan 10 17:05:44 ross-Laptop kernel: [104512.579725] PM: Preparing system for mem sleep
Jan 10 17:05:44 ross-Laptop kernel: [104512.616228] PM: Entering mem sleep
Jan 10 17:05:44 ross-Laptop kernel: [104512.847948] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.879 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.910893] PM: suspend of drv:sd dev:0:0:0:0 complete after 278.357 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.910935] PM: suspend of drv:scsi dev:target0:0:0 complete after 278.353 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.910960] PM: suspend of drv:scsi dev:host0 complete after 278.264 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.923924] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 195.965 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.924018] PM: suspend of drv: dev:pci0000:00 complete after 195.862 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.924148] PM: suspend of devices complete after 292.102 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104512.924150] PM: suspend devices took 0.308 seconds
Jan 10 17:05:44 ross-Laptop kernel: [104512.988068] PM: late suspend of devices complete after 63.934 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104513.068838] PM: Saving platform NVS memory
Jan 10 17:05:44 ross-Laptop kernel: [104513.696404] PM: Restoring platform NVS memory
Jan 10 17:05:44 ross-Laptop kernel: [104514.646117] PM: early resume of devices complete after 1.746 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.824143] PM: resume of drv:hub dev:2-1:1.0 complete after 177.045 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.824149] PM: resume of drv: dev:ep_00 complete after 176.996 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.824157] PM: resume of drv: dev:ep_81 complete after 177.033 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.989733] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.591 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.989743] PM: resume of drv: dev:ep_00 complete after 342.512 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.989749] PM: resume of drv: dev:ep_01 complete after 342.583 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.989763] PM: resume of drv: dev:ep_81 complete after 342.576 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.989766] PM: resume of drv: dev:ep_82 complete after 342.556 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.996157] PM: resume of drv:sd dev:0:0:0:0 complete after 349.331 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.996257] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 233.161 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104514.996273] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.402 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104515.071750] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 425.382 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104515.204508] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 557.295 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104515.204520] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 557.269 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104515.204527] PM: resume of drv: dev:ep_83 complete after 557.295 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104515.204533] PM: resume of drv: dev:ep_00 complete after 557.257 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104516.467872] PM: resume of drv:sd dev:4:0:0:0 complete after 1821.412 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104516.467967] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1821.440 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104516.467974] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1472.151 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104516.470828] PM: resume of devices complete after 1825.249 msecs
Jan 10 17:05:44 ross-Laptop kernel: [104516.470886] PM: resume devices took 1.824 seconds
Jan 10 17:05:44 ross-Laptop kernel: [104516.470909] PM: Finishing wakeup.
Jan 10 18:38:59 ross-Laptop kernel: [105463.133236] PM: Syncing filesystems ... done.
Jan 10 18:38:59 ross-Laptop kernel: [105463.138315] PM: Preparing system for mem sleep
Jan 10 18:38:59 ross-Laptop kernel: [105463.170769] PM: Entering mem sleep
Jan 10 18:38:59 ross-Laptop kernel: [105463.402401] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.535 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.465539] PM: suspend of drv:nvidia dev:0000:01:00.0 complete after 181.915 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.465588] PM: suspend of drv:pcieport dev:0000:00:03.0 complete after 181.664 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.465756] PM: suspend of drv:sd dev:0:0:0:0 complete after 278.569 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.465801] PM: suspend of drv:scsi dev:target0:0:0 complete after 278.520 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.465821] PM: suspend of drv:scsi dev:host0 complete after 278.289 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.478492] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 194.748 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.478587] PM: suspend of drv: dev:pci0000:00 complete after 194.596 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.478608] PM: suspend of devices complete after 292.016 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.478613] PM: suspend devices took 0.308 seconds
Jan 10 18:38:59 ross-Laptop kernel: [105463.542597] PM: late suspend of devices complete after 63.999 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105463.623374] PM: Saving platform NVS memory
Jan 10 18:38:59 ross-Laptop kernel: [105464.250953] PM: Restoring platform NVS memory
Jan 10 18:38:59 ross-Laptop kernel: [105465.184601] PM: early resume of devices complete after 1.756 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.362752] PM: resume of drv:hub dev:2-1:1.0 complete after 177.128 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.362761] PM: resume of drv: dev:ep_00 complete after 177.056 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.362766] PM: resume of drv: dev:ep_81 complete after 177.094 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.518781] PM: resume of drv:sd dev:0:0:0:0 complete after 333.681 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.518884] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 333.740 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.518894] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 214.577 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.528474] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.706 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.528489] PM: resume of drv: dev:ep_00 complete after 342.618 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.528501] PM: resume of drv: dev:ep_01 complete after 342.703 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.528515] PM: resume of drv: dev:ep_81 complete after 342.697 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.528519] PM: resume of drv: dev:ep_82 complete after 342.672 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.618070] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 433.292 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.736814] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.930 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.736827] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.910 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.736834] PM: resume of drv: dev:ep_83 complete after 550.933 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105465.736840] PM: resume of drv: dev:ep_00 complete after 550.904 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105466.995585] PM: resume of drv:sd dev:4:0:0:0 complete after 1810.774 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105466.995627] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1810.729 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105466.995709] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1477.254 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105466.998585] PM: resume of devices complete after 1814.485 msecs
Jan 10 18:38:59 ross-Laptop kernel: [105466.998644] PM: resume devices took 1.816 seconds
Jan 10 18:38:59 ross-Laptop kernel: [105466.998667] PM: Finishing wakeup.
Jan 10 19:19:43 ross-Laptop kernel: [106180.633853] PM: Syncing filesystems ... done.
Jan 10 19:19:43 ross-Laptop kernel: [106180.638870] PM: Preparing system for mem sleep
Jan 10 19:19:43 ross-Laptop kernel: [106180.668117] PM: Entering mem sleep
Jan 10 19:19:43 ross-Laptop kernel: [106180.903803] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.007 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.962552] PM: suspend of drv:sd dev:0:0:0:0 complete after 277.931 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.962648] PM: suspend of drv:scsi dev:target0:0:0 complete after 277.936 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.962673] PM: suspend of drv:scsi dev:host0 complete after 277.676 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.975780] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 190.124 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.975876] PM: suspend of drv: dev:pci0000:00 complete after 189.786 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.975908] PM: suspend of devices complete after 291.907 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106180.975912] PM: suspend devices took 0.308 seconds
Jan 10 19:19:43 ross-Laptop kernel: [106181.039996] PM: late suspend of devices complete after 64.099 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106181.120797] PM: Saving platform NVS memory
Jan 10 19:19:43 ross-Laptop kernel: [106181.748290] PM: Restoring platform NVS memory
Jan 10 19:19:43 ross-Laptop kernel: [106182.653994] PM: early resume of devices complete after 1.754 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.832172] PM: resume of drv:hub dev:2-1:1.0 complete after 171.054 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.832178] PM: resume of drv: dev:ep_00 complete after 171.021 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.832210] PM: resume of drv: dev:ep_81 complete after 171.074 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.997770] PM: resume of drv:usb dev:2-1.3:1.0 complete after 336.631 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.997790] PM: resume of drv: dev:ep_00 complete after 336.578 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.997794] PM: resume of drv: dev:ep_01 complete after 336.639 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.997809] PM: resume of drv: dev:ep_81 complete after 336.637 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106182.997812] PM: resume of drv: dev:ep_82 complete after 336.619 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.020271] PM: resume of drv:sd dev:0:0:0:0 complete after 359.372 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.020290] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 359.373 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.078791] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 424.703 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.170114] PM: resume of drv:battery dev:PNP0C0A:00 complete after 509.413 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.206206] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 545.025 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.206222] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 545.006 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.206229] PM: resume of drv: dev:ep_83 complete after 545.030 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106183.206234] PM: resume of drv: dev:ep_00 complete after 545.000 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106184.489094] PM: resume of drv:sd dev:4:0:0:0 complete after 1828.543 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106184.489152] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1828.584 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106184.489162] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1270.837 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106184.491736] PM: resume of devices complete after 1838.255 msecs
Jan 10 19:19:43 ross-Laptop kernel: [106184.491793] PM: resume devices took 1.840 seconds
Jan 10 19:19:43 ross-Laptop kernel: [106184.491815] PM: Finishing wakeup.
Jan 10 21:54:07 ross-Laptop kernel: [107919.224726] PM: Syncing filesystems ... done.
Jan 10 21:54:07 ross-Laptop kernel: [107919.229536] PM: Preparing system for mem sleep
Jan 10 21:54:07 ross-Laptop kernel: [107919.262869] PM: Entering mem sleep
Jan 10 21:54:07 ross-Laptop kernel: [107919.494603] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.911 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.557483] PM: suspend of drv:sd dev:0:0:0:0 complete after 278.115 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.557574] PM: suspend of drv:scsi dev:target0:0:0 complete after 278.112 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.557589] PM: suspend of drv:scsi dev:host0 complete after 277.951 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.570613] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 196.128 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.570700] PM: suspend of drv: dev:pci0000:00 complete after 195.658 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.570726] PM: suspend of devices complete after 291.913 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.570730] PM: suspend devices took 0.308 seconds
Jan 10 21:54:07 ross-Laptop kernel: [107919.634762] PM: late suspend of devices complete after 64.047 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107919.715632] PM: Saving platform NVS memory
Jan 10 21:54:07 ross-Laptop kernel: [107920.343049] PM: Restoring platform NVS memory
Jan 10 21:54:07 ross-Laptop kernel: [107921.252816] PM: early resume of devices complete after 1.731 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.430828] PM: resume of drv: dev:ep_00 complete after 177.086 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.430833] PM: resume of drv:hub dev:2-1:1.0 complete after 177.143 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.430905] PM: resume of drv: dev:ep_81 complete after 177.189 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.596612] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.872 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.596621] PM: resume of drv: dev:ep_00 complete after 342.805 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.596623] PM: resume of drv: dev:ep_01 complete after 342.862 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.596637] PM: resume of drv: dev:ep_82 complete after 342.839 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.596639] PM: resume of drv: dev:ep_81 complete after 342.857 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.602965] PM: resume of drv:sd dev:0:0:0:0 complete after 349.588 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.602977] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.527 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.603102] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 280.866 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.681167] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 428.264 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.805753] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 551.968 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.805761] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 551.942 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.805765] PM: resume of drv: dev:ep_83 complete after 551.963 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107921.805767] PM: resume of drv: dev:ep_00 complete after 551.931 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107923.110468] PM: resume of drv:sd dev:4:0:0:0 complete after 1857.398 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107923.110562] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1857.464 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107923.110693] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1508.045 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107923.113514] PM: resume of devices complete after 1861.217 msecs
Jan 10 21:54:07 ross-Laptop kernel: [107923.113573] PM: resume devices took 1.860 seconds
Jan 10 21:54:07 ross-Laptop kernel: [107923.113596] PM: Finishing wakeup.
Jan  9 15:17:45 ross-Laptop kernel: [84481.546491] PM: Syncing filesystems ... done.
Jan  9 15:17:45 ross-Laptop kernel: [84481.552007] PM: Preparing system for mem sleep
Jan  9 15:17:45 ross-Laptop kernel: [84481.582006] PM: Entering mem sleep
Jan  9 15:17:45 ross-Laptop kernel: [84481.805756] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.526 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.862688] PM: suspend of drv:sd dev:0:0:0:0 complete after 279.950 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.862777] PM: suspend of drv:scsi dev:target0:0:0 complete after 279.946 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.862806] PM: suspend of drv:scsi dev:host0 complete after 279.720 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.877786] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 190.915 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.877875] PM: suspend of drv: dev:pci0000:00 complete after 190.480 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.877902] PM: suspend of devices complete after 295.697 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84481.877907] PM: suspend devices took 0.296 seconds
Jan  9 15:17:45 ross-Laptop kernel: [84481.941889] PM: late suspend of devices complete after 63.997 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84482.022669] PM: Saving platform NVS memory
Jan  9 15:17:45 ross-Laptop kernel: [84482.654214] PM: Restoring platform NVS memory
Jan  9 15:17:45 ross-Laptop kernel: [84483.603885] PM: early resume of devices complete after 1.751 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.781943] PM: resume of drv:hub dev:2-1:1.0 complete after 176.927 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.781958] PM: resume of drv: dev:ep_00 complete after 176.904 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.781966] PM: resume of drv: dev:ep_81 complete after 176.931 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.947616] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.576 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.947624] PM: resume of drv: dev:ep_00 complete after 342.510 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.947627] PM: resume of drv: dev:ep_01 complete after 342.568 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.947639] PM: resume of drv: dev:ep_82 complete after 342.543 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.947641] PM: resume of drv: dev:ep_81 complete after 342.562 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.954025] PM: resume of drv:sd dev:0:0:0:0 complete after 349.231 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.954040] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.227 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84483.954163] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 233.297 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84484.035089] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 431.160 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84484.156018] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.929 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84484.156033] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.906 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84484.156040] PM: resume of drv: dev:ep_83 complete after 550.930 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84484.156045] PM: resume of drv: dev:ep_00 complete after 550.899 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84485.383189] PM: resume of drv:sd dev:4:0:0:0 complete after 1778.725 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84485.383279] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1778.797 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84485.383414] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1429.680 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84485.386156] PM: resume of devices complete after 1782.795 msecs
Jan  9 15:17:45 ross-Laptop kernel: [84485.386215] PM: resume devices took 1.784 seconds
Jan  9 15:17:45 ross-Laptop kernel: [84485.386237] PM: Finishing wakeup.
Jan  9 16:06:34 ross-Laptop kernel: [85484.671921] PM: Syncing filesystems ... done.
Jan  9 16:06:34 ross-Laptop kernel: [85484.677111] PM: Preparing system for mem sleep
Jan  9 16:06:34 ross-Laptop kernel: [85484.712119] PM: Entering mem sleep
Jan  9 16:06:34 ross-Laptop kernel: [85484.947820] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.954 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.005871] PM: suspend of drv:sd dev:0:0:0:0 complete after 277.261 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.005969] PM: suspend of drv:scsi dev:target0:0:0 complete after 277.296 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.005992] PM: suspend of drv:scsi dev:host0 complete after 277.091 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.019812] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 192.092 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.019962] PM: suspend of drv: dev:pci0000:00 complete after 191.835 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.020040] PM: suspend of devices complete after 292.007 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.020043] PM: suspend devices took 0.308 seconds
Jan  9 16:06:34 ross-Laptop kernel: [85485.083994] PM: late suspend of devices complete after 63.967 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85485.164761] PM: Saving platform NVS memory
Jan  9 16:06:34 ross-Laptop kernel: [85485.792361] PM: Restoring platform NVS memory
Jan  9 16:06:34 ross-Laptop kernel: [85486.726033] PM: early resume of devices complete after 1.752 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85486.904138] PM: resume of drv:hub dev:2-1:1.0 complete after 176.611 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85486.904148] PM: resume of drv: dev:ep_00 complete after 176.579 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85486.904151] PM: resume of drv: dev:ep_81 complete after 176.599 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.069901] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.344 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.069911] PM: resume of drv: dev:ep_00 complete after 342.272 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.069915] PM: resume of drv: dev:ep_01 complete after 342.333 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.069930] PM: resume of drv: dev:ep_81 complete after 342.329 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.069933] PM: resume of drv: dev:ep_82 complete after 342.310 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.084227] PM: resume of drv:sd dev:0:0:0:0 complete after 356.955 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.084241] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 356.947 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.084246] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 236.685 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.150903] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 424.771 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.278345] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.731 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.278361] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.686 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.278369] PM: resume of drv: dev:ep_83 complete after 550.729 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85487.278374] PM: resume of drv: dev:ep_00 complete after 550.675 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85488.557954] PM: resume of drv:sd dev:4:0:0:0 complete after 1831.014 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85488.557980] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1831.013 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85488.558030] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1474.227 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85488.560852] PM: resume of devices complete after 1835.330 msecs
Jan  9 16:06:34 ross-Laptop kernel: [85488.560910] PM: resume devices took 1.836 seconds
Jan  9 16:06:34 ross-Laptop kernel: [85488.560932] PM: Finishing wakeup.
Jan  9 17:05:17 ross-Laptop kernel: [87497.357526] PM: Syncing filesystems ... done.
Jan  9 17:05:17 ross-Laptop kernel: [87497.362392] PM: Preparing system for mem sleep
Jan  9 17:05:17 ross-Laptop kernel: [87497.393006] PM: Entering mem sleep
Jan  9 17:05:17 ross-Laptop kernel: [87497.636643] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.479 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.690131] PM: suspend of drv:sd dev:0:0:0:0 complete after 280.498 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.690191] PM: suspend of drv:scsi dev:target0:0:0 complete after 280.434 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.690217] PM: suspend of drv:scsi dev:host0 complete after 280.341 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.704616] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 188.602 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.704707] PM: suspend of drv: dev:pci0000:00 complete after 188.492 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.704831] PM: suspend of devices complete after 295.880 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.704833] PM: suspend devices took 0.312 seconds
Jan  9 17:05:17 ross-Laptop kernel: [87497.768813] PM: late suspend of devices complete after 63.996 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87497.849595] PM: Saving platform NVS memory
Jan  9 17:05:17 ross-Laptop kernel: [87498.477138] PM: Restoring platform NVS memory
Jan  9 17:05:17 ross-Laptop kernel: [87499.370869] PM: early resume of devices complete after 1.720 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.548975] PM: resume of drv:hub dev:2-1:1.0 complete after 177.188 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.549022] PM: resume of drv: dev:ep_81 complete after 177.205 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.549029] PM: resume of drv: dev:ep_00 complete after 177.153 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.704983] PM: resume of drv:sd dev:0:0:0:0 complete after 333.693 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.705069] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 333.638 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.705083] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 260.828 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.714648] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.759 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.714665] PM: resume of drv: dev:ep_00 complete after 342.658 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.714669] PM: resume of drv: dev:ep_01 complete after 342.755 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.714685] PM: resume of drv: dev:ep_81 complete after 342.751 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.714688] PM: resume of drv: dev:ep_82 complete after 342.702 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.799233] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 428.188 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.923932] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 551.946 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.923947] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 551.919 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.923956] PM: resume of drv: dev:ep_83 complete after 551.951 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87499.923962] PM: resume of drv: dev:ep_00 complete after 551.906 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87501.188278] PM: resume of drv:sd dev:4:0:0:0 complete after 1817.202 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87501.188364] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1817.204 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87501.188374] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1483.728 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87501.191091] PM: resume of devices complete after 1820.732 msecs
Jan  9 17:05:17 ross-Laptop kernel: [87501.191151] PM: resume devices took 1.820 seconds
Jan  9 17:05:17 ross-Laptop kernel: [87501.191173] PM: Finishing wakeup.
Jan  9 18:15:59 ross-Laptop kernel: [89074.292018] PM: Syncing filesystems ... done.
Jan  9 18:15:59 ross-Laptop kernel: [89074.297524] PM: Preparing system for mem sleep
Jan  9 18:15:59 ross-Laptop kernel: [89074.328135] PM: Entering mem sleep
Jan  9 18:15:59 ross-Laptop kernel: [89074.559756] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 120.825 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.623533] PM: suspend of drv:sd dev:0:0:0:0 complete after 278.868 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.623646] PM: suspend of drv:scsi dev:target0:0:0 complete after 278.895 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.623663] PM: suspend of drv:scsi dev:host0 complete after 278.609 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.639894] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 201.358 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.640005] PM: suspend of drv: dev:pci0000:00 complete after 200.884 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.640109] PM: suspend of devices complete after 296.081 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.640112] PM: suspend devices took 0.312 seconds
Jan  9 18:15:59 ross-Laptop kernel: [89074.703974] PM: late suspend of devices complete after 63.879 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89074.784749] PM: Saving platform NVS memory
Jan  9 18:15:59 ross-Laptop kernel: [89075.412295] PM: Restoring platform NVS memory
Jan  9 18:15:59 ross-Laptop kernel: [89076.349973] PM: early resume of devices complete after 1.766 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.528048] PM: resume of drv:hub dev:2-1:1.0 complete after 176.825 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.528054] PM: resume of drv: dev:ep_00 complete after 176.651 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.528063] PM: resume of drv: dev:ep_81 complete after 176.698 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.693787] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.353 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.693802] PM: resume of drv: dev:ep_00 complete after 342.236 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.693813] PM: resume of drv: dev:ep_01 complete after 342.356 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.693828] PM: resume of drv: dev:ep_81 complete after 342.346 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.693831] PM: resume of drv: dev:ep_82 complete after 342.322 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.708081] PM: resume of drv:sd dev:0:0:0:0 complete after 357.553 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.708092] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 357.332 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.708097] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 231.108 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.775489] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 425.443 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.904115] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 552.567 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.904126] PM: resume of drv: dev:ep_00 complete after 552.495 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.904133] PM: resume of drv: dev:ep_83 complete after 552.563 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89076.904140] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 552.551 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89078.211053] PM: resume of drv:sd dev:4:0:0:0 complete after 1860.615 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89078.211225] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1860.654 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89078.211305] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1503.662 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89078.214072] PM: resume of devices complete after 1864.615 msecs
Jan  9 18:15:59 ross-Laptop kernel: [89078.214130] PM: resume devices took 1.864 seconds
Jan  9 18:15:59 ross-Laptop kernel: [89078.214152] PM: Finishing wakeup.
Jan  9 18:34:45 ross-Laptop kernel: [89635.461944] PM: Syncing filesystems ... done.
Jan  9 18:34:45 ross-Laptop kernel: [89635.466703] PM: Preparing system for mem sleep
Jan  9 18:34:45 ross-Laptop kernel: [89635.499305] PM: Entering mem sleep
Jan  9 18:34:45 ross-Laptop kernel: [89635.726999] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.933 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.792311] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.628 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.792365] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.548 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.792392] PM: suspend of drv:scsi dev:host0 complete after 276.299 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.806937] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 198.039 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.807021] PM: suspend of drv: dev:pci0000:00 complete after 197.934 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.807151] PM: suspend of devices complete after 291.972 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.807155] PM: suspend devices took 0.308 seconds
Jan  9 18:34:45 ross-Laptop kernel: [89635.871049] PM: late suspend of devices complete after 63.941 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89635.951782] PM: Saving platform NVS memory
Jan  9 18:34:45 ross-Laptop kernel: [89636.579028] PM: Restoring platform NVS memory
Jan  9 18:34:45 ross-Laptop kernel: [89637.496284] PM: early resume of devices complete after 1.723 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.674279] PM: resume of drv:hub dev:2-1:1.0 complete after 176.501 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.674287] PM: resume of drv: dev:ep_00 complete after 176.446 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.674291] PM: resume of drv: dev:ep_81 complete after 176.467 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.839899] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.155 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.839910] PM: resume of drv: dev:ep_00 complete after 342.096 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.839914] PM: resume of drv: dev:ep_01 complete after 342.152 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.839934] PM: resume of drv: dev:ep_81 complete after 342.155 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.839936] PM: resume of drv: dev:ep_82 complete after 342.138 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.870199] PM: resume of drv:sd dev:0:0:0:0 complete after 372.798 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.870325] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 372.894 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.870334] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 250.852 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89637.928948] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 432.738 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89638.051327] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 553.618 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89638.051342] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 553.598 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89638.051349] PM: resume of drv: dev:ep_83 complete after 553.621 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89638.051354] PM: resume of drv: dev:ep_00 complete after 553.593 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89639.329125] PM: resume of drv:sd dev:4:0:0:0 complete after 1832.742 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89639.329217] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1832.816 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89639.329229] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1460.055 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89639.331911] PM: resume of devices complete after 1837.052 msecs
Jan  9 18:34:45 ross-Laptop kernel: [89639.331968] PM: resume devices took 1.836 seconds
Jan  9 18:34:45 ross-Laptop kernel: [89639.331991] PM: Finishing wakeup.
Jan  9 20:30:49 ross-Laptop kernel: [90276.296401] PM: Syncing filesystems ... done.
Jan  9 20:30:49 ross-Laptop kernel: [90276.301817] PM: Preparing system for mem sleep
Jan  9 20:30:49 ross-Laptop kernel: [90276.331809] PM: Entering mem sleep
Jan  9 20:30:49 ross-Laptop kernel: [90276.559531] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.089 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.624511] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.380 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.624603] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.387 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.624636] PM: suspend of drv:scsi dev:host0 complete after 276.173 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.639499] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 198.235 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.639599] PM: suspend of drv: dev:pci0000:00 complete after 197.943 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.639709] PM: suspend of devices complete after 292.084 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.639713] PM: suspend devices took 0.308 seconds
Jan  9 20:30:49 ross-Laptop kernel: [90276.703647] PM: late suspend of devices complete after 63.949 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90276.784439] PM: Saving platform NVS memory
Jan  9 20:30:49 ross-Laptop kernel: [90277.411978] PM: Restoring platform NVS memory
Jan  9 20:30:49 ross-Laptop kernel: [90278.349644] PM: early resume of devices complete after 1.752 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.527742] PM: resume of drv:hub dev:2-1:1.0 complete after 176.939 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.527757] PM: resume of drv: dev:ep_00 complete after 176.901 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.527761] PM: resume of drv: dev:ep_81 complete after 176.930 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.691898] PM: resume of drv:sd dev:0:0:0:0 complete after 341.517 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.691915] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 341.455 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.691921] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 225.625 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.693307] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.452 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.693316] PM: resume of drv: dev:ep_00 complete after 342.302 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.693319] PM: resume of drv: dev:ep_01 complete after 342.438 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.693330] PM: resume of drv: dev:ep_81 complete after 342.367 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.693332] PM: resume of drv: dev:ep_82 complete after 342.342 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.781068] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 431.243 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.901765] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.773 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.901781] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.725 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.901788] PM: resume of drv: dev:ep_83 complete after 550.751 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90278.901794] PM: resume of drv: dev:ep_00 complete after 550.721 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90280.146214] PM: resume of drv:sd dev:4:0:0:0 complete after 1796.148 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90280.146275] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1796.144 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90280.146285] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1454.793 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90280.148865] PM: resume of devices complete after 1799.716 msecs
Jan  9 20:30:49 ross-Laptop kernel: [90280.148923] PM: resume devices took 1.800 seconds
Jan  9 20:30:49 ross-Laptop kernel: [90280.148945] PM: Finishing wakeup.
Jan  9 20:52:25 ross-Laptop kernel: [91556.736282] PM: Syncing filesystems ... done.
Jan  9 20:52:25 ross-Laptop kernel: [91556.740966] PM: Preparing system for mem sleep
Jan  9 20:52:25 ross-Laptop kernel: [91556.771353] PM: Entering mem sleep
Jan  9 20:52:25 ross-Laptop kernel: [91557.007077] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.387 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.036710] PM: suspend of drv:nvidia dev:0000:01:00.0 complete after 148.166 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.036728] PM: suspend of drv:pcieport dev:0000:00:03.0 complete after 147.983 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.067901] PM: suspend of drv:sd dev:0:0:0:0 complete after 280.068 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.068017] PM: suspend of drv:scsi dev:target0:0:0 complete after 280.122 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.068041] PM: suspend of drv:scsi dev:host0 complete after 279.895 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.083185] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 194.599 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.083273] PM: suspend of drv: dev:pci0000:00 complete after 194.515 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.083396] PM: suspend of devices complete after 296.021 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.083398] PM: suspend devices took 0.312 seconds
Jan  9 20:52:25 ross-Laptop kernel: [91557.147331] PM: late suspend of devices complete after 63.950 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91557.228111] PM: Saving platform NVS memory
Jan  9 20:52:25 ross-Laptop kernel: [91557.855624] PM: Restoring platform NVS memory
Jan  9 20:52:25 ross-Laptop kernel: [91558.781321] PM: early resume of devices complete after 1.754 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91558.959466] PM: resume of drv:hub dev:2-1:1.0 complete after 177.184 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91558.959476] PM: resume of drv: dev:ep_00 complete after 177.121 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91558.959485] PM: resume of drv: dev:ep_81 complete after 177.158 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.115463] PM: resume of drv:sd dev:0:0:0:0 complete after 333.556 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.115594] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 217.940 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.115611] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 333.679 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.125064] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.704 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.125073] PM: resume of drv: dev:ep_00 complete after 342.614 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.125075] PM: resume of drv: dev:ep_01 complete after 342.690 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.125088] PM: resume of drv: dev:ep_81 complete after 342.676 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.125090] PM: resume of drv: dev:ep_82 complete after 342.650 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.210923] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 429.480 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.334207] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 551.773 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.334222] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 551.754 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.334229] PM: resume of drv: dev:ep_83 complete after 551.776 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91559.334234] PM: resume of drv: dev:ep_00 complete after 551.748 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91560.645994] PM: resume of drv:sd dev:4:0:0:0 complete after 1864.455 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91560.646080] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1864.428 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91560.646226] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1531.089 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91560.649016] PM: resume of devices complete after 1868.225 msecs
Jan  9 20:52:25 ross-Laptop kernel: [91560.649075] PM: resume devices took 1.868 seconds
Jan  9 20:52:25 ross-Laptop kernel: [91560.649097] PM: Finishing wakeup.
Jan  9 21:26:42 ross-Laptop kernel: [91741.576009] PM: Syncing filesystems ... done.
Jan  9 21:26:42 ross-Laptop kernel: [91741.581225] PM: Preparing system for mem sleep
Jan  9 21:26:42 ross-Laptop kernel: [91741.611788] PM: Entering mem sleep
Jan  9 21:26:42 ross-Laptop kernel: [91741.839648] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 116.700 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.904644] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.563 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.904733] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.651 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.904766] PM: suspend of drv:scsi dev:host0 complete after 276.523 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.919672] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 196.783 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.919696] PM: suspend of drv: dev:pci0000:00 complete after 196.711 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.919734] PM: suspend of devices complete after 291.862 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91741.919739] PM: suspend devices took 0.308 seconds
Jan  9 21:26:42 ross-Laptop kernel: [91741.983844] PM: late suspend of devices complete after 64.088 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91742.064656] PM: Saving platform NVS memory
Jan  9 21:26:42 ross-Laptop kernel: [91742.692553] PM: Restoring platform NVS memory
Jan  9 21:26:42 ross-Laptop kernel: [91743.610741] PM: early resume of devices complete after 1.739 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.788968] PM: resume of drv:hub dev:2-1:1.0 complete after 177.490 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.788975] PM: resume of drv: dev:ep_00 complete after 177.472 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.788990] PM: resume of drv: dev:ep_81 complete after 177.505 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.954500] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.961 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.954509] PM: resume of drv: dev:ep_00 complete after 341.567 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.954518] PM: resume of drv: dev:ep_01 complete after 341.610 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.954541] PM: resume of drv: dev:ep_81 complete after 341.617 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.954547] PM: resume of drv: dev:ep_82 complete after 341.605 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.957049] PM: resume of drv:sd dev:0:0:0:0 complete after 345.652 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.957111] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 345.659 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91743.957125] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 229.314 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91744.038228] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 427.191 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91744.164655] PM: resume of drv: dev:ep_00 complete after 551.513 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91744.164664] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 551.544 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91744.164674] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 551.529 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91744.164747] PM: resume of drv: dev:ep_83 complete after 551.626 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91745.375035] PM: resume of drv:sd dev:4:0:0:0 complete after 1763.339 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91745.375126] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1763.393 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91745.375137] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1417.734 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91745.378129] PM: resume of devices complete after 1766.994 msecs
Jan  9 21:26:42 ross-Laptop kernel: [91745.378190] PM: resume devices took 1.768 seconds
Jan  9 21:26:42 ross-Laptop kernel: [91745.378214] PM: Finishing wakeup.
Jan  9 21:50:34 ross-Laptop kernel: [91993.331018] PM: Syncing filesystems ... done.
Jan  9 21:50:34 ross-Laptop kernel: [91993.335934] PM: Preparing system for mem sleep
Jan  9 21:50:34 ross-Laptop kernel: [91993.367296] PM: Entering mem sleep
Jan  9 21:50:34 ross-Laptop kernel: [91993.579075] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.059 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.645127] PM: suspend of drv:sd dev:0:0:0:0 complete after 277.429 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.645218] PM: suspend of drv:scsi dev:target0:0:0 complete after 277.465 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.645239] PM: suspend of drv:scsi dev:host0 complete after 277.303 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.658978] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 197.022 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.659002] PM: suspend of drv: dev:pci0000:00 complete after 196.991 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.659071] PM: suspend of devices complete after 291.605 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.659076] PM: suspend devices took 0.292 seconds
Jan  9 21:50:34 ross-Laptop kernel: [91993.723112] PM: late suspend of devices complete after 64.052 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91993.803890] PM: Saving platform NVS memory
Jan  9 21:50:34 ross-Laptop kernel: [91994.431414] PM: Restoring platform NVS memory
Jan  9 21:50:34 ross-Laptop kernel: [91995.361317] PM: early resume of devices complete after 1.754 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.539273] PM: resume of drv:hub dev:2-1:1.0 complete after 176.986 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.539286] PM: resume of drv: dev:ep_00 complete after 176.945 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.539289] PM: resume of drv: dev:ep_81 complete after 176.977 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.704873] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.543 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.704882] PM: resume of drv: dev:ep_00 complete after 342.463 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.704885] PM: resume of drv: dev:ep_01 complete after 342.535 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.704896] PM: resume of drv: dev:ep_81 complete after 342.521 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.704899] PM: resume of drv: dev:ep_82 complete after 342.498 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.711232] PM: resume of drv:sd dev:0:0:0:0 complete after 349.297 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.711339] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 228.996 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.711361] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 349.411 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.789008] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 427.609 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.913288] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 550.885 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.913303] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 550.853 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.913310] PM: resume of drv: dev:ep_83 complete after 550.882 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91995.913316] PM: resume of drv: dev:ep_00 complete after 550.844 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91997.184080] PM: resume of drv:sd dev:4:0:0:0 complete after 1822.394 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91997.184169] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1822.450 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91997.184286] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1473.391 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91997.186925] PM: resume of devices complete after 1826.115 msecs
Jan  9 21:50:34 ross-Laptop kernel: [91997.186983] PM: resume devices took 1.828 seconds
Jan  9 21:50:34 ross-Laptop kernel: [91997.187005] PM: Finishing wakeup.
Jan 10 13:00:51 ross-Laptop kernel: [95743.851440] PM: Syncing filesystems ... done.
Jan 10 13:00:51 ross-Laptop kernel: [95743.857057] PM: Preparing system for mem sleep
Jan 10 13:00:51 ross-Laptop kernel: [95743.886461] PM: Entering mem sleep
Jan 10 13:00:51 ross-Laptop kernel: [95744.118112] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 117.876 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.178169] PM: suspend of drv:nvidia dev:0000:01:00.0 complete after 178.111 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.178190] PM: suspend of drv:pcieport dev:0000:00:03.0 complete after 177.853 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.179282] PM: suspend of drv:sd dev:0:0:0:0 complete after 276.259 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.179400] PM: suspend of drv:scsi dev:target0:0:0 complete after 276.268 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.179415] PM: suspend of drv:scsi dev:host0 complete after 276.080 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.194106] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 193.991 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.194197] PM: suspend of drv: dev:pci0000:00 complete after 193.844 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.194310] PM: suspend of devices complete after 291.919 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.194314] PM: suspend devices took 0.308 seconds
Jan 10 13:00:51 ross-Laptop kernel: [95744.258250] PM: late suspend of devices complete after 63.951 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95744.339080] PM: Saving platform NVS memory
Jan 10 13:00:51 ross-Laptop kernel: [95744.966577] PM: Restoring platform NVS memory
Jan 10 13:00:51 ross-Laptop kernel: [95745.876318] PM: early resume of devices complete after 1.722 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.054348] PM: resume of drv:hub dev:2-1:1.0 complete after 176.636 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.054354] PM: resume of drv: dev:ep_00 complete after 176.593 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.054415] PM: resume of drv: dev:ep_81 complete after 176.679 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.220007] PM: resume of drv:usb dev:2-1.3:1.0 complete after 342.231 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.220017] PM: resume of drv: dev:ep_00 complete after 342.156 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.220022] PM: resume of drv: dev:ep_01 complete after 342.227 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.220036] PM: resume of drv: dev:ep_82 complete after 342.200 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.220039] PM: resume of drv: dev:ep_81 complete after 342.220 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.242406] PM: resume of drv:sd dev:0:0:0:0 complete after 364.986 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.242458] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 364.981 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.242472] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 244.974 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.302408] PM: resume of drv:nvidia dev:0000:01:00.0 complete after 426.006 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.429405] PM: resume of drv:uvcvideo dev:2-1.5:1.0 complete after 551.556 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.429419] PM: resume of drv:uvcvideo dev:2-1.5:1.1 complete after 551.499 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.429427] PM: resume of drv: dev:ep_83 complete after 551.559 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95746.429433] PM: resume of drv: dev:ep_00 complete after 551.487 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95747.726634] PM: resume of drv:sd dev:4:0:0:0 complete after 1849.537 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95747.726655] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1849.504 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95747.726734] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1484.713 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95747.729545] PM: resume of devices complete after 1853.744 msecs
Jan 10 13:00:51 ross-Laptop kernel: [95747.729604] PM: resume devices took 1.852 seconds
Jan 10 13:00:51 ross-Laptop kernel: [95747.729626] PM: Finishing wakeup.

```

---

### Post by Toz on 2012-01-10
Since the keyboard still works, try the following when you resume and have no touchpad response:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

Does the touchapad start working again?

Curious question. Do you have a joystick or gamepad attached to your computer?

---

### Post by josephellengar on 2012-01-10
> **Toz said:**
> Since the keyboard still works, try the following when you resume and have no touchpad response:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

Does the touchapad start working again?

Curious question. Do you have a joystick or gamepad attached to your computer?

Just suspended and unsuspended until my touchpad froze, and yes, your commands did unfreeze it. However, I do not have a joystick or gamepad attached. Is there any way to get these commands to run every time I wake up my computer from suspend?

EDIT: Thanks for the help!

---

### Post by Toz on 2012-01-10
First, lets try the recommended way.
1. Create (or edit if it already exists) the file **/etc/pm/config.d/config**:
```
gksudo gedit /etc/pm/config.d/config
```

2. Add the following to the file:
```
SUSPEND_MODULES="psmouse"
```

3. Save the file.

Now try it again and see if it works. If it doesn't, there is a second, slightly more complicated way of doing this.

---

### Post by josephellengar on 2012-01-10
> **Toz said:**
> First, lets try the recommended way.
1. Create (or edit if it already exists) the file **/etc/pm/config.d/config**:
```
gksudo gedit /etc/pm/config.d/config
```

2. Add the following to the file:
```
SUSPEND_MODULES="psmouse"
```

3. Save the file.

Now try it again and see if it works. If it doesn't, there is a second, slightly more complicated way of doing this.

Thanks! As of now it seems to work, after 3 suspends/unsuspends. I'll mark the thread solved, but I'll post back if the problem shows up again, so please don't unsubscribe. I really appreciate the help.

---

