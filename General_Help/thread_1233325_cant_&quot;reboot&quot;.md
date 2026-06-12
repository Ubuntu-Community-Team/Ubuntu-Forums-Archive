---
title: "cant &quot;reboot&quot;"
date: 2009-08-06
forum: General Help
---

### Post by Repus on 2009-08-06
New, clean, install of 9.04 (previously 8.04) everything works fine minus reboot. Whenever I choose to reboot the system it will hang indefinitely. The hang takes place just after identifying the hard drives and prior to listing the IRQ assignments (before grub). The system will boot without issues from a cold boot.

I don't even know where to begin looking for the problem on this one. google and these forums provide an abundance of hits on subjects that use similar key words but are simply not this problem.

Any help would be appreciated.

---

### Post by warp99 on 2009-08-06
What is the make/model of the computer, or motherboard if it's home built? I have this problem on one HP laptop (Ubuntu's not installed), but it will hang if I reboot the system via a USB pendrive.

---

### Post by nikhilbhardwaj on 2009-08-06
sudo reboot -f
will reboot forcefully
but you many not want that

---

### Post by Repus on 2009-08-06
> **warp99 said:**
> What is the make/model of the computer, or motherboard if it's home built? I have this problem on one HP laptop (Ubuntu's not installed), but it will hang if I reboot the system via a USB pendrive.

Motherboard is gigabyte ga-p35-ds3l rev2. When does your reboot hang?

nikhilbhardwaj:
I dont think that is what i need but ill try it. the reboot process seems to shutdown well enough its the starting back up that hits a snag

---

### Post by warp99 on 2009-08-06
Well I did a quick search and others are having a similar issue, even with Windows so I don't believe this is Linux specific. This thread talks about issues with that board and rebooting:

[http://www.tomshardware.com/forum/246575-30-ds3l-restart-problem](http://www.tomshardware.com/forum/246575-30-ds3l-restart-problem)

Even one poster stated this was a Vista problem with hotfixes KB930261 and KB929777 doing nothing. I would go through your BIOS settings, especially the hardrive settings, and make some changes to see if this helps. 

My reboot will hang just at the system boots. I believe this is because the system doesn't see the USB drive on reboot, so it really has nothing to do with Ubuntu.

---

### Post by Repus on 2009-08-14
> **warp99 said:**
> Well I did a quick search and others are having a similar issue, even with Windows so I don't believe this is Linux specific. This thread talks about issues with that board and rebooting:

[http://www.tomshardware.com/forum/246575-30-ds3l-restart-problem](http://www.tomshardware.com/forum/246575-30-ds3l-restart-problem)

Even one poster stated this was a Vista problem with hotfixes KB930261 and KB929777 doing nothing. I would go through your BIOS settings, especially the hardrive settings, and make some changes to see if this helps. 

My reboot will hang just at the system boots. I believe this is because the system doesn't see the USB drive on reboot, so it really has nothing to do with Ubuntu.

My system is dual boot vista / ubuntu. 
Vista is on 1 hdd and Ubuntu is spread across 3. Vista reboots just fine Ubuntu doesn't. 
I am beginning to think its grub related. I had this system dual booting xp / ubuntu for years then Vista / Ubuntu with no problems. It wasnt until Jaunty that this issue showed up. I seem to recall Jaunty is using a new Grub. Any ideas how I could debug the boot if it never completes? 

Thanks for any help from anyone.

---

### Post by Repus on 2009-08-17
Monday bump and more info.

I've found that the system will reboot fine from Ubuntu if USB support is turned off. (unfortunately I require USB support during boot)

so in summary..
[LIST]
[*]Ubuntu Jaunty boots just fine.
[*]System hangs on reboot when the reboot is initiated from Ubuntu Jaunty. Hang occurs during post after pci and just prior to listing irq assignments
[*]Same system Vista boots and reboots with no issues
[*]Same system Ubuntu 8.04 boots and reboots with no issues
[*]Ubuntu Jaunty with bios USB support turned off boots and reboots no issues
[/LIST]

Anyone have an idea how to fix this?

---

