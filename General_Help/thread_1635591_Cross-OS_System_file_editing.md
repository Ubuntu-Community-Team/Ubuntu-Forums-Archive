---
title: "Cross-OS System file editing"
date: 2010-12-02
forum: General Help
---

### Post by bcschmerker on 2010-12-02
Recently I have been having significant instability on my eMachines®/Acer® EL1210-09, and traced it to severe damage to the Registry on its Microsoft® Windows® 6.0.6002 installation.  I managed to export to a USB memory chip a copy of C:\Windows\System32\Config\Software.reg, which contains the bad subkeys of HKey_Local_Machine\Software that RegEdt32.exe has been unable to overwrite.

Can this Registry file be successfully edited in GNOME Editor under Ubuntu® 10.04-LTS, as I suspect the case to be?  Microsoft Corporation formatted most of the Registry keys in question in a text-based form for RegEdt32.exe to handle; the Strings are encoded in hexadecimal format.

---

### Post by TeoBigusGeekus on 2010-12-02
Have you tried CCleaner?

---

### Post by prasannavl89 on 2010-12-02
The most reliable way I would suggest is to figure out a way to boot your Windows system with some recovery option and editing it there. But however if you really want to edit it in Linux, try this.

1. Install Wine. 
2. Backup your wine's system.reg (/home/<user>/.wine/system.reg)
3. Replace the Wine's system.reg with your software.reg and then run the regedit.exe in wine. Edit it.
4. Copy your old files back.

Hope it helps. Happy Regediting :D

---

### Post by bcschmerker on 2010-12-02
Problem is, even Startup Recovery has been booting inconsistently.  All critical System files load OK, but the process stalls during loading of the most critical Executables and Dynamic-Load Libraries for the user interface due to the aforementioned severe Registry damage.  As far as I have been able to determine, Microsoft® never included any kind of DLL for Reg.exe consistent with the autoremove function of Debian® APT.

Microsoft® having already submitted to its user base, through MS-Developer Network, a beta of Windows® 7.0 Service Pack 1 for field testing; most Windows® Vista&#8482; installation discs on the market only including Service Pack 1 (I had Service Pack 2 as of 1 December 2010); and given the lack of information on building a Registry from scratch (normally done during a new Windows® installation):  It may be more expedient to upgrade to 7.0.8002 than continue repair efforts on a critically damaged 6.0.6002.

Toward the Dist-Upgrade contingency, I am currently searching for a Mini-ITX power converter of 300W capacity to supersede the Lite-On® stocker in the EL1210-09 (220W) and pricing the 1 TB version of the Western Digital® Caviar® Black at several stores in the Contra Costa, CA, USA, area (I have already been pricing all capacities of Caviar® Green for a return to 10.04.1-LTS, AMD64 Edition, on the hybrid Everex® that I use for Ubuntu®).

---

### Post by pricetech on 2010-12-02
Your registry files can be edited in a text editor, but you'll need a "dos like" text editor since *nix based text editors are different.

I'd use a windows machine to do the editing.

Any data to be concerned with on the corrupt computer ??  If not, a reinstall would probably take less time, though it would also be a lot less fun.

---

### Post by bcschmerker on 2010-12-05
During the initial install of [Cakewalk® by Roland® Music Creator 3.0]("http://www.cakewalk.com/"), I was unfamiliar with how the Cakewalk® installer operated, and my musical data (which is yet to be recovered, as of 4 December 2010) ended up incorrectly in C:\Program Files\Cakewalk\Music Creator, rather than C:\Users\***********\AppData\Local\Cakewalk.  All other User data has been successfully backed up to DVD+R.

I found that Microsoft® Windows® NT, 2000 Professional, XP, and 6.0-up (all of which use some version of the NT File System) actually use a kernel evolved from OS/2 to operate correctly in 32/64-bit protected mode, with Cmd.exe as a shell.  Earlier versions of RegEdit.exe were designed to run in a terminal/shell environment consistent with OS/2 and FreeDOS; I do not know if that is the case with RegEdit.exe vv. 6.0.6000-up (correct for Vista and Se7en installations, and capable of editing C:\Windows\System32\Config\Software.reg, do.\SAM.reg, do.\Security.reg, do.\System.reg, and do.\_Default.reg).

---

### Post by prasannavl89 on 2010-12-09
Yes. They are consistent. The format of the registry has not been changed. And hence, any of them should do the job. 

Also, why don't you just use the RegEdit from Wine, as mentioned in my earlier post.

PS: If you're this much concerned, why don't you just keep backup of the reg files, modify them and see if your system boots up? If yes, good! or else, throw the files and try another method again. Simple.

---

### Post by bcschmerker on 2010-12-19
The EL1210-09 actually Startup-Recovered after I stripped all external accessories except the stock IBM 8530-compatible keyboard, Logitech® TrackMan® Wheel (via the stock mouse port), and Hewlett-Packard® HP 2009m display unit (via HDMI-to-DVI adapter cable from the EL1210-09's HDMI jack).  Iolo Technologies® System Mechanic 10 found new bad sectors on the stock Hitachi® hard disc after Registry fixes were executed; meaning, the Western Digital® Caviar Green®, rather than Caviar Black®, is on for the Dist-Upgrade to Windows® 7.0.8002 from 6.0.6002.  (Power-supply upgrades are impracticable, as any Mini-ITX PSU on the market would require modifications to the case to fit properly in place of the stock, and limited-to-220W continuous, Lite-On® PS-5221-06.)

Under consideration for upgrades are an Advance Micro Devices® Athlon X2 5050e (45*max*W, same as the stock Athlon LE-1620), RAM upgrade to 4 GB PC6400 (meaning, two 2 GB DIMMs; the two 1 GB stock DIMMs would be transferred to the Everex'® Gigabyte MA78GM-S2HP, bringing my Ubuntu® 10.04.1-LTS system to 4 GB from the prior 2 GB), and one Auzentech® X-Fi® Forte™ 7.1 PCI-Express x1 audio card (Creative® CA20K2 chipset, only supported for Microsoft® Windows® XP and 6-up as of 19 December 2010) to supplant the stock Realtek® ALC-889 planar audio chip (due to an identified hum issue with the mic preamplifier in the latter); the modem, unused since the EL1210-09 was purchased, would be deleted in the X-Fi® Forte™ install.

Thanks, everybody, for your input; an updated RegEdit.exe in the Wine™ virtual machine will probably come in handy for examining archive/backup Registry hives on the Everex®.

---

### Post by bcschmerker on 2011-01-15
As of 15 January 2011, the [eMachines®/Acer® EL1210-09]("http://www.emachines.com/") has been superseded by an [ASUS® CM1630-06]("http://usa.asus.com/"), which packs an improved all-AMD® chipset (Athlon II X2 220, 760G chipset, 4 GM DDR3 RAM) from my hybrid Everex® (Athlon X2 5600+/Socket AM2, 780G chipset, 4 GB DDR2 RAM).  Issues with the SATA controller board on the EL1210-09's stock 160GB Hitachi® Deskstar hastened the whole-system solution.

---

