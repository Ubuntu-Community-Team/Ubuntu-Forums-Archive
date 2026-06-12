---
title: "Uninstalling Ubuntu"
date: 2011-04-01
forum: General Help
---

### Post by newblueboy on 2011-04-01
SOLVED!!! Go to page 3 to read the solution. This is for a Vista PC!!!!!

Thanks everyone who helped!!

---

### Post by operatorace on 2011-04-01
As with any OS install issue, backup all files that matter and just format the entire disk back to Windows.

---

### Post by safarin on 2011-04-01
> **newblueboy said:**
> Hi All,
     This seems dangerous doing this, so I want to make sure this article is fully correct before I do it and possibly ruin my PC.

I want to uninstall Ubuntu. Don't say something like "But it's so great!". I understand, but I have many of my own reasons.

Here's the article I am thinking of using as a reference: [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/]("http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/")

Please tell me if this is the way to do it, and if I will not have any of the files that I had previously. I do have a Windows CD that came with my Gateway PC, with the Gateway logo on it and the title "Operating System Disc".

Thanks for any help, and the sooner the better!!!

I think you should came with detail explanation.
Such as your installation type (eg: Windows base, wubi or by partition)

I don't know how other do, but when I uninstall Ubuntu, I just use live cd with Gparted, delete the ubuntu and swap partition and reformat that partition to windows type partition (eg: NTFS).

---

### Post by 3Miro on 2011-04-01
Backup everything first.

If you used wubi, then you can just uninstall it from within windows. 

If you used separate partitions, boot from windows disk, restore the windows boot loader and then you can delete/reformat the partition form within windows.

---

### Post by newblueboy on 2011-04-01
Okay, so now I'm somewhat confused. I started by using Ubuntu Desktop edition and the Universal USB installer from ubuntu.com to try ubuntu out. I then installed it and I installed it by making a 50 GB partition on my 320 GB hard drive. To uninstall it, all I need to do is delete the partition in Windows Computer Management, shut down and boot from my Windows OS Disc, and then run two lines of code which are "bootrec /fixmbr" and "bootrec /fixboot", right?

I have a Gateway NV with a 2.2 GHz intel processor, 4 GB of RAM, Vista Home Premium x64, and a 15.6" display. 

I don't know much at all about Linux, so if you could, speak in simpleton talk. Thanks!!

---

### Post by Lateralis on 2011-04-01
To be honest there's nothing to uninstalling any OS.  Because in a way, you don't "uninstall" it like you would a program.  If you want to purge the OS from your system you simply reformat that partition into whichever format you like.  

To be honest I have no idea about reinstalling the bootloader for Windows 7 but those commands sound vaguely correct.  

But yes.  If you want Ubuntu gone, just reinstall the Windows bootloader and delete the Ubuntu partition.  Simples. ;)

---

### Post by newblueboy on 2011-04-01
Okay, so how do I reinstall the windows bootloader?

And to delete the linux partition, I just go into Computer Management > Disk Management > and delete the partition that ubuntu is on??

And do I install the Bootloader BEFORE I remove the linux partition??

---

### Post by grahammechanical on 2011-04-01
You really should be asking this question on a Windows forum. Unless any of us have done what you want to do, we cannot guarantee the accuracy of the advice. 

Regards.

---

### Post by newblueboy on 2011-04-01
Okay I think I have most of the pieces together, just one last thing.

Do I repair the bootloader BEFORE or AFTER deleting the partition.

Another way of saying it: Do I delete the Ubuntu partition before or after I repair the bootloader using the Vista CD?

---

### Post by ajgreeny on 2011-04-01
> **newblueboy said:**
> Okay I think I have most of the pieces together, just one last thing.

Do I repair the bootloader BEFORE or AFTER deleting the partition.

