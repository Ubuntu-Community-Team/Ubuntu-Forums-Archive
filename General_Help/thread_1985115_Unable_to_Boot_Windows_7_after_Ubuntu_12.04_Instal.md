---
title: "Unable to Boot Windows 7 after Ubuntu 12.04 Install"
date: 2012-05-22
forum: General Help
---

### Post by mydogcanpurr on 2012-05-22
The title says it all, but I'll fill in a few gaps. I recently installed Ubuntu 12.04 from a cd to dual-boot with Windows 7. The installation went just fine. I can now boot into Ubuntu via Wubi. When I choose the Windows 7 loader option, however, the computer just restarts. There is no error message. All it does is restart and go straight to Wubi. I am running a 32-bit version of Windows 7 and Ubuntu. I read in the help that running startup repair from the Windows 7 disc would help. When I put in the disc and try to boot from it, however, it loads the files and goes to the windows 7 startup - as if I'm booting Windows, which is very weird. After it does this, it just goes to the generic windows 7 wallpaper with nothing on the screen besides the cursor. Any help would be appreciated as I am new to Ubuntu and Linux in general, thanks.

Edit: I forgot to mention that I ran the Boot Repair tool in Ubuntu. Here is a URL it gave me after it finished running: [http://paste.ubuntu.com/1002203/](http://paste.ubuntu.com/1002203/)

---

### Post by wilee-nilee on 2012-05-22
This is a partitioned install not a wubi.

You may need a chkdsk /f/r run it looks like you may have resized windows and not gotten the auto chkdsk.

Boot the recovery disc to the recovery terminal and put in.

chkdsk /f/r

This can be run from a F8 prompt possibly from the windows boot from the grub menu, if you can get a terminal there

---

### Post by mydogcanpurr on 2012-05-22
When I referred to Wubi I meant the boot manager. I guess I must have gotten it confused with something else. I have a Windows installation disc as mentioned but it simply didn't work. (It has worked in the past if  you are wondering....)

---

### Post by wilee-nilee on 2012-05-22
> **mydogcanpurr said:**
> When I referred to Wubi I meant the boot manager. I guess I must have gotten it confused with something else. I have a Windows installation disc as mentioned but it simply didn't work. (It has worked in the past if  you are wondering....)

It may just not be getting booted try a f12 prompt at powering on to get a choice of boot menu. Your bios flash not the actual bios may tell you what key or keys to press to get this menu. This menu is outside of the bios.

I had to edit my first post as well.

---

### Post by MadmanRB on 2012-05-22
It might be that you borked your windows install and if you did then I am sorry.
This is why I usually defrag and compress windows before installing linux, the reason why both are important is that windows is a very greedy OS and if anything gets changed it wont work.
If you installed from CD then its more then possible you might have altered something in windows by mistake, this is no fault of Ubuntu as it only does what you tell it and its up to you to taske the steps needed.
See if Microsoft will give you a replacement disk if you need windows and your installer disk for it inst working, back up what you can.
If you have lost data then I am sorry, but that comes with the dual booting as it can mess things up if you dont take the steps.

---

### Post by YannBuntu on 2012-05-22
Hello

> **mydogcanpurr said:**
> I ran the Boot Repair tool in Ubuntu. Here is a URL it gave me after it finished running: [http://paste.ubuntu.com/1002203/](http://paste.ubuntu.com/1002203/)

Please run Boot-Repair, update it, click "Advanced options", go to the "GRUB options" tab, tick the "FlexNet" option, apply, then indicate the new URL that will appear.

---

### Post by wilee-nilee on 2012-05-22
> **YannBuntu said:**
> Hello



Please run Boot-Repair, update it, click "Advanced options", go to the "GRUB options" tab, tick the "FlexNet" option, apply, then indicate the new URL that will appear.

Good eye I missed the flexnet. :)

---

### Post by YannBuntu on 2012-05-22
that's something we couldn't have seen via the "standard" BootInfo ;)

---

### Post by wilee-nilee on 2012-05-22
> **YannBuntu said:**
> that's something we couldn't have seen via the "standard" BootInfo ;)

We used to see it sometimes but I will take your word on that. :)

If it was the most efficient method every-time, I would have everybody run the script from the boot-repair tool, sometimes it isn't though so I have to work within the situation.

---

