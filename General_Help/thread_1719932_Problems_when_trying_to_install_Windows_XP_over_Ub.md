---
title: "Problems when trying to install Windows XP over Ubuntu"
date: 2011-04-02
forum: General Help
---

### Post by TotalMarko on 2011-04-02
I have an older laptop that will not run quickly on newer operating system. I installed Ubuntu, but unfortunately it does not support the wireless card installed in the system. So now I am trying to install Windows XP as it will allow the laptop to run quite quickly and will support my wireless card. I thought it would be simple process, but unfotunately when I try to boot from a Windows XP install CD nothing happens, it just continues straight to the Ubuntu desktop. Is there any way I can solve this problem? I have searched for a solution, but to no avail. Any help would be appreaciated.
 
-Marko

---

### Post by TeoBigusGeekus on 2011-04-02
1)Are you sure the winxp cd is valid? Have you tested it on another pc?
2)Are your bios settings correct, ie. CD-ROM as first boot device?

---

### Post by TotalMarko on 2011-04-02
> **TeoBigusGeekus said:**
> 1)Are you sure the winxp cd is valid? Have you tested it on another pc?
2)Are your bios settings correct, ie. CD-ROM as first boot device?
 
1. Yes, the Windows XP CD is valid and has been tested
 
2. Yes, the CD-ROM has been set as the first boot device

---

### Post by TeoBigusGeekus on 2011-04-02
Try to press a button before grub starts loading.
Perhaps a message like "Press button to boot from cd" flashes very quickly on startup and you can't see it.

---

### Post by wilee-nilee on 2011-04-02
> **TotalMarko said:**
> 1. Yes, the Windows XP CD is valid and has been tested
 
2. Yes, the CD-ROM has been set as the first boot device

There is a per session key prompt to get to a choose the booting media menu, outside of the bios. Mine is f12 look for yours, sometimes this is needed to probably catch the disc spin up and see it. You hit the key at powering on.

---

### Post by TotalMarko on 2011-04-02
> **TeoBigusGeekus said:**
> Try to press a button before grub starts loading.
Perhaps a message like "Press button to boot from cd" flashes very quickly on startup and you can't see it.
 
I thought that maybe the "Press any key to boot from CD" message was not appearing, so I restarted the computer and constantly tapped enter but once again it proceeded to the Ubuntu desktop.

---

### Post by Mark Phelps on 2011-04-02
> **TotalMarko said:**
> I thought that maybe the "Press any key to boot from CD" message was not appearing, so I restarted the computer and constantly tapped enter but once again it proceeded to the Ubuntu desktop.

Sorry, the "enter" key is never the key you press to interrupt boot.

It's either something like the "del" key or one of the function keys.

---

### Post by TotalMarko on 2011-04-02
> **wilee-nilee said:**
> There is a per session key prompt to get to a choose the booting media menu, outside of the bios. Mine is f12 look for yours, sometimes this is needed to probably catch the disc spin up and see it. You hit the key at powering on.
 
Yes, I have gone to that menu then selected the CD-ROM drive, but once again it boots into Ubuntu.

---

### Post by wilee-nilee on 2011-04-02
> **TotalMarko said:**
> Yes, I have gone to that menu then selected the CD-ROM drive, but once again it boots into Ubuntu.

Are you sure this menu is outside of the bios and not a bios trigger key prompt.

---

### Post by TotalMarko on 2011-04-02
> **wilee-nilee said:**
> Are you sure this menu is outside of the bios and not a bios trigger key prompt.
 
Yes, I am positive the menu is outside of the bios.

---

### Post by TotalMarko on 2011-04-02
> **Mark Phelps said:**
> Sorry, the "enter" key is never the key you press to interrupt boot.
 
It's either something like the "del" key or one of the function keys.
 
I know the enter key never interupts boot. What I am trying to say is that once I have interupted the boot using F10, which brings me to my device boot order. I select the CD-ROM drive. After this usually a message would be displayed saying "Press any key to boot from CD". I thought that the system may have been displaying this message to quickly and I wasn't able to see it, so I rapidly tapped the enter key to see if this may have been the case, but Ubuntu still booted.

---

