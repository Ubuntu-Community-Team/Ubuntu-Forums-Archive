---
title: "GRUB booting problem!"
date: 2010-01-25
forum: General Help
---

### Post by CMR21 on 2010-01-25
Hi, I'm extremely new to Ubuntu. I've been dual-booting Ubuntu 9.10 with Windows XP. I was having a lot of problems with 9.10 since I first installed it (notably no sound), and finally decided, after much messing around with installing different programs, that it might be a better idea just to delete my Ubuntu partition and restart from scratch (a bad idea in retrospect). When I deleted the Ubuntu partition (I thought I was careful not to delete the Windows one), and next restarted my computer, I was no longer able to boot up under Windows or Ubuntu (or anything else for that matter). I only received the error message: GRUB loading. error: no such partition grub rescue>

I can't do anything at this point--no matter what I type, I get the message "Unknown command." The only exception to this that I have found so far is that if I type "ls," I get the message: (hd0) (hd0,1) (fd0)

Can someone please help me? I have absolutely no clue what to do at this point. I do not have a CD to reinstall XP (though I do have the Ubuntu 9.10 installation CD, if that makes any difference...). 

Any help you have to offer would be EXTREMELY appreciated, and please, I beg you, be as specific and step-by-step as possible. I'm so unfortunately new to this. :(

Thank you!

---

### Post by L4U on 2010-01-25
To get you computer back running, put your livecd in and install Ubuntu again over the same Linux partition you had created.

There is a specific procedure to uninstall a Linux distro from a dual boot, but I'm not sure how.  I'm sure there's threads here discussing the procedure.

---

### Post by cenzorrll on 2010-01-25
check this page for more information about grub2:

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

i don't know if this will really help, but if it's only grub that's messed up it should (the part where you said you "thought you were careful not to delete the windows parition" scares me a little) The livecd will be able to tell you if its there.  

i definitely prefer formatting through gparted whenever i have a partition i want to keep safe, rather than the default install partitioner. mostly because i'm a very visual person and seeing a picture representing the partitions really helps to keep what's what in line.

---

### Post by Jackzor on 2010-01-25
All you need to do is fix the master boot record for windows.

You deleted grub and now you need to replace it. Google it. my girlfriend is killing me.

---

### Post by cenzorrll on 2010-01-25
> **Jackzor said:**
> All you need to do is fix the master boot record for windows.

You deleted grub and now you need to replace it. Google it. my girlfriend is killing me.

i doubt it, if grub was deleted you wouldn't see the word GRUB when you boot, black screen and no bootable media shows up when you delete grub

---

### Post by Jackzor on 2010-01-25
> **cenzorrll said:**
> i doubt it, if grub was deleted you wouldn't see the word GRUB when you boot, black screen and no bootable media shows up when you delete grub

Grub is installed in two places. Most of it being on your linux partition. He deleted that part of grub. And only that part. EITHER way he will need to fix the master boot record.

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If for some reason that doesn't solve it then post back. Either way we fixed one problem. If all you have is Windows XP then there is no reason to have grub. So you HAVE to have the windows MBR.

Grub overwrites the windows MBR making it impossible to boot to windows without ubuntu installed. (in this case)

---

### Post by CMR21 on 2010-01-25
Thanks for your help, everyone! I got it working again.

---

