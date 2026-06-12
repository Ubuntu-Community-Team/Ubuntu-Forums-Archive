---
title: "initramfs cannot boot"
date: 2010-03-21
forum: General Help
---

### Post by lightspd on 2010-03-21
Hello All,

     I'm hoping someone can help me with this problem. I recently setup an external dvd burner on my eee netbook.  I was having problems with burn speed, so following several suggestions on other forums and this one, I added "pata_ali atapi_dma=1" to "/etc/initramfs-tools/modules" and ran update-initramfs -u.  No errors reported.

     I rebooted the laptop and now when I try to boot, I get dropped to initramfs terminal with the error of not being able to find root device UUID....  when I check that UUID is not in /dev/disk/by-uuid for that UUID it is indeed not there, but there seems to be a new UUID for /dev/sda5.

     I tried to set root=/dev/sda5 in grub, as suggested in some forums through google search, but I see the splash screen and then nothing.  It just sits there and never gives any kind of error.

    I'm downloading a live cd now, so I can boot up and have some tools available.  Ideally I would just undo the changes to initramfs, update, and hope it works, but wanted to get some advice first as there might be a simple solution to my problem.

    I have tried selecting older kernals, but same issue.

Cheers.

---

### Post by lightspd on 2010-03-21
Ok. Update.  I got a boot cd and tried to just fix grub and no go. I did find out that sda5 is the swap and sda6 is ext3. So I edited boot options and specified the 6.  Got further, booted but gave mount error and it put me terminal mode.  Ran fsck and got unable to resolve uuid.  Checked fstab and it shows correct uuid for both sda5 and 6, but /dev/disk/by-uuid doesn't show sda6.  I would paste an example but typing from cell phone.

---

