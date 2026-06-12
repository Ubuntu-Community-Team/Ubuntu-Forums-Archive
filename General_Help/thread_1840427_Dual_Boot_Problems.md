---
title: "Dual Boot Problems"
date: 2011-09-07
forum: General Help
---

### Post by axelbrora on 2011-09-07
Hi,
 
I have downloaded and installed Ubuntu on a separate partition on my hard drive to allow me to transfer my data to it, and then format my C: drive and reinstall Windows XP. during the XP installation I get a "error loading operating system" the first time XP tries to reboot. I think this is because I now have two operating systems and there is no option to choose which one to use, it just goes to error. 
 
Can anyone help?
 
Axel

---

### Post by Bucky Ball on 2011-09-07
Welcome.

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Should fix your problems. You have Ubuntu installed on the same drive? It has screwed up the master bootloader and this will install Ubuntu's Grub to the MBR and pick up all operating systems and include them in your menu at boot.

Just a question: if you wanted to transfer all the data from a Windows install to another partition, why didn't you just do that rather than install Ubuntu? You realise Ubuntu and Windows are not compatible? They can dual-boot and run together on the same hard drive happily but they are totally different and Win programs aren't going to run natively in Ubuntu.

Also, Win does not recognise Ubuntu drives. They are EXT format, not NTFS or FAT. ;)

---

### Post by New00Folder on 2011-09-07
Without going into details I can tell you that it would have been much better if you had installed xp first and then ubuntu. Maybe you can try again.

---

### Post by Blasphemist on 2011-09-07
I'm thinking that what you may be wanting to do is end up with a clean windows install, files saved from your existing installation and a working ubuntu install. Is that right? It also sounds like you are fine until you install the win xp over the existing xp. Is that right? I recommend that you boot to the ubuntu live cd environment and install boot-repair from the software center. If you want to just start with having it create a boot info summary that will post automatically. You then just have to give us the page address that you'll be provided. Boot-repair can likely repair what is broken but if it isn't clear what needs fixed just let us see the summary.

---

### Post by axelbrora on 2011-09-07
Hi,
 
Many thanks for the prompt replies.  Some clarification follows:
 
I only had a single partition on a 500MB drive with XP installed.
 
XP would not boot up and the recovery consul repair (chkdsk) on the XP disk did not work.  Neither did the second repair option installing new XP replacement files and leaving settings intact, I got continuous error messages after several attempts.
 
I decided to do a format and clean install of XP, but needed to retrieve about 45GB of important data from the HD.  I booted from Ubuntu, then installed Ubuntu creating a 100Mb partition on the HD in the process.  I then copied the data from the XP drive to the Ubuntu partitioned drive.  I do not have a portable device that will take anything like 45GB, try 2GB, and I could not get the Ubuntu network linked with my laptop to transfer the data via the home network.  So I formatted the 400GB partiton (C:) and tried to install XP.  I would then have transferred the data back and left Ubuntu on the 100MB partition as an alternative OS and storage area.
 
All has gone wrong and now I am stuck!
 
I hope this clarifies the current situation and answers some of the questions.  Any help on now I should now proceed would be most appreciated.
 
Axel

---

### Post by Blasphemist on 2011-09-07
That does help explain what the current condition may be. The problem may just be in the mbr.

