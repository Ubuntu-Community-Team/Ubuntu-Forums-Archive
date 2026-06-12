---
title: "Can you fix my grub please."
date: 2011-01-08
forum: General Help
---

### Post by VanJoe on 2011-01-08
If it ain't broke don't fix it. I should have listened. Here's my story. I installed a distribution called backtrack on a small partition beside ubuntu. Apparently Backtrack installs its own version of of grub making backtrack the default OS. No problem I thought, I'll just change the default option. I found /boot/grub/menu.lst It seemed to be the file I wanted so I changed the default, then figured while I was there I would change some other things. I changed the timeout time and then because the names for the the Ubuntu options were alittle funny I changed the titles on them. I think that may have been the problem. I then proceeded to reboot forgetting to run  update-grub. when I try to run ubuntu I get told "file not found" so I boot into backtrack and replace the edited menu.lst with a backed up menu.lst that I had put on a thumb drive. then ran update-grub. when I rebooted I still got nothing for ubuntu. I'm considering just deleting the backtrack partition will that work? Any better Idea's?

---

### Post by dcstar on 2011-01-08
> **VanJoe said:**
> If it ain't broke don't fix it. I should have listened. Here's my story. I installed a distribution called backtrack on a small partition beside ubuntu. Apparently Backtrack installs its own version of of grub making backtrack the default OS. No problem I thought, I'll just change the default option. I found /boot/grub/menu.lst It seemed to be the file I wanted so I changed the default, then figured while I was there I would change some other things. I changed the timeout time and then because the names for the the Ubuntu options were alittle funny I changed the titles on them. I think that may have been the problem. I then proceeded to reboot forgetting to run  update-grub. when I try to run ubuntu I get told "file not found" so I boot into backtrack and replace the edited menu.lst with a backed up menu.lst that I had put on a thumb drive. then ran update-grub. when I rebooted I still got nothing for ubuntu. I'm considering just deleting the backtrack partition will that work? Any better Idea's?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by wojox on 2011-01-08
I would [Reinstall Grub2 from a Live-CD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") and boot into ubuntu and 

```
sudo update-grub
```

It should find BT4 no problem.

---

### Post by VanJoe on 2011-01-09
thanks guys. Reinstalling grub from live cd worked. It didn't find the BT4 (I think I was supposed to mount it before I reinstalled grub) but that's fine I didn't like it anyway. I'll just delete that partition.

---

