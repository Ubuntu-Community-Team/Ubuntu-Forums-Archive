---
title: "Live USB 11.04 Ubuntu won't boot!"
date: 2011-06-28
forum: General Help
---

### Post by Perpetual_Bliss on 2011-06-28
A little history of my computer:

I'm currently experiencing HDD problems with my Acer Netbook. I can still enter BIOS, but when I turn the netbook on, it gives me the following message:
[B]Pri Master Hard Disk: S.M.A.R.T. status bad, backup and replace. 
Press F1 to resume.[/B]

When I press F1, it tells me: 
**Error loading operating system.**

So, I decided to load up my live USB of 11.04 (which works fine on my other laptop), and it didn't work - it kept giving me error messages, and then when the error count ran out (I think), it went to the ubuntu logo page and didn't change for 20mins, at which point I forced shutdown.

Does anyone know why this is happening? Is this failure to load Live USB due to my computer hardware problems?

Thanks in advance!

---

### Post by Ozymandias_117 on 2011-06-28
Assuming your hard drive is the only hardware problem, they shouldn't be related.

I believe pressing esc during that logo screen should let you get a verbose boot, which might tell you what it's getting hung on.

---

### Post by varunendra on 2011-06-28
> **Ozymandias_117 said:**
> Assuming your hard drive is the only hardware problem, they shouldn't be related..
I feel otherwise. I have personally experienced more than once all kind of booting attempts getting failed or painfully delayed if there is a failing hard-drive connected. I don't have any accurate idea about the reason, but have a theory of my own which may or may not be correct. It goes like this-

"While booting, all connected devices are scanned to detect their type/configuration etc. Hard drives are also scanned and at least their MBR is read to get the partition info. Now if a drive is failing, the computer will detect a hard drive connected, but will have difficulty reading its partition info. Hence the error messages and possible freeze-ups."

So if my guess is correct, then pulling out only the hard drive should make the usb drive boot again without complains.

@Perpetual_Bliss,
If you have some important data on that hard drive, I'd suggest not to use it until getting a backup arrangement ready. If you think it (hard drive) is completely dead, you may wish to give the FREEZER TRICK a try (see [here]("http://lifehacker.com/5515337/save-a-failed-hard-drive-in-your-freezer-redux") and [here]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html")).

Also, it may help to know that if it is a SATA drive, you may plug it in while the laptop is running (just like USB drives)! SATA drives are by default plug-n-play type. Just make sure its power connector pins are NOT symmetrically laid out (the ground prints are longer so they get connected first).

---

### Post by Perpetual_Bliss on 2011-06-28
^ Thanks for your advice. I tried that and here's what I caught as errors (I tried to get it all down best as I could because it kept moving fast):

> 
worker [76] unexpectedly returned with status 0x0100
worker [76] failed while handling '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda1'
worker [77] unexpectedly returned with status 0x0100
worker [77] failed while handling '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda/sda2'

Auto rellocate failed
exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
irq_stat 0x40000008
media error

failed command: READ FPDMA QUEDED
status: { DRDY ERR }
error: { UNC }
configured for UDMA/133
EH complete

The last two paragraphs of errors kept repeating over and over again. Sda1 and sda2 are partitions on my hard drive that I can no longer access.

Can someone please help me out with this? I need to get this done by the end of the week, so unfortunately I'm on a very restricted timeline. Thank you.

---

### Post by seawolf167 on 2011-06-28
I'd try re-downloading the LTS cd, [MD5SUMing ]("https://help.ubuntu.com/community/HowToMD5SUM")the  download, then burning it on your slowest supported rate and try  booting off it again. Also ensure that you have your drive mode  configurations set properly in BIOS (SATA / AHCI / IDE).

That said, I have a WD VelicoRapter drive that spits out the errors you are getting  over and over again when trying to image the drive with Clonezilla  (both builds)
 
 > failed command: READ FPDMA QUEDED
  status: { DRDY ERR }
  error: { UNC }
  configured for UDMA/133
 
 The WD tools show the drive is fine, S.M.A.R.T. status is ok, and all  drive checks pass with flying colors so I know in that instance it is a  kernel issue - if I can find the article again I'll post it (one of the  devs from the mailing list said it was a known issue but of low  importance).

---

