---
title: "Invalid Encoding"
date: 2010-07-30
forum: General Help
---

### Post by skiptomailou on 2010-07-30
Hey all, I'm still a bit of a newbie. I'm having trouble with special characters, like Norwegian or French, in file names. Instead of the correct characters I get the boxes with question marks. I found this thread:

[http://ubuntuforums.org/showthread.php?t=1239904](http://ubuntuforums.org/showthread.php?t=1239904)

How or where would I add what's needed to fstab to fix this? I know how to open it. I'm just not sure where to add what that person did in that thread. Oh, and I have installed unifont as well. If it's needed I use Nautilus and my file system is ext3.

Even if you just have links to good places for someone new to Linux to get started I'd appreciate it. It all just seems overwhelming and a little intimidating. There's so much information out there. Some of it is over my head and some of it seems like it might be outdated. I can say I've had quite a few problems and this is only the second question I've had to ask. Thank you.

---

### Post by skiptomailou on 2010-07-30
After rereading that thread I felt I should clarify that the files are on my Ubuntu drive not my Windows drive. So, perhaps modifying fstab won't fix my problem?

---

### Post by skiptomailou on 2010-07-31
Ok, I tried this to fix the files I have:
```
convmv -r --notest -f windows-1255 -t UTF-8 *
```It looks like it took the invalid encoding part off of most the file names. Instead of adding the correct characters though, it did this "D&#8250;d" when it should be "Død". There are a few files that still have the black boxes and invalid encoding. The funny thing is I could see at least most of the correct characters in the terminal. This is just frustrating. I've searched all over. It seems like everybody else is having this problem with files on a separate FAT or NTFS partition.

I just had another thought. At one point I went through a how to for cleaning up unnecessary junk files somewhere on this forum. One of the steps is to install localepurge. Since I still don't really understand what I got rid of, obviously I shouldn't have done it. I already removed localepurge. Sorry, as I said I'm frustrated and just trying to give as much information as possible.

---

