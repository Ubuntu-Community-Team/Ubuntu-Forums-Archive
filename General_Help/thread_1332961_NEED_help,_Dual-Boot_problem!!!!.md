---
title: "NEED help, Dual-Boot problem!!!!"
date: 2009-11-20
forum: General Help
---

### Post by Dirj15 on 2009-11-20
I am on my school computer. I dual booted Ubuntu with windows 7. I accidentaly deleted the partition that had Ubuntu on it. Now when i boot up my computer it tries to load GRUB but there is an error and GRUB cannot load. I tried installing Ubuntu again on my partition i made, but my computer still thinks the previous instance of Ubuntu is there. I need to finish projects this weekend. What should I do? PLEASE HELP.

If you were wondering Ubuntu 9.10 is the version I'm using

Also the only way I can get on is by booting with the live disk I made to install it.

---

### Post by lisati on 2009-11-20
> **Dirj15 said:**
> 
Also the only way I can get on is by booting with the live disk I made to install it.

If, as you say, you've deleted the Ubuntu partition, this will be the only way to go if you want Ubuntu back.

---

### Post by Dirj15 on 2009-11-20
I don't want Ubuntu back, its horrible. I want to get into Windows. And even if I did want Ubuntu back, it wont let me install it because my computer thinks I already have it

---

### Post by oldfred on 2009-11-20
You can always reinstall Ubuntu as it will rewrite the MBR to point to the new install. Use manual install and tell it to use the same partitions.

If you just want windows you have to use the Windows 7 install CD to repair to MBR. It is the same procedure for Vista & 7, they use the same MBR, but it is different than XP and all prior windows. You cannot install a winXP boot loader to the MBR and have 7 work.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by iNaitvad on 2009-11-21
Just boot Win7 CD, choose repair... All Done!
U are @ ubuntuforums, you shouldnt say "ubuntu its horrible" just like that IMHO... I use both, and I still love Ubuntu...
But, just answering your question, just boot win7 cd...

---