### Post by mydogcanpurr on 2012-05-23
I was able to run chdsk C: /f/r from a repair disk, but that didn't work. I just ran the flexnet option in boot-repair. This is the url it gave me: [http://paste.ubuntu.com/1003645/](http://paste.ubuntu.com/1003645/)   Will try to reboot now.

Edit: Still can't boot Windows ):

---

### Post by mydogcanpurr on 2012-05-23
I tried purging and reinstalling grub along with the flexnet fix in boot-repair. This appeared to have removed the flexnet error, but I still cannot boot into Windows 7. New URL: [http://paste.ubuntu.com/1003777/](http://paste.ubuntu.com/1003777/)

---

### Post by wilee-nilee on 2012-05-23
Is this thread linked to the boot-repair thread so that yannBuntu sees any posts if needed.

[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

You can just post there with the script and a link here if you want.

---

### Post by YannBuntu on 2012-05-23
> **mydogcanpurr said:**
> I am unable to boot into Windows 7 after installing Ubuntu 12.04. I have run this utility along with chkdsk from a repair disk and startup repair. All to no avail. Here is my latest URL: [http://paste.ubuntu.com/1003777/](http://paste.ubuntu.com/1003777/)

Edit: To be specific, when I choose the Windows 7 loader, the computer just reboots.
Link of thread where this problem was originally posted: [http://ubuntuforums.org/showthread.php?t=1985115](http://ubuntuforums.org/showthread.php?t=1985115)

Please delete these 3 files that are in your Windows partition:
/boot.ini
/ntldr
/NTDETECT.COM
Then reboot.
If still not good, please try to repair your Windows boot via a Windows CD, it should give you direct access to Windows. Then just click the Recommended repair again to get your GRUB menu back.

---

### Post by mydogcanpurr on 2012-05-23
I deleted the three files as directed. I could not boot into Windows after a reboot. I ran startup repair from the repair disk. No dice.

---

### Post by wilee-nilee on 2012-05-23
> **mydogcanpurr said:**
> I deleted the three files as directed. I could not boot into Windows after a reboot. I ran startup repair from the repair disk. No dice.

Generally I have not seen the startup repair work if grub is in the mbr.

Can you run the script from the boot-repair tool again.

Any changes done needs a new script seen if you can.

---

### Post by mydogcanpurr on 2012-05-23
I generated the new boot info from the boot-repair utility. The new url is as follows: [http://paste.ubuntu.com/1003917/](http://paste.ubuntu.com/1003917/)

---

### Post by YannBuntu on 2012-05-23
In case the startup repair is blocked by GRUB in the MBR, you can try this:
1) Run Boot-Repair, click "Advanced repair", tick the "Restore MBR"  option (generates a generic MBR that boots on Windows), apply. Indicate the new URL.
2) Reboot and check if you can boot Windows or not.
3) if not, via a Windows CD type the following commands:
BootRec.exe /fixMBR
chkdsk C: /r /f (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
Then reboot, and check if you have direct access to Windows.
4) Finally, Boot-Repair's "Recommended repair" will recover GRUB menu
to access both Ubuntu and Windows.

---

### Post by wilee-nilee on 2012-05-23
> **YannBuntu said:**
> In case the startup repair is blocked by GRUB in the MBR, you can try this:
1) Run Boot-Repair, click "Advanced repair", tick the "Restore MBR"  option (generates a generic MBR that boots on Windows), apply. Indicate the new URL.
2) Reboot and check if you can boot Windows or not.
3) if not, via a Windows CD type the following commands:
BootRec.exe /fixMBR
chkdsk C: /r /f (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
Then reboot, and check if you have direct access to Windows.
4) Finally, Boot-Repair's "Recommended repair" will recover GRUB menu
to access both Ubuntu and Windows.

A big +1 here.

---

