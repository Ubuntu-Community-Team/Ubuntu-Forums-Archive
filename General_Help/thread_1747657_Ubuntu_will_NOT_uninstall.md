---
title: "Ubuntu will NOT uninstall"
date: 2011-05-02
forum: General Help
---

### Post by Rand alThor on 2011-05-02
Hi guys.

I'll give you a quick run-down on the issues I am having.

I am running Win 7 Home Edition on a Toshiba Satellite Pro Laptop (2GB RAM, 2.3GHz processor, 250GB HDD). I decided to install Ubuntu last year on my laptop and dual boot it alongside Windows. That worked well for about 3 months and then I decided to reformat my laptop (specifically the Windows OS component). After I did that I realised I hadn't been using Ubuntu and decided to get rid of it. I used the uninstall option in Ubuntu and it told me it successfully removed Ubuntu from my laptop...

I then restarted as prompted and found that in the boot options mention Ubuntu was still there. I logged into Windows and using the partition manager attempted to delete the whole partition and put it back in the original Windows partition. That went well until I rebooted and saw Ubuntu was still present (just with no space allocated on my HDD). Just so you are aware, I can log into Ubuntu and use it even though there is no space allocated on the HDD.

I then decided to try a Ubuntu USB drive. That didn't work as it wouldn't detect the Ubuntu installation present on my laptop. I then tried the Live Parted CD option, and things got a little messy. It resized the partition, "deleted" Ubuntu and then resized the partition for Windows. However, it changed by Boot Record and wouldn't let me boot into Windows. Following the instructions in an earlier topic in this forum, I used the command terminal in Ubuntu and the Windows 7 Repair disc to fix my Boot Record.

So at the end of this process I have Windows 7 Home Edition still working fine with the whole HDD dedicated to it, and Ubuntu with no space allocated yet still present on my laptop and able to be used if I log in.

I thought I should come here and see if I can get some advice on how to proceed regarding the removal of Ubuntu as I don't want to corrupt my Windows OS and certainly don't want to damage the HDD in my laptop.

Any comments/suggestions would be greatly appreciated. :D

---

### Post by wojox on 2011-05-02
You just have grub still installed in your mbr. Windows 7 should have fixed that. I've done it with Vista. Microsoft.com may have an answer for restoring with Windows 7.

---

