---
title: "System freeze after failed USB flash drive eject"
date: 2011-04-25
forum: General Help
---

### Post by Archie18 on 2011-04-25
Dear Forum,

When I returned to my Ubuntu 10.10 x64 (2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux) desktop this morning my sytem was frozen. Only a hard power off would reset it.

Last thing I did with the desktop was to copy a couple of files to my USB thumb drive. When I tried to eject the drive via Nautilus a message appeared stating: "Saving data to USB drive <NAME>. To prevent data loss wait..." (or similar). However, that message never disappeared. I was in a hurry, so I just plugged the flash drive off. After a few moments the drive disappeared from the mount table. But the root device /dev/sdc did not disapprear. All files were transfered successfully. I had to check this with a different computer because the USB flash drive wouldn't mount anymore.

After this, according to the logs, it took one more day until the freeze. Here's a snippet of my /var/log/messages log file:

```
Apr 21 19:20:55 archimedes kernel: [263957.279651] usb 7-1.2: new full speed USB device using uhci_hcd and address 5
Apr 21 19:20:55 archimedes kernel: [263957.384618] usb 7-1.2: not running at top speed; connect to a high speed hub
Apr 21 19:20:55 archimedes kernel: [263957.510871] Initializing USB Mass Storage driver...
Apr 21 19:20:55 archimedes kernel: [263957.511249] scsi6 : usb-storage 7-1.2:1.0
Apr 21 19:20:55 archimedes kernel: [263957.511399] usbcore: registered new interface driver usb-storage
Apr 21 19:20:55 archimedes kernel: [263957.511403] USB Mass Storage support registered.
Apr 21 19:20:56 archimedes kernel: [263958.512151] scsi 6:0:0:0: Direct-Access     Imation  Flash Drive      1.20 PQ: 0 ANSI: 2
Apr 21 19:20:56 archimedes kernel: [263958.513127] sd 6:0:0:0: Attached scsi generic sg3 type 0
Apr 21 19:20:56 archimedes kernel: [263958.518131] sd 6:0:0:0: [sdc] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
Apr 21 19:20:56 archimedes kernel: [263958.521146] sd 6:0:0:0: [sdc] Write Protect is off
Apr 21 19:20:57 archimedes kernel: [263958.536124]  sdc: sdc1
Apr 21 19:20:57 archimedes kernel: [263958.800999] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Apr 21 19:24:40 archimedes kernel: [264181.835572] usb 7-1.2: USB disconnect, address 5
Apr 21 20:00:29 archimedes kernel: [266329.317291] aptd[13742] general protection ip:4d36f0 sp:7fffe4ec5568 error:0 in python2.6[400000+21a000]
Apr 21 20:06:29 archimedes kernel: [266689.185995] aptd[13761] general protection ip:467400 sp:7fffe7251f40 error:0 in python2.6[400000+21a000]
Apr 21 20:11:30 archimedes kernel: [266989.936163] aptd[13763] general protection ip:4d36f0 sp:7fff8dd369b8 error:0 in python2.6[400000+21a000]
Apr 21 20:22:31 archimedes kernel: [267650.587214] aptd[13784] general protection ip:467400 sp:7fff27c27a80 error:0 in python2.6[400000+21a000]
Apr 21 21:34:37 archimedes kernel: [271974.096050] aptd[13892] general protection ip:467400 sp:7fff713de570 error:0 in python2.6[400000+21a000]
Apr 21 21:57:38 archimedes kernel: [273354.325256] aptd[13926]: segfault at 31 ip 000000000044d5a2 sp 00007fffc0ab2920 error 4 in python2.6[400000+21a000]
Apr 21 22:13:40 archimedes kernel: [274315.709528] aptd[13953] general protection ip:4d36f0 sp:7fff92045ff8 error:0 in python2.6[400000+21a000]
Apr 21 22:35:42 archimedes kernel: [275637.009251] aptd[13990] general protection ip:467400 sp:7fffa26728f0 error:0 in python2.6[400000+21a000]
Apr 21 22:53:42 archimedes kernel: [276716.332137] aptd[14013] general protection ip:467400 sp:7fff2b916500 error:0 in python2.6[400000+21a000]
Apr 21 22:59:42 archimedes kernel: [277076.182834] aptd[14020] general protection ip:467400 sp:7fff563d3550 error:0 in python2.6[400000+21a000]
Apr 21 23:41:48 archimedes kernel: [279600.734828] aptd[14103] general protection ip:467400 sp:7fff428039d0 error:0 in python2.6[400000+21a000]
Apr 22 00:04:49 archimedes kernel: [280980.941936] aptd[14133] general protection ip:4d4120 sp:7fffcd5bb1f0 error:0 in python2.6[400000+21a000]
Apr 22 00:27:50 archimedes kernel: [282361.150776] aptd[14177] general protection ip:467400 sp:7fff48e4d660 error:0 in python2.6[400000+21a000]
```One more piece of information: I have two harddisks and run several partitions in a RAID 1.

Any hints are highly appreciated. My Ubuntu Maverick installation is pretty fresh (2 weeks) but was unfortunately very unstable from the first day...

Cheers,
Andy

---

### Post by Sirkyuubi on 2011-04-25
From what I see in your error log it looks like your system is detecting the flash drive as scsi. Also you have 2 python errors. Error 0 and 4. Sorry I can't help you any further, but look up those python errors.

---

### Post by KegHead on 2011-04-25
Hi!

Just curious about the last time you updated you kernel?

KegHead

---

### Post by Archie18 on 2011-04-25
> **KegHead said:**
> Just curious about the last time you updated you kernel?

My kernel version is: Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011

That should be the latest from the official repositories. sudo apt-get update doesn't do any updates. The USB problem appeared 3 days after the last kernel update.

Are you suggesting it could be a kernel issue? 

Cheers,
Andy

---

### Post by KegHead on 2011-04-25
Hmm,

Let's try;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

advise.

KegHead

---

### Post by Archie18 on 2011-04-25
Done.

Only sudo apt-get install linux-image -f had work to do.

Andy

---

### Post by niallp on 2011-04-27
> **Archie18 said:**
> My kernel version is: Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011

That should be the latest from the official repositories. sudo apt-get update doesn't do any updates. The USB problem appeared 3 days after the last kernel update.

Are you suggesting it could be a kernel issue? 

Cheers,
Andy

I've recently noticed problems with USB on my system (lots of device waiting on external harddrive, failure to recognize wwan modem consistently), nothing definitive yet but seems better when reverting back to 2.6.35-27-generic.

... Niall

---

### Post by KegHead on 2011-04-27
Hi!

If you had a problem w/apt-get

Try;

sudo apt-get update

sudo aptitude install linux-image -f

KegHead

---

### Post by Archie18 on 2011-06-13
My overall instable system was due to a defective RAM module.
After switching the broken module all is fine.

Cheers!

---

### Post by trellis2 on 2011-09-23
How do you know if a ram module is defective???

---

### Post by Archie18 on 2011-09-23
Reboot and select Memtest86 from the Linux boot manager and let it check your memory over night.

Best,
Andreas

---