So lets try this. Boot to the ubuntu live cd and choose try ubuntu. Then install boot-repair. To do that open a terminal using the menu's and run this code.
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```
Run boot-repair and click on advanced options. Review the checked items on all tabs and if you have any questions, just click back on advanced options and it will take you back to the main screen. You could then just click on create bootinfo summary and post the web page address it will give you. We can then answer your question(s). I'm not sure what clicking recommended repair would do exactly but it might well fix it up.

---

### Post by axelbrora on 2011-09-08
OK update as follows:

Followed the instructions and run Boot-Repair.  Clicked on Recommended Repair and was advised that the problem was fixed.  Shut down, removed the Ubuntu CD and rebooted.  The computer booted straight into the hard disk copy of Ubuntu, (XP not yet installed on the C: partition) and all was well.

Shut down again and booted from the XP CD and started to install Windows on my C: drive.  Same problem as before, the first time Windows tried to reboot I got "error loading operating system".  Shut down again, removed the XP CD and rebooted.  This time the  "error loading operating system" came up right away and it would not boot into Ubuntu, so back to the Ubuntu CD.

It appears that the Boot-Repair fixed things to make Ubuntu boot then XP must have changed things back while copying files so that nothing boots!

Boot summary as follows:   [http://paste.ubuntu.com/685045/](http://paste.ubuntu.com/685045/)

Axel

---

### Post by YesWeCan on 2011-09-08
Have you tried fixing it so it boots Ubuntu, then open a terminal and do
sudo update-grub

Then reboot and you should have a menu with choice of Ubuntu, memtest and XP. Select XP and see if it boots.

If it doesnt there is probably some incompatibility between XP and your hardware. What changed originally pior to XP no longer booting?

---

### Post by axelbrora on 2011-09-08
Hi,
 
Thanks for the reply. I tried it again and this time selected the restore MBR option in Boot-Repair and it has worked and I have now reinstalled Windows XP on my C: drive and all boot problems appear to be resolved.
 
My problem now is getting my data that I moved to the Ubuntu partition back on to the C: drive. I am getting access denied, as you do not own them, to the main folder with a large amount of data. I was able to access this folder before, after I moved it accross. The other folders I moved at the same time can be accessed but I am denied permission to move then back to the C: drive. 
 
I believe that the main data folder, the one I cannot access, was transferred when I had started Ubuntu from the hard disk and the others were transferred when I had booted from the CD.  This would possibly explain why I cannot now access the main folder as I am currently working from the CD.  When there is no CD I boot straight into XP and I do not want to mess with the boot option again now that all is working fine.  In any case even if I could access the main folder I still cannot copy to my C: drive because of the permission issue.  
 
Any help with these permissions would be appreciated.   
 
Axel

---

### Post by YesWeCan on 2011-09-08
> **axelbrora said:**
> Hi,
 
Thanks for the reply. I tried it again and this time selected the restore MBR option in Boot-Repair and it has worked and I have now reinstalled Windows XP on my C: drive and all boot problems appear to be resolved.
Good. Don't mess with the MBR now. :)
 
> My problem now is getting my data that I moved to the Ubuntu partition back on to the C: drive. I am getting access denied, as you do not own them, to the main folder with a large amount of data. I was able to access this folder before, after I moved it accross. The other folders I moved at the same time can be accessed but I am denied permission to move then back to the C: drive. 
Would you explain not just what you are doing but how you are doing it? Nautilus, command line.

You will not be allowed to write to the "C:" partition as a regular user. This is to protect your Windows. You'll need to be root. This means you'll need to use a terminal and mount the "C:" partition somewhere.

Suppose your "C:" partition is sda1
```
[COLOR="DarkSlateBlue"]sudo mount /dev/sda1 /mnt
sudo rsync -avx /filesToRestoreDirPath/ /mnt/WindowsDestinationFolderPath/[/COLOR]
```

---

### Post by axelbrora on 2011-09-08
[QUOTE=YesWeCan;11230305] Would you explain not just what you are doing but how you are doing it? Nautilus, command line. QUOTE]
 
Hi,
 
Thanks again for your help. I have booted from the CD and I am simply trying to drag and drop the folders back to my Windows drive. Not very familiar with the terminal or command lines. I was able to drag and drop the folders from the old duff Windows installation into Ubuntu so I thought it would be just a case of dragging them back where they came from in the new windows installation.
 
Do I just paste the code you have given or do I need to change to or add the correct path? Also how do I know that the C: drive is sda1 or someother number? The computer view just lists it as 400GB Filesystem.  Also is that one command or a separate command on each line?  
 
Axel

---

### Post by YesWeCan on 2011-09-08
That's much clearer, thanks :)

Would you open a command terminal and post the output of
sudo fdisk -lu

---

### Post by YesWeCan on 2011-09-08
I have thought of something easier. :)

It's sort of naughty, tho. [-X

Use the live CD. In Places click on your C: drive and your Ubuntu drive like you did before to try to copy from one to the other. But this time close or minimize the browser windows to get them out of the way. The icons for the two drives should still be on the desktop.

Now open a command terminal and type these two comamnds:
gksudo nautilus &
gksudo nautilus &

This will open two new browser windows with root user permissions. Navigate to one drive in one browser and vice-versa and see if you can drag & drop the files. Be careful because you are now root and there are no safeguards.

**[edit]** I am a little worried about this. Not sure why. But perhaps you should first drag & drop an unimportant folder and then boot XP and make sure it has copied ok, before you do the whole lot.

---

### Post by Bodsda on 2011-09-08
> **YesWeCan said:**
> I have thought of something easier. :)
 
It's sort of naughty, tho. [-X
 
Use the live CD. In Places click on your C: drive and your Ubuntu drive like you did before to try to copy from one to the other. But this time close or minimize the browser windows to get them out of the way. The icons for the two drives should still be on the desktop.
 
Now open a command terminal and type these two comamnds:
gksudo nautilus &
gksudo nautilus &
 
This will open two new browser windows with root user permissions. Navigate to one drive in one browser and vice-versa and see if you can drag & drop the files. Be careful because you are now root and there are no safeguards.
 
**[edit]** I am a little worried about this. Not sure why. But perhaps you should first drag & drop an unimportant folder and then boot XP and make sure it has copied ok, before you do the whole lot.
 
/me watches with interest to see what will happen to the file permissions :popcorn:

---

### Post by YesWeCan on 2011-09-08
> **Bodsda said:**
> /me watches with interest to see what will happen to the file permissions :popcorn:
Thanks. Exactly.
A test copy is in order, methinks.

What method would you recommend to copy the files?

---

### Post by Bodsda on 2011-09-08
> **YesWeCan said:**
> Thanks. Exactly.
A test copy is in order, methinks.
 
What method would you recommend to copy the files?
 
Should make absolutely no difference because NTFS doesnt understand permissions. A standard drag and drop should work fine, but I think i'll stay and watch anyway :)
 
If the windows machine currently boots, try copying over something that would cause an obvious error, like NTLDR (after making suitable backups of course)

---

### Post by YesWeCan on 2011-09-08
@axelbrora

You should be aware that when you drag & drop you can choose to copy or to move. When you do a move all the attributes of the original file are transferred (where possible) but when you do a copy it makes a brand new file whose owner and group are now those of the user doing the copy and whose date is todays date. So doing a move is better than doing a copy if you are trying to keep everything the same.

Having said this, Windows files don't have many attributes. Creation date, access date, read-only, archive. Something like that. So this may be a non-issue.

But when you drag & dropped the files from XP to Ubuntu in the first place did you copy them or move them? If you copied them then their attributes will have changed anyhow.

So anyway, the bona fide way to do this, *in both directions*, is to use rsync from the command line (recursive, archive copy).


If you want to do an archive copy, you need to boot live CD and then mount the two partitions. Use sudo fdisk -lu to see the partition names.
Example: C: partition is sda1, Ubuntu partition is sda5
[COLOR="DarkSlateBlue"]sudo mkdir /mnt/windows /mnt/ubuntu
sudo mount /dev/sda1 /mnt/windows
sudo mount /dev/sda5 /mnt/ubuntu

sudo rsync -avx /mnt/ubuntu/pathToSourceDirectory/ /mnt/windows/pathToDestFolder/[/COLOR]

---

### Post by YesWeCan on 2011-09-08
> **Bodsda said:**
> Should make absolutely no difference because NTFS doesnt understand permissions. A standard drag and drop should work fine, but I think i'll stay and watch anyway :)
Vulture!
:p:p:p

---

### Post by Bucky Ball on 2011-09-08
gksudo nautilus.

You are root in the file manager. Copy what you want, you have permission to do anything. Close the window. You are no longer root. Won't change any permissions permanently. Not sure what all the fuss is about. Just copy what you want and don't do anything else, but I would start with copying one of your own files over as a test and forget about NTLDR. You're only interested in getting your files there and copying the other might not work for various reasons which bear no relevance to what you're wanting to do (and you DON'T want to accidentally remove NTLDR from the Win install). ;)

---

### Post by axelbrora on 2011-09-11
> **Bucky Ball said:**
> gksudo nautilus.
 
You are root in the file manager. Copy what you want, you have permission to do anything. Close the window. You are no longer root. Won't change any permissions permanently. Not sure what all the fuss is about. Just copy what you want and don't do anything else, but I would start with copying one of your own files over as a test and forget about NTLDR. You're only interested in getting your files there and copying the other might not work for various reasons which bear no relevance to what you're wanting to do (and you DON'T want to accidentally remove NTLDR from the Win install). ;)
 
Thanks for all the help, but yes I am getting confused with all of the options.  All I want to do is get permission to move or copy what I want, like as administartor in Windows.  
 
"gksudo nautilus" Not sure what this mean?  Is this a command you put into the terminal which make you root?  Can someone give me a simple step by step on how to make myself root?
 
Axel

---

### Post by Bucky Ball on 2011-09-11
> **axelbrora said:**
> 
"gksudo nautilus" Not sure what this mean?  Is this a command you put into the terminal which make you root?
Axel

Yes. It will open the Nautilus file manager with you as root so you have permission to do whatever. Move files and that only for now, then close the file manager.

---

