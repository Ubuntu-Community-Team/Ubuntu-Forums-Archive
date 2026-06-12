---
title: "How to uninstall Ubunutu and GRUB on dual boot HP"
date: 2010-12-11
forum: General Help
---

### Post by MrBalll on 2010-12-11
[Solved]

Hello, everyone.

I am wanting to uninstall Ubuntu and GRUB on my HP laptop to get it back to just Windows. Earlier I figured deleting the partition in Windows would be enough, was being lazy the time. So, I rebooted and got a GRUB error. I tried a few things to fix the error and had no luck.

So, I installed Ubuntu 10.10 and it fixed my GRUB error so now I can access Windows and Ubuntu just fine.

So, I am wondering how I can uninstall Ubuntu and GRUB so that when I push the power button on my laptop it goes right into Windows after POST.

Thanks,

MrBalll

Also, I do not have a Windows install disc, only the recovery discs that came with the laptop.

---

### Post by oldfred on 2010-12-11
If you have Vista/7 you should have a repair CD.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub

Whats wrong with dual booting?

---

### Post by Quackers on 2010-12-11
You should be able to make a Windows repair disc.
Go to Control Panel and select Backup and Restore (in later versions) and on the left side of the new window there should be an option to make a recovery cd (that's actually the repair cd, not the recovery dvd's).

---

### Post by MrBalll on 2010-12-11
Thanks for all the info, oldfred. A few minutes after posting this I remembered a website called [[COLOR="RoyalBlue"]YouTube[/COLOR]]("http://www.youtube.com/watch?v=_BVpkrvExyI"). [IMG]http://www.overclock.net/images/smilies/doh.gif[/IMG]

Nothing wrong with dual booting. I just wanted Windows only on this laptop for the time being. I needed all the space I partitioned for Linux way back when and just wanted to remove it for a week or two.
Don't worry though. It will be right back on there after a short time. :D

---

### Post by holycow131415 on 2010-12-11
tutorial here: [http://www.youtube.com/watch?v=K95gKIX-BbI](http://www.youtube.com/watch?v=K95gKIX-BbI)

---

