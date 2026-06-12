---
title: "Need help, may have messed up MP3 Player."
date: 2009-07-25
forum: General Help
---

### Post by Rifester on 2009-07-25
Hi!
I am new to Ubuntu and have run into my first major problem (one I cannot correct).
I bought a new Sansa Fuse and have updating  the firmware (successfully) and copy my music onto it something was corrupted (it locked up on refreshing media).  I could not get past this screen and sent to the Sansa forum where the suggestion was to format the MP3 player from the OS (they said it would only format the items I wrote to the players).   I downloaded gparted from the package manager and formated it with the same FAT format that was on the player.   Now the player says "FAT is corruped, please connect device to PC and recover FAT".  Now gparted and the computer won't even recognize the MP3 player while it is plugged in.   Any ideas?

Thanks, 
Mark

---

### Post by Whiffle on 2009-07-25
If you hook it up, and immediately run "dmesg" in terminal, it'll show you what device the player is being detected as, something along the lines of "/dev/sdx".  

Do you know if its FAT16 or FAT32 or something else?

---

### Post by Rifester on 2009-07-25
I thought I selected the correct FAT format.   I have yet to venture into terminal.  If I go in how do I come back?  Sorry to be such a beginner, but I was really trying to get my computer and music players set up before exploring the ominous terminal.  I am familiar with DOS so I am not scared to go there, just need to know what to do to come back or does it open in a seperate window?

Mark

---

### Post by Whiffle on 2009-07-25
> **MRife said:**
> I thought I selected the correct FAT format.   I have yet to venture into terminal.  If I go in how do I come back?  Sorry to be such a beginner, but I was really trying to get my computer and music players set up before exploring the ominous terminal.  I am familiar with DOS so I am not scared to go there, just need to know what to do to come back or does it open in a seperate window?

Mark

Oh its just another window.  Applications > Accessories > Terminal.  You can copy from it with Ctrl+Shift+C  

And honestly, there is probably a GUI way to do this, but I have no clue what it would be because I do all this kind of stuff in a terminal, its just faster for me :)

---

### Post by Rifester on 2009-07-25
This is what I got at the end of a long string of info...  Is it possible my player might just have a bad drive on it?

[22860.678570] ata5.00: status: { DRDY }
[22860.678614] ata5: soft resetting link
[22860.905591] ata5.00: configured for UDMA/33
[22860.917883] ata5: EH complete
[22879.928081] usb 1-3: new high speed USB device using ehci_hcd and address 51
[22895.040095] usb 1-3: device descriptor read/64, error -110
[22896.296119] hub 1-0:1.0: unable to enumerate USB device on port 3
[22899.992080] usb 1-3: new high speed USB device using ehci_hcd and address 52

---

### Post by Whiffle on 2009-07-25
> **MRife said:**
> This is what I got at the end of a long sting of info...  Is it possible my player might just have a bad drive on it?

[22860.678570] ata5.00: status: { DRDY }
[22860.678614] ata5: soft resetting link
[22860.905591] ata5.00: configured for UDMA/33
[22860.917883] ata5: EH complete
[22879.928081] usb 1-3: new high speed USB device using ehci_hcd and address 51
[22895.040095] usb 1-3: device descriptor read/64, error -110
[22896.296119] hub 1-0:1.0: unable to enumerate USB device on port 3
[22899.992080] usb 1-3: new high speed USB device using ehci_hcd and address 52

Its possible but unlikely.  I did some googling there are some issues with that MP3 player and linux.  I'll keep looking and see what turns up.

---

### Post by Rifester on 2009-07-25
Is it possible I ruined the player selecting the wrong FAT format?

---

### Post by Whiffle on 2009-07-25
I doubt it.  The operating system should see it as a device, but won't be able to mount it because the file system is messed up.  Its analogous to an "Unformatted Drive" in Windows, you can see it, but you can't use it without getting it formatted correctly first.  

Right now linux isn't seeing it as a device that could have a filesystem on it, and I think thats Ubuntu's fault, not yours or the players.

---

### Post by Chronon on 2009-07-25
I read elsewhere that you should be able to force MSC mode by starting with the device turned off and inserting the USB cable while the Hold switch is engaged AND you are holding the Select button.

This thread at the SanDisk forums looks relevant for you.
[http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=25925&view=by_date_ascending&page=1](http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=25925&view=by_date_ascending&page=1)

---

