---
title: "Slow boot and possible hardware problem, Ubuntu 9.04"
date: 2009-08-25
forum: General Help
---

### Post by billjoie on 2009-08-25
Hi.  I have been using Ubuntu 9.04 since it's release to great satisfaction on my Acer Aspire laptop.  Recently, boot time really drastically increased.  Before the log-in screen appears, I now enjoy a totally black screen that seems to last minutes, with my CPU obviously going wild.  I printed dmesg, and it declares a lot of errors I do not understand.  You will find this file in attachment.  

The exception that seems to repeat itself for over 60 seconds is as follows:

[  161.632215] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  161.632227] ata1.00: BMDMA stat 0x65
[  161.632245] ata1.00: cmd c8/00:38:50:a8:03/00:00:00:00:00/e3 tag 0 dma 28672 in
[  161.632250]          res 51/40:38:50:a8:03/00:00:00:00:00/e3 Emask 0x9 (media error)
[  161.632259] ata1.00: status: { DRDY ERR }
[  161.632266] ata1.00: error: { UNC }
[  161.648666] ata1.00: configured for UDMA/100
[  161.664535] ata1.01: configured for UDMA/33
[  161.664561] ata1: EH complete


Thank you very much for your help.

---

### Post by rootless on 2009-08-28
I have almost the exact same problem. My processor shows %100 usage, but only when I startx. When I'm in the CLI, it works fine.

It's a Thinkpad R40.

```
[various changing numbers] ata1.01: status: {DRDY ERR}
[various changing numbers] ata1.01 ERROR: {unc}
[various changing numbers] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[various changing numbers] ata1.01 cmd c8/00:08:5f:99:e5/00:00:00:00:00/f0 tag 0 dma 4069 in

```

I will let you know if I find a solution to this. Nobody here has tried to tackle it though. I think it's a pretty obscure error.

---

### Post by billjoie on 2009-08-28
Thank you rootless for your reply.  I *sort of* fixed the problem.  Boot is not slow anymore, though error messages in dmesg are just as weird as ever.  From what I was able to google, this sort of error seems to be associated with hard-drive corruption.  I first made fresh back-ups, then used the following tutorials to locate the corrupted blocks and corrupted files.

[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/]("http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/")
[http://smartmontools.sourceforge.net/badblockhowto.html]("http://smartmontools.sourceforge.net/badblockhowto.html")

I found that the first corrupted block belonged to:
/var/lib/preload/preload.state

I realocated the blocks using dd, as explained in the tutorial.  No improvement.  I then simply deleted the file.  This resulted in a normal boot, with no more lagging time.  I then ran 
e2fsck -fccv /dev/sda6 
from a liveCD, which corrected more bad blocks on the partition.

If anyone really understands what's going on, please make yourself heard.  I still get error messages, and smartctl still says that my harddrive is corrupted.  Is the whole system about to die on me?  Would a fresh reinstall be an option?

---

### Post by Cajhne on 2009-10-13
Hey all. After having the same problem with my EEEPC 901 (spanning multiple versions of Ubuntu), I came across this solution which has worked brilliantly, and frankly quite magically:

sudo apt-get remove --purge hddtemp

I found it on a EEEUbuntu forum, even though I have a standard install of Ubuntu 8.10 (Intrepid), which I luvs muchly, save for 7 minutes of boot-time embarassment, involving the message: ata2.00 status {drdy}

Tip source:

User named Okkie:
------------------------------------
It seems the hddtemp package tries to read some S.M.A.R.T settings from the SSD and fails - slowly.

I solved this problem on my 900 by issuing the following command in a shell:

sudo apt-get remove --purge hddtemp
 
------------------------------------
[http://forum.eeebuntu.org/viewtopic.php?f=28&t=1255](http://forum.eeebuntu.org/viewtopic.php?f=28&t=1255)


This reduced my boot time from 7 minutes to under 30 seconds(!)

Note: I'm not an expert, nor do I know what the consequences of removing hddtemp is (if my laptop catches fire or melts, I'll let you know via my new comp :D)

This error might have something to do with the fact that my primary and secondary HDs are SSDs without a lot of the fancy crap that those archaic disk-spinning mechanisms in non solid-state technology has (maybe including something that returns the temperature of the thing?

Anyhow, this is what worked for me. I'm posting this to all the threads I've visited trying to find this information. It's taken me 5 hours to locate tthe above. Hopefully it will save some one else time! :D

Cheers, mates.
-Caj

---

### Post by Mykef on 2009-10-18
I have an almost identical problem in Ubuntu 8.04.

I do not have a black screen when the problem occurs - but the system hangs for about 10 seconds. I've been using Ubuntu for a long time now without any problems - is this a sign that my hard disk may be about to fail - or do others have similar problems?

[  171.211620] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  171.211632] ata1.00: BMDMA stat 0x65
[  171.211643] ata1.00: cmd c8/00:f8:6f:f9:29/00:00:00:00:00/e2 tag 0 dma 126976 in
[  171.211645]          res 51/40:f8:28:fa:29/00:00:00:00:00/e2 Emask 0x9 (media error)
[  171.211650] ata1.00: status: { DRDY ERR }
[  171.211653] ata1.00: error: { UNC }
[  171.235257] ata1.00: configured for UDMA/100
[  171.242363] ata1.01: configured for UDMA/100
[  171.242383] ata1: EH complete

---

