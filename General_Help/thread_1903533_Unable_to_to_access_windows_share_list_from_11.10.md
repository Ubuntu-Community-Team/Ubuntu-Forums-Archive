---
title: "Unable to to access windows share list from 11.10"
date: 2012-01-02
forum: General Help
---

### Post by step12dude on 2012-01-02
I was running 11.04 and decided to upgrade to 11.10 by doing a fresh install of 64-bit Ubuntu.  The installation went fine, but I find that I now cannot access windows shares on a network attached storage device that I am trying to access through my network from the 11.10 system.

Sometimes I can see the device that I wish to access, and sometimes I cant.  But if/when I see it, I get a message "unable to fetch share list" when I try to access the shares on the device from the 11.10 system.  

I have another computer on the same network running 11.04, and it is not having a problem accessing the network storage device or the shares on it that are in question.  In addition, I am running VMware Player on the 11.10 system with a Windows 7 guest, and even the Windows 7 guest can access the shares in question on the network attached storage device even though the host Ubuntu system upon which VMware Player and the guest Windows 7 system cannot.  

Am I missing something?  Any suggestions, anybody?  Is there something different about 11.10 vs. 11.04 that I need to be aware of?

Thanks for any help!

---

### Post by plucky on 2012-01-03
> Am I missing something? Any suggestions, anybody? Is there something different about 11.10 vs. 11.04 that I need to be aware of?


Have you installed samba?


Right click on a folder and select **Sharing Options** and share a folder.If Samba is not installed,it will install it for you.
You might have to reboot before it takes effect.

Good Luck

---

### Post by step12dude on 2012-01-03
Yes, Samba had been installed.  I just went out and verified it and also tried your suggestion of selecting a folder and sharing it, just to see.  I then went to another system on my network that is running 11.04 and was able to see the share that I created on the 11.10 system.

Any other thoughts?  Thanks!

---

