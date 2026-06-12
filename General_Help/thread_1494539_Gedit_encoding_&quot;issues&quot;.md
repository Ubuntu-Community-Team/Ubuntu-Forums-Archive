---
title: "Gedit encoding &quot;issues&quot;"
date: 2010-05-27
forum: General Help
---

### Post by playcat on 2010-05-27
Hello,

This is probably a silly question, but it's regarding smt that I find as a quite annoyance.

When trying to open some files (in this example some c++ source code), I'm being informed by gedit that it cannot open the file since it cannot detect character encoding.

Now, nano or joe or vi open it in terminal with no problem, but I don't want to use that because I'm only using it for a paper I need to compose.

Is there a way to tell gedit simply to open the file without trying to guess anything. I'm totally happy if some characters are shown as dots, boxes, or some other signs.

Thanks,
Dan

---

### Post by playcat on 2010-05-27
Okay,

while my question still remains open, it appears that I was too quick to say that nano can open it OK. I think the actual problem is in my force shut-down of the computer last night, while this file was on ntfs partition :rolleyes:
Obviously, not a very good idea.

Cheers

---

### Post by dino99 on 2010-05-27
gedit often refuse for some reasons, use notepad, wordpad, ooo in case it refuse

---

### Post by dcstar on 2010-05-27
> **playcat said:**
> Okay,

while my question still remains open, it appears that I was too quick to say that nano can open it OK. I think the actual problem is in my force shut-down of the computer last night, while this file was on ntfs partition :rolleyes:
Obviously, not a very good idea.

Cheers

You cannot use Gedit on NTFS partitions because the backup file it creates by default uses an illegal character on that filesystem.

Use Linux tools on Linux filesystems, not foreign ones.

---

### Post by egalvan on 2010-05-27
> **dcstar said:**
> **You cannot use Gedit on NTFS partitions** because the backup file it creates by default uses an illegal character on that filesystem.


Well, someone should have told me that two years ago...
here I've been using gedit on NTFS to manage text files on my Hardy/XP dual-boot.
(But I also use mousepad. at times)

There are add-on packages for gedit that may help with this, but I don't have the info to hand.


I've NEVER encountered a problem with the ~ files....
but then I routinely erase them immediately after finishing the edits, so maybe that explains my lack of problems?


> Use Linux tools on Linux filesystems, not foreign ones.

At times one is forced (by circumstance) to use "foreign" stuff.
But Linux tools seem to do an admirable job anyway :)

---

### Post by StuartN on 2010-05-27
> **dcstar said:**
> You cannot use Gedit on NTFS partitions because the backup file it creates by default uses an illegal character on that filesystem.

Gedit correctly operates on an NTFS filesystem, creating a backup file~ if set to do so in Preferences->Editor. (Windows may later choke).

Failure to create the backup file prior to saving would not, in any case, prevent Gedit from opening the file, which is more likely due to file corruption in this case.

Try **iconv --list** for a list of encodings and then use iconv to translate the file into a useable format. hexdump, tr and sed will recover a difficult file.

---