### Post by Rifester on 2009-07-25
Luckily or unluckily I have two of these players.   It appears that my OGG formatted music may be corrupted (according to the player) and is a common problem on these players (according to the Sansa forum).  So I may have to burn my CDs again in a different format (yeah!).   I hooked up the half functioning player (unformatted in Ubuntu) and it is located at /dev/sdb, disklabel type is MSDOS.  Is there a way I can get Ubuntu to recognize the other player or should I go try to hook it up to a Windows machine and re-format it there?

Mark

---

### Post by Rifester on 2009-07-25
I hooked the player up to a windows machine and it acknowledges something hooked up to the USB port but cannot recognize it, so it won't let me format it to restore FAT.  Any ideas?  I did try to force it into MSC mode.

Mark

---

### Post by Whiffle on 2009-07-25
> **MRife said:**
> I hooked the player up to a windows machine and it acknowledges something hooked up to the USB port but cannot recognize it, so it won't let me format it to restore FAT.  Any ideas?  I did try to force it into MSC mode.

Mark

Where did you try to format it?  I think if you go to Control Panel > Administrative Tools > Computer Management > Storage > Disk Management , you may be able to do it from there.

---

### Post by Rifester on 2009-07-25
It is the same thing, the MP3 player does not show up, even after forcing it into MSC mode.  It must be bad.  I don't know what else to do.  I can see the hard drive c: and d: in XP computer management, I refreshed under "Actions" and it still doesn't show up.  I can see it under Device Manager->Universal Serial Bus Controllers->Unknown Device.   But it will not let me format it.

---

### Post by Rifester on 2009-07-26
Is there any way I can force the computer to mount the MP3 player at the USB port in terminal?  Or is there a terminal command I can use to force it to format the device in the FAT 32 format?

Mark

---

### Post by Whiffle on 2009-07-26
Well, it depends if you can get it to show up as a device or not.  If you can get it to show up as a device, then you can do it.  This is how I would go about it:

Since it didn't come up as a block device...we'll try unloading the USB2 module and reloading it.  Plug in the device, and then run "sudo modprobe -r ehci_hcd" and then "sudo modprobe ehci_hcd" in a terminal.  Now run dmesg again, and see if it shows up now.  If it doesn't then we'll have to find something else to try.

But once we do get it to show up, you can do "sudo fdisk -l" and it will display all of the available partitions on the system (including the device).  Using that, and the information from "dmesg," we can run "mkfs.vfat /dev/sdxy" where X is the letter of the device and y is the number of the partition, and that will format it.

---

### Post by Rifester on 2009-07-26
Whiffle,
I have the MP3 connected and it is showing up in GPARTED now.   It is located at /dev/SDB.  I can see it but GPARTED won't let me format it for some reason.  The option is grayed out, I cannot select it.   I tried running the format command in terminal using the format command then dev/sdb1 and it said "No such file or directory".   I assumed the partition would be 1, am I wrong?

---

### Post by Whiffle on 2009-07-26
Are you running gparted as root ?  

what is the output of "sudo fdisk -l /dev/sdb"

---

### Post by Chronon on 2009-07-26
Swissknife has allowed me to format very badly corrupted drives before (e.g. an iriver H120 that would not appear as a drive to Windows).  It might be able to help you.

[http://www.compuapps.com/download/Swissknife/swissknife.htm](http://www.compuapps.com/download/Swissknife/swissknife.htm)

I suggest it because I see you have a Windows box and it's an option that has worked for me in the past.  The site suggests it works on Linux, but it says no more than this.  I'm not sure if they mean through WINE or what.  The only download links are for a .exe.

---

### Post by Rifester on 2009-07-26
Whiffle, 
Thank you so much for your help!   I got the player fixed.   I configured a new partition on the MP3 player and returned it to the proper FAT format!   I so appreciate your help!  

Take care!   And I love your avatar!

Mark

---

### Post by Whiffle on 2009-07-26
Good to hear :) 

For all the folks following along at home, and future reference in searches, what did you end up having to do ?

---

### Post by Rifester on 2009-07-26
I left the player off over night.  When I tried connecting it today it went beyond the "FAT Corrupted Warning".  The player would not let me access it as a device even though I forced it into MSC mode.   I went to GPARTED and found the device there, set a new partition on the MP3 Player, then reformatted in FAT32, disconnected the player and it was as good as new.   I have read on the Sansa forums that the original problemss could be caused by corrupt tagging and/or OGG files.  I am in the process of re-burning music to MP3.  So far it looks like this may be the way to go...  I will update after this is complete to see if the problem persists after coverting to MP3.  Thanks again for all of your help!

---

