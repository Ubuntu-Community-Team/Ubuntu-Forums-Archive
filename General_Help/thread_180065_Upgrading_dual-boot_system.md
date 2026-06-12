---
title: "Upgrading dual-boot system"
date: 2006-05-21
forum: General Help
---

### Post by HowardH on 2006-05-21
I am currently running a dual-boot system with Ubuntu and Windows 98se.  Although I am a relative newbie to the Linux world, I greatly enjoy it and spend most of computing time at home in Ubuntu.  The problem is that it has become necessary for me to upgrade to Widows XP and I'm not sure how to approach it.  Can I just boot into Windows and follow the normal upgrade procedure, or will the XP upgrade potentially trash my Linux partition and Grub?  

I have done a search on ubuntuforums and google, but haven't found guidelines for this situation.  Looking for advice before I make the leap!

---

### Post by rich.bradshaw on 2006-05-21
If you upgrade Windows it should be fine, though it will overwrite grub in the MBR, meaning that when you reboot after upgrade it will go straight into windows.

To recover grub, boot from the live-cd and there will prob be a tool on there somewhere (I don't use ubuntu, but the Kanotix live-cd has this feature) to restore grub to the MBR.

I think that it should be rather trivial to get grub back, someone will know!

---

### Post by Fass on 2006-05-21
You will have to tell XP to install to your win98 partition and it shouldn't then touch the ubuntu one, but it will, however trash grub. You'll have to fix it by booting with a liveCD and repairing the MBR.

---

### Post by confused57 on 2006-05-21
Here's a wiki guide for restoring grub:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

or

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

I assume you can probably can just boot up with the WinXP upgrade CD and choose to install on the partition that win98 is located on, then restore Grub to the mbr of Windows.  I've never done it before...

---

### Post by HowardH on 2006-05-21
Thanks.  I'll be taking the plunge this week and post how it went.

---

