---
title: "why can't I rename a file on fat32 win usb hard drive"
date: 2012-03-29
forum: General Help
---

### Post by D_E_H0987 on 2012-03-29
I figure this is on here some place but I searched and kept getting stuff about setting the volume label, editing the partition table, etc. which wasn't exactly what I was looking into.

Anyway here is what happened as far as I can tell I ran into a strange setting on a downloaded file, for some reason I could not rename a file on a fat32 windows formated USB hard drive using the file manager in Ubuntu 11.10.  

It kept giving me this error "The item could not be renamed.  The name "wxyz0001.wmv" is already used in this folder. Please use a different name."

I even moved the file to a new empty directory I created, but it still had the same bug. Mind you it was the only file in the directory now.

I also copied the file to a new empty directory on the windows drive, still same problem.

Now when I copied the file to my Ubuntu hard drive I was able to change the name just fine.  

I was able to rename a different file on the drive just fine in Ubuntu.

I did try changing the file permissions on the file properties on the file on the windows drive using the Ubuntu file manager but that made no difference.

I would really like to know what I need to do so I can rename these kinds of files in the future with Ubuntu.

---

### Post by Vaphell on 2012-03-29
what kind of change have you tried to do? because when i experience something like that it's about upper- or lowercasing the name. FAT and NTFS are not really case sensitive (as in you can't have TEST.TXT, test.TXT and Test.txt in the same directory) and the new name is from the filesystem point of view the same. I agree it is buggy though and it should do it anyway (recognize that the file conflicts with itself and allow for update).
As a workaround i just add some char, confirm and then edit again to achieve the final form.

---

### Post by D_E_H0987 on 2012-03-29
> **Vaphell said:**
> what kind of change have you tried to do? because when i experience something like that it's about upper- or lowercasing the name. FAT and NTFS are not really case sensitive (as in you can't have TEST.TXT, test.TXT and Test.txt in the same directory) and the new name is from the filesystem point of view the same. I agree it is buggy though and it should do it anyway (recognize that the file conflicts with itself and allow for update).
As a workaround i just add some char, confirm and then edit again to achieve the final form.

I thank you for your reply.

I was gona mention you didn't read my post as I almost misread yours, but after re-reading your post again as I was figuring how to reply with out being to big a pain it dawned on me this was exactly what I was doing.

I was renaming a file that was out of order in a sequence as the letter case was different.

Thanks, you should get a medal for figuring out information I didn't think to include as I was thinking this was more like fixing a few question marks or other weird characters or weird properties in a windows file name.

And I have to ware a dunce cap for being an idiot and not trying other characters.

Its late or early depending on your point of view so that must be it, yea right, I'll probably do something just as stupid again latter.  Hell, Maybe even latter today.

Thanks again.

---

