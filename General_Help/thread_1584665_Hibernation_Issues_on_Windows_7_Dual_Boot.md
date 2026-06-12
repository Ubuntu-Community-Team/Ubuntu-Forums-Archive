---
title: "Hibernation Issues on Windows 7 Dual Boot"
date: 2010-09-29
forum: General Help
---

### Post by Hack.The.Pow. on 2010-09-29
Hello All!

I have been having problems hibernating my windows 7 partition recently.  It happened approximately right after I set up the dual boot.   

I have found other topics where it says to make sure that the windows 7 partition is marked as the active partition.  I have since done so and it has not changed anything.  I did it with Partition Magic on Windows.  I did find it suspicious though that my Dell Recovery partition is labeled as boot while the Windows one is marked as Active and System.  

However when I looked at it using disk utility in Ubuntu the windows 7 partition is marked as Bootable while the recovery partition is not.

Hibernation works on Ubuntu with a couple error messages while shutting down and some weird screen issues while booting up.  But it ends up working decently.

I was wondering if anybody would be able to help me with this.  Thanks!

P.S.  Under Disk Utility the Ubuntu Partition is not marked as Bootable.  Should it be?

---

### Post by Mark Phelps on 2010-09-29
If you're having hibernation problems with Win7, this is not really the right place to go.  Yeah, a lot of use DO use Win7, but the real Win7 experts are at the Win7 forum: sevenforums.com.  You should check there for Win7 help.

IF you're having problems with Ubuntu hibernation, then you ARE in the right place ... but sorry, I can't personally help because I've NEVER got hibernation to work on any of my Ubuntu installations.

---

### Post by Hack.The.Pow. on 2010-09-29
thanks for the reply.  I just thought it would help that people here are probably more knowledgeable with dual booting machines then anybody on sevenforums.

as far as Ubuntu hibernation it seems like something is wrong with it but it still sorta works so I'm not complaining too much.

---

### Post by nickd on 2010-10-28
I disagree with Mark.  This is something that Ubuntu appears to do to a Windows installation.

The response from many Windows "experts" is to restore the MBR and thus lose access to Linux.

I can make this work by putting ubuntu 10.10 and bootloader onto a different disk and selecting that disk from the bios at boot time.

Attempting to install the bootloader onto my windows disk kills the hibernate functionality.

I'm running an up-to-date Win 7 Pro on a Thinkpad X201s, alongside 10.10.

All wake-on-LAN type stuff disabled.

I suspect that this might be connected with the Lenovo hidden recovery partitions, but there's no likelihood of me getting support from them on this issue.

It's a double-pain, as I like to use hibernate to flip between Windows and Linux, so that I return to each system in the state that I left them. 

I understand that this problem is hardly going to keep Ubuntu devs awake at night, but if someone with a bit of time and insight could take a look at this then there would be at least two very happy people out there.

---

### Post by Hack.The.Pow. on 2010-10-29
> **nickd said:**
> I disagree with Mark.  This is something that Ubuntu appears to do to a Windows installation.

The response from many Windows "experts" is to restore the MBR and thus lose access to Linux.

I can make this work by putting ubuntu 10.10 and bootloader onto a different disk and selecting that disk from the bios at boot time.

Attempting to install the bootloader onto my windows disk kills the hibernate functionality.

I'm running an up-to-date Win 7 Pro on a Thinkpad X201s, alongside 10.10.

All wake-on-LAN type stuff disabled.

I suspect that this might be connected with the Lenovo hidden recovery partitions, but there's no likelihood of me getting support from them on this issue.

It's a double-pain, as I like to use hibernate to flip between Windows and Linux, so that I return to each system in the state that I left them. 

I understand that this problem is hardly going to keep Ubuntu devs awake at night, but if someone with a bit of time and insight could take a look at this then there would be at least two very happy people out there.

thanks for the reply nickd.

after much research on the subject I came to the conclusion that when setting up the dual boot I managed the partitions incorrectly.  I did not put ubuntu on the first(leftmost) partition on the drive and thus the bootloader might be causing some problems.

I figure having two hds would make this a ton easier but unfortunately I do not have them. 

In the end I decided that since I rarely use windows anymore hibernation for that is not completely neccessary.  I did not feel like going through the hassle of messing around with my partitions just to get rid of this problem and maybe having to reinstall os's just to do this. It simply was not worth the effort.

---

### Post by jasker on 2010-11-29
This is nothing that Ubuntu "does" to the partition, it's a result of Windows' crappy BCD bootloader.

See my post here:
[http://ubuntuforums.org/showthread.php?p=10179205#post10179205](http://ubuntuforums.org/showthread.php?p=10179205#post10179205)

---

### Post by Hack.The.Pow. on 2010-11-30
Yeah I just found it strange that I worked once before and now it doesn't work.  O well

---