### Post by mydogcanpurr on 2012-05-23
New URL: [http://paste.ubuntu.com/1003940/](http://paste.ubuntu.com/1003940/)
Will do as you asked and post back.

---

### Post by mydogcanpurr on 2012-05-24
After restoring the MBR from boot-repair, the computer went into a continuous boot-reboot cycle. Next I put in my repair disk and ran the commands you gave me. Upon a reboot, I booted into Windows 7 just like normal. Next I ran boot-repair from a live cd. Upon rebooting, I found grub reinstalled and could boot into Ubuntu. I could not, however, boot into Windows 7 and was greeted by a restart just like my original problem.

Edit: I forgot to add that on a sidenote, after I ran BootRec.exe /ScanOs  It said that it didn't detect any operating systems. I could boot into Windows and everything was normal afterwards, however.

---

### Post by YannBuntu on 2012-05-24
Hello

> **mydogcanpurr said:**
> I could boot into Windows and everything was normal afterwards, however.

Is everything ok now?

If not, please use the Windows CD to repair direct access to Windows, then use the "Recommended repair" and indicate the new URL.

---

### Post by mydogcanpurr on 2012-05-24
I must have been unclear. What I meant was that after I ran the commands from the command prompt from a repair disk, I was able to boot into Windows normally (grub was gone). However, after I ran boot-repair, I was stuck with my exact original problem. I have done everything over again with the following new url: [http://paste.ubuntu.com/1005736/](http://paste.ubuntu.com/1005736/)
I will report back if I can boot into windows and ubuntu this time.

Edit: Still can't boot into Windows. I have the exact same problem as stated at the start of the thread unfortunately. (Windows is completely intact, I just can't boot into it via grub for whatever reason...)

---

### Post by wilee-nilee on 2012-05-24
> **mydogcanpurr said:**
> I must have been unclear. What I meant was that after I ran the commands from the command prompt from a repair disk, I was able to boot into Windows normally (grub was gone). However, after I ran boot-repair, I was stuck with my exact original problem. I have done everything over again with the following new url: [http://paste.ubuntu.com/1005736/](http://paste.ubuntu.com/1005736/)
I will report back if I can boot into windows and ubuntu this time.

Edit: Still can't boot into Windows. I have the exact same problem as stated at the start of the thread unfortunately. (Windows is completely intact, I just can't boot into it via grub for whatever reason...)

Have you run in the terminal in ubuntu.

```
sudo update-grub
```

---

### Post by mydogcanpurr on 2012-05-24
Just ran that from the terminal, will post back with results . . .

Edit: That did not work.

---

### Post by YannBuntu on 2012-05-24
Please burn a [SuperGrubDisk]("http://www.supergrubdisk.org/super-grub2-disk/"), boot on it, and tell us if you can access Windows via it.

---

### Post by mydogcanpurr on 2012-05-25
I don't know if I'm just not waiting long enough, but when I choose the detect OS option, it just displays a blank screen with an underscore in the top left corner.

---

### Post by YannBuntu on 2012-05-25
I don't know SuperGrubDisk enough to interpret this blank screen, you should ask SGD's developer.
Maybe there is a problem in the Windows entry created by GRUB, yo should create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)

Then, if still no solution via GRUB, i would advise to try EasyBCD in order to use Windows bootloader as main bootloader.

---

### Post by mydogcanpurr on 2012-06-03
Good news (at least for me), I have fixed my problem. I repaired the windows 7 boot from a windows 7 repair disk and then booted from an ubuntu live cd. Next I ran boot-repair with the "Repair Windows boot files" option unticked. This was ticked automatically by default for me. By unticking this option, I am able to boot into, either Windows 7 or Ubuntu via grub2. Thanks for all of your help. I really appreciate, considering you didn't have to help me. :)

Edit: Turns out that didn't work but using EasyBcd works 100% for me.

---

### Post by YannBuntu on 2012-06-04
**@mydogcanpurr:** good job! :)
I am not sure i understood your last message (i'm not native English-speaker): after using Boot-Repair without the "Windows repair" option, what did you observe at reboot? (did you see the GRUB menu? could you boot into Windows? into Ubuntu?)
Please could you run Boot-Repair, click "Advanced options", click "Backup partition tables...", save the ZIP file somewhere then send it to me by email (yannubuntu ATT gmail DOTT com). This may help me improve Boot-Repair. Thank you!

---

### Post by mydogcanpurr on 2012-06-04
It turns out that what I did actually didn't work (It worked only once for some reason). What I meant was that I had that option unselected (turned off). It was turned on automatically for me. I don't know why. The best solution for me at this point is to just use EasyBcd. (It works 100% for me, anyway)

---

### Post by YannBuntu on 2012-06-04
I checked the logs in your ZIP file. In your case, the "Repair Windows" option just performed a check but found nothing to fix, so the action performed by Boot-repair was the same with and without this option: it only reinstalled GRUB in the MBR.
I don't know why GRUB could not allow booting into Windows. I suggest you create a bug report here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug](https://bugs.launchpad.net/ubuntu/+source/grub2/+filebug)  (please indicate us the URL of this report so that we can follow up).

---

