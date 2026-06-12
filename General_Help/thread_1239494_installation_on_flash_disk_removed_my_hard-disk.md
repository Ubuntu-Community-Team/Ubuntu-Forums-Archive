---
title: "installation on flash disk removed my hard-disk"
date: 2009-08-13
forum: General Help
---

### Post by tarumar on 2009-08-13
Please, I need urgent help. I have a company notebook - installed win xp. I tried to install ubuntu on a flash disk, so that I can use it for private purposes. But it's a mess now. Without flash disk, on start up, it gives grup error. Also on grub screen I can not see windows system. What can I do?

---

### Post by zkriesse on 2009-08-13
Do you have a windows xp disk?

---

### Post by matthewbpt on 2009-08-13
What you've done it seems is installed the GRUB bootloader to the hard-disk master boot record, and kept the /boot directory in the flash disk. This erased the windows boot loader from the mbr so when you boot up the laptop without the flash disk GRUB get stuck in stage 1 because it's trying to find /boot directory in the flash disk, which isnt installed. What I recomend is you search in Google how to restore the Windows XP bootloader, then when you isntall ubuntu on the memory stick, in the last step theres a button that says 'advanced' (see [http://news.softpedia.com/images/extra/LINUX/large/installinggutsy-large_006.png](http://news.softpedia.com/images/extra/LINUX/large/installinggutsy-large_006.png)). Going into advanced you can choose where the bootloader is installed, make sure you install it on the flash drive and not the internal drive, the internal will probably be listed as sda, while the flash drive is probably sdb.

Here's a google search to get you started on restoring the bootloader [http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=restore+xp+bootloader](http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=restore+xp+bootloader)

---

### Post by Slywire on 2009-08-13
Well, the easiest is to boot from an XP cd and at the first screen, select "Repair using recovery console: or something like that. Select your windows installation and type the command fixmbr. That should restore the normal XP loader

---

### Post by tarumar on 2009-08-13
I understand what I did wrong. I have a windows xp cd but when I boot there, it gives a blue screen and error. I'm googling now xp bootloader.

---

### Post by tarumar on 2009-08-13
> **Slywire said:**
> Well, the easiest is to boot from an XP cd and at the first screen, select "Repair using recovery console: or something like that. Select your windows installation and type the command fixmbr. That should restore the normal XP loader

So I absolutely need a xp cd, right? I have 2, but I can not go to repair screen, it gives a blue screen and error. 
The second one does not even boot. Is there an alternative solution?

---

### Post by michy99 on 2009-08-13
Try this:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by tarumar on 2009-08-13
> **michy99 said:**
> Try this:

[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

I'm trying to find a bootable xp cd. If it doesn't work, I'll try this. Do you think it's safe? I mean, is there a risk to delete my whole disk?

---

### Post by michy99 on 2009-08-13
It shouldn't touch the Windows partition, only the master boot record (MBR).

---

### Post by SPr on 2009-08-13
> **tarumar said:**
> Do you think it's safe? I mean, is there a risk to delete my whole disk?

Only from your company's IT department. They may not like anyone messing with equipment that is their responsibility to maintain. And be prepared to lose all your work.

If you do get the computer to boot into a Windows CD run the command
```

map

```
first to be certain of running fixmbr on the correct drive. (I had my USB HDD plugged into a laptop and ran fixmbr on the Ext. HDD instead of the internal HDD :rolleyes: I even ignored the warning :( Thank God for SysRescueCD.)

---

### Post by tarumar on 2009-08-13
I'm still struggling with xp cd's. I'll never touch the computer again, I only wish to save my work.

---

