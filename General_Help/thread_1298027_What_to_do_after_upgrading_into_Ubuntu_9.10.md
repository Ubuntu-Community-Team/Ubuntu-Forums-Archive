---
title: "What to do after upgrading into Ubuntu 9.10?"
date: 2009-10-22
forum: General Help
---

### Post by Tapas Bose, India on 2009-10-22
Hallo everybody.
Currently I am upgrading my Ubuntu 9.04 into Ubuntu 9.10 beta. My download process is going on. I want to know few things. How to I upgrade into Ubuntu 9.10 final release from beta version? I was came to know that my ext3 file system will not upgrade into ext4 and I will not have grub 2 also, because I am not doing fresh installation. After googling I found how to convert ext3 into ext4. But I am very much worried about that. Because I was trying to work with grub, installing gfxboot, but I was failed and I had to format my laptop for two times. I want to know, am I going to face similar problem during ext3 to ext4 conversion? And what about grub 2? Is there any problem during the first boot after upgrading process? I don't have yet Ubuntu 9.10 LiveCD.

Please do reply..

---

### Post by P4man on 2009-10-22
If you keep doing your upgrades you'll end up with the final release version. 

Migrating to Ext4 is possible without reinstalling, but provides no real benefit. I wouldnt bother. 

As for grub2, I think you will get grub2 when its done upgrading. But i could be wrong.

---

### Post by Tapas Bose, India on 2009-10-22
> **P4man said:**
> If you keep doing your upgrades you'll end up with the final release version. 

Migrating to Ext4 is possible without reinstalling, but provides no real benefit. I wouldnt bother. 

As for grub2, I think you will get grub2 when its done upgrading. But i could be wrong.
Thanks P4man.
Do you want to mean update via Synaptic or update manager or upgrade using update-manager -d command?
Is there any way to know what is my grub?
Can you please let me know briefly what is the benefit of ext4 over ext3?

---

### Post by P4man on 2009-10-22
> **Tapas Bose, India said:**
> Thanks P4man.
Do you want to mean update via Synaptic or update manager or upgrade using update-manager -d command?

Just the regular updates via update manager or synaptic. you wont need the -d until 10.04 alpha is released.


> Is there any way to know what is my grub?

If the grub menu says 1.97 beta, then you have grub 2, If it says 0.9 something then you have grub 1,

```

Can you please let me know briefly what is the benefit of ext4 over ext3?

```

[http://www.lmgtfy.com/?q=benefits+of+ext4](http://www.lmgtfy.com/?q=benefits+of+ext4)

---

### Post by Tapas Bose, India on 2009-10-22
Thank you very much for your kind reply P4man.

---

### Post by P4man on 2009-10-22
np. I guess the bottomline of ext4 is that its marginally faster than ext3, but only if you do a fresh install, and there is slightly bigger potential for dataloss.

---

### Post by zzzBrett on 2009-10-22
If you want to upgrade to ext4, make sure you have the entire partition backed up beforehand -- I almost lost all of my files that weren't backed up!

---

