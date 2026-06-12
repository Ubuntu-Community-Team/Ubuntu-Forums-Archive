---
title: "Deja Dup - restoring from S3 to a second PC"
date: 2010-09-05
forum: General Help
---

### Post by RogerD on 2010-09-05
Hi

I've been using deja dup to backup key files to Amazon's S3 service - easy to use, and, as a test, I've successfully restored the files onto my PC's desktop.

However, the real point of backing-up off-site, as with S3, is to save my key files in the event of a total failure, e.g. a hard disk crash on my PC. To allow for this eventuality, I have two PCs, but when I tried restoring my previously backed-up files to my second spare PC, I couldn't get it to work. I'm not sure why, but deja dup seemed unable to cope with the situation where there had been no prior backup from the PC I was trying to restore to.

It's all very frustrating, deja dup is a great piece of software, but needs wider support and more extensive documentation.

Using s3fox, I've managed to transfer the previously backed up files onto the desktop of my second PC, but this doesn't seem to help, as I can't get deja dup to restore from this desktop folder - so near, yet so far away.

Has anyone managed to get deja dup to backup from S3 to a second PC, and, if so, how is it done?

Regards

Roger D

---

### Post by RogerD on 2010-09-12
Hi

Seems a bit silly to be replying to my own message, but with the help of Mike Terry, the developer of Deja Dup, I've now got to the bottom of my little problem.

Deja Dup is perfectly capable of restoring from a second PC, you just have to be careful to ensure that the entry in the 'Folder' window, in 'Deja Dup Preeferences' exactly matches the name of the folder being used for backups on S3. If you're in any doubts, S£fox, a very useful Firefox add-on, is a great way of seeing what's going on with your S3 files/folders. Once you've got 'Deja Dup Preferences' filled in correctly, everything works a treat.

Hopefully this will be of help to others wishing to manage their off-site backup via S3 and Deja Dup.

Roger D

---