Another way of saying it: Do I delete the Ubuntu partition before or after I repair the bootloader using the Vista CD?
It does not really matter which order you do it.  If it were me I would probably restore the vista MBR first and make sure it works properly, as if you do it the other way round you will have no OS at all if the MBR restore is unsuccessful.  It should be quite easy to do, however, and I did it once or twice on XP, my last use of windows, but never on vista, so am unsure of the details of that.

---

### Post by oldfred on 2011-04-01
If you do not have the windows boot loader installed and try to reboot with grub's boot loader in the MBR which tell the computer to jump to the rest of the boot code in the Ubuntu partition which you have deleted then you will have boot problems.

Is your Gateway disk a repair CD/DVD or just a recovery? Recovery DVDs are just an image of your hard drive as it was the day you purchased it. It your reinstall that then all your data is also gone.

I would have the correct version of one of these, if I were you:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by newblueboy on 2011-04-01
Would re-installing Windows with a Recovery CD repair the boot loader?

Also, I've accessed Windows Startup Repair before w/o a CD. I did a cold reboot once while in Windows and Windows asked me if I wanted to try startup repair. Could I also do this??

---

### Post by oldfred on 2011-04-01
I am saying you probalby do not want to use the recovery disk unless you have to. It will restore system to as purchased but then you have to do all the updates, software installs & restore all your data from your backups.

You just need to run fixMBR (XP) or BootRec.exe /fixMBR (Vista/7) from a windows repair disk.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by newblueboy on 2011-04-01
Okay my problem is I cannot get a Windows Repair Disk even with the link you specified. It's complicated, but I cannot. 

If I started and logged on to Windows, shut down by holding down the power button, and selected "Run Startup Repair" or something when asked if I want to do that or go into safe mode, would that have the same effect of using a CD or no?

---

### Post by newblueboy on 2011-04-01
Wait a second, I think I've got it. 

My CD might also be a repair disc, I'll update soon!!


Thanks all who have helped me so far!!!!!

---

### Post by snafu006 on 2011-04-01
Step by step [IMG]http://www.astahost.com//style_emoticons/default/biggrin.gif[/IMG]

1. Put Disc in drive 

2. Start PC

3. Let the PC run into the CD

4. Choose the Recovery Console 

5. Type you admin username

6. Type your admin password

7. Type Fixmbr

8. Type exit

9. Eject Disc

10. Load windows ! 

11. Enjoy !

---

### Post by snafu006 on 2011-04-01
Hit F12 as soon as the computer starts

---

### Post by newblueboy on 2011-04-01
do you mean command prompt when you say recovery console

---

### Post by newblueboy on 2011-04-01
Okay, I got it fixed using all of your suggestions. Thank you ALL very much for helping me, it was more than fantastic. Because I have successfully uninstalled Linux, I will be leaving the forum. You all were a great help, and I am so very thankful that I joined this forum with it's great community. I will be posting a reply after this telling the world how I solved this in a summary fashion.

Thanks a ton!!!:P

---

### Post by snafu006 on 2011-04-01
No put in your windows cd restart your computer after you placed the cd in hit F12 as soon as the computer starts it should say something about boot from cd in the windows cd is a recovery

---

### Post by newblueboy on 2011-04-01
**Before doing this, back up ALL of your data that you may want.**


1. Use a Windows Repair Disk (probably came with your PC) and boot off it. To boot off a disk, put it in your PC, restart, and press any key when your computer tells you to. You can download an .iso image at [http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/). 

2. When everything is loaded and ready to go, select your language and press Next.

3. Select Repair Your Computer on the bottom of the window.

4. Select Command Prompt and Type this:
bootrec /fixmbr [press enter] botrec /fixboot

5. Close the window and select restart. 

6. You will boot into Windows, without being able to boot into Ubuntu.

7. Right click My Computer in Windows and select Manage.

8. Go to Disk Management on the left side.

9. Select the partition that has linux. Right click it and select Remove Volume. There should be more than one.

10. You are done! Congrats, you now have a Linux-Free PC!

P.S. If I made any mistakes, please look below for corrections by me or other members.

---

