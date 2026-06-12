---
title: "After installing Oneiric, Windows will not boot"
date: 2011-10-28
forum: General Help
---

### Post by zia.newversion on 2011-10-28
I never had this problem before. I have been dual booting Windows with Ubuntu for many years. Never once in this whole time has Windows or Ubuntu refused to work with each other. And the Windows version is the same as ever, the Ubuntu is newer. So I think it is something with Oneiric.

The boot-menu (grub2) appears. It lists Windows (loader) as well. However, as I boot into Windows, after a long time staring at the black we're-almost-there screen, the Windows 7 displays the "Launch startup repair" black screen. I have the OEM version of Windows which came with my Dell laptop. So naturally (and I hate this) I don't have a Windows disk. All I have are two backup DVDs through which I can only restore my laptop to company configuration. It would kill my Ubuntu installation and all the data that I already had on the disk (so much for "backup").

So, it gives me two options... Launch startup repair or continue booting windows normally (actually, it gives me a third option as well, but it's not listed: "roll-over and die, because Microsoft owns you"). I cannot select the first option because I have no Windows disk. So I select option 2 (not option 3 because I am too egoistic to admit that). And option 2 brings me to a BSOD saying that Windows failed to acquire access rights to a vital resource (which I presume to be the boot sector of sda which grub2 has so royally selected as its final residence). So the BSOD shows for a while, takes a dump in my computer (and doesn't tell me where so that I could clean it) and reboots the system.

After trying to boot for a thousand times, I got bored with the beautiful blue screen of death and ventured here to seek a solution if there is any.

O wise and worthy masters of the enlightened land of UnixVille, I plea to thee, grant me help, for I am helplessly in need of my Windows installation so I can make my presentation for tomorrow's lecture.

---

### Post by Blaqksheep on 2011-10-28
Hi.  Can you show me your partition table?  I'd like to have a gander at how your HDD is arranged.

Also can you take a picture of your BSOD?  If not can you get me the hex codes and the summary that pops up?  Should look something like:

```
STOP: 0x00000007B (0x000000000, 0x000000000, 0x000000000, 0x000000000)
INACCESSABLE_BOOT_DEVICE
```

Those crazy numbers actually tell me a lot about what's going on.

Have you TRIED the first option?  In all honesty your recovery disc is probably a hidden partition on your hard drive.

---

### Post by zia.newversion on 2011-10-29
Hello Blaqksheep... Nice of you to reply. You seem to be an expert at Microsoft Operating Systems. That's good, because there aren't many at UF...

And I cannot take a picture of the BSOD. I don't have a digital camera!
I can't memorize the codes by heart... And the BSOD stays for such a short time that I can't even properly read one of those hex strings.

And yes I have tries the first option. I forgot to mention... But in the first option, it says put your disc in the DVD ROM and reboot. If you do not have a disc, contact your system administrator (myself) or the  vendor (who won't tell me anything farther than the backup discs)...

And I tried booting up with the Backup discs as well... But it gives me only the options of restoration to factory settings or restore your computer to a previous restore point. I have only no restore point on HDD and only one restore point on the backup DVD itself (which is basically the same as restore to factory settings)...

In any case, I am gonna grab a pirated DVD of Windows 7 Pro and try running Startup Repair through it... Microsoft can sue me all they want!

---

### Post by Blaqksheep on 2011-10-29
Yeah I'm actually an A+ certified tech with a love for UNIX.  Ironically I fumble in DOS compared to Shell.  :P

The pirated version for startup recovery shouldn't be problematic at all so no worries of the DMA police knocking down your door.

I'll caution you on Startup Repair.  That will probably replace GRUB with Windows MBR, so you'll have to restore GRUB as well.  If that's the case, try [EasyBCD](http://cdn.neosmart.net/software/EasyBCD/community/EasyBCD%202.1.exe?AWSAccessKeyId=1HCB7Z221V5CV2K1ZDG2&Expires=1319939209&Signature=3j%2Ffwwn0HB3MnQYr3iFgw%2FbEyQ0%3D&response-content-disposition=attachment;%20filename=%22EasyBCD%202.1.exe%22).  It's a Windows executable so you'll have to fix Winderz first but it's a very easy way to pick your bootloader.

Also, restoring to factory default probably wont effect your Ubuntu partition.  I was working on a client's netbook a while back who had a Lubuntu partition and a factory restore left it and GRUB alone.  After a little thinking, I figured out why.  As I mentioned, a LOT of OEMs will make a separate, hidden partition for recovery purposes.  Because of this, Windows Recovery has to seek out the partition that Windows is installed on to do repairs/restores.  In addition at least in Windows 7, the Windows bootloader and other important files are hidden on a separate, ~100MB partition.  This means that it'd be impractical and self-defeating to format the ENTIRE hard drive.  When you do a factory restore, it only formats the partition Windows is on.  Windows by default also doesn't know how to read or reference ext filesystems that Ubuntu utilizes.  If it can't read it, it wants nothing to do with it.

**tl;dr version:  Restoring to factory defaults only wipes the partition Windows is on.  It wont touch Ubuntu, GRUB, or any other partition.**

---

### Post by oldtimer7777 on 2011-10-29
> **Blaqksheep said:**
> 
I'll caution you on Startup Repair.  That will probably replace GRUB with Windows MBR, so you'll have to restore GRUB as well.  If that's the case, try [EasyBCD]("http://cdn.neosmart.net/software/EasyBCD/community/EasyBCD%202.1.exe?AWSAccessKeyId=1HCB7Z221V5CV2K1ZDG2&Expires=1319939209&Signature=3j%2Ffwwn0HB3MnQYr3iFgw%2FbEyQ0%3D&response-content-disposition=attachment;%20filename=%22EasyBCD%202.1.exe%22").  Put this on a blank cd or flash drive and boot to it.  It's a Windows executable so you'll have to fix Winderz first but it's a very easy way to pick your bootloader.


Here is how you can restore your Grub2 if you get stuck:

[https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/](https://debianhelp.wordpress.com/2011/07/05/how-to-recover-grub2-after-windows-installation/)

---

### Post by Blaqksheep on 2011-10-29
Thank you for quoting that!  I originally linked to something else that was bootable but didn't erase that part.

I fixed it in my post.  EasyBCD is not bootable, it is a Windows program.  It's supposed to restore Grub from the Windows application but I've only used it to restore MBR so I can't vouch for that function.  Thanks for providing the proven method.

---

### Post by zia.newversion on 2011-11-05
Thanks all. I used a pirated Windows disk to run the Windows Startup Repair and then used the oldtimer7777 method to restore my grub. It worked fine. Now I have Windows and Ubuntu both booting fine in my system. :)

---

