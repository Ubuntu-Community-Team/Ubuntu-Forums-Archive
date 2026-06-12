---
title: "Regular system hard lock-ups"
date: 2009-10-04
forum: General Help
---

### Post by Thomas Kenobi on 2009-10-04
I'm experiencing constant system hard lock ups (no response to Ctrl-Alt-F# / Ctrl-Alt-Backspace / RSEINUB), that seem to be happening almost at random with no discernible pattern. Neither the HDDs nor the CPU are under any particular load, when the problem occurs and I can find nothing relevant at the logs. The last attempt  to solve this issue was to install the latest nVidia drivers for my 8800 GTS and that appeared to have solved the problem for a couple of days. However, today, I got 3 consecutive lock-ups, one out of the blue, with no particular load on the CPU or HDDs, the second about a minute after boot and the third right after the login screen on the second reboot, which caused the intro music to get stuck on a loop.


 I have been experiencing some unidentified hardware problems lately, which resulted in a perfectly fine HDD intermittently not being recognised by the BIOS. This has caused 1-2 lockups in Vista as well, however nothing in the same magnitude as this. The HDD in question has been removed from the system and I'm not entirely convinced that the problems are related, however due to the lack of data, I can really discount no possibilities.


 Also I have run memtest for about an hour with no errors and mprime (small FFTs) for almost 4 hours, to verify CPU stability, again with no errors.
 Lastly, there could be some correlation between the problem and the BIOS suspend mode. I changed it from S1 to S3 suspend earlier this day, but I never set the system to sleep. Vista has been experiencing problems with S3 so it could be something BIOS or hardware related. In any case I think this correlation is tentative at best, I'm only mentioning it for completeness.


 I could really appreciate some help, as I'm at a loss about what else to do to trace this problem to its root.
If you need any particular logs or want me to run some test, let me know and I'll try to post the results as soon as possible.


Specs:
Linux home-pc01-main 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
Ubuntu 9.04 "jaunty"
 Asus P5B Deluxe M/B
Core 2 Duo E6600
Geforce 8800 GTS
OCZ Platinum DDR2 4GB


Originally posted on the Launchpad Answers section four days ago, but since I got no response I'm posting here as well.

---

### Post by JC Cheloven on 2009-10-04
Hi thomas,

From what you did, you obviously suspect from a hardware problem. I entirely agree with that. As I progressed reading your post, I was thinking "well, the typical ram failure".
But then I read that you alreay did the ram test and passed. So I'm a bit clueless at this point. 

I'd still suspect from a hardware problem. Perhaps related to heating. Does the system locks-up more often when it has been running for long, or after intensive tasks?

---

### Post by Thomas Kenobi on 2009-10-04
I didn't run the RAM test for too long, only for about an hour I think. I'll try to run it again for several hours tomorrow or the day after tomorrow and see what happens.

Now the temperatures are quite normal on both the GPU and the CPU and I can't see a connection between intensive applications and the lock-ups. I've had lock-ups with minimal CPU and HDD activity. And on the other hand, as I said, the system passed a 4 hour mprime stress test without a hitch.

It's quite puzzling really...

---

### Post by Primefalcon on 2009-10-04
> **Thomas Kenobi said:**
> I didn't run the RAM test for too long, only for about an hour I think. I'll try to run it again for several hours tomorrow or the day after tomorrow and see what happens.

Now the temperatures are quite normal on both the GPU and the CPU and I can't see a connection between intensive applications and the lock-ups. I've had lock-ups with minimal CPU and HDD activity. And on the other hand, as I said, the system passed a 4 hour mprime stress test without a hitch.

It's quite puzzling really...
Are you using ext4?

---

### Post by Thomas Kenobi on 2009-10-05
Ok here's an update. I run memtest for about 8 hours tonight and it returned no errors, so the memory is probably fine.
[I]
[COLOR=Black]@Primefalcon: [/COLOR][/I][COLOR=Black]I'm using ext4 on the boot partition Ubuntu is in and NTFS on all the other partitions. Could this be connected to the problem?[URL="http://ubuntuforums.org/member.php?u=543184"]
[/URL][/COLOR]

---

### Post by Primefalcon on 2009-10-05
> **Thomas Kenobi said:**
> Ok here's an update. I run memtest for about 8 hours tonight and it returned no errors, so the memory is probably fine.
[I]
[COLOR=Black]@Primefalcon: [/COLOR][/I][COLOR=Black]I'm using ext4 on the boot partition Ubuntu is in and NTFS on all the other partitions. Could this be connected to the problem?[URL="http://ubuntuforums.org/member.php?u=543184"]
[/URL][/COLOR]
Yes.. if your using 9.04 with ext4 it's not 100% stable as yet.

