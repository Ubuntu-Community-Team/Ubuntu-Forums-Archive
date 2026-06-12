---
title: "Nautilus Deletes Files Without Warning"
date: 2010-11-14
forum: General Help
---

### Post by djrobthaman on 2010-11-14
Hi,

I've noticed since upgrading to Maverick that nautilus has become very buggy and crashes quite a bit (I've noticed it tends to happen during multiple file transfers but really it happens often and not only because of transfers).

While I've been able to tolerate this crashiness, today I came across a problem that is very distressing. If I have two files in a folder and I rename one so that it has the same filename as the other, nautilus does not display an error message. Instead what seems to happen is that it retains one file and deletes the other permanently (There seems to be nothing in the trash as far as I can tell).

Has anyone come across this error before? If you have, I'd really appreciate any advice on how to fix it. Thanks.

---

### Post by djrobthaman on 2010-11-14
I just did a bit of testing and it seems this error does not occur when I'm editing files that are local to my computer but the error continues to show itself while editing files on a writeable samba share

---

### Post by The Cog on 2010-11-14
Aha! Could it be something to do with upper/lower case handling? I suspect you can get the same issue locally if you use a FAT/NTFS filesystem where you try to create two files that only differ by case.

---

### Post by djrobthaman on 2010-11-14
I've actually done that before, and just tested it a while ago on a local ntfs formatted drive, and what happens is that it allows for both upper/lower case files to co-exist and linux can tell the the difference between the files perfectly. Windows, of course, has an odd problem where it lists both files correctly but reading from them is interesting.

Anyway, it doesn't look like it's a case sensitivity situation. It appears that the files are being renamed and are simply overwriting any other file that originally had that name.

I'm still searching online for any hint of this happening but so far nothing really. If you have any other suggestions though, I'd really appreciate them.

---

### Post by djrobthaman on 2010-11-14
Actually I've found a reference to a similar bug in debian but this dates back to Jan / May 2009. So I'm not sure what came of that. And, of course, I wasn't having this problem with ubuntu around that time so I don't know whether it's related.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=510564](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=510564)

---

