---
title: "Cannot restore Evolution"
date: 2009-11-03
forum: General Help
---

### Post by Minsky on 2009-11-03
I'm running a clean install of Karmic after wiping Jaunty from my system but I've hit a problem, before wiping Jaunty I backed up my Evolution mail/profile using **Backup Settings...**. However, when I attempt to restore the backup file I get an error message stating that I have to select a valid backup file to restore. I've had no problems in the past with restoring evolution using the backup files with Jaunty so I assume that this must be a bug which will eventually be fixed, but in the meantime can anyone help me so that I can transfer my backed up mail over to my new system?

---

### Post by Commander_Keen on 2009-11-03
I had the same issue.
if you go to the folder that has the Evolution backup 
Lets call the Evolution backup called filename123.tar.gz.
just double click on filename123.tar.gz.
tell it to extract.
and it will create the correct folders under the correct location.

beware that anything under memo's will not be there.

---

### Post by Minsky on 2009-11-03
Glad you can help CK, I've followed your instructions but the backup file just extracted to its current location. How do I get the extracted files into Evolution, or have I made a mistake somewhere?

---

### Post by Commander_Keen on 2009-11-03
for all intest purpose, lets call this file a zip file.
In this file has the following evolution, evoltuion\folder1 ; evolution folder2, evolution folder 3.

Double clikc on the file.
and tell it to extract to Home\Your User ID. ( Home\jrothschild would be mine)

---

### Post by brwrdrvr on 2009-11-03
> **Minsky said:**
> Glad you can help CK, I've followed your instructions but the backup file just extracted to its current location. How do I get the extracted files into Evolution, or have I made a mistake somewhere?

I had the backup file evolution-backup.tar.gz on a USB external drive and was trying to restore from that location. It failed with the same message. I moved evolution-backup.tar.gz file to my home directory, went back into Evolution and tried the restore again. Pointed to the file in my home directory and it worked. So hopefully it will work for the rest of you.

---

### Post by tacantara on 2009-11-03
> **brwrdrvr said:**
> I had the backup file evolution-backup.tar.gz on a USB external drive and was trying to restore from that location. It failed with the same message. I moved evolution-backup.tar.gz file to my home directory, went back into Evolution and tried the restore again. Pointed to the file in my home directory and it worked. So hopefully it will work for the rest of you.

+1

I had the same issue, and resolved it exactly that way, only difference is that I copied the .tar.gz file to my desktop from the USB memory stick.  I then opened Evolution and clicked File > Restore Settings, and picked the file I placed on the desktop.  Worked like a charm.

---

### Post by brwrdrvr on 2009-11-03
> **tacantara said:**
> +1

I had the same issue, and resolved it exactly that way, only difference is that I copied the .tar.gz file to my desktop from the USB memory stick.  I then opened Evolution and clicked File > Restore Settings, and picked the file I placed on the desktop.  Worked like a charm.

Good show and thanks for the +1. I usually try to keep as much as I can in my Home directory for these times when dealing with a fresh install. I just backup my home folder, Evolution backup file, and my Bookmarks from Firefox to my USB drive. That way I'm not looking around trying to remember if I have everything. I can wipe the drive and start over fresh. I can install programs as I need them. This also lets me get rid of programs I've installed and didn't like or use after due to "not exactly what I was looking for".

---

### Post by Minsky on 2009-11-04
Thankyou for all the replies, I've successfully restored my Evolution settings.I think that the problem may have been due to an incopatibility between the ext3 and ext4 file systems, I saved the Jaunty Evolution backup file in ext3 format to an external disk but I installed Karmic using the ext4 file system, copying the file to my desktop and restoring from there did the trick.

---

### Post by Goodbytes on 2009-11-05
> **tacantara said:**
> +1

I had the same issue, and resolved it exactly that way, only difference is that I copied the .tar.gz file to my desktop from the USB memory stick.  I then opened Evolution and clicked File > Restore Settings, and picked the file I placed on the desktop.  Worked like a charm.

For some reason I can't get Evolution to restore from a backup that wasn't generated *on the same o/s install* for anything. Starting with a clean install of Karmic i386, fully updated, I ran Evolution, set up my email accounts, imported my mail from Thunderbird and was happy.

Then I had Evolution do a backup, appropriately named Evolution Karmic i386.tar.gz. Installed Karmic amd64 separately, updated everything, ran Evolution and found that it wouldn't restore from the backup I'd just made.

