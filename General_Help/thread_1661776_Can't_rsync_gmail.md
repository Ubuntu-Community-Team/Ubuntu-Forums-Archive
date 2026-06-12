---
title: "Can't rsync gmail"
date: 2011-01-07
forum: General Help
---

### Post by xtheunknown0 on 2011-01-07
I'd like some help with rsync, please.

When I run rsync --recursive --times --perms --links --delete --exclude-from='Documents/exclude.txt' ./ /media/myusb/

where Documents/exclude.txt is

- /Downloads/
- /Desktop/books/

the files in those directories are still copied onto my USB.

Why?

And...
I used fetchmail to download all my gmail emails. When I run rsync -ar --exclude-from='/home/xtheunknown0/Documents/exclude.txt' ./ /media/myusb/ I get the first image at [https://sites.google.com/site/xtheunknown0/linux-1](https://sites.google.com/site/xtheunknown0/linux-1)

Why?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2011-01-08
bump

---

### Post by xtheunknown0 on 2011-01-09
bump

---

### Post by papibe on 2011-01-11
It believe that the --exclude-from= points to a file with patterns, not directories. So try changing the paths for something like this:
```
Downloads/*
Desktop/books/*
```
Good Luck!

---

### Post by xtheunknown0 on 2011-01-15
bumping 2nd question

---

### Post by papibe on 2011-01-15
I checked the pic, but since the lines are trim I'm not sure about the message error. Could you paste a few complete lines?

What kind of file system is the USB? Is it NTFS? FAT?

Regards.

---

### Post by xtheunknown0 on 2011-01-16
> **papibe said:**
> I checked the pic, but since the lines are trim I'm not sure about the message error. Could you paste a few complete lines?

What kind of file system is the USB? Is it NTFS? FAT?

The USB has the FAT file system. The pic has been replaced with the last (and relevant) part of the log file.

TIA,
xtheunknown0

---

### Post by papibe on 2011-01-16
It seems the files have filenames with characters that are not allowed on a FAT (or NTFS) file system, like the colon ( : ).

Are you using the USB like just like "transportation" or the files are going to end on a Windows system?

Regards.

---

### Post by xtheunknown0 on 2011-01-18
> **papibe said:**
> It seems the files have filenames with characters that are not allowed on a FAT (or NTFS) file system, like the colon ( : ).

Are you using the USB like just like "transportation" or the files are going to end on a Windows system?...

I'm intending for it to be used by Ubuntu only, but if Ubuntu becomes unbootable or is damaged I should still be able to edit a few files on Windows.

xtheunknown0

---

### Post by xtheunknown0 on 2011-01-18
> **papibe said:**
> It seems the files have filenames with characters that are not allowed on a FAT (or NTFS) file system, like the colon ( : ).

Are you using the USB like just like "transportation" or the files are going to end on a Windows system?...

I'm intending for it to be used by Ubuntu only, but if Ubuntu becomes unbootable or is damaged I should still be able to edit a few files on Windows.

xtheunknown0

---

### Post by xtheunknown0 on 2011-01-20
> **papibe said:**
> It seems the files have filenames with characters that are not allowed on a FAT (or NTFS) file system, like the colon ( : ).

Are you using the USB like just like "transportation" or the files are going to end on a Windows system?

Regards.

What effect would there be if I were to replace/remove those characters "not allowed"?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2011-01-21
bump

---