ext4 is stable as of 9.10 but until Karmic stick with ext3, I had the same issue myself a whle back and ended up having to go back to ext3, that why ext4 was not default as of jaunty, and also why i was able to guess you were using ext4

---

### Post by Thomas Kenobi on 2009-10-05
It's a possibility... I'm not going to be formating the boot partition right now, so I'll have to wait until the 29th to test this.

I'm still not discounting the possibility of hardware problems though. Mainly because of the issues I experienced in Vista. I'll be installing Win7 in a couple of days, so I'll see if any problems pop up there as well.

---

### Post by userid on 2009-10-10
I've been on ubuntu for a couple of releases, and its always been a stable ride; since I installed karmic (clean install with encrypted home) I've been getting LOTS of horrible lockups as described above.. I haven't been able to do much diagnostic work on this as the system logs don't show anything.

---

### Post by Thomas Kenobi on 2009-10-10
> **userid said:**
> I've been on ubuntu for a couple of releases, and its always been a stable ride; since I installed karmic (clean install with encrypted home) I've been getting LOTS of horrible lockups as described above.. I haven't been able to do much diagnostic work on this as the system logs don't show anything.

  Karmic is still in beta. So your lock-ups could be attributed to any number of factors. Perhaps you could rollback to Jaunty and wait untill Karmic is officially released.  Funny thing is... I'm waiting for the release of Karmic to see if that will fix the lock-ups.

> **Thomas Kenobi said:**
> I'll be installing Win7 in a couple of days, so I'll see if any problems pop up there as well.

I finished the installation of Win7 (dual-boot) and so far seems pretty stable with none of the issues I've encountered in Ubuntu. So again no diagnostic data to work with.

---

### Post by userid on 2009-10-14
> **Thomas Kenobi said:**
> Karmic is still in beta. So your lock-ups could be attributed to any number of factors. Perhaps you could rollback to Jaunty and wait untill Karmic is officially released.  Funny thing is... I'm waiting for the release of Karmic to see if that will fix the lock-ups.

Funnily enough, I'm hoping it'll fix itself with every update. It occurs at any stage, with or without usb disks, on dual or single screen, straight after boot or after hours, but *very* frequently.

Sadly I don't have any leads for investigation..

Having said that, the last entry in kernel.log always seems to be:

```
Oct 12 19:13:07 monster kernel: [  934.008179] USB Mass Storage support registered.
Oct 12 19:13:07 monster kernel: [  934.011489] usb-storage: device found at 2
Oct 12 19:13:07 monster kernel: [  934.011493] usb-storage: waiting for device to settle before scanning
Oct 12 19:13:07 monster kernel: [  939.009946] usb-storage: device scan complete
Oct 12 19:13:07 monster kernel: [  939.010553] scsi 2:0:0:0: Direct-Access     Maxtor   Basics Desktop   0122 PQ: 0 ANSI: 4
Oct 12 19:13:07 monster kernel: [  939.011698] sd 2:0:0:0: Attached scsi generic sg2 type 0
```

-> Could be the USB after all?

But sometimes I get this:

```
Oct 12 16:28:02 monster kernel: [  123.525410] Valid eCryptfs headers not found in file header region or xattr region
```

or this:

```
Either the lower file is not in a valid eCryptfs format, or the 
key could not be retrieved. Plaintext passthrough mode is not enabled; 
returning -EIO
```

-> Which may be related to my ecryptfs-encrypted home..

---

### Post by userid on 2009-10-18
Also cf [this thread]("http://ubuntuforums.org/showthread.php?t=1276146")

---

### Post by razorxpress on 2009-11-01
I have a clean installation. But ubuntu locks up quite frequently. Don't know when. But sometimes opening new tab in browser. Sometimes starting a movie. Playing songs in songbird. It might be due to ext4. Since this is a release version. I don't want to reinstall ubuntu by changing the filesystem, because i have so much software already installed. Besides frequent lock up, everthing else is so good.

---

### Post by P4man on 2009-11-01
I dont understand why everyone points to Ext4. Much more likely is an acpi incompatibility. Try booting with noapic and/or nolapic kernel options. See here for a how to:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

(note the permanent fix described lower applies to grub1, not grub2. If adding those options solves the issue post back if you need help fixing it permanently with grub2)

---

### Post by Thomas Kenobi on 2009-11-01
I have installed Karmic and so far there haven't been any hard lock-ups. I'm going to list this as [SOLVED] and I'll reopen, if the problem emerges again.

Thanks for the input everyone.

---