I tried moving the backup archive from the external it was on to my home directory, checking extensions (.tar.gz vs .gz), I tried extracting the backup archive and recompressing it, in case it was a filesystem difference as was mentioned. No dice, Evolution always insists I need to feed it a *valid* backup. I even tried removing the .evolution dir and replacing it with the one extracted from the backup archive, hoping it would notice and parse the backup-restore-gconf.xml on startup, but no.

What *finally* worked was to go ahead and setup a dummy email account just to get through the startup wizard. From there, I made a backup (expletive.tar.gz) and opened it alongside my original i386 backup, and dragged the backup-restore-gconf.xml from it to the new expletive.tar.gz. Closed those both out, ran Evolution and restored expletive.tar.gz. Tada! Now my email accounts are set up. Extracting the actual mboxes from my i386 backup gives me the mail itself again.

What a pain.

---

### Post by philinux on 2009-11-05
> **tacantara said:**
> +1

I had the same issue, and resolved it exactly that way, only difference is that I copied the .tar.gz file to my desktop from the USB memory stick.  I then opened Evolution and clicked File > Restore Settings, and picked the file I placed on the desktop.  Worked like a charm.

I've done this a few times using the same archive on different machines and it's always worked.

The tar file extracts to a folder .evolution so it's only tarring up ~/.evolution anyway.

---

### Post by Goodbytes on 2009-11-05
> **philinux said:**
> The tar file extracts to a folder .evolution so it's only tarring up ~/.evolution anyway.

It's *mostly* tarring up .evolution, but not *only*. First it exports some of your gconf settings (for email accounts, etc.) to xml's. Check inside the backups Evolution generates - there should be a few extra files that aren't in the original ~/.evolution folder: backup-restore-gconf.xml, categories.xml, datetime-formats, etc.

---

### Post by Goodbytes on 2009-11-05
> **Goodbytes said:**
> Closed those both out, ran Evolution and restored expletive.tar.gz. Tada! Now my email accounts are set up. Extracting the actual mboxes from my i386 backup gives me the mail itself again.

What a pain.

What's killing me about this is now that I've got my email and accounts running on the amd64 install and Everything's Fine(tm), I went ahead and had Evolution make a backup: Evolution Karmic amd64.tar.gz. Five minutes later I got curious and had Evolution try to restore from the backup that I'd just made. It told me to select a valid backup to restore. Something's really messed up here.

---

### Post by Minsky on 2009-11-05
It seems to me that Evolution is prone to throwing a wobbly with Karmic at the moment, earlier on in the day it insisted on passwords for all my mail accounts when I attempted to download my mail and wouldn't accept any of them. Just tried again and it was happy with them this time round. Why I had to type in passwords after using it for a week with no problems I don't know. Roll on the updates!

---

### Post by dcstar on 2009-11-05
> **Goodbytes said:**
> What's killing me about this is now that I've got my email and accounts running on the amd64 install and Everything's Fine(tm), I went ahead and had Evolution make a backup: Evolution Karmic amd64.tar.gz. Five minutes later I got curious and had Evolution try to restore from the backup that I'd just made. It told me to select a valid backup to restore. Something's really messed up here.

Be aware that there may still be the problem that 32-bit Evolution can only handle a max 2GB individual file size, if you have some files greater than that in your 64-bit archive it may stop a restore on a 32-bit platform.

---

### Post by mjones41 on 2009-11-18
Yes this problem is still killing me.  My Evolution backup is 6GB uncompressed and 4GB compressed.  9.10 still will not accept the file.  Even trying to extract the file with 9.10 I get an error message that the end of the file is missing.

But going back to a 9.04 install everything is fine, I can restore the backup, the very one that 9.10 will not load.

I can confirm that directory location, spaces and file names have no affect on the problem I am encountering.  I have 3 years of work emails I want to get loaded.  

Please help Evolution peeps.

Matt

---

### Post by cynodon on 2010-01-16
> **mjones41 said:**
> Yes this problem is still killing me.  My Evolution backup is 6GB uncompressed and 4GB compressed.  9.10 still will not accept the file.  Even trying to extract the file with 9.10 I get an error message that the end of the file is missing.

But going back to a 9.04 install everything is fine, I can restore the backup, the very one that 9.10 will not load.

I can confirm that directory location, spaces and file names have no affect on the problem I am encountering.  I have 3 years of work emails I want to get loaded.  

Please help Evolution peeps.

Matt
i had the same problem. in my case the evolution-backup.tar.gz was on a specific folder i use for all my backups...I just moved the evolution-backup.tar.gz to my Home folder and started the rocovery process after that and it worked....
good luck

---

### Post by snir on 2010-02-15
it seems that theres a bug here. when trying to restore from external ntfs drive he cant restore and when copiyng to the home folder it does....

---

