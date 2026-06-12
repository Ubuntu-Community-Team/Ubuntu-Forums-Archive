---
title: "Help! Windows not booting on dualboot with precise"
date: 2012-08-29
forum: General Help
---

### Post by hofko on 2012-08-29
Hello!

I have always used Windows, but recently I realised how much Ubuntu is better. I have been using Ubuntu for  around two months and I wanted to make it my default OS. I still need Windows for some tasks, so I left it installed.

I came across a nice program called EasyBCD to configure my boot options. I set Ubuntu to default. Now it does boot  as a default OS but there I don't know any way for me to run Windows 8 now. I can't undo what I've done, because there is no Ubuntu version of EasyBCD. All my files are still on my disk, as well as Windows is there too.

Can I by any means boot to Windows 8 by not removing all my data?
Can I boot to Windows 8 from Grub?

Sorry if this is in the wrong thread, I'm a newbie to this forum.

Thanks in advance...
Hofko

---

### Post by oldfred on 2012-08-29
I do not know details of EasyBCD, but some here do like it that are primarily Windows users. Most of us use grub2.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by hofko on 2012-08-29
Thank you! Here is the link:
[http://paste.ubuntu.com/1174336/](http://paste.ubuntu.com/1174336/)

Thanks for the other links, I didn't even know that. No files on my computer were, as far as I know, corrupted or deleted. I just can't get to Windows...

---

### Post by oldfred on 2012-08-29
You are running wubi which is just a file inside the Windows NTFS partition. It uses the Windows boot loader and then shows a grub menu like a full partitioned install. It runs pretty much like a full partitioned install, but if you have Windows issues, you will not be able to boot Ubuntu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Do not know EasyBCD or BCDedit, but Windows boot entries & the wubi boot entry are in the BCD file. The BCD replaced the text file boot.ini in XP with a hive like the registry, so you need BCDedit to see or change it.

---

### Post by hofko on 2012-08-29
So...

I screwed up my computer even more...
I usually don't run anything on my computer unless I think I know what I am doing. When I set the configuration this morning i thought I knew what was I doing. But I didn't. So that's what happened.
Now I decided to run boot-repair. It said I should do some backups. I clicked X. It asked me if if I had done with the backups and if it should proceed with doing whatever it does. I clicked X instead of no. But it started doing things...
So I took out the battery of my laptop. I regret this now...
Now it won't even boot Ubuntu. 
Now it says Windows Boot Manager on top and goes on like this:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."
If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status: 0xc000000f
Info: The boot selection failed because a required device is inaccessible.

I put my Windows recovery disc in the laptop, clicked that it should boot from CD and it put out this again. Then I put an Ubuntu disc in. Run the Boot-Repair thingy and yet again it shows this.

Is there anyway to fix my computer now myself (i have done all backups, because I wanted to reformat my HDD because of all the junk, and this is a great way to do it ;)) or should I give to a computer repair guy?

Thank you for your help, and I know I screwed up bad this time.

---

### Post by oldfred on 2012-08-29
Abnormal shutdown often requires chkdsk from the Windows repairCD as some file is corrupted. 

For Windows Boot-Repair will usually just add a Windows boot loader and make sure the boot flag is one a bootable Windows partition. Otherwise you have to run Windows repairs.

Windows should see boot partition and you have to run the auto repair 3 times.

---

### Post by hofko on 2012-08-29
So I need a Windows installation disk?

---

### Post by oldfred on 2012-08-29
Or a repairCD.

If you have another system, know someone or can run this from any other computer. The old free site now charges $10 for a repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by hofko on 2012-08-29
Ok, I think I'll get a repairCD, as I don't seem to be able to run OS from a USB-stick.

I'll do that tomorrow. Thank you very much!

---

### Post by drmrgd on 2012-08-29
I want to chime in and say that EasyBCD is a great utility.  However, I learned recently that it does not support GPT / UEFI.  I'm not quite sure if you can boot Windows 8 in BIOS mode at all, but please to correct me if I'm wrong.  

I suspect that (aside from the Wubi question) if you want to dual boot Windows 8 and Ubuntu, you may have more work to do that just simply changing the bootloader with EasyBCD.  Please do correct me if I'm misguided though!

---

### Post by oldfred on 2012-08-29
Current Windows 8 is just like Windows 7. It only boots BIOS/MBR or UEFI/gpt. It will be soon when we start seeing the vendors versions as those will only be UEFI and have the secure boot enabled in UEFI.

I would think Microsoft would still sell Windows 8 as an upgrade to Windows 7 and all those computers do not have UEFI or those that do may not even be installed with UEFI mode. I doubt they will only offer it on secure boot systems, but we have yet to see.

---

### Post by hofko on 2012-08-30
I installed Wubi using Windows 8 and it worked, I could boot to Ubuntu. But first it booted to Windows, then it asked me if I want to go with Ubuntu. When I clicked on Ubuntu it restarted the computer and booted to Ubuntu.

Now I've created a repairCD using an another Windows PC. This one is running Windows 7, I hope that's not too bad.
My computer can't be repaired automatically and I'm having issues sending inforamtion to Microsoft. If I want to do a syswtem recovery (it gives me an option and I have the recovery disc), it asks me for my username and password. There is only one (my) username. I select it and it wants my password. I am 120% sure I've never had a password on Windows.
I know this isn't an Ubuntu problem anymore, but what can I do?

---

### Post by drmrgd on 2012-08-30
I'm unclear on your goal, and what problem you're describing after you installed Ubuntu Wubi.  From what you describe, the Wubi install in Windows 8 was successful.  What made you decide to try to create a repair CD, and what are you trying to repair?  

I would also suggest that using a Windows 7 recovery CD on a Windows 8 installation is not a good idea.  While I don't know the exact specifics of how each is set up, what I've read so far suggests that Windows 8 and Windows 7 handle the boot process a bit differently, and I would guess that might be why the recovery CD you made is not working.

You also should realize that Wubi is not the same as an independent installation of Ubuntu.  Wubi is not quite a virtual machine, but also not quite a stand alone installation.  You'll be running the OS stand alone, but using Windows to manage how the computer boots.  So, if you're getting the Windows boot manager, and you can boot into either Windows or Ubuntu, then you've successfully created a Wubi install. In case you don't have it already, here are the instructions for creating a Wubi installation, which, while vague, may provide some useful information:

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

Also, there is some detailed instructions from the ever excellent Psychocats tutorials:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

