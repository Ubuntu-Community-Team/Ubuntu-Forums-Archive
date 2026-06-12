---
title: "Triple boot (win7, Ubuntu and Mint) failed"
date: 2012-07-28
forum: General Help
---

### Post by GiftedIdiot on 2012-07-28
After already having a dual boot (win7 and Ubuntu) I wanted to add Mint. During installation from flash, the install had an error while configuring the HDD partition and apparently deleted a partition and GRUB. I downloaded "repair-boot" and let it run. Now GRUB doesn't even show. The comp boots only into win7. No GRUB at all. Here's the fix/pasted file  [http://paste.ubuntu.com/1115527/](http://paste.ubuntu.com/1115527/).  Did I wipe my Ubuntu distro? Is it still there?  I would still like to do the triple boot. Is there help?:confused:

---

### Post by oldfred on 2012-07-28
You converted a large partition sda5 to swap and the sda6 swap seems to have some issue.

If sda5 was your install then you need to change it back from swap. But many liveCDs including Ubuntu mount swap to speed of the CD and may write data into it. If you really have data then that gets overwritten by the swap process.

I think gparteded liveCD does not auto mount swap, or you can check on others. You then may want to use testdisk to see if it can recover your data.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by charliebp on 2012-07-28
> **GiftedIdiot said:**
> After already having a dual boot (win7 and Ubuntu) I wanted to add Mint. During installation from flash, the install had an error while configuring the HDD partition and apparently deleted a partition and GRUB. I downloaded "repair-boot" and let it run. Now GRUB doesn't even show. The comp boots only into win7. No GRUB at all. Here's the fix/pasted file  [http://paste.ubuntu.com/1115527/](http://paste.ubuntu.com/1115527/).  Did I wipe my Ubuntu distro? Is it still there?  I would still like to do the triple boot. Is there help?:confused:

I had a similer problem with a xp/ubuntu/mint triple install which gummed up, I used the usb key with mint on it to boot from usb and check the partitions and they were OK so I had another go at installing mint and it reinstalled grub at the same time but when it loaded xp did not show up on the options menu but running update-grub from ubuntu terminal, xp turned up.  Not sure if this helps but running from usb/cd may help get to your ubuntu data to make sure it's ok.
Good Luck

---

