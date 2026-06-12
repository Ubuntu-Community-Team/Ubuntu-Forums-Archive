---
title: "Applications becoming unresponsive, software raid too slow?"
date: 2009-11-16
forum: General Help
---

### Post by raix on 2009-11-16
Hi,

a month ago I freshly installed Ubuntu 9.04 on my new PC.
It's a Core2Duo E6300 with 8GB RAM. One 160GB HDD as / and a software-raid 1 of two 1.5TB HDD as /home.

/ and /home are encrypted with luks(cryptsetup).

Now I'm getting strange behavior:

Running applications are becoming unresponsive (windows are grey) but the processes keep running. And eventual the windows are responding again.
It seems to occur randomly. I can't find a pattern in this.

What I've noticed so far:

No entries in logfiles syslog, kernel, messages
No error-messages with mdadm --detail
No errors with smartctl

But:
When the applications are unresponsive, top shows that %wa (io wait?) is getting up to 90%. The other stats (cpu, ram) are normal.
Iotop shows that virtually no data is written at that time. 
Right now I'm making a backup of /home to an external USB-Drive. The copy-command started around 30MB/s and is now down to 3-4MB/s.

Is there any way I can determine the cause of the problem and fix it?

---

### Post by fluffman86 on 2009-11-16
My specs are nowhere near as nice as yours, so this may be different, but if I have desktop effects enabled my windows will freeze up sometimes.  Try going to System > Preferences > Appearance, then the Viusal Effects tab at the top, and select none.

---

### Post by raix on 2009-11-17
No, the applications are freezing without effects, too.

---

### Post by patate91 on 2009-11-17
I have the same issue.( same behavior)  I'm on firefox or evolution ( I'm having this issue with other apps as well ) and the current page is becoming grey and unresponsive. I still can move the cursor. I can open the other windows in the task bar, but I can't do anything esle.   The ''freeze'' has a duration of about 45 seconds, sometime more.    My config :   Karmic Koala *fresh install - Intel core 2 duo 2,8 - 6 Go ram - ATI mobility Radeon HD 3670

---

### Post by raix on 2009-11-17
I've noticed that the load goes up to 5 and more.
But I can't find a process that generates so much load.

---

### Post by patate91 on 2009-11-18
Are you running Evlution? It seems that my gray screens comes from evolution. Since I'm keeping it close I got no more  gray screens. The only one I'm getting is  when I open it to get my emails.

---

### Post by whoop on 2009-11-18
> **patate91 said:**
> Are you running Evlution? It seems that my gray screens comes from evolution. Since I'm keeping it close I got no more  gray screens. The only one I'm getting is  when I open it to get my emails.

More interestingly, are you running software raid? I run software raid and I do not experience these problems...

---

### Post by whoop on 2009-11-18
> **raix said:**
> Hi,
Right now I'm making a backup of /home to an external USB-Drive. The copy-command started around 30MB/s and is now down to 3-4MB/s.

Is there any way I can determine the cause of the problem and fix it?

Backing up before experimenting is always wise... I don't think it is due to software raid as I use it myself and have no problems.... It could be that the combination of encryption with software raid is causing it. I don't have my entire home encrypted but I do have an encrypted private folder (no issues with that as well).

You could try (temporarily) disabling software raid and see if you still get the problem. If you still get it, it has nothing to do with software raid, you guessed it.
Maybe this post is usefull:[http://ubuntuforums.org/showthread.php?t=394281](http://ubuntuforums.org/showthread.php?t=394281)

---

### Post by patate91 on 2009-11-18
In my case I'm not running software raid, or encryption app.

---

### Post by blueridgedog on 2009-11-18
Software Raid and disk encryption must really be CPU intensive during heavy disk activity.  I recommend one or the other, but to stack them on top of one another seems to invite system performance issues.

---

### Post by raix on 2009-11-18
I agree that an encrypted software raid is CPU-intensive.
But, the I would expect to see such a process with top, before the system hangs.
And as I said, I build the system about 4 weeks ago. This heavy problems occured just 1 week ago.


So I looked up some more things.

At first the hdd-part of the boot-message:

> 
[    4.850057] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.850069] ata1.01: SATA link down (SStatus 0 SControl 300)
[    4.850233] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.850244] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.872259] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-08, max UDMA7
[    4.872263] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.890451] ata2.00: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    4.890454] ata2.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.890611] ata2.01: ATA-8: WDC WD15EADS-00P8B0, 01.00A01, max UDMA/133
[    4.890614] ata2.01: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.912139] ata1.00: configured for UDMA/133


