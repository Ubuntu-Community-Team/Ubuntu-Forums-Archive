---
title: "lenovo s10-3t stacking when suspend"
date: 2012-01-07
forum: General Help
---

### Post by afrilas on 2012-01-07
hi,

i noticed that some times my laptop hang after i am trying to wake it up from suspend mode

---

### Post by afrilas on 2012-01-08
well this does not happens with hibernate, only when suspend and it is like 70-80% that it will hang after a suspend.. some times it works though. could it be a bios problem?

---

### Post by Toz on 2012-01-08
> **afrilas said:**
> well this does not happens with hibernate, only when suspend and it is like 70-80% that it will hang after a suspend.. some times it works though. could it be a bios problem?

What would help would be some log file information. A sample of a good suspend and a bad suspend. The main log file is **/var/log/pm-suspend**. Also of benefit would be the results of:
```
cat /var/log/syslog* | grep PM:
```

If you could provide samples of the 2 above after a successful suspend and after an unsuccessful suspend, we could compare for differences.

---

### Post by afrilas on 2012-01-09
may i post the whole log file? because is huge.

---

### Post by Toz on 2012-01-09
Sure. Just post it between code tags. See the following link for more information: [http://ubuntuforums.org/misc.php?do=bbcode#code]("http://ubuntuforums.org/misc.php?do=bbcode#code")

btw: here is a link that might help with your issue: [http://www.organicdesign.co.nz/Lenovo_Ideapad_S10-3]("http://www.organicdesign.co.nz/Lenovo_Ideapad_S10-3")

---

### Post by afrilas on 2012-01-13
> **Toz said:**
> What would help would be some log file information. A  sample of a good suspend and a bad suspend. The main log file is **/var/log/pm-suspend**. Also of benefit would be the results of:
```
cat /var/log/syslog* | grep PM:
```If you could provide samples  of the 2 above after a successful suspend and after an unsuccessful  suspend, we could compare for differences.

Hello, sorry for late response ,my sister had the laptop for couple of day and i want able to work on it.
I wasn't able to make a successful suspend, after trying some times it always hang and i had to press the power button for 5 sec to close it (i attached 2 log files after bad suspends). here is the results of "cat /var/log/syslog* | grep PM:"

```
kostas@kostas-Lenovo-Ideapad-S10-3t:~$ cat /var/log/syslog* | grep PM:
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.160575] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 12 18:32:13 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.155529] PM: Hibernation image not present or could not be loaded.
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.168577] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 12 19:09:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.084513] PM: Hibernation image not present or could not be loaded.
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.160576] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 12 22:45:50 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.055837] PM: Hibernation image not present or could not be loaded.
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.168575] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 15:28:29 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.125098] PM: Hibernation image not present or could not be loaded.
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.172887] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 18:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.007744] PM: Hibernation image not present or could not be loaded.
Jan 13 19:07:20 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2402.887244] PM: Syncing filesystems ... done.
Jan 13 19:07:20 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2402.896176] PM: Preparing system for mem sleep
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2403.444279] PM: Entering mem sleep
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2403.656125] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.304 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.035813] PM: suspend of drv:sd dev:0:0:0:0 complete after 589.878 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.035876] PM: suspend of drv:scsi dev:target0:0:0 complete after 589.831 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.035929] PM: suspend of drv:scsi dev:host0 complete after 589.524 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.052170] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 515.575 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.052227] PM: suspend of drv: dev:pci0000:00 complete after 514.666 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.052244] PM: suspend of devices complete after 607.528 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.052250] PM: suspend devices took 0.608 seconds
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.069017] PM: late suspend of devices complete after 16.750 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.120256] PM: Saving platform NVS memory
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.224808] PM: Restoring platform NVS memory
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.588455] PM: early resume of devices complete after 4.251 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708203] PM: resume of drv:hub dev:4-0:1.0 complete after 116.512 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708233] PM: resume of drv: dev:ep_00 complete after 116.397 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708254] PM: resume of drv: dev:ep_81 complete after 116.494 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708339] PM: resume of drv:hub dev:5-0:1.0 complete after 116.348 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708374] PM: resume of drv: dev:ep_00 complete after 116.087 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.708393] PM: resume of drv: dev:ep_81 complete after 116.185 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.763178] PM: resume of drv:i915 dev:0000:00:02.0 complete after 174.533 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812199] PM: resume of drv:hub dev:2-0:1.0 complete after 221.039 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812229] PM: resume of drv: dev:ep_00 complete after 221.049 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812248] PM: resume of drv: dev:ep_81 complete after 221.082 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812268] PM: resume of drv:hub dev:3-0:1.0 complete after 220.896 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812292] PM: resume of drv: dev:ep_00 complete after 220.774 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.812313] PM: resume of drv: dev:ep_81 complete after 220.866 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.840247] PM: resume of drv: dev:ep_00 complete after 249.143 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.840257] PM: resume of drv:hub dev:1-0:1.0 complete after 249.184 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.840308] PM: resume of drv: dev:ep_81 complete after 249.237 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2404.854181] PM: resume of drv:battery dev:PNP0C0A:00 complete after 245.059 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.097522] PM: resume of drv:uvcvideo dev:1-8:1.1 complete after 504.837 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.097540] PM: resume of drv:uvcvideo dev:1-8:1.0 complete after 505.008 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.097564] PM: resume of drv: dev:ep_00 complete after 504.800 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.097583] PM: resume of drv: dev:ep_81 complete after 504.969 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347660] PM: resume of drv:usb dev:3-2:1.0 complete after 753.729 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347667] PM: resume of drv:usb dev:3-2:1.2 complete after 753.201 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347690] PM: resume of drv:usb dev:3-2:1.1 complete after 753.457 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347697] PM: resume of drv: dev:ep_81 complete after 753.686 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347711] PM: resume of drv:usb dev:3-2:1.3 complete after 753.024 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347719] PM: resume of drv: dev:ep_82 complete after 753.629 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347727] PM: resume of drv: dev:ep_84 complete after 753.188 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347734] PM: resume of drv: dev:ep_02 complete after 753.578 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347741] PM: resume of drv: dev:ep_04 complete after 753.129 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347774] PM: resume of drv: dev:ep_03 complete after 753.388 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347783] PM: resume of drv: dev:ep_00 complete after 753.008 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.347790] PM: resume of drv: dev:ep_83 complete after 753.479 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.598376] PM: resume of drv:usbhid dev:3-1:1.0 complete after 1005.221 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.598402] PM: resume of drv: dev:ep_00 complete after 1005.084 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.598409] PM: resume of drv: dev:ep_81 complete after 1005.179 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.855232] PM: resume of drv:usbhid dev:2-1:1.1 complete after 1261.609 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.855240] PM: resume of drv:usbhid dev:2-1:1.0 complete after 1261.760 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.855253] PM: resume of drv: dev:ep_00 complete after 1261.483 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.855264] PM: resume of drv: dev:ep_82 complete after 1261.567 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2405.855288] PM: resume of drv: dev:ep_81 complete after 1261.741 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.002681] PM: resume of drv:sd dev:0:0:0:0 complete after 2409.821 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.002738] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2130.649 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.003404] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2410.405 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.003466] PM: resume of devices complete after 2414.938 msecs
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.004145] PM: resume devices took 2.416 seconds
Jan 13 19:07:29 kostas-Lenovo-Ideapad-S10-3t kernel: [ 2407.004227] PM: Finishing wakeup.
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.164571] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:08:42 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.987400] PM: Hibernation image not present or could not be loaded.
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.164574] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:10:53 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.994450] PM: Hibernation image not present or could not be loaded.
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.164573] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:17:15 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.003957] PM: Hibernation image not present or could not be loaded.
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.172575] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:22:34 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.023688] PM: Hibernation image not present or could not be loaded.
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.168573] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:27:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.003169] PM: Hibernation image not present or could not be loaded.
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:37:27 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.160578] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:37:28 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.999448] PM: Hibernation image not present or could not be loaded.
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:39:40 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.156567] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:39:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.995821] PM: Hibernation image not present or could not be loaded.
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.168576] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:43:07 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.002157] PM: Hibernation image not present or could not be loaded.
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.172574] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:45:30 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.055948] PM: Hibernation image not present or could not be loaded.
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.164573] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:48:09 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.050337] PM: Hibernation image not present or could not be loaded.
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.164571] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:51:31 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.999594] PM: Hibernation image not present or could not be loaded.
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.172565] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 13 19:53:59 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.002154] PM: Hibernation image not present or could not be loaded.
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    0.168413] PM: Registering ACPI NVS region at 3f5e0000 (12288 bytes)
Jan 12 14:07:41 kostas-Lenovo-Ideapad-S10-3t kernel: [    1.145585] PM: Hibernation image not present or could not be loaded.
kostas@kostas-Lenovo-Ideapad-S10-3t:~$ 

```BTW i tryed adding GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  intel_idle.max_cstate=0  nohpet" at [I]/etc/default/grub but it didn't made a difference
[/I]

---

### Post by Toz on 2012-01-13
> BTW i tryed adding GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=0 nohpet" at /etc/default/grub but it didn't made a difference
Did you run:
```
sudo update-grub
```
afterwards?
Try it one more time, and when you boot with the new parameters, post back the results of:
```

cat /proc/cmdline
```

--- 

Also, can you also try the following (to get a more detailed log file):
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend

```
On restart (assuming it doesn't restore) post back the contents of /var/log/pm-suspend.log.

---

### Post by afrilas on 2012-01-14
> **Toz said:**
> Did you run:
```
sudo update-grub
```afterwards?
Try it one more time, and when you boot with the new parameters, post back the results of:
```

cat /proc/cmdline
```--- 

Also, can you also try the following (to get a more detailed log file):
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend

```On restart (assuming it doesn't restore) post back the contents of /var/log/pm-suspend.log.

hello,
thanks for the response, did everything as you said,

Here is the resaults of  "cat /proc/cmdline" 

```
kostas@kostas-Lenovo-Ideapad-S10-3t:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=104e443f-3080-4f3a-8810-cfdeecf81ada ro quiet splash intel_idle.max_cstate=0 nohpet vt.handoff=7
```and here is the contends of pm-suspend.log after after the failed suspend

pm-suspend.log

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Sat Jan 14 10:30:54 EET 2012: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sat Jan 14 10:30:54 EET 2012: Running hooks for suspend. = -n ]
+ printf %s\n Sat Jan 14 10:30:54 EET 2012: Running hooks for suspend.
Sat Jan 14 10:30:54 EET 2012: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs=     

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS=     

+ uniq
+ sort
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS=     

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
+ lsmod
Module                  Size  Used by
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746810  0 
reiserfs              230932  0 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
brcmsmac              591864  0 
snd_seq_midi           13132  0 
btusb                  18160  1 
videodev               85626  1 uvcvideo
brcmutil               16885  1 brcmsmac
snd_rawmidi            25241  1 snd_seq_midi
hid_multitouch         12851  0 
mac80211              393459  1 brcmsmac
psmouse                73673  0 
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 brcmsmac,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
crc_ccitt              12595  1 brcmsmac
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
i915                  505159  3 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
wmi                    18744  0 
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       1015728     864548     151180          0      49900     485700
-/+ buffers/cache:     328948     686780
Swap:      1036284          0    1036284
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ + trsed -d s/109//  

+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=kostas
+ save_pulse_state sink kostas
+ su kostas -c -- pacmd list-sinks
+ index=
+ read field value
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:kostas:sink0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ save_pulse_state source kostas
+ index=
+ read field value
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ su kostas -c -- pacmd list-sources
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:kostas:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:kostas:source1 no
+ [ -n no ]
+ echo no
+ read field value
+ su kostas -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ awk -F: {print $3}
+ getent passwd pulse
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ sed s/109//
+ tr -d  
+ ps -C pulseaudio -o uid=
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=kostas
+ su kostas -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink kostas
+ + index=
sed+  -nread s/^[[:space:]*]*//; /\(index\|mute\)/p field
 value
+ su kostas -c -- pacmd list-sinks
+ [ index = index ]
+ index=0
+ su kostas -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source kostas
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
+ su kostas -c -- pacmd list-sources
+ [ index = index ]
+ index=0
+ su kostas -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su kostas -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> + read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Selected interface 'wlan0'
OK
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
       --quirk-dpms-suspend
       --quirk-s3-mode
       --quirk-s3-bios
       --quirk-vbe-post
       --quirk-vbe-post
       --quirk-vga-mode-3
       --quirk-vbemode-restore
       --quirk-vbestate-restore
       --quirk-reset-brightness
       --quirk-radeon-off
       --quirk-no-fb
       --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=24CN62WW
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=24CN62WW
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=08/30/2010
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=08/30/2010
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=20040M18
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=20040M18
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Lenovo Ideapad S10-3t'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Lenovo Ideapad S10-3t'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=Caucasus2
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=Caucasus2
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Rev 1.0'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Rev 1.0'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=LENOVO
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:00:02.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x8086
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:00:02.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0xa011
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0xa011
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0xa011
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:00:02.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:00:02.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../bus/pci/drivers/i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=i915
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@85(videoget): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=true
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
    system.firmware.release_date
        system.hardware.vendor
    system.hardware.product 
        system.hardware.version
    system.board.product 
        system.board.version 
        system.board.vendor
    system.hardware.primary_video.vendor
    system.hardware.primary_video.product
    system.hardware.primary_video.driver
    system.hardware.primary_video.using_kms
    system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@239(has_parameter): get_parameters
//usr/lib/pm-utils/functions@234(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@243(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@360(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@361(): add_parameters --quirk-no-chvt
/usr/lib/pm-utils/functions@226(add_parameters): remove_parameters --quirk-no-chvt
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-no-chvt = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-chvt
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@227(add_parameters): for x in '"$@"'
/usr/lib/pm-utils/functions@228(add_parameters): echo --quirk-no-chvt
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@362(): echo 'Kernel modesetting video driver detected, not using quirks.'
Kernel modesetting video driver detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=--quirk-no-chvt
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ QUIRK_NO_CHVT=true
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set true
+ return 0
+ return
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS=     

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS=     

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Sat Jan 14 10:30:57 EET 2012: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sat Jan 14 10:30:57 EET 2012: performing suspend = -n ]
+ printf %s\n Sat Jan 14 10:30:57 EET 2012: performing suspend
Sat Jan 14 10:30:57 EET 2012: performing suspend
+ sync
+ do_suspend
+ echo -n mem
```pm-suspend.log.BAK

```
Initial commandline parameters: 
Sun Jan  8 09:05:01 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
wl                   2646601  0 
lib80211               14570  1 wl
snd_seq_midi           13132  0 
bcma                   19571  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
hid_multitouch         12851  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              591864  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
btusb                  18160  1 
i915                  505159  3 
psmouse                73673  0 
drm_kms_helper         32889  1 i915
cfg80211              172392  2 brcmsmac,mac80211
bluetooth             148839  23 rfcomm,bnep,btusb
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
crc_ccitt              12595  1 brcmsmac
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     930280      85448          0      30008     513208
-/+ buffers/cache:     387064     628664
Swap:      1036284       8796    1027488

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jan  8 09:05:07 EET 2012: performing suspend
Initial commandline parameters: 
Sun Jan  8 10:15:24 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
snd_seq_midi           13132  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
btusb                  18160  1 
brcmsmac              591864  0 
hid_multitouch         12851  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
bluetooth             148839  23 bnep,rfcomm,btusb
brcmutil               16885  1 brcmsmac
binfmt_misc            17292  1 
mac80211              393459  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 brcmsmac,mac80211
wmi                    18744  0 
i915                  505159  3 
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     647896     367832          0      77284     419192
-/+ buffers/cache:     151420     864308
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jan  8 10:15:27 EET 2012: performing suspend
Initial commandline parameters: 
Sun Jan  8 10:42:00 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
ideapad_laptop         13575  0 
bluetooth             148839  23 bnep,rfcomm,btusb
sparse_keymap          13658  1 ideapad_laptop
hid_multitouch         12851  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              591864  0 
binfmt_misc            17292  1 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 brcmsmac,mac80211
wmi                    18744  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505159  3 
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     554464     461264          0      56560     316440
-/+ buffers/cache:     181464     834264
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jan  8 10:42:03 EET 2012: performing suspend
Sun Jan  8 10:42:17 EET 2012: Awake.
Sun Jan  8 10:42:17 EET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Jan  8 10:42:20 EET 2012: Finished.
Initial commandline parameters: 
Tue Jan 10 23:39:40 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  8 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
btusb                  18160  1 
hid_multitouch         12851  0 
snd_hda_intel          24262  10 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                73673  0 
snd_pcm                80435  4 snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
i915                  505159  4 
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_midi           13132  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
crc_ccitt              12595  1 brcmsmac
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
snd                    55902  27 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  5 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     761264     254464          0      25908     378216
-/+ buffers/cache:     357140     658588
Swap:      1036284      70948     965336

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jan 10 23:39:45 EET 2012: performing suspend
Wed Jan 11 14:28:08 EET 2012: Awake.
Wed Jan 11 14:28:08 EET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: Returned exit code 1.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Initial commandline parameters: 
Wed Jan 11 18:31:51 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
btusb                  18160  1 
hid_multitouch         12851  0 
snd_hda_intel          24262  4 
bluetooth             148839  13 bnep,rfcomm,btusb
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                73673  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
i915                  505159  4 
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_midi           13132  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
crc_ccitt              12595  1 brcmsmac
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
snd                    55902  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   192194  5 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     693372     322356          0      16660     388132
-/+ buffers/cache:     288580     727148
Swap:      1036284     190596     845688

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Jan 11 18:31:55 EET 2012: performing suspend
Wed Jan 11 18:34:36 EET 2012: Awake.
Wed Jan 11 18:34:36 EET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: Returned exit code 1.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Initial commandline parameters: 
Fri Jan 13 19:07:16 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 622556  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31444  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55577  2 vfat,msdos
jfs                   175084  0 
xfs                   746810  0 
reiserfs              230932  0 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
bnep                   17923  2 
rfcomm                 38408  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
joydev                 17393  0 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
hid_multitouch         12851  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
btusb                  18160  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             148839  13 bnep,rfcomm,btusb
cfg80211              172392  2 brcmsmac,mac80211
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
crc_ccitt              12595  1 brcmsmac
binfmt_misc            17292  1 
soundcore              12600  1 snd
wmi                    18744  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i915                  505159  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     835088     180640          0      36852     555276
-/+ buffers/cache:     242960     772768
Swap:      1036284       1368    1034916

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:07:20 EET 2012: performing suspend
Fri Jan 13 19:07:29 EET 2012: Awake.
Fri Jan 13 19:07:29 EET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level    = 128

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jan 13 19:07:32 EET 2012: Finished.
Initial commandline parameters: 
Fri Jan 13 19:09:26 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
bnep                   17923  2 
rfcomm                 38408  8 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
joydev                 17393  0 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
hid_multitouch         12851  0 
psmouse                73673  0 
serio_raw              12990  0 
brcmsmac              591864  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
brcmutil               16885  1 brcmsmac
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              393459  1 brcmsmac
i915                  505159  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
wmi                    18744  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     485912     529816          0      43864     274200
-/+ buffers/cache:     167848     847880
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:09:31 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:21:21 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
bnep                   17923  2 
rfcomm                 38408  8 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  2 
psmouse                73673  0 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
serio_raw              12990  0 
snd_hwdep              13276  1 snd_hda_codec
hid_multitouch         12851  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
brcmsmac              591864  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
snd_seq_midi           13132  0 
brcmutil               16885  1 brcmsmac
i915                  505159  3 
snd_rawmidi            25241  1 snd_seq_midi
mac80211              393459  1 brcmsmac
binfmt_misc            17292  1 
drm_kms_helper         32889  1 i915
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   192194  4 i915,drm_kms_helper
crc_ccitt              12595  1 brcmsmac
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     698016     317712          0      46376     411904
-/+ buffers/cache:     239736     775992
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:21:24 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:26:11 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
rfcomm                 38408  8 
bnep                   17923  2 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
videodev               85626  1 uvcvideo
btusb                  18160  2 
psmouse                73673  0 
bluetooth             148839  23 rfcomm,bnep,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
hid_multitouch         12851  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
cfg80211              172392  2 brcmsmac,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt              12595  1 brcmsmac
binfmt_misc            17292  1 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
i915                  505159  3 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
wmi                    18744  0 
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     695148     320580          0      53580     401592
-/+ buffers/cache:     239976     775752
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:26:14 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:30:41 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  8 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
btusb                  18160  2 
joydev                 17393  0 
snd_hda_intel          24262  2 
hid_multitouch         12851  0 
bluetooth             148839  23 bnep,rfcomm,btusb
brcmsmac              591864  0 
psmouse                73673  0 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
serio_raw              12990  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  505159  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
binfmt_misc            17292  1 
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
crc_ccitt              12595  1 brcmsmac
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     700256     315472          0      50992     414232
-/+ buffers/cache:     235032     780696
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:30:44 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:38:13 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
uvcvideo               67271  0 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
videodev               85626  1 uvcvideo
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
btusb                  18160  2 
psmouse                73673  0 
bluetooth             148839  23 bnep,rfcomm,btusb
hid_multitouch         12851  0 
joydev                 17393  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
i915                  505159  3 
wmi                    18744  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
drm                   192194  4 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     458508     557220          0      51412     280868
-/+ buffers/cache:     126228     889500
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:38:17 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:41:37 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
bnep                   17923  2 
rfcomm                 38408  8 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
videodev               85626  1 uvcvideo
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
hid_multitouch         12851  0 
psmouse                73673  0 
btusb                  18160  1 
serio_raw              12990  0 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq_midi           13132  0 
brcmsmac              591864  0 
snd_rawmidi            25241  1 snd_seq_midi
ideapad_laptop         13575  0 
brcmutil               16885  1 brcmsmac
sparse_keymap          13658  1 ideapad_laptop
mac80211              393459  1 brcmsmac
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  505159  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
wmi                    18744  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     480096     535632          0      49692     292552
-/+ buffers/cache:     137852     877876
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:41:39 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:44:08 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
bnep                   17923  2 
rfcomm                 38408  8 
snd_hda_codec_conexant    52418  1 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
snd_hda_intel          24262  2 
serio_raw              12990  0 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
btusb                  18160  2 
hid_multitouch         12851  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
brcmsmac              591864  0 
binfmt_misc            17292  1 
brcmutil               16885  1 brcmsmac
i915                  505159  3 
mac80211              393459  1 brcmsmac
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     469664     546064          0      52336     282576
-/+ buffers/cache:     134752     880976
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:44:11 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:46:29 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  8 
wl                   2646601  0 
bnep                   17923  2 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73673  0 
serio_raw              12990  0 
btusb                  18160  2 
bluetooth             148839  23 rfcomm,bnep,btusb
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
hid_multitouch         12851  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
brcmsmac              591864  0 
snd_seq_midi_event     14475  1 snd_seq_midi
brcmutil               16885  1 brcmsmac
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              393459  1 brcmsmac
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 brcmsmac,mac80211
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505159  3 
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     457568     558160          0      47992     275068
-/+ buffers/cache:     134508     881220
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'wlan0'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:46:33 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:49:34 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
uvcvideo               67271  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
videodev               85626  1 uvcvideo
btusb                  18160  2 
hid_multitouch         12851  0 
snd_seq_midi           13132  0 
bluetooth             148839  23 bnep,rfcomm,btusb
psmouse                73673  0 
brcmsmac              591864  0 
snd_rawmidi            25241  1 snd_seq_midi
serio_raw              12990  0 
brcmutil               16885  1 brcmsmac
mac80211              393459  1 brcmsmac
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172392  2 brcmsmac,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
crc_ccitt              12595  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
i915                  505159  3 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
wmi                    18744  0 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     511232     504496          0      47592     283884
-/+ buffers/cache:     179756     835972
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:49:38 EET 2012: performing suspend
Initial commandline parameters: 
Fri Jan 13 19:52:51 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux kostas-Lenovo-Ideapad-S10-3t 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
bnep                   17923  2 
rfcomm                 38408  8 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
hid_multitouch         12851  0 
btusb                  18160  1 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
brcmutil               16885  1 brcmsmac
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
mac80211              393459  1 brcmsmac
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
i915                  505159  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 i915
wmi                    18744  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  1 hid_multitouch
hid                    77367  2 hid_multitouch,usbhid
ahci                   21634  2 
libahci                25727  1 ahci
tg3                   132972  0 
             total       used       free     shared    buffers     cached
Mem:       1015728     475276     540452          0      48508     286140
-/+ buffers/cache:     140628     875100
Swap:      1036284          0    1036284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jan 13 19:52:54 EET 2012: performing suspend
```

---

### Post by Toz on 2012-01-14
Hmmm. Log files look okay (except of course for the fact that the system doesn't awake on resume).

Can you try the following kernel options:
- **nohpet** (by itself)
- **hpet=disable**
- **intel_idle.max_cstate=0 hpet=disable**

Not sure if you've come across this, but there is a bug report for this problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/598664").

Also, this thread on ubuntuforums: [http://ubuntuforums.org/showthread.php?t=1415915]("http://ubuntuforums.org/showthread.php?t=1415915").

---

