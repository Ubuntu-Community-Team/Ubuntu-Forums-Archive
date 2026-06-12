---
title: "Removing GRUB in Windows 7 dual boot pc"
date: 2010-05-11
forum: General Help
---

### Post by BlueDevilBlue on 2010-05-11
I recently installed 9.04 on my Windows 7 pc as a dual boot.  Shortly thereafter 10.04 was released and I tried to upgrade.  The upgrade failed, so I wiped out my ubuntu partition and tried to do a clean installation.  Unfortunately, wiping the partiting messed up GRUB, and now I couldn't get into either OS.  I looked on the forums for help, but all references to fixing GRUB on a Windows PC was to Vista or older versions of Windows.  Changes to Windows 7 meant that none of the posts had the proper fix to the problem.
 
However, after much searching I came across a post on a Microsoft forum (Microsoft Answers) that provided the solution.  The original solution posted by a Microsoft moderator didn't work (shocking, I know).  However, another forum member did supply a solution that worked perfectly (credit here goes to Ramin15 - well done!).  The original post is here:
 
[http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/42d3f550-bf5f-459d-94ed-4cbadd7c933c](http://social.answers.microsoft.com/Forums/en-US/w7repair/thread/42d3f550-bf5f-459d-94ed-4cbadd7c933c)
 
But the relevant part for removing GRUB is here (I note here that his situation matched mine perfectly - your condition may be different so proceed at your own discretion):
 
"Quick and easy fix to remove the dirty GRUB and get Windows again.
 
1. Put the Windows 7 installation disc in the disc drive, and power cycle your PC after setting it to boot from CD Drive in BIOS.

2. Press a any key when you are prompted & select [language, time, currency, keyboard etc.] & click **Next** . Select **Repair Your Computer** option in the dialog window.

3. In the ‘System Recovery Options’ window Click the 1<sup>st</sup> Option **Startup Repair** and let it do what it wants to do, but in my case it didn’t solve the problem so I went to the next step.

4. In the ‘System Recovery Options’ dialog box, go to the last option i.e. **Command Prompt** .

5. Once in the command prompt (**X:\Sources>** ), type exactly the following commands in the same sequence
**bcdedit /export C:\BCD_Backup **
**C: **
**CD Boot **
**Attrib bcd –s –h –r **
**ren c:\boot\bcd bcd.old **
**bootrec /RebuildBcd **
 
then it said
[FONT=Courier New]“Scanning all disks for windows installations.[/FONT]
[FONT=Courier New]Please wait, since this may take a while…[/FONT]
[FONT=Courier New]Successfully scanned windows installations: 1[/FONT]
[FONT=Courier New][1] C:\windows[/FONT]
[FONT=Courier New]Add installations to boot list? Yes(y)/No(N)/All(A) : “[/FONT]
 I pressed **‘Y’** as there was only one instance of windows installation.   Then it said [FONT=Courier New]The operation completed successfully.[/FONT]
6. Next entred the following command      **bootrec /fixmbr **   It said [FONT=Courier New]The operation completed successfully.[/FONT]
7. Next entred the following command      **bootrec /FixBoot  **Again It said [FONT=Courier New]The operation completed successfully.[/FONT]
8. Set the BIOS again to boot from the HDD and reboot.
 
GRUB was gone & finally the cool windows 7 was booting again."
 
Now that my pc is working again, I will go back and try installing 10.04 again - I hope it works this time!  :P

---

### Post by EazyEVM on 2011-08-01
[FONT="Verdana"]Hi there,

I just wanted to say that your post was EXTREMELY helpful!!!  Thanks so much.  I would only add that one must press "Enter" after each Command Prompt line.  True to the noob that I am, I entered all of the commands then pressed "Enter" only to find out that nothing resulted.  Once I tried it again (one line at a time) it worked like a charm.  Thanks and have a great day![/FONT]

---

### Post by montoya_007 on 2012-02-11
It worked for me too, very good description of the steps to follow.

Thanks a lot!

---

### Post by darkomano on 2012-02-17
It is possible that the active partition is not mapped to c: !!
 
The boot process in Windows is centered on the active partition !
To find out what the actual mapping of partitions is you can use 
**diskpart** - command line tool for managing disk partitions.
 
Once an active partition is set the automatic **StarUP Repair** (should be run up to 3 times with rebooting after each run) usually solves boot problems for Windows 7.
 
Problems with booting Windows 7 can be solved easily once the boot process is understood:
 
1. BIOS loads MBR of first disk which
2. loads partition boot record (PBR) of active partition which
3. loads \bootmgr from active partition (bootmgr uses BCD in \Boot directory again on active partition). BCD is Boot Configuration Data.

---

### Post by trondhindenes on 2012-06-20
Brilliant, this solved it for me too. Looks like the WInPE assigns C:\ to the system/boot partition (it doesn't normally have a drive letter when you're bootet into your regular windows OS), so the procedure above worked perfectly for me.

---

### Post by SnakeJayd on 2013-04-04
Thanks for this post.
I signed up to this forum just to say thanks and that it worked for me too.
Cheers

---

### Post by matt_symes on 2013-04-04
I'm glad it worked for you as well. However this is an old thread so **thread closed**.

---

