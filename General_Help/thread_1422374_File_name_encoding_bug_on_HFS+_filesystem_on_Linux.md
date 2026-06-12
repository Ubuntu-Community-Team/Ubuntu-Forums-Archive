---
title: "File name encoding bug on HFS+ filesystem on Linux??"
date: 2010-03-05
forum: General Help
---

### Post by dodamn on 2010-03-05
OS
Linux - Ubuntu Karmic 64bit, 2.6.31-19-generic
Mac OS - Mac OS X Snow Leopard 10.6.2 32bit.

Steps to reprocude
1. Prepare HFS+ filesystem.
    - Be sure the HFS+ fs does not have journaling.
    - It is not important whether the HFS+ fs is made on Linux or Mac OS.
    - It is not important whether the HFS+ fs is case-sensitive or case-insensitive.
2. Make any Korean-named file in HFS+ fs on Linux.
    - For example, run "touch '&#54620;'" on terminal.
    - '&#54620;' is D55C in Unicode.
3. Run 'ls' on Mac OS.
4. You will see error "ls: cannot access &#54620;: No such file or directory".

* If you make any Korean-named file in HFS+ fs on Mac OS and run 'ls' on Linux, you will same error.
* I tested for some umlaut characters. But I could not see any error.

I know that HFS+ stores file name with decomposed Unicode form. I wanted to see whether file name was really decomposed or not. So I used hfsdebug-lite on Mac OS. It is debugger for HFS+. It shows real unicode value of the file name. You can find it from [http://osxbook.com/software/hfsdebug/man.html](http://osxbook.com/software/hfsdebug/man.html).

For the file '&#54620;' made on Linux, hfsdebug-lite shows %D55C. And for the file '&#54620;' made on Mac OS, hfsdebug-lite shows %1112%1161%11AB.

'&#54620;' is composed with 3 syllabics - '&#12622;', '&#12623;' and '&#12596;'. '&#12622;' is 1112 in Unicode. '&#12623;' is 1161. And '&#12596;' is 11AB. Therefore, file name '&#54620;' should be presented with %1112%1161%11AB on HFS+ fs. Because it is dec
omposed form.

But for the file name which consists of umlaute characters, they are decomposed properly regardless that
they are made on Linux or Mac OS.

Maybe Linux kernel stores Korean file name as precomposed form for HFS+ fs. I think it should be fixed.

Does anybody know this problem?

---

### Post by dcstar on 2010-03-06
> **dodamn said:**
> 
.......
Maybe Linux kernel stores Korean file name as precomposed form for HFS+ fs. I think it should be fixed.
.......

Do you have all the various Korean language files installed on your Linux system?

---

### Post by dodamn on 2010-03-06
> **dcstar said:**
> Do you have all the various Korean language files installed on your Linux system?

No. I just tested only '&#54620;'. It is just one test case.
In Linux kernel source code at least 2.6.33, I can't find any decomposition routine for Korean(Hangul) file name.

---

### Post by acmc on 2010-05-21
I'm encountering the same issue! Fuuun.

---

### Post by bkadoctaj on 2010-09-23
Does anyone have an update/resolution to this issue?  :)

---

### Post by bkadoctaj on 2010-12-26
The problem is still here, and very frustrating.  This seems to be an issue with any Linux distribution and Mac OS X.  Any file created with Korean characters in its name in either Linux or Mac OS X on an HFS+ partition is unreadable by the other.

Overall, this might not be a big issue, except for two things:

1.) Some users of both Linux and Mac OS X are Korean.  This has got to be a pure disaster for them, only resolvable by actually using another type of filesystem for a shared partition than HFS+, which is for most sharing purposes the best around.

2.) Some users have audio and video files with Korean characters in their names, and this means that while files will appear and play in media players in the operating system that originated the files, the media players in the other OS can't even touch them.  This is my issue.  I have the files read perfectly in iTunes (Mac OS X) but unusable by Pana/Rhythmbox/Banshee/younameit (Linux Mint/Arch Linux/etc.).

In essence the only solutions are to use another type of partition (NTFS or FAT) or to have two copies of your files.  Neither are cool solutions.  :(

---

