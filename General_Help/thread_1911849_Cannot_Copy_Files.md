---
title: "Cannot Copy Files"
date: 2012-01-19
forum: General Help
---

### Post by jorpoveda on 2012-01-19
Hello, I hope I can find a solution for this very rare problem I have. I am trying to copy a file that has 6.6 GB but when it is copying to the USB Drive it stop and says that: "There was an error copying the file into /media/KINGSTON." and also "Error splicing file: File too large".

What can I do to solve this? Is there a solution?

Thank you.

---

### Post by kc1di on 2012-01-19
how much space to you have on the usb drive?

Sounds like your running out of room.

---

### Post by tersogar on 2012-01-19
> **jorpoveda said:**
> Hello, I hope I can find a solution for this very rare problem I have. I am trying to copy a file that has 6.6 GB but when it is copying to the USB Drive it stop and says that: "There was an error copying the file into /media/KINGSTON." and also "Error splicing file: File too large".

What can I do to solve this? Is there a solution?

Thank you.

What is the size and filesystem of the usb drive?

---

### Post by WorMzy on 2012-01-19
What filesystem does it use? It's common for USB drives to come with a FAT32 filesystem, which cannot support filesizes greater than 4GB.

[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

---

### Post by ubudog on 2012-01-19
Seems you're running out of space... could also be the filesystem as WorMzy said.

---

### Post by jorpoveda on 2012-01-19
> **WorMzy said:**
> What filesystem does it use? It's common for USB drives to come with a FAT32 filesystem, which cannot support filesizes greater than 4GB.

[http://support.microsoft.com/kb/314463](http://support.microsoft.com/kb/314463)

Yes indeed it is FAT32, and the file size is 6.6GB. I have to transfer the file to a Mac so how can I copy the file from Ubuntu and transfer it to the Mac?

---

### Post by WorMzy on 2012-01-19
Well, you could split the file into two parts using [split]("http://www.techiecorner.com/107/how-to-split-large-file-into-several-smaller-files-linux/"), copy the parts over to the USB stick, then onto the mac, then join them again using cat (the application, not an actual cat).

Or you could reformat the USB stick with a filesystem that supports larger file sizes (e.g. ntfs, ext4), then copy the big file.

Or you could burn the file to a CD (seems a bit wasteful).

Or you could upload the file to a file sharing website that the FBI hasn't ripped off the 'net yet.

It's up to you.

---

### Post by jorpoveda on 2012-01-19
> **WorMzy said:**
> Or you could reformat the USB stick with a filesystem that supports larger file sizes (e.g. ntfs, ext4), then copy the big file..

This is the way I did it, I went for a NTFS File System format and then copy to it the large file. Anyway thanks for the multiple solutions.

---

### Post by ubudog on 2012-01-19
If all fails, you could of course use Dropbox or something like that.

---

