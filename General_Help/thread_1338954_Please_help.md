---
title: "Please help"
date: 2009-11-27
forum: General Help
---

### Post by seaofdreams on 2009-11-27
I'm sorry if this has been bought up in a previous thread but I'm extremely new to Ubuntu and not great at all with the terminology so you'll have to bear with me and put everything in the simplest terms possible, haha.
I have Windows Vista and Ubuntu Karmic on a partitioned Presario CQ60.
I just downloaded and installed some updates and ever since that, GRUB lists double of everything (2 Ubuntus, 2 Windows Vista, 2 Windows Vista Recovery mode etc.) and won't boot into anything except for only one of the Ubuntus. I don't have a Windows Vista disk so it's not possible for me to wipe everything and reinstall. I had wanted to remove Ubuntu and restore Vista but I can't boot into Windows. When I try, it asks if I want to repair the startup so I do that but it still doesn't want to boot, it just stays on the loading screen.
Help please.

---

### Post by plucky on 2009-11-27
> I don't have a Windows Vista disk so it's not possible for me to wipe everything and reinstall. I had wanted to remove Ubuntu and restore Vista but I can't boot into Windows.

1) If you have a recovery partition,I recommend that you make a copy onto DVD before you do anything else.
2) Backup your files just in case something un-toward happens.
3) Checkout this link  [Recovering Vista Bootloader](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Never tried it, so cannot vouch for it.

Good Luck

p.s If your hard drive crashed,how would you recover Vista?

---

### Post by StuartN on 2009-11-27
> **seaofdreams said:**
> I just downloaded and installed some updates and ever since that, GRUB lists double of everything (2 Ubuntus, 2 Windows Vista, 2 Windows Vista Recovery mode etc.)

It does not explain it all, but when you download a new kernel, both the new kernel and old kernel are listed in Grub. You can edit the file /boot/grub/menu.lst to delete the older entries once you are satisfied that the new kernel works.

If a new kernel is the reason for the doubling-up then you would have two options with titles like this:

```
title		Ubuntu 8.10, kernel 2.6.27-15-generic
...
title		Ubuntu 8.10, kernel 2.6.27-14-generic
```

But that would only partially explain it.

---

### Post by HereInOz on 2009-11-27
If your Vista install is completely lost, there will be some way of booting the machine and running the Recovery to Factory from the hard disk. You may have to check your manual for what keys to press at boot.

Compaqs always have a recovery partition, which you can use to recover from a borked system by recovering to out of box situation.

You will lose all your data, but then you have backups of that, don't you?

Might be the easiest way.

---

### Post by raghuveerkr on 2009-11-30
Hi,
I have similar problem.
System is Dell inspiron 1525 that came pre-installed with Windows vista home premium.
I installed Karmic the day it was released and I used to dual boot without any problem so far. 
Yesterday onwards I am not able to boot vista. Even with startup recover option. It doesnt move from the "Microsoft corporation" screen even after hours at that stage.
I tried hitting F8 at startup (for system recovery to factory image), even that doesnt move beyond the same screen.
I have not changed anything in grub/boot settings
I have back up of all files. Also I can access all files on C: from ubuntu.
please help
thanks
raghu

---

### Post by StuartN on 2009-11-30
> **raghuveerkr said:**
> It doesnt move from the "Microsoft corporation" screen even after hours at that stage....
Also I can access all files on C: from ubuntu.

This implies a) your Windows partition is selected by Grub (otherwise the Microsoft splashcreen would not display) and b) the partition is probably recoverable.

Try booting to a command line and running **CHKDSK.EXE /f** to request a disk repair at next boot. I had a glitch with booting Vista stuck at the splashscreen that fixed just by running **BCDEDIT.EXE** to rebuild the Vista boot list.

You can get a Vista boot recovery CD from [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) if you do not have the Windows DVD and can not access your recovery partition.

---

### Post by raghuveerkr on 2009-12-01
Serendipity: I had kubuntu live cd in the drive and powered up my system selecting vista (start windows normally) and it booted fine!!
now I am scared to shut it down!
I like Ubuntu and all, but looks like I need more time before I migrate for good. So I am thinking I will uninstall Ubuntu/Wubi to save my vista.
By the way, I had to use wubi because the guided install option was not available for partitioning (only option was to erase the entire hd).
thanks for all of your help
best
raghu

---