Is UDMA/133 ok for a SATA-HDD?

And I also activated debugging in /proc/sys/vm/block_dumps. There I found this message occuring multiple times every second:

> 
Nov 18 18:12:53  kernel: [79741.050081] kjournald(1310): WRITE block 1465092672 on dm-3
Nov 18 18:12:53  kernel: [79741.050085] kjournald(1310): WRITE block 1465092680 on dm-3
Nov 18 18:12:53  kernel: [79741.050088] kjournald(1310): WRITE block 1465092688 on dm-3
Nov 18 18:12:53  kernel: [79741.050091] kjournald(1310): WRITE block 1465092696 on dm-3
Nov 18 18:12:53  kernel: [79741.050095] kjournald(1310): WRITE block 1465092704 on dm-3
Nov 18 18:12:55  kernel: [79743.251312] kjournald(1310): WRITE block 1465092712 on dm-3


And I think just before a hiccup occurs this message comes around:

> 
Nov 18 18:13:46  kernel: [79794.471174] gnome-terminal(3435): dirtied inode 1998977 (?) on dm-1
Nov 18 18:13:48  kernel: [79796.272280] firefox(3153): dirtied inode 75703291 (?) on dm-3


The first one is from the ext3 journaling system, but I don't know what the second one means.

I'm trying now to mount the disks with "noatime" as ext2 to stop the journaling-process from accessing every second.

---

### Post by blueridgedog on 2009-11-18
I have the same effect when burning a DVD (various applications).  Top shows no real load (I have a quad core cpu), but Firefox will gray out and be non-responsive for chunks of time.  I don't burn enough disks to need trace it, but I bet the cause is similar.

---

### Post by raix on 2009-11-20
So, I switched back to 9.04. I did a clean install, reformated the raid-array, this time unencrypted, moved my /home back onto it.

And the result is:
Still hiccups with a high %wa. Now I really don't know what to try next.

Perhaps I should give debian a try ;)

---

### Post by whoop on 2009-11-20
> **raix said:**
> So, I switched back to 9.04. I did a clean install, reformated the raid-array, this time unencrypted, moved my /home back onto it.

And the result is:
Still hiccups with a high %wa. Now I really don't know what to try next.

Perhaps I should give debian a try ;)

Well, you didn't try what I suggested (try disabling raid temporarily). As I said I run raid 1 for my home, I don't experience hiccups, not even with my encrypted private folder (I do see significant cpu usage when writing to private, but no hiccups).
It's not entirely impossible that it has nothing to do with raid and/or encryption.

---

### Post by raix on 2009-11-21
I didn't disable raid because I'm sure that it's the source of the problems.

Right now I'm downloading the Debian 5 DVD Image. 

At first I tried to save it on /home (unencrypted soft-raid 1) but after ~400MB, io-wait went up, firefox freezed and the transfer died.

Now I'm saving it to /tmp (different sata-hdd, no raid) it goes down without problems. CPU is 90% idle and %wa is about 2%.

So, any ideas what could be wrong with the raid setup?

---

### Post by patate91 on 2009-11-24
I think I solved my freezes problem. My Ubuntu was installed on a 500 Go hard drive. Firts 350 Go (ntfs) was for Windows. So ubuntu was installed at the end of the HD. And when I was having the freezes my HD was running as hell. Since I reinstalled ubuntu without windows I got no more freezes.

---

