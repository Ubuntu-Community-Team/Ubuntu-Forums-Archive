---
title: "Windows 7 | Linux Ubuntu"
date: 2010-03-09
forum: General Help
---

### Post by Rockstar6336 on 2010-03-09
Hi, I just installed Linux Ubuntu and I did that partitions and everything but it won't let me switch back to Windows 7 and my computer was made with Windows 7 so there is no installation cd and when I try to do system restore on startup it just pops up with the select os screen, what can I do to either switch back to Windows 7 or remove Linux and get back to windows.

---

### Post by patchwork on 2010-03-09
Try pressing SHIFT after the bios screen and before the ubuntu symbol, this should bring you to a boot selection menu (grub).

---

### Post by Villiam on 2010-03-09
From [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
If you have a problem with changing the MBR code, you might prefer to just install the code for pointing to GRUB to the first sector of your Ubuntu partition instead. If you do that during the Ubuntu installation process, then Ubuntu won't boot until you configure some other boot manager to point to Ubuntu's boot sector. Windows Vista no longer utilizes boot.ini, ntdetect.com, and ntldr when booting. Instead, Vista stores all data for its new boot manager in a boot folder. Windows Vista ships with an command line utility called bcdedit.exe, which requires administrator credentials to use. You may want to read [http://go.microsoft.com/fwlink/?LinkId=112156](http://go.microsoft.com/fwlink/?LinkId=112156) about it.

---

### Post by garvinrick4 on 2010-03-09
> **Rockstar6336 said:**
> Hi, I just installed Linux Ubuntu and I did that partitions and everything but it won't let me switch back to Windows 7 and my computer was made with Windows 7 so there is no installation cd and when I try to do system restore on startup it just pops up with the select os screen, what can I do to either switch back to Windows 7 or remove Linux and get back to windows.
Just a FYI you do get to make your own Windows 7 disks from within Windows 7. It takes 3 DVD's and you get one chance make them. You can make all the recovery disks you want. Soon
as you get back to 7 I would make them.  If you do not get help in this Forum on your problem with grub just google you will get a million entrys. Mine also came with 7 but I no longer use it. Just update it now and again but it does fit well with Grub2 and have had no problems so once repaired you should be fine.

---

### Post by Kurtosis on 2010-03-09
Not an expert, but if I had that problem I would first try to add Windows 7 to GRUB boot loader manually.  

Ubuntu tries to do this automatically when you install it beside Win 7 (unless you another other option during the install process).  But apparently it didn't on your install.  Are you sure you chose to install Ubuntu "beside" Windows 7, and not over it?

Here's a thead I found on adding Win 7 to GRUB manuallyu, in case it gives you some leads:

[http://ubuntuforums.org/showthread.php?t=1036547](http://ubuntuforums.org/showthread.php?t=1036547)

---

### Post by Nicolas.Perrault on 2010-03-09
You can't access Windows 7 at all?

---

### Post by Rockstar6336 on 2010-03-09
> **Nicolas.Perrault said:**
> You can't access Windows 7 at all?

No and when I goto GRUB it's not on the list...

---

### Post by MasterNetra on 2010-03-09
try running "sudo update-grub" from terminal and perhaps it will be detected. Afterwards you can try restarting and loading into it. (Note: The Grub list will come up automatically if there is more then one OS entry present, which case it will default to the first option if a choice isn't made in x amount of seconds. Its only when there is only Ubuntu present that it skips the list.) Also is the windows partition still present? Can you mount it from Ubuntu and see the contents? Also what version of Ubuntu are you using? Its Hardy, Interpid, or Jaunty the entry may say Vista. Karmic should see Windows 7 as Windows 7.

---

### Post by jusalgt2 on 2010-03-09
> **Rockstar6336 said:**
> No and when I goto GRUB it's not on the list...
i think you have over write your ntfs partition if that the case. ubuntu will automatically install or map drives including ntfs during installation of your unbuntu. grub loader will be installed too.

---

### Post by MasterNetra on 2010-03-09
> **jusalgt2 said:**
> i think you have over write your ntfs partition if that the case. ubuntu will automatically install or map drives including ntfs during installation of your unbuntu. grub loader will be installed too.

He may have but he should load into Ubuntu and check to see if he can mount the parition. If there is just his partition then probably he did. Also to note Window 7 uses TWO partitions one for its normal files and a 100MB partition. I hope he didn't delete either.

---

### Post by jusalgt2 on 2010-03-10
he must have win7 installation dvd to repair his system with fixmbr, fixboot and rebuildBCD commandto able to boot in win7 OS.

---

### Post by MasterNetra on 2010-03-10
> **jusalgt2 said:**
> he must have win7 installation dvd to repair his system with fixmbr, fixboot and rebuildBCD commandto able to boot in win7 OS.

Not if he wants to switch back and forth between win7 and ubuntu. Grub/Grub2 can handle it. Now if he decides to go ahead and just remove ubuntu and restore sole control to windows then yea. Either case is acceptable to the OP though.

> **Rockstar6336 said:**
> Hi, I just installed Linux Ubuntu and I did that partitions and everything but it won't let me switch back to Windows 7 and my computer was made with Windows 7 so there is no installation cd and when I try to do system restore on startup it just pops up with the select os screen, **what can I do to either switch back to Windows 7 _or_ remove Linux and get back to windows.**

I want to see first if both the main Win7 Partition and the small 100MB partition is still intact before any further advice is slinged around. Because if either are gone he's gonna have to re-install win7 then in turn re-install grub.

---

### Post by MasterNetra on 2010-03-10
Its 15 mins past midnight for me so I'm off to bed.
@OP if both the main Win7 partition and the 100MB partition are still in tact just update grub2 to get it to search for it.
For more info on Grub2 go here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) . It should be noted that if you just wanted to play around with Ubuntu you should of just installed in inside Windows. It would install like a program, gives a menu after booting up that allows you to go into ubuntu or windows and unlike dual booting there is no danger to windows. Downside sense Ubuntu is on ntfs it maybe somewhat slower then if it was running on its own cozy and speedy ext4 partition.

---

### Post by wilee-nilee on 2010-03-10
Here is a link to a W7 recovery disc, in case it is needed.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

