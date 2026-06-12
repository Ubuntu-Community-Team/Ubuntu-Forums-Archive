---
title: "File recovery."
date: 2011-08-01
forum: General Help
---

### Post by JamesBwoii on 2011-08-01
I was using a USB to boot Ubuntu but not install it. From Ubuntu I accidentally deleted by "TV" folder. Now I am trying to recover it using data recovery software, I have tried Easeus and currently trying Recuva, but I don't think it's working. Is this because Ubuntu deletes files in a different way to what the recovery software is looking for? If so, can I boot back into Ubuntu and use an Ubuntu recovery software and if so what would you recommend?

---

### Post by coffeecat on 2011-08-01
Is this TV folder on a NTFS partition? If you simply used the delete key and didn't delete the trash, the folder and contents may still be there in a hidden folder (hidden in Linux - but not in Windows) in the root of the filesystem.

If this is a NTFS partition and it's your Windows partition, boot into Windows, open "Computer" and then look in your C: drive (or D:/E:, whatever it is, if a separate partition). Look in the root of the filesystem for a folder called .Trash-1000 (with the live session, this may be .Trash-999). Note the leading dot which hides it in Linux but not in Windows. Have a look in there. Hopefully, your deleted folder and files will be in the files folder inside .Trash-1000/.Trash-999/.Trash-whatever.

There are some data recovery tools you can use from the Ubuntu live session, but let's see if your files are still there first.

---

### Post by JamesBwoii on 2011-08-01
> **coffeecat said:**
> Is this TV folder on a NTFS partition? If you simply used the delete key and didn't delete the trash, the folder and contents may still be there in a hidden folder (hidden in Linux - but not in Windows) in the root of the filesystem.

If this is a NTFS partition and it's your Windows partition, boot into Windows, open "Computer" and then look in your C: drive (or D:/E:, whatever it is, if a separate partition). Look in the root of the filesystem for a folder called .Trash-1000 (with the live session, this may be .Trash-999). Note the leading dot which hides it in Linux but not in Windows. Have a look in there. Hopefully, your deleted folder and files will be in the files folder inside .Trash-1000/.Trash-999/.Trash-whatever.

There are some data recovery tools you can use from the Ubuntu live session, but let's see if your files are still there first.

Yes this TV folder is an NTFS partiton.

In the .trash-999 folder, there are 3 files;
expunged
files
info

All of which are empty.

---

### Post by blind2314 on 2011-08-01
> **JamesBwoii said:**
> Yes this TV folder is an NTFS partiton.
 
In the .trash-999 folder, there are 3 files;
expunged
files
info
 
All of which are empty.
 
If these files are on the root partition of your windows install (i.e., where your WINDOWS folder resides) then I would refrain from booting as much as possible. Windows, as well as other OS's, likes to write temp files and use swap space on its root partition. This can ruin any chance of getting your data back, provided it's still there now.
 
If not, can you see the files from windows?

---

### Post by coffeecat on 2011-08-01
> **JamesBwoii said:**
> 
All of which are empty.

I'm sorry to hear that. I don't know whether the live system empties the trash automatically when you power down - I would hope not - but for whatever reason the trash was emptied. Just FYI, Windows uses a similar system. Use the delete key and the "deleted files" are moved to the $RECYCLE folder (which is hidden in Windows but not in Linux) and only physically deleted when you empty the recycle bin.

Data recovery software:

There are some data recovery utilities you can use from the live Ubuntu session. See here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Ignore the testdisk part, because testdisk is for recovering lost partitions, not lost files. But you have to install testdisk to get photorec. There are also some other data recovery utilities mentioned.

---

### Post by JamesBwoii on 2011-08-01
> **coffeecat said:**
> I'm sorry to hear that. I don't know whether the live system empties the trash automatically when you power down - I would hope not - but for whatever reason the trash was emptied. Just FYI, Windows uses a similar system. Use the delete key and the "deleted files" are moved to the $RECYCLE folder (which is hidden in Windows but not in Linux) and only physically deleted when you empty the recycle bin.

Data recovery software:

There are some data recovery utilities you can use from the live Ubuntu session. See here:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Ignore the testdisk part, because testdisk is for recovering lost partitions, not lost files. But you have to install testdisk to get photorec. There are also some other data recovery utilities mentioned.

I'll let the Recuva file recovery finish and see what it finds, if nothing, then I'll have to try it in Ubuntu. 

Thanks for all the help.

---

### Post by JamesBwoii on 2011-08-01
> **blind2314 said:**
> If these files are on the root partition of your windows install (i.e., where your WINDOWS folder resides) then I would refrain from booting as much as possible. Windows, as well as other OS's, likes to write temp files and use swap space on its root partition. This can ruin any chance of getting your data back, provided it's still there now.
 
If not, can you see the files from windows?

Would rebooting matter that much, since the files were stored on a 2tb hard drive that is used for storage only, no OS files. If they were to go to the C:\ drive there wouldn't have been enough room seeing as that drive is only 500gb and the TV folder was 600gb.

---

### Post by JamesBwoii on 2011-08-01
Recuva found nothing apart from really old files. I'll try one of the Ubuntu file recoveries in a bit. If that doesn't work are they gone?

---

### Post by coffeecat on 2011-08-01
> **JamesBwoii said:**
> If that doesn't work are they gone?

Well, yes, I guess so. But I'd be surprised if they're totally gone. That would normally only happen if they were overwritten, and with a 2TB drive you'd have to do a lot of new writing to the drive to overwrite them all.

---

### Post by JamesBwoii on 2011-08-01
> **coffeecat said:**
> Well, yes, I guess so. But I'd be surprised if they're totally gone. That would normally only happen if they were overwritten, and with a 2TB drive you'd have to do a lot of new writing to the drive to overwrite them all.

I haven't touched the drive since the data was lost. I'll try a file recovery software in Ubuntu now and see what happens then. If that doesn't work then I don't know what to do, I can't understand how it's gone since I have recovered formatted drives before.

---

### Post by JamesBwoii on 2011-08-01
I've hit a few problems using PhotoRec. The first being that when selecting what files I want to look for there is no option for .avi or .mkv which seems a little odd. Secondly I can't choose anyone to restore them to other than Ubuntu which doesn't have enough space. Also, seeing as it's unwise to recover them to the drive they were lost from, I don't have room to recover the whole 600gb, so I want to choose around 300gb to recover which doesn't seem possible.

---

