---
title: "Recovering Deleted Files of a Specific Name"
date: 2010-03-21
forum: General Help
---

### Post by chome4 on 2010-03-21
I need to get back two avi movie files but I've deleted hundreds and any recovery might try and drop them back on my small hard disk and overwhelm it! I know the files include the word 'Archer' but I'm using Formost, which is very easy to use, but it doesn't seem to allow for the searching of specific files by name. I can recover by type ie, avi, jpeg, pdf.....

Are there any recovery programs that will list files in a table so I can pick the ones I want to recover or do a search in Terminal for my 'Archer' files?

---

### Post by pandion on 2010-03-29
Ubuntu has a Trash bin (like Windows Recycle Bin). If you didn't empty it, the files may be in Trash.

I'm assuming since your system is running Ubuntu that your drive is formatted as ext3. If that's correct, it's my understanding that deleting a file clears the inode, which destroys the record of the filename as well as the pointers and references to the file. This is why you can't easily search for it by filename using a tool like photorec (data carver). Photorec searches for file types based on their file signatures (not sure if it uses both header and footer signatures), which is how if recovers them.

File Formats Recovered By PhotoRec: [http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

The next question is, have you used or mounted the drive as read-write since the files were deleted? If you have this decreases the chance of recovery.

What's the capacity of the drive, and do you have an external drive or flash drive available that might be large enough to hold the avi files? Flash Drives are pretty cheap now, so if it would fit on one it would be a good option. In order to recover the files, you need a separate storage device, since the drive they were deleted from should only be mounted as read-only to prevent them from being overwritten.

---

