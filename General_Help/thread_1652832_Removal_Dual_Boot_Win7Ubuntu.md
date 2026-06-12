---
title: "Removal Dual Boot Win7/Ubuntu"
date: 2010-12-25
forum: General Help
---

### Post by Jamesey162 on 2010-12-25
I've installed Ubuntu (latest) on my laptop but im not ready to use it as an everyday operating system. 

Its dual-booted with Windows 7 64bit, i would like to remove Ubuntu and the menu on startup selecting boot loader and automatically going into Windows 7.

Anyone shed any light on how to do this, i have googled it some people were saying just to delete the partition other were saying not to etc. 

Thanks very much :)

James

---

### Post by Ceiber Boy on 2010-12-25
When ubuntu installs it replaces the windows boot loader with GRUB, which boots windows and ubuntu, you would have to reinstall the windows boot loader. As for the partition where ubuntu is installed, you could wipe it but I don't think you could get windows to consume that space again!

Assuming windows have plenty of space i'dd leave ubuntu installed make windows the default os in the boot loader and use ubuntu for maintainace for windows (virus scans, data backup and stuff)

---

### Post by sikander3786 on 2010-12-25
Welcome to the forums :-)

Deleting the Ubuntu partition is sufficient for removing Ubuntu. Then recreate a new partition in the freed up space.

But once you delete Ubuntu partition, you'll be left with a broken Grub and won't be able to boot Windows any more. For that, you need to repair the Windows startup. And obviously, you need a Windows install/repair disc. If you don't have one, download it here. (Its legit)

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You'll need to perform startup repair at least 3 times.

[http://www.intowindows.com/how-to-easily-repair-windows-7-boot-problems-using-startup-repair/](http://www.intowindows.com/how-to-easily-repair-windows-7-boot-problems-using-startup-repair/)

Or if that is unsuccessful, you can use bootrec.exe.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Good Luck!

---

### Post by wilee-nilee on 2010-12-25
> **Jamesey162 said:**
> I've installed Ubuntu (latest) on my laptop but im not ready to use it as an everyday operating system. 

Its dual-booted with Windows 7 64bit, i would like to remove Ubuntu and the menu on startup selecting boot loader and automatically going into Windows 7.

Anyone shed any light on how to do this, i have googled it some people were saying just to delete the partition other were saying not to etc. 

Thanks very much :)

James

Can you from the Ubuntu terminal post the output of
```
sudo fdisk -lu
```

If it is just restoring the W7 bootloader to the MBR you can make a recovery disc from W7 or download one. Then it is just one command from the disc booted. Then remove the Ubuntu and expand the W7 partition if there is unallocated or make another NTFS.

---

### Post by Jamesey162 on 2010-12-25
Thanks for the replies :)

I've created a System restore disk in Windows so all i have to do is boot into it and restore it then go to computer management then delete the linux partitions? 

Does it matter if the restore disk was created after the linux install?

---

### Post by Ceiber Boy on 2010-12-25
> **Jamesey162 said:**
> Thanks for the replies :)

I've created a System restore disk in Windows so all i have to do is boot into it and restore it then go to computer management then delete the linux partitions? 

Does it matter if the restore disk was created after the linux install?

No, windows operates as normal when duel booting so weather you make the disk before or after a ubuntu install should not make any difference

---

### Post by Jamesey162 on 2010-12-25
No? 

What do you mean?

EDIT: Okay thanks :)

---

### Post by Ceiber Boy on 2010-12-25
> **Jamesey162 said:**
> No? 

What do you mean?

As above.

---

### Post by Jamesey162 on 2010-12-25
Okay i tried system repair disk and start up repair, it said it had successfully repaired the system i reboot my laptop to find its still got that list.  

Should i delete the ubuntu partition first, then try the system repair disk.

P.S. the laptop is only new 2 weeks ago and i really wouldn't like to break it.

---

### Post by axept on 2010-12-25
Just delete the partition from win 7, then do this:

Here is the quick and very easy fix to remove GRUB and get Windows working again. These instructions are from Microsoft's site but with my own added tips for a brainless recovery:

1. Put the Windows 7 installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).

2. Press a key when you are prompted.

3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.

4. Click Repair your computer.

5. Click the operating system that you want to repair (Win 7 in this case), and then click Next.

6. In the System Recovery Options dialog box, click Command Prompt.

7. Once in the command prompt, type exactly Bootrec.exe /FixMbr and then press ENTER. You will see "operation completed successfully."

8. Reboot and set BIOS to boot from the HDD again.

---

### Post by Jamesey162 on 2010-12-25
Thanks very much, ill take a look at this tomorrow :)

:')  thanks for the help so far! :)

---

### Post by Ceiber Boy on 2010-12-26
> **Jamesey162 said:**
> Okay i tried system repair disk and start up repair, it said it had successfully repaired the system i reboot my laptop to find its still got that list.  

Should i delete the ubuntu partition first, then try the system repair disk.

P.S. the laptop is only new 2 weeks ago and i really wouldn't like to break it.

Don't worry you won't break it! The worst that can happen is to reinstall windows from scratch. But the process your following is a well worn path so the experience of the forum members will help you through it.

The boot loader is on the Master Boot Record (MBR) which I THINK is separate to the ubuntu partition. So if you delete the ubuntu partition I just think it will remove the operating system and not do any think to the boot loader (do a bit more research first before you commit)

---

### Post by Jamesey162 on 2010-12-26
Thanks got it sorted! :)

Everything worked perfectly.

---

