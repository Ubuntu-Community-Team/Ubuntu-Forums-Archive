---
title: "Suspend not working"
date: 2012-08-03
forum: General Help
---

### Post by emagar on 2012-08-03
Running ubuntu 12.04. System suspends fine, but will not return to life. Only a reset button will do it. (CTRL-ALT-DEL unresponsive, CTRL-ALT-F1 opens a shell that will not let you do anything). 

I have found threads on this problem for quite old releases. Only [this (see #123)]("http://ubuntuforums.org/showthread.php?t=1968155&page=13") by [Cavsfan]("http://ubuntuforums.org/member.php?u=889820") seems to raise the issue for 12.04. 

Problem is that the proposed [solution]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/") in that post is related to nVidia card that my machine doesn't have (it has intel HD 3000). 

Has anyone encountered the problem and found a workaround? I'm fairly new to Linux and don't know what info I should provide to diagnose my problem. 

Any help will be greatly appreciated.

---

### Post by Toz on 2012-08-07
Can you provide the following further information:
[LIST=1]
[*]The make and model of your computer

[*]A copy of your pm-suspend.log file
From a terminal prompt, type in
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

[*]The results of the following commands:
```
cat /proc/cmdline
cat /var/log/syslog | grep PM:
```
[/LIST]

---

### Post by emagar on 2012-08-07
Thanks for the reply, Toz! Below is the info.

> **Toz said:**
> Can you provide the following further information:
[LIST=1]
[*]The make and model of your computer
[*]A copy of your pm-suspend.log file
From a terminal prompt, type in
```
pastebinit /var/log/pm-suspend.log
```...and post back the link that is generated.
[*]The results of the following commands:
```
cat /proc/cmdline
cat /var/log/syslog | grep PM:
```
[/LIST]


1. Dell xps13 i5core. BIOS updated before nuking windows.
2. [http://paste.ubuntu.com/1135401/](http://paste.ubuntu.com/1135401/)
3a. ```
eric@eric-xps13:~/$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic root=UUID=12365743-f47a-4f91-afd2-14ab3a8b8520 ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7

```3b. (My shell runs out of memory to display more... is this enough?) ```
Aug  7 16:21:50 eric-xps13 kernel: [10672.817363] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 847.961 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817375] PM: resume of drv:generic-usb dev:0003:045E:0773.0001 complete after 422.482 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817378] PM: resume of drv: dev:ep_82 complete after 847.963 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817406] PM: resume of drv: dev:ep_81 complete after 848.030 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817410] PM: resume of drv:usbhid dev:2-1.2:1.2 complete after 847.978 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817419] PM: resume of drv: dev:ep_00 complete after 847.948 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817471] PM: resume of drv: dev:ep_83 complete after 848.019 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020065] PM: resume of drv:uvcvideo dev:1-1.5:1.0 complete after 1050.951 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020070] PM: resume of drv:uvcvideo dev:1-1.5:1.1 complete after 1050.910 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020081] PM: resume of drv:video4linux dev:video0 complete after 202.756 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020105] PM: resume of drv: dev:ep_00 complete after 1050.934 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020112] PM: resume of drv: dev:ep_87 complete after 1050.980 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020210] PM: resume of devices complete after 1052.766 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020483] PM: resume devices took 1.052 seconds
Aug  7 16:21:50 eric-xps13 kernel: [10673.020521] PM: Finishing wakeup.
eric@eric-xps13:~/Dropbox/data/vetopol/usa/escritos/postate$ 
eric@eric-xps13:~/Dropbox/data/vetopol/usa/escritos/postate$ cat /var/log/syslog | grep PM:
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000d910d000 - 00000000daeef000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000daeef000 - 00000000daf9f000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000daf9f000 - 00000000dafff000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000dfa00000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed08000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed08000 - 00000000fed09000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed09000 - 00000000fed10000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffd80000
Aug  7 10:35:58 eric-xps13 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffd80000 - 0000000100000000
Aug  7 10:35:58 eric-xps13 kernel: [    0.493058] PM: Registering ACPI NVS region at daeef000 (720896 bytes)
Aug  7 10:35:58 eric-xps13 kernel: [    1.107563] PM: Hibernation image not present or could not be loaded.
Aug  7 11:24:37 eric-xps13 kernel: [ 2925.627153] PM: Syncing filesystems ... 
Aug  7 11:24:37 eric-xps13 kernel: [ 2925.641470] PM: Preparing system for mem sleep
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.524914] PM: Entering mem sleep
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.737085] PM: suspend of drv:psmouse dev:serio1 complete after 212.014 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.858443] PM: suspend of drv:sd dev:0:0:0:0 complete after 333.399 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.858503] PM: suspend of drv:scsi dev:target0:0:0 complete after 333.439 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.858536] PM: suspend of drv:scsi dev:host0 complete after 119.491 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.880605] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 141.282 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.960544] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 220.978 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.960610] PM: suspend of drv: dev:pci0000:00 complete after 220.857 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.960642] PM: suspend of devices complete after 435.878 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2926.960646] PM: suspend devices took 0.436 seconds
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.040536] PM: late suspend of devices complete after 79.933 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.052776] PM: Saving platform NVS memory
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.265045] PM: Restoring platform NVS memory
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.412015] PM: early resume of devices complete after 2.454 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533410] PM: resume of drv: dev:ep_00 complete after 120.829 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533421] PM: resume of drv: dev:ep_00 complete after 120.322 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533436] PM: resume of drv:hub dev:3-0:1.0 complete after 120.891 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533447] PM: resume of drv:hub dev:4-0:1.0 complete after 120.745 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533466] PM: resume of drv: dev:ep_81 complete after 120.894 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.533469] PM: resume of drv: dev:ep_81 complete after 120.731 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589354] PM: resume of drv: dev:ep_00 complete after 175.844 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589365] PM: resume of drv:hub dev:1-1:1.0 complete after 175.969 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589374] PM: resume of drv:hub dev:2-1:1.0 complete after 175.793 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589392] PM: resume of drv: dev:ep_00 complete after 175.706 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589400] PM: resume of drv: dev:ep_81 complete after 175.925 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.589405] PM: resume of drv: dev:ep_81 complete after 175.821 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.745401] PM: resume of drv:sd dev:0:0:0:0 complete after 332.424 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.745418] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 332.411 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.745447] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 219.184 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757701] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 343.920 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757706] PM: resume of drv:usbhid dev:2-1.2:1.2 complete after 343.878 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757713] PM: resume of drv: dev:ep_82 complete after 343.913 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757716] PM: resume of drv: dev:ep_00 complete after 343.848 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757722] PM: resume of drv: dev:ep_83 complete after 343.877 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757728] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 343.993 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.757744] PM: resume of drv: dev:ep_81 complete after 343.988 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2927.847167] PM: resume of drv:i915 dev:0000:00:02.0 complete after 435.305 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256208] PM: resume of drv:usb dev:2-1.5:1.0 complete after 842.645 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256214] PM: resume of drv:usb dev:2-1.5:1.1 complete after 842.555 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256223] PM: resume of drv:bluetooth dev:hci0 complete after 409.234 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256236] PM: resume of drv: dev:ep_00 complete after 842.514 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256248] PM: resume of drv: dev:ep_81 complete after 842.664 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256256] PM: resume of drv: dev:ep_83 complete after 842.560 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256264] PM: resume of drv: dev:ep_03 complete after 842.589 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256266] PM: resume of drv: dev:ep_02 complete after 842.658 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.256269] PM: resume of drv: dev:ep_82 complete after 842.640 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460513] PM: resume of drv:uvcvideo dev:1-1.5:1.1 complete after 1047.340 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460517] PM: resume of drv: dev:ep_00 complete after 1047.320 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460537] PM: resume of drv:uvcvideo dev:1-1.5:1.0 complete after 1047.414 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460557] PM: resume of drv:video4linux dev:video0 complete after 204.465 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460580] PM: resume of drv: dev:ep_87 complete after 1047.435 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460649] PM: resume of devices complete after 1049.251 msecs
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.460998] PM: resume devices took 1.052 seconds
Aug  7 11:57:35 eric-xps13 kernel: [ 2928.461036] PM: Finishing wakeup.
Aug  7 13:11:05 eric-xps13 kernel: [ 7334.456460] PM: Syncing filesystems ... 
Aug  7 13:11:05 eric-xps13 kernel: [ 7334.493384] PM: Preparing system for mem sleep
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.211307] PM: Entering mem sleep
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.423545] PM: suspend of drv:psmouse dev:serio1 complete after 212.084 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.543013] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 117.181 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.544671] PM: suspend of drv:sd dev:0:0:0:0 complete after 333.160 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.544734] PM: suspend of drv:scsi dev:target0:0:0 complete after 333.204 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.544752] PM: suspend of drv:scsi dev:host0 complete after 119.391 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.566997] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 141.453 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.567065] PM: suspend of drv: dev:pci0000:00 complete after 141.046 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.567088] PM: suspend of devices complete after 355.856 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.567091] PM: suspend devices took 0.356 seconds
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.646993] PM: late suspend of devices complete after 79.952 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.659229] PM: Saving platform NVS memory
Aug  7 14:08:21 eric-xps13 kernel: [ 7335.871468] PM: Restoring platform NVS memory
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.002618] PM: early resume of devices complete after 2.524 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123868] PM: resume of drv: dev:ep_00 complete after 119.948 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123873] PM: resume of drv: dev:ep_00 complete after 120.541 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123898] PM: resume of drv:hub dev:3-0:1.0 complete after 120.638 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123908] PM: resume of drv:hub dev:4-0:1.0 complete after 120.150 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123939] PM: resume of drv: dev:ep_81 complete after 120.673 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.123943] PM: resume of drv: dev:ep_81 complete after 120.148 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179824] PM: resume of drv: dev:ep_00 complete after 175.640 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179830] PM: resume of drv: dev:ep_00 complete after 175.558 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179845] PM: resume of drv:hub dev:1-1:1.0 complete after 175.706 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179859] PM: resume of drv:hub dev:2-1:1.0 complete after 175.639 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179877] PM: resume of drv: dev:ep_81 complete after 175.718 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.179884] PM: resume of drv: dev:ep_81 complete after 175.636 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.335857] PM: resume of drv:sd dev:0:0:0:0 complete after 331.971 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.335878] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 218.666 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.335902] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 331.996 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.421600] PM: resume of drv:i915 dev:0000:00:02.0 complete after 419.116 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683956] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 679.861 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683961] PM: resume of drv:usbhid dev:2-1.2:1.2 complete after 679.824 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683967] PM: resume of drv: dev:ep_82 complete after 679.857 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683970] PM: resume of drv: dev:ep_83 complete after 679.819 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683981] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 679.929 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.683997] PM: resume of drv: dev:ep_81 complete after 679.925 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.684001] PM: resume of drv: dev:ep_00 complete after 679.826 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.684007] PM: resume of drv:generic-usb dev:0003:045E:0773.0001 complete after 262.488 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846641] PM: resume of drv:usb dev:2-1.5:1.1 complete after 842.442 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846668] PM: resume of drv: dev:ep_03 complete after 842.449 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846673] PM: resume of drv:usb dev:2-1.5:1.0 complete after 842.573 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846677] PM: resume of drv: dev:ep_83 complete after 842.431 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846681] PM: resume of drv: dev:ep_00 complete after 842.423 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846687] PM: resume of drv: dev:ep_81 complete after 842.572 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846692] PM: resume of drv: dev:ep_02 complete after 842.536 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.846697] PM: resume of drv: dev:ep_82 complete after 842.521 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.886886] PM: resume of drv:uvcvideo dev:1-1.5:1.1 complete after 883.037 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.886892] PM: resume of drv: dev:ep_00 complete after 883.022 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.886911] PM: resume of drv:uvcvideo dev:1-1.5:1.0 complete after 883.106 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.886926] PM: resume of drv: dev:ep_87 complete after 883.100 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.886929] PM: resume of drv:video4linux dev:video0 complete after 202.999 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.887006] PM: resume of devices complete after 884.881 msecs
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.887299] PM: resume devices took 0.888 seconds
Aug  7 14:08:21 eric-xps13 kernel: [ 7336.887338] PM: Finishing wakeup.
Aug  7 14:30:22 eric-xps13 kernel: [ 8656.180034] PM: Syncing filesystems ... 
Aug  7 14:30:22 eric-xps13 kernel: [ 8656.200606] PM: Preparing system for mem sleep
Aug  7 14:35:46 eric-xps13 kernel: [ 8656.878740] PM: Entering mem sleep
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.098710] PM: suspend of drv:psmouse dev:serio1 complete after 219.812 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.210097] PM: suspend of drv:sd dev:0:0:0:0 complete after 331.171 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.210163] PM: suspend of drv:scsi dev:target0:0:0 complete after 331.222 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.210181] PM: suspend of drv:scsi dev:host0 complete after 110.185 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.218428] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 117.869 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.230428] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 130.245 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.230471] PM: suspend of drv: dev:pci0000:00 complete after 129.754 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.230495] PM: suspend of devices complete after 351.840 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.230497] PM: suspend devices took 0.352 seconds
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.310425] PM: late suspend of devices complete after 79.978 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.322658] PM: Saving platform NVS memory
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.534907] PM: Restoring platform NVS memory
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.670034] PM: early resume of devices complete after 2.474 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.791308] PM: resume of drv:hub dev:3-0:1.0 complete after 120.439 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.791323] PM: resume of drv: dev:ep_00 complete after 120.162 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.791328] PM: resume of drv: dev:ep_81 complete after 120.404 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.795298] PM: resume of drv: dev:ep_00 complete after 123.969 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.795303] PM: resume of drv:hub dev:4-0:1.0 complete after 124.054 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.795348] PM: resume of drv: dev:ep_81 complete after 124.049 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847231] PM: resume of drv:hub dev:1-1:1.0 complete after 175.702 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847238] PM: resume of drv: dev:ep_00 complete after 175.597 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847245] PM: resume of drv: dev:ep_81 complete after 175.636 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847264] PM: resume of drv:hub dev:2-1:1.0 complete after 175.574 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847297] PM: resume of drv: dev:ep_00 complete after 175.561 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8657.847311] PM: resume of drv: dev:ep_81 complete after 175.599 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.003305] PM: resume of drv:sd dev:0:0:0:0 complete after 332.080 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.003377] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 219.199 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.003382] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 332.065 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.093062] PM: resume of drv:i915 dev:0000:00:02.0 complete after 423.168 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350172] PM: resume of drv:usb dev:2-1.5:1.0 complete after 678.457 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350176] PM: resume of drv:usb dev:2-1.5:1.1 complete after 678.368 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350187] PM: resume of drv: dev:ep_02 complete after 678.430 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350190] PM: resume of drv: dev:ep_03 complete after 678.365 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350194] PM: resume of drv: dev:ep_82 complete after 678.414 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350196] PM: resume of drv: dev:ep_83 complete after 678.353 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350199] PM: resume of drv: dev:ep_00 complete after 678.334 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.350204] PM: resume of drv: dev:ep_81 complete after 678.469 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515286] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 843.864 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515290] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 843.819 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515304] PM: resume of drv: dev:ep_82 complete after 843.821 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515307] PM: resume of drv:generic-usb dev:0003:045E:0773.0001 complete after 422.425 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515334] PM: resume of drv: dev:ep_81 complete after 843.892 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515340] PM: resume of drv:usbhid dev:2-1.2:1.2 complete after 843.834 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515351] PM: resume of drv: dev:ep_83 complete after 843.822 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.515359] PM: resume of drv: dev:ep_00 complete after 843.809 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.553950] PM: resume of drv:uvcvideo dev:1-1.5:1.1 complete after 882.620 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.553954] PM: resume of drv:uvcvideo dev:1-1.5:1.0 complete after 882.665 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.553986] PM: resume of drv: dev:ep_00 complete after 882.638 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.554004] PM: resume of drv: dev:ep_87 complete after 882.698 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.554082] PM: resume of devices complete after 884.544 msecs
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.554377] PM: resume devices took 0.884 seconds
Aug  7 14:35:46 eric-xps13 kernel: [ 8658.554414] PM: Finishing wakeup.
Aug  7 15:09:20 eric-xps13 kernel: [10670.468862] PM: Syncing filesystems ... 
Aug  7 15:09:20 eric-xps13 kernel: [10670.497936] PM: Preparing system for mem sleep
Aug  7 16:21:50 eric-xps13 kernel: [10671.168814] PM: Entering mem sleep
Aug  7 16:21:50 eric-xps13 kernel: [10671.381048] PM: suspend of drv:psmouse dev:serio1 complete after 212.062 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.500506] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 117.157 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.508362] PM: suspend of drv:sd dev:0:0:0:0 complete after 339.400 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.508439] PM: suspend of drv:scsi dev:target0:0:0 complete after 339.459 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.508489] PM: suspend of drv:scsi dev:host0 complete after 125.474 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.532503] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 149.346 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.532572] PM: suspend of drv: dev:pci0000:00 complete after 149.042 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.532602] PM: suspend of devices complete after 363.879 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.532613] PM: suspend devices took 0.364 seconds
Aug  7 16:21:50 eric-xps13 kernel: [10671.612495] PM: late suspend of devices complete after 79.932 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10671.624724] PM: Saving platform NVS memory
Aug  7 16:21:50 eric-xps13 kernel: [10671.836976] PM: Restoring platform NVS memory
Aug  7 16:21:50 eric-xps13 kernel: [10671.968019] PM: early resume of devices complete after 2.484 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089423] PM: resume of drv:hub dev:4-0:1.0 complete after 120.171 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089430] PM: resume of drv: dev:ep_00 complete after 120.077 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089435] PM: resume of drv: dev:ep_00 complete after 120.324 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089443] PM: resume of drv: dev:ep_81 complete after 120.136 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089448] PM: resume of drv:hub dev:3-0:1.0 complete after 120.360 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.089462] PM: resume of drv: dev:ep_81 complete after 120.372 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145311] PM: resume of drv: dev:ep_00 complete after 175.626 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145317] PM: resume of drv: dev:ep_00 complete after 175.772 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145324] PM: resume of drv:hub dev:1-1:1.0 complete after 175.847 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145335] PM: resume of drv: dev:ep_81 complete after 175.824 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145346] PM: resume of drv:hub dev:2-1:1.0 complete after 175.759 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.145377] PM: resume of drv: dev:ep_81 complete after 175.785 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.301387] PM: resume of drv:sd dev:0:0:0:0 complete after 332.147 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.301437] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 332.134 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.301442] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 218.569 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316386] PM: resume of drv:usb dev:2-1.5:1.1 complete after 346.440 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316390] PM: resume of drv:usb dev:2-1.5:1.0 complete after 346.520 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316400] PM: resume of drv: dev:ep_83 complete after 346.416 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316403] PM: resume of drv: dev:ep_81 complete after 346.518 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316415] PM: resume of drv: dev:ep_03 complete after 346.449 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316425] PM: resume of drv: dev:ep_00 complete after 346.421 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316428] PM: resume of drv: dev:ep_82 complete after 346.501 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.316434] PM: resume of drv: dev:ep_02 complete after 346.529 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.395109] PM: resume of drv:i915 dev:0000:00:02.0 complete after 427.149 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817358] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 848.000 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817363] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 847.961 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817375] PM: resume of drv:generic-usb dev:0003:045E:0773.0001 complete after 422.482 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817378] PM: resume of drv: dev:ep_82 complete after 847.963 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817406] PM: resume of drv: dev:ep_81 complete after 848.030 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817410] PM: resume of drv:usbhid dev:2-1.2:1.2 complete after 847.978 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817419] PM: resume of drv: dev:ep_00 complete after 847.948 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10672.817471] PM: resume of drv: dev:ep_83 complete after 848.019 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020065] PM: resume of drv:uvcvideo dev:1-1.5:1.0 complete after 1050.951 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020070] PM: resume of drv:uvcvideo dev:1-1.5:1.1 complete after 1050.910 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020081] PM: resume of drv:video4linux dev:video0 complete after 202.756 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020105] PM: resume of drv: dev:ep_00 complete after 1050.934 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020112] PM: resume of drv: dev:ep_87 complete after 1050.980 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020210] PM: resume of devices complete after 1052.766 msecs
Aug  7 16:21:50 eric-xps13 kernel: [10673.020483] PM: resume devices took 1.052 seconds
Aug  7 16:21:50 eric-xps13 kernel: [10673.020521] PM: Finishing wakeup.

```

---

### Post by Toz on 2012-08-07
According to your log files, suspend and resume is working. I'm guessing your getting a black screen (i.e. don't get the gui back).

What exactly do you mean by:> CTRL-ALT-F1 opens a shell that will not let you do anything)

Have you/can you try the following when you resume:
1. Ctrl+Alt+F1 and then back to Ctrl+Alt+F7
2. Blindly type in your password and press enter
3. Try using your brightness function keys (in case its coming back with the brightness fully dimmed).

Can you also post back the results of the following command (to determine your video card and driver):
```
sudo lspci -vnn | grep -A10 VGA
```

Edit: You might as well get me this as well. Run this command and post the results to get info about your backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/actual_brightness; cat $interface/brightness; done
```

---

### Post by Toz on 2012-08-07
Okay, I think I know what might be happening. Have a look at this PPA which is for a tailored kernel for the XPS 13 to address some issues including backlight (which I think is what is happening to your laptop on resume) and the trackpad: [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise]("https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise").

---

### Post by emagar on 2012-08-08
> **Toz said:**
> Okay, I think I know what might be happening. Have a look at this PPA which is for a tailored kernel for the XPS 13 to address some issues including backlight (which I think is what is happening to your laptop on resume) and the trackpad: [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise]("https://launchpad.net/%7Ecanonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise").

Thanks again. I will look a these carefully tomorrow morning.

System froze again. I managed to get a shell back, but the system appears to resume in read-only mode. I ran again the PM: command, and these two lines appended to what I reported above. I then tried to reboot unsuccessfully.

```

Aug  7 22:28:01 eric-xps13 kernel: [32627.127878] PM: syncing file systems ...
Aug  7 22:28:01 eric-xps13 kernel: [32627.127878] PM: preparing system for mem sleep

eric@eric-xps13:~/sudo reboot
[sudo] password for eric:
sudo: unable to open /var/lib/sudo/eric/0: Read-only file system

```

Does this change anything from your last diagnosis?
I really appreciate your help.

---

### Post by emagar on 2012-08-08
> **Toz said:**
> Okay, I think I know what might be happening. Have a look at this PPA which is for a tailored kernel for the XPS 13 to address some issues including backlight (which I think is what is happening to your laptop on resume) and the trackpad: [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise]("https://launchpad.net/%7Ecanonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise").

I have added the PPA described in the post. I'll monitor my system and report in a couple of days if this is SOLVED. Thanks a lot.

---

### Post by emagar on 2012-08-12
> **Toz said:**
> Okay, I think I know what might be happening. Have a look at this PPA which is for a tailored kernel for the XPS 13 to address some issues including backlight (which I think is what is happening to your laptop on resume) and the trackpad: [https://launchpad.net/~canonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise]("https://launchpad.net/%7Ecanonical-hwe-team/+archive/sputnik-kernel?field.series_filter=precise").

I added the PPA. Now, whenever I sudo apt-get update, I get this error at the end of the process:

```

...
Fetched 96.4 kB in 3s (30.6 kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 23BEB290D9AAAA49 Launchpad PPA for Canonical Hardware Enablement Team

```What does this mean and how can I fix it?
My original suspend problem remains unsolved... could this  be related to this error?

Thanks again.

---

### Post by Toz on 2012-08-13
Try running these commands to rebuild the cache:
```

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit

```

---

### Post by emagar on 2012-08-13
> **Toz said:**
> Try running these commands to rebuild the cache:
```

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit

```

Thanks (again!) Toz. This has solved the PPA error issue. I'll monitor if the suspend issue has also been resolved, and report back. Have a nice day.

---

### Post by emagar on 2012-10-04
After months of miseries, I discovered that the problem was hardware-related. My hard drive was faulty, preventing system recovery after suspending the machine. Thanks a lot for the input, for it helped pave the way to finding a solution. 
Cheers!

---

